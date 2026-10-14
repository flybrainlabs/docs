# GitHub community identity and tasks

The `community-github-20261014-v1` update integrates GitHub into the existing
`/social/` community service. It shares Wallet Mining V3 SIWS sessions, SQLite/WAL,
the immutable points ledger, profile summaries, ranking and allocation snapshots.
It never starts a token transfer, follows an account or stars a repository.

## Task contract

| Task key | Public target | Points, once per identity |
|---|---|---:|
| `github_connect_v1` | Original GitHub user ID | 50 |
| `github_follow_flybrainlabs_v1` | <https://github.com/flybrainlabs> | 10 |
| `github_star_miner_v1` | <https://github.com/flybrainlabs/miner> | 1 |
| `github_star_explorer_v1` | <https://github.com/flybrainlabs/explorer> | 1 |
| `github_star_contracts_v1` | <https://github.com/flybrainlabs/contracts> | 1 |
| `github_star_protocol_v1` | <https://github.com/flybrainlabs/protocol> | 1 |
| `github_star_node_v1` | <https://github.com/flybrainlabs/node> | 1 |
| `github_star_sdk_v1` | <https://github.com/flybrainlabs/sdk> | 1 |
| `github_star_infra_v1` | <https://github.com/flybrainlabs/infra> | 1 |
| `github_star_research_v1` | <https://github.com/flybrainlabs/research> | 1 |
| `github_star_docs_v1` | <https://github.com/flybrainlabs/docs> | 1 |
| `github_star_examples_v1` | <https://github.com/flybrainlabs/examples> | 1 |

The maximum configured total is 70 points. Follow/Star rewards have a separate
`GITHUB_ENGAGEMENT_REWARDS_ENABLED` operational gate. It remains **off** until the
platform rules review required by the owner is completed. Identity binding is
independently enabled when the application credentials are configured. A paused
interaction task is visible with disabled verification and an accurate status.

The auxiliary public `examples` repository contains original read-only API,
SDK integration, byte-integrity and synthetic research-format demonstrations.
It is outside the ten-component assembly. The `web` component remains private.
Repository IDs are pinned in `node/config/github-community-tasks-v1.json` and
verified again using the official API before any Star completion.

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
`bindingEnabled` and `engagementRewardsEnabled`. The encryption key is 32 random
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
| `POST /api/social/github/verify` | SIWS + CSRF + Origin | Verify a fixed Follow/Star task |

The only verification input is `taskId`. Owner, repository, user identity, wallet
and points come from server records. Follow uses `/users/{bound_login}/following/`
`flybrainlabs`; Star uses `/user/starred/flybrainlabs/{fixed_repository}`. A 204
proves the relationship, a 404 means it is absent, and authorization, rate-limit,
timeout and service errors award no points. At most four provider requests are
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

Upgrade uses `infra/tools/upgrade_community_v3.sh`. A coherent SQLite backup
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
relationships. Real wallet-extension consent and real OAuth completion remain
separate acceptance items until a user performs them. Follow/Star production
awards remain gated pending the specified platform review.
