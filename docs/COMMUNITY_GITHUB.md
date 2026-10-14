# GitHub community identity and tasks

The original `community-github-20261014-v1` update integrates GitHub into the existing
`/social/` community service. It shares Wallet Mining V3 SIWS sessions, SQLite/WAL,
the immutable points ledger, profile summaries, ranking and allocation snapshots.
It never starts a token transfer, follows an account or stars a repository.

## Task contract

| Task key | Public target | Points, once per identity |
|---|---|---:|
| `github_connect_v1` | Original GitHub user ID | 50 |
| `github_star_miner_v1` | <https://github.com/flybrainlabs/miner> | 1 |
| `github_star_infra_v1` | <https://github.com/flybrainlabs/infra> | 1 |
| `github_star_node_v1` | <https://github.com/flybrainlabs/node> | 1 |

The owner reduced the interaction list to `miner`, `infra` and `node` on
2026-10-14. Binding remains an independent identity prerequisite with its existing
once-only reward. The current configured total is 53 points, including binding.
Follow and the other seven Star task definitions, completion records and earned
points remain stored for history. They are excluded from the public task list
and cannot be verified through stale clients, even when the interaction gate is
enabled. No GitHub repository is deleted by this selection.

Star verification and points have independent operational controls. A configured
service permits read-only Star checks by default (`starVerificationEnabled` can
pause them). `GITHUB_ENGAGEMENT_REWARDS_ENABLED` remains off until the platform
rules review requested in the original specification passes. The existing
GitHub AUP review did not approve the incentive-based Star configuration.

### Open GitHub and verify, 2026-10-14

The owner requested an explicit two-button flow. For each of `miner`, `infra` and
`node`, **Open GitHub** opens its fixed public repository in a separate tab with
opener/referrer isolation. After the wallet is signed in and GitHub is bound,
opening that repository enables only its **Verify** button. This prerequisite
survives language changes and normal renders, and resets on refresh, disconnect
or wallet/session changes. It never proves that the user starred a repository.

Verify checks the original numeric GitHub identity, the fixed repository ID and
its public visibility, then the authenticated `/user/starred` relationship. A
successful check with rewards paused records `star_verified` evidence in the
existing immutable audit table. The profile exposes `verifiedTaskIds`, displays
**Verified**, and retains progress on refresh. The points ledger and reward
completion receipts are untouched. Repeat checks reuse the proof without adding
provider requests or duplicate evidence. Missing Stars, revoked authorization,
provider errors and rate limits retain explicit retry/reconnect feedback.

When the separately reviewed reward gate is enabled, verified-but-unrewarded
relationships must be checked again before the existing once-only award can
commit. Opening a repository cannot award points; editable task metadata cannot
bypass either operational gate. Historical points and completion records remain
intact. The interface shows that Star points are paused and does not advertise
those credits as claimable. This is a specific current availability status, not
an additional generic points disclaimer.

The `github-star-flow-20261014-v1` source rollout replaces only three community
service files with a coherent database backup and unchanged private configuration.
It adds no migration and restarts only the community service. Its website update
retains the complete atlas, science, mining, wallets, RPC and OAuth bridge.

The auxiliary public `examples` repository contains original read-only API,
SDK integration, byte-integrity and synthetic research-format demonstrations.
It is outside the ten-component assembly. The `web` component remains private.
Selected repository IDs are pinned in `node/config/github-community-tasks-v2.json`;
the original v1 manifest is retained unchanged. Repository IDs and public
visibility are verified again using the official API before any Star completion.

The `github-task-selection-20261014-v1` rollout changes the manifest and two
community source files through `infra/tools/upgrade_github_task_selection.sh`.
It makes a coherent SQLite backup, checks historical rows and private
configuration hashes, and restarts only the community service. It applies no
new schema migration and retains the old manifest, credentials, completed
receipts and ledger entries.

## OAuth and wallet isolation

1. Connect the Solana wallet and sign in using the existing SIWS flow.
2. `POST /api/social/github/start` requires Bearer SIWS, CSRF and the authorized
   Origin. The service generates 256-bit state, a browser-binding cookie and an
   S256 PKCE verifier. The state expires in ten minutes.
3. The browser opens GitHub's official authorization page with `read:user` scope.
   No repository-write, automatic Follow or automatic Star permission is requested.
4. `GET /api/auth/github/callback` checks one-use state, the HttpOnly browser
   cookie, the original unrevoked wallet session, PKCE and expiration. Token
   exchange and `/user` lookup use fixed official GitHub origins.
5. The callback stores an encrypted pending result and returns to `/social/`.
   It does **not** credit a wallet before checking the wallet currently selected
   in the returning browser.
6. `POST /api/social/github/complete` requires the **same original SIWS session**,
   CSRF and cookie. Binding, encrypted credentials, the existing completion receipt,
   the 50-point ledger entry and verification audit commit in one transaction.

