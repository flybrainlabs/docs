# Social community system

## Purpose and release scope

The Social module connects an authenticated Solana wallet to a verified public X
identity, records community contributions and derives a reproducible ranking.
It uses the existing Wallet Standard browser connection and SIWS authentication;
it does not introduce another wallet, session store or token issuer.

The public route is `/social/`. The administration route is `/social/admin/`.
Five sections appear in order: Community Airdrop Allocation, My Community,
Community Tasks, Community Leaderboard and Activity. Visitors can read the
budget, published rules and real leaderboard without connecting a wallet.
Authenticated participants can generate challenges, submit public evidence,
choose public username visibility and read their private contribution history.
A contribution link exposes sanitized public point sources, never session
identifiers, private reasons, risk flags or administrator evidence.

## Budget and asset identity

| Budget | FBW | Atoms at 8 decimals |
|---|---:|---:|
| Community & Ecosystem Pool | 31,183,323 | 3118332300000000 |
| Community airdrop budget | 25,000,000 | 2500000000000000 |
| Other ecosystem uses | 6,183,323 | 618332300000000 |

The airdrop budget is approximately 80.17% **of the community pool**. It is
neither additional supply nor 80% of total token supply. The canonical new
budget file is `config/community-allocation-v1.json`; initialization checks
it against the frozen `web/data/economic-policy-v2.json`. Historical policy bytes
and their old symbol remain unchanged. The current project is flybrainlabs;
the existing token is flybrainwork, displayed as FBW on Solana Devnet.

A finalized, read-only chain inspection before development confirmed the
community vault balance and unallocated atoms were both 3118332300000000.
The mint had no remaining issuance authority. This does not create a dedicated
airdrop vault or imply that the budget is locked on chain. Approved community
reservations are internal bookkeeping. Operators must reconcile future uses of
the same community pool before authorizing any asset execution.

Community points are not tokens. There is no fixed conversion, distribution
calendar, guaranteed personal amount or automatic claim. The service has no
payment signer, relayer loop, mint instruction or transfer endpoint.

## Wallet authentication

The existing mining gateway issues a five-minute SIWS nonce containing domain,
wallet, URI, chain/genesis identity, program, issuance and expiration times.
Actual Ed25519 control is checked server-side. Login requires no chain fee.
The resulting eight-hour session lives in `mining_v3_sessions`. Bearer tokens
and CSRF secrets are stored only as hashes in the database. Social reads these
same sessions through `WalletMiningService.authenticate`.

Each private read validates an allowed Origin and the session. Mutations also
require `X-Mining-CSRF` and JSON content type. The server always takes the wallet
from the authenticated session. A submitted wallet field cannot change the
participant. Explicit disconnect, wallet changes and stale response guards reuse
the existing WalletSession behavior. Browser local storage remembers only the
selected provider/account; matching unexpired login is retained in the same tab.

Unbinding and sensitive administration require a sign-in within the last five
minutes. The client signs in again when required. Administration is authorized
by the runtime `communityAdminWallets` allowlist; when absent it defaults to the
already configured project wallet. A public project address is not a credential.
A normal wallet cannot access administration through a hidden button or direct API.

## X public challenge

The initial enabled task is `connect_x_identity_v1`, worth 100 community points.
The reward/revision is captured when each challenge is admitted. Later task
configuration changes do not alter that challenge or historical completions.

1. An authenticated user requests a challenge.
2. The backend generates 16 random bytes (128 bits), rendered as
   `FBW-VERIFY-` followed by 32 hexadecimal characters.
3. Challenge ID, code hash, wallet, session hash, expiry and reward revision are
   committed. There is one active challenge per wallet; regeneration invalidates
   its predecessor, including any in-progress provider result.
4. The user chooses neutral verification wording or edits an introduction.
   Neither wording earns extra points. The complete code must remain in the
   original post body. X Web Intent opens the user's own confirmation screen;
   the application never sends an X post.
5. The user submits an HTTPS `x.com` or `twitter.com` status URL within 30 minutes.
6. The backend requests evidence from the fixed official oEmbed endpoint.
7. Verified binding, completion, points, summary and verification audit commit
   together in one `BEGIN IMMEDIATE` transaction.

