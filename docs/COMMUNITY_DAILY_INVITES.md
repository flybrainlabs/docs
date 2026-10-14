# Community daily contributions and invitations

Release: `community-daily-invites-20261014-v1`.

## Rules

| Contribution | Points | Frequency and prerequisite |
|---|---:|---|
| Unique X identity verification | 10 | Once per wallet and known X identity |
| Wallet check-in | 1 | Once per UTC day, authenticated wallet |
| Original daily X post | 1 | At most three per UTC day; active bound author |
| Verified invited registration | 10 to inviter | One award per new invitee; no inviter count cap |

Days reset at 00:00 UTC. Daily codes expire after 30 minutes or at that boundary,
whichever comes first. Each rewarded post needs its own 128-bit original-body
code and a new original X post. The server checks the bound author, snowflake
timestamp, current login, code, period, previously used post and remaining slots.
Official public oEmbed verification and authorized manual evidence review reuse
the existing identity-verification flow. Provider failure yields durable review,
never an assumed point reward.

## Registration and referral attribution

Opening `/social/?ref=<code>` retains a public invitation code in the current
tab. After real Wallet Standard connection and signed login, the client calls
`POST /api/social/register` before loading its private profile or starting a
task. The first successful community registration fixes attribution. An invalid
code does not consume registration. Existing participants and migrated wallets
cannot be relabeled as invited users. Generating or visiting a link gives no
points. Known identity uniqueness prevents a previously rewarded X identity from
qualifying another wallet.

The inviter's 10-point entry and referral receipt commit in the same transaction
as the invitee's identity binding, 10-point entry and completion. A failure rolls
back every record. Unique invitee and completion keys prevent repeated rewards;
there is no per-inviter count cap. The private invitation panel reads actual
registered and verified counts and total earned invitation points. Links are
stable and generated only for authenticated participants.

## Public presentation

The desktop leaderboard occupies the right column. Narrow screens use a single
column. Ranking rows and API payloads show the wallet at its original length
with exactly eight middle characters replaced by asterisks. They include neither
full wallet addresses nor X usernames. The wallet-copy action and public X
username setting are removed. Own-wallet and X binding details remain available
inside the authenticated profile. The requested allocation disclaimer is removed
from the Social page and its bilingual guide.

## Additive migration and retained records

`config/social-community-v1.sql` stays byte-for-byte unchanged. The new
`config/social-community-v2.sql` is a separately hashed transaction recorded in
`social_schema_migrations`. It adds repeat rules, immutable daily completions,
global post-use receipts, daily challenges, fixed registrations, invitation links
and immutable referral rewards. Existing ledger, binding, completion, snapshot,
allocation and budget records are retained. Existing earned totals are preserved.
Uncompleted identity challenges switch to the new 10-point rule; public username
visibility is disabled. Old task schema identifiers remain compatibility inputs.

Repeated completions and referral points use the existing append-only points
ledger. Daily counters have indexed wallet/task/period keys and unique slot keys.
Complete transaction checks protect concurrent last-slot submissions. Frozen
snapshots count both the historical one-time and new daily task completions.

## Deployment and verification

`infra/tools/upgrade_community_v2.sh` accepts only the reviewed public upload and
checks expected installed hashes. It saves existing sources and a coherent online
SQLite backup, restarts only the community process and verifies migration hashes,
database integrity and exact historical community rows. Private runtime settings
remain unchanged; scientific and financial services keep running.

The static builder applies only community presentation, SDK transport and
bilingual guide changes to an independent complete export. It checks retained
wallet, RPC, grant, WASM, model, documentation engine and atlas hashes before a
scoped backed-up deployment. Source publication uses existing owning repositories
and normal fast forwards with updated infrastructure pins.

Run from the assembled workspace:

```sh
node tests/social_community.mjs
node tests/social_daily_invites.mjs
npm run typecheck:community
npm run lint:community
python3 tests/social_browser.py --release /path/to/export --report /private/local.json
python3 tests/social_public.py --site https://flybrain.work --report /private/public.json
```

Authentication tests use isolated Wallet Standard providers with actual Ed25519
signatures and SQLite transactions. X evidence is isolated public-evidence fixture
data. Public acceptance creates no participants or posts and performs no point
mutations. Actual extension-wallet confirmation, live human X evidence and
physical-device acceptance require their own evidence.

## Rollback and the earlier mining issue

Retain the coherent backup and append-only records. Do not replace the database
with an older backup after legitimate writes. Reconcile or roll forward an
application mismatch; an older UI cannot correctly operate repeat tasks or new
invitation endpoints. All existing allocation authorities and token execution
boundaries remain unchanged.

The wallet SDK, RPC configuration and financial/scientific execution assets are
retained. This community release does not activate a private RPC provider or
claim to resolve the earlier mining RPC, claim-lifecycle or Worker failures.