The extra finalization step rejects wallet changes during external authorization,
including provider account changes that did not revoke a historical SIWS session.
The callback accepts no client-provided wallet authority. It returns only fixed
`/social/` destinations with public status codes and never returns a token or code.
The front end removes callback status parameters from the address bar.

The numeric GitHub ID and wallet are permanently unique. Reauthorization of the
same identity renews credentials and keeps historical points. It cannot replace
an identity or earn the binding reward twice. Display-name changes are updated
after `/user` proves the same numeric identity.

## Private configuration

Local authorized application inputs are stored outside repositories in
`/workspace/.private/github-community/oauth.json`. Production loads the separate
`/etc/flypow/github-community.json` file; `GITHUB_OAUTH_CONFIG` can select another
private location. The original wallet runtime is retained unchanged.

Configuration fields are `clientId`, `clientSecret`, `encryptionKey`, `callbackUrl`,
`bindingEnabled`, optional `starVerificationEnabled` and `engagementRewardsEnabled`. The encryption key is 32 random
bytes encoded as 64 hexadecimal characters. Protect the production file with
root ownership, `flypow` group and mode `0640`; back up its key securely. The public
template is `infra/deploy/target-v2/github-community.example.json` and contains
only variable names. Missing configuration leaves the original Social service
available and displays an unavailable GitHub connection state.

Set the GitHub OAuth App's **Authorization callback URL** to:

`https://flybrain.work/api/auth/github/callback`

The owner confirmed this callback URL on 2026-10-14. A real user's consent and
wallet-extension outcome still require user acceptance; fixture tests cannot
establish them.

Tokens and refresh tokens use AES-256-GCM with wallet/GitHub identity-bound
authenticated context. The database holds ciphertext and expiration metadata.
Expiring tokens are refreshed using a bounded, shared in-process refresh request;
revocation, expired refresh credentials and wrong numeric identities require
reauthorization. Credentials never enter browser storage or public builds.

## Routes and verification

| Route | Authentication | Purpose |
|---|---|---|
| `POST /api/social/github/start` | SIWS + CSRF + Origin | Create OAuth state/cookie |
| `GET /api/auth/github/callback` | One-use state + browser cookie + original session | Exchange code and verify identity |
| `POST /api/social/github/complete` | Original SIWS + CSRF + cookie | Atomically bind and credit |
| `GET /api/social/github/binding` | SIWS | Private identity and task progress |
| `POST /api/social/github/verify` | SIWS + CSRF + Origin | Verify one of the three selected Star tasks |

The only verification input is `taskId`. Owner, repository, user identity, wallet
and points come from server records. Active Star tasks use
`/user/starred/flybrainlabs/{fixed_repository}`. A 204
proves the relationship, a 404 means it is absent, and authorization, rate-limit,
timeout and service errors save no positive proof and award no points. At most four provider requests are
active in the process, with short retries, wallet/task leases and retry cooldowns.

The existing client retains `credentials: omit` for ordinary requests. Only Start
and Complete use a same-origin bridge and `credentials: same-origin`. The static
hosting bridge forwards exactly these two paths and the callback, uses verified
HTTPS to the original node, contains no secret and rejects arbitrary targets.
The export validator accepts its exact reviewed bytes through an explicit
`static-with-oauth-bridge` deployment mode. Other executable files remain rejected.
The node Nginx callback location suppresses access and upstream-error query logs.
Managed hosting must likewise restrict/redact OAuth callback query logging.

## Third migration and retained state

`social-community-v3.sql` adds identity, OAuth flow, encrypted credential,
verification audit, stable task target and verification lease tables. Versions 1
and 2 remain byte-identical and are checked against their recorded hashes.
One-time tasks use the existing `social_task_completions` table and immutable
`community_points_ledger`; GitHub does not use daily completion slots.

The original third-migration rollout used `infra/tools/upgrade_community_v3.sh`.
A coherent SQLite backup
includes committed WAL state. Raw database/WAL/SHM copies are retained separately.
Before/after checks prove historical row prefixes, ledger/profile totals,
migration hashes, wallet-runtime hashes and the unchanged process identities of
the science/payment services. Only the community process is restarted.

GitHub credits enter normal personal history, ranking and future cutoff snapshots.
Existing snapshots, distributions, exact token amounts, X attribution, daily
contributions and X-triggered invitation rewards remain unchanged. GitHub binding
does not trigger an invitation credit.

## Acceptance boundaries

Isolated tests cover actual SQLite transactions and Ed25519 SIWS, provider
response contracts, callback/browser correlation, code/state replay, account
uniqueness, wallet switches, encryption, expiry/refresh/revocation, unchanged
snapshots, atomic rollback and concurrent one-time rewards. Chromium checks cover
both languages, narrow/desktop layouts and the actual front-end/API integration.

The public checks are read-only. They create no production fixture users or GitHub
relationships. The owner's reported production binding is supported by the
aggregate one-binding and 50-point ledger observation. This update performs no
direct wallet-extension or physical-device acceptance session. Star production
checks are available after opening the target; awards remain gated because the specified platform review has not approved them.