Challenges are wallet/session bound, one-use and limited to five creation
requests per wallet per five minutes. Each challenge has at most five verification
attempts; up to four provider requests run in a process. Nginx also applies the
existing shared request limit. Invalid evidence never earns points.

## oEmbed evidence and limitations

`XPublicVerificationProvider` fixes its outbound destination to
`https://publish.x.com/oembed`, using `url`, `omit_script=true` and
`hide_thread=true`. It rejects redirects, limits the response to 128 KiB and uses
an eight-second timeout. The submitted URL is parsed, not fetched directly.
Credentials, non-HTTPS schemes, arbitrary hosts and malformed status IDs fail.

`parse5` parses inert HTML. The provider requires a single `twitter-tweet`
blockquote with one original paragraph. The authoritative `author_url` must be
an X/Twitter profile; the footer must identify the same status ID and author.
Only original text and permitted paragraph markup contribute to the challenge.
Links, attributes, image descriptions, scripts, display names and nested quotes
cannot establish control. The code is matched as a complete token.

The saved verification level is `challenge_verified`, not OAuth. oEmbed does
not provide a reliable stable numeric identity; `x_user_id` stays NULL. Display
names never define uniqueness. Normalized usernames and status IDs remain unique
even after unbinding, preventing reuse of the known first contribution.
Username changes/reassignments remain an external identity limitation. The module
cannot prove that two newly named accounts are not the same person.

Unavailable, truncated or unverifiable evidence becomes a durable `needs_review`
record. Refresh recovers its state. A 30-second lease prevents duplicate work;
a stale lease is recoverable after process restart. Administrators must inspect
the actual original public post/author and supply body evidence and a review
reason. Review can approve atomically or reject with an audit. Neither a copied
code nor the username in a user-supplied URL is enough. Expired challenges and
expired original SIWS sessions require a new participant challenge.

Official public endpoint availability is a deployment acceptance item. Live
endpoint probes and fixture-based evidence tests must be reported separately.
Never relabel a fixture as a successful live X identity verification.

## Additive database migration

`config/social-community-v1.sql` is migration version 1. It is applied inside a
transaction and recorded with its SHA-256 in `social_schema_migrations`. A changed
checksum for an already applied version fails startup. Additional releases must
use a new migration version rather than editing deployed migration bytes.

The existing SQLite database/WAL and financial/scientific tables remain intact.
The community process uses a separate SQLite connection with foreign keys, WAL
and a ten-second busy timeout. It shares sessions; it does not call financial
admission initialization or start a relayer.

| Tables | Responsibility |
|---|---|
| `social_tasks` | Versioned task configuration; only installed verifiers enable |
| `social_x_challenges` | Scoped nonce, expiry, lease, attempt count, review state |
| `social_x_bindings` | Known identity and post uniqueness; retained unbinding |
| `social_task_completions` | One-time task completion and admitted reward |
| `community_profiles` | Trigger-maintained points/count, tie time, privacy/review |
| `community_points_ledger` | Append-only contribution and adjustment history |
| `social_verification_audit` | Immutable evidence decisions and hashes |
| `community_admin_audit` | Immutable actor, reason, operation key and result |
| `community_leaderboard_snapshots` / entries | Frozen ranking, cutoff, rules, hash |
| `community_distribution_rules` | Immutable rule versions and publication state |
| `community_airdrop_allocations` / entries | Immutable integer candidate amounts |
| `community_budget_ledger` | Append-only reservation and cancellation releases |

Unique constraints enforce wallet/task, known identity, post, operation key and
snapshot/rules combination. Triggers prohibit edits/deletion of point ledgers,
completions, audits and frozen content. Point writes atomically update the
summary; underflow/overflow rolls back the operation. Administration never edits
an old point record: corrections append a signed-in actor/reason adjustment.

## Ranking and snapshots

Public ranking considers normal profiles with positive effective community
points, ordered by points descending, time those points were reached ascending,
then stable wallet address. Mining throughput, token balance and stake are not
ranking inputs. Indexed summaries serve Top 100 and paginated reads. The server
computes the current wallet's independent rank even outside Top 100.

Snapshots recompute ledger totals up to a selected UTC cutoff, record review
eligibility as of creation, and store complete deterministic entries. A review
flag is explicitly visible to administrators and excludes a profile from live
ranking. It does not silently delete points. Public rules explain this treatment.
Frozen snapshot entry/metadata hashes are checked before export or allocation.
The current implementation caps a snapshot at 100,000 wallets, requiring an
operator review above that capacity. Pagination is a live view: positions may
change between requests when new contributions arrive. Frozen exports give
reproducible rankings at a cutoff.

Approval does not overwrite a snapshot. Superseding preserves its contents and
records an audit; an approved allocation must first be cancelled. Corrections
require a new snapshot and published rule version, preserving the old evidence.

## Allocation engine and administration

The administration UI provides task creation/configuration (new verifiers stay
paused), manual X review, wallet lookup, point adjustments, review flags, snapshot
creation/approval/supersession, immutable rule creation/publication, candidate
allocation, approval/cancellation, CSV/JSON export and recent audit records.

The installed allocation algorithm is `proportional_points_largest_remainder_v1`:

- Filter the frozen snapshot by its eligible status and the rule's minimum points.
- Compute each share as `budgetAtoms * points / eligiblePoints` using BigInt.
- Distribute remaining atoms by largest remainder, then snapshot rank.
- Hash the snapshot hash, rule hash, exact budget and ordered output entries.

The algorithm is deterministic for the same frozen inputs. A candidate has no
budget reservation. Approval requires an approved unsuperseded snapshot, published
rules, no current wallet review flags and sufficient remaining budget. Approved
unexecuted allocations count against the 25M cap. An idempotency key and unique
snapshot/rule constraint prevent double preparation/reservation. Cancellation
appends a release; old allocation bytes remain readable. Exported amounts are
strings in atoms, not floating-point token calculations.

This is distribution **preparation**. The service cannot execute exported rows.
Future execution needs published cutoff/eligibility/calculation/claim terms,
confirmed asset/program/precision/balances, explicit authorization, independent
approvals or multisig, simulation, recipient validation, durable execution keys,
finalized signatures and reconciliation of unknown outcomes. No private signing
material is stored in Social tables.

## APIs

Public GET: `/api/social/tasks`, `/api/social/leaderboard`,
`/api/social/contributions/{wallet}`, `/api/community/airdrop/allocation`,
`/api/community/rules`, `/api/social/health`.

Authenticated GET: `/api/social/profile`, `/api/social/x/challenge`,
`/api/social/x/binding`, `/api/social/leaderboard/me`,
`/api/social/points/history`.

Authenticated POST: `/api/social/x/challenge`, `/api/social/x/verify`,
`/api/social/x/unbind`, `/api/social/profile/visibility`.

Administrator GET: `/api/social/admin`, `/api/social/admin/users?wallet=...`,
`/api/social/admin/snapshots/{id}/export?format=json|csv`,
`/api/social/admin/allocations/{id}/export?format=json|csv`.

Administrator POST under `/api/social/admin/`: `tasks/update`, `points/adjust`,
`users/review-status`, `x/review`, `x/reject`, `snapshots/create`,
`snapshots/approve`, `snapshots/supersede`, `rules/create`, `rules/publish`,
`allocations/create`, `allocations/approve`, `allocations/cancel`.

Use `requestId` (16–80 safe characters) and a meaningful reason for administrator
writes. Retry the same payload/key after an unknown response; changing intent
requires a new key. Public point history uses `before` sequence cursors; ranking
uses `offset` and a maximum `limit` of 100. Private responses are `no-store`.
Errors distinguish invalid/expired challenge, body mismatch, unavailable post,
unverifiable author, identity conflict, pending review, rate limits, permission,
approval prerequisites and budget/integrity failure.

## Configuration and deployment

No X password, cookie or OAuth token is required. Community configuration uses
the existing private runtime JSON (database, project wallet, allowed origins,
cluster and mint). Optional `communityAdminWallets` contains public authorized
wallet addresses. No new secret environment variable is required. The canonical
pool/airdrop/other budget atoms are in the public allocation JSON; they are checked
against frozen economic policy, not accepted from browser input.

1. Assemble the authenticated component release and run backend/type/browser tests.
2. Back up the current SQLite database through its online backup API; verify
   integrity, original table counts and private runtime/config hashes.
3. Install only Social modules, additive migration, public budget, parser
   dependencies and the new systemd/nginx files. Preserve the existing services.
4. Start `flybrainlabs-community.service` on loopback 8791. Startup applies the
   additive transaction. The financial gateway remains on 8789.
5. Proxy `/api/social/` and `/api/community/` to 8791 with request limits,
   bounded bodies and no caching. Verify nginx before reloading.
6. Verify the migrated checksum, integrity, original counts, real empty public
   leaderboard, session/role failures and live oEmbed behavior.
7. Deploy the scoped website release with verified backup and old/new hashes.
8. Verify public HTTP assets, mobile/desktop rendering and release pins; publish
   English component commits and an authenticated independent checkout.

Rollback stops the new service, removes its nginx include and restores changed
public modules from the verified backup. Leave additive tables and real new
contribution data intact. Restore a database backup only after stopping every
writer and reconciling all subsequent business writes; blindly restoring an old
database would erase legitimate financial/scientific/community activity.

## Test evidence and remaining acceptance

The automated database suite uses real SQLite/WAL and actual scripted Ed25519
SIWS verification. It covers parser failures, nonce scope/expiry/regeneration,
atomic completion, concurrent replay, historical identity reuse, provider review,
transaction failure, points/ranking, authorization/CSRF, immutable snapshots,
exact atom allocations, approved reservation cap, restart and no transfer route.
The browser suite uses actual Chromium against an isolated backend/database and
a scripted Wallet Standard signer. It tests page flow, refresh, privacy, reviews,
rank/activity, administrator protections/exports and responsive layouts.

The final release acceptance record reports exact counts and deployment results.
These tests do not certify an actual wallet extension confirmation, physical
Android/GPU behavior, independent community operators, official OAuth or live
human X ownership. No fixture users or fake rankings are installed in production.

## Future OAuth upgrade

Add an official X OAuth adapter with state/PKCE and approved app callback/origin
configuration. Obtain a trusted numeric user ID and enforce uniqueness. Upgrade
an existing binding only after wallet control plus matching official X control,
with audited conflict handling. Preserve first-task reward history and immutable
completion/ledger records. Do not infer numeric IDs from usernames, automatically
transfer disputed identities or reward likes/follows/reposts. New contribution
verifiers need separately published evidence, scoring and moderation rules.


## Published acceptance: 2026-10-13

Release `social-community-20261013-v1` is live at `/social/` and `/social/admin/`.
Schema V1 checksum is
`829fb58a2281be20607175790734269f18343c895adef3f57010000ccf4a7c6a`.
The online backup and migration integrity check passed; original business counts
and private runtime hash are unchanged. Initial point/profile rows and approved
reservations were zero, reflecting the real database rather than demo users.
The server uses free loopback 8791 after verifying that the retained authority
already owns 8790. Startup policy bytes were matched to the existing public HTTP
policy before installation; the frozen source was not rewritten.

Acceptance passed 45 backend checks, 31 isolated Chromium checks, 18 read-only
public Chromium checks, 24 native library tests, eight export tests, opt-in new
module type checks, syntax lint and browser bundling. Scoped deployment verified
78 objects; public HTTP verified all 70 changed uncompressed objects. The public
handbook now has 26 guides, eight categories, 15,177 words and eight diagram
designs. Official X oEmbed returned HTTP 200 without redirect for a historical
public-post environment probe; this is not a real human challenge acceptance.
Actual extension confirmation, physical devices and official OAuth remain open.
No token transaction, production fixture user or new scientific reward task was
created. Allocation exports and approvals remain preparation scope.

Full structured evidence is in `docs/SOCIAL_COMMUNITY_ACCEPTANCE.json`.
