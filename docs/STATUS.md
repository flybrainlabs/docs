# Implementation and acceptance status

Updated: 2026-10-13. Repository organization does not change production capability.

## Mining availability and restored wallet sessions

The current-stage mining header now shows only one of download, build or mining.
A prepared model and an open task are separate prerequisites. The live authority
reports `RESEARCH_STAGE_COMPLETE`, no open round and exhausted calibrated supply;
the interface explains the completed test plan instead of suggesting that Start
mining will begin work. Check for new tasks synchronizes the authority without
starting a worker. New rewarded work still requires prospective calibrated supply
and a new finite frozen budget; the prior two-unit plan is not reused.

The browser remembers the selected Wallet Standard provider and public account,
scoped to the Devnet genesis and program. Refresh and navigation silently restore
existing provider permission, and retain an unexpired same-tab login for that
account. A stored address alone is never a connected session. Locked/missing
providers request reconnection; expired login requests sign-in while retaining
the connection. Temporary node failures retain a valid login. Explicit disconnect
clears restoration preference, and stale/different account responses stay isolated.
Restoration requests no signatures, deposits, new grants or computation. Wallet
keys and nonextractable grant keys retain their existing private storage.

Acceptance: 37 local and 37 public Chromium checks passed, including 18
width/language/stage presentations per run. The provider and prepared-model
presentation are fixtures, not extension confirmation or full-model computation.
All 67 changed uncompressed HTTP objects and 77 scoped deployment objects matched
the verified release. Eleven core execution/configuration assets and the complete
atlas stayed unchanged; no model download, financial transaction or state reset
was required.

## Public handbook and compact navigation

The documentation center is published at [flybrain.work/docs](https://flybrain.work/docs/)
with 25 English guides, seven categories, 13,353 rendered words, seven diagram
designs in ten figures and 162 searchable title/section entries. Header/footer
navigation and Help link to the handbook. Categories cover project introduction,
mining, storage, wallets/grants, scientific model/tasks/replay, atlas/results,
economics/Explorer, services/Marketplace, development/operations and support.

The native HTML guides include breadcrumbs, section links, previous/next reading,
Markdown download, explicit print/PDF and copy-link actions. Search filters only
a public static index in the browser. Content and ordinary navigation remain
readable without JavaScript. Current implementation, finite Devnet scope and
pending acceptance are clearly identified. Maintenance: [documentation center](DOCUMENTATION_CENTER.md).

Compact headers place the existing language switch inside the menu. The menu,
document directory, section navigation, search results, tables, figures and
footer stay in document flow with bounded scrolling and no overlap over prose.
Current public token labels, translations and whitepaper downloads use **FBW**;
its name remains **flybrainwork**. Published supply amounts remain readable when
the product API is unavailable, from the unchanged public policy reference.
Frozen policy objects, scientific identities, token/program addresses and
historical contracts remain unchanged. No token issuance or payment was repeated.

Acceptance: 26 documentation pages, 1,964 internal links, 25 checksum-matched
Markdown downloads; eight export tests and native web compilation passed.
The V2 reading release passed 50 local and 50 public viewport/language layouts.
Its local and public compact regression each passed 24 menu/language/reflow cases,
including 125% zoom and unchanged supply/pool values displayed as FBW, with
64 HTTP objects matched. The V3 wallet-entry update additionally matched all
43 changed uncompressed HTTP objects and the scoped remote deployment hashes.
These are simulated viewports, not physical Android or extension-wallet
acceptance. The preceding documentation/wallet-entry revision was
`documentation-20261013-v3`; current session corrections use
`mining-session-20261013-v1`. The full 11,751-type atlas and 11 checked
execution/configuration assets are retained byte-for-byte. Research-app and
wallet-interface wrappers were deliberately updated for wallet-first entry;
no model download or state reset was required.

The primary mining entry now requires wallet connection and then sign-in before
preparation or computation. Pause and pending artifact recovery remain available.
Inactive throughput displays **Not running** with no updates-per-second unit;
only actual measured active rates display the unit. Nine wallet/task state checks
and six local plus six public Chromium entry/layout cases passed without
transactions. The layout check reveals the idle presentation panel without
loading a model. Actual extension-wallet confirmation remains pending.

The current authority reports `RESEARCH_STAGE_COMPLETE` with no open round after
the two paid Devnet units. A connected wallet cannot reopen this plan. Further
reward mining needs new calibrated task supply and a prospectively frozen finite
budget; no idle page can report an active simulation rate.

## Deployed capabilities from the retained release

- Website mining on the complete registered MaleCNS graph, cached model reuse,
  real telemetry, worker adjustment, pause/resume and persistent results.
- Three-stage download/build/mine workflow, pending-output recovery and compact
  monochrome interface. Throughput label, value and unit stay on one line.
- Complete paired replay, durable unique winner and a distinct next target.
- Explicit scientific publication, reproducible result packages and private
  customer tickets with authorization and retention boundaries.
- Public Explorer projection and independent query process. Decoratively removing
  UI network badges does not change the actual network identity.
- X social link points to `https://x.com/flybrainwork`.

The latest retained Explorer/public-site acceptance includes eight public checks,
six viewport/language throughput checks and six X-link checks. Model downloads
were zero in the retained-cache public acceptance. Recovery testing used real OPFS
with synthetic archives and quota injection; it does not prove recovery of a
particular user's physical Android storage.

## Current repository ownership and publication

The owner selected `flybrainlabs` as both the project name and GitHub account on
2026-10-12 and authorized recreating all ten component repositories: web, node,
miner, explorer, protocol, contracts, sdk, infra, research and docs. Each has an
English README, an ownership map and the English development agreement.
See [project identity](PROJECT_IDENTITY.md) for the branding and compatibility
policy and the infrastructure `release-manifest.json` for verified publication
status and exact dependency revisions.

The replacement SSH key authenticates as `flybrainlabs`. CLI/API authentication
is verified independently before repository creation. Repository access and exact
remote commits must be checked even when SSH recognizes a key. Publication uses
normal fast forwards to the new account and never falls back to a retired one.

Historical deployment evidence is retained locally. Repository publication does
not re-execute it or claim a new production deployment.

### Historical migration attempt

The earlier `flybrainwork` account created ten repositories and accepted four
initial source uploads before GitHub reported an account suspension. The protocol
upload was unconfirmed and six uploads remained unverified or pending. Those
records describe the earlier attempt only; they are not evidence of current
`flybrainlabs` access or publication. Source commits and verified local bundles
were retained during the account transition.

## Logo release and FBW Devnet token

The owner made `flybrainlabs/web` private on 2026-10-12. Authenticated API
visibility and SSH clone access were verified; anonymous access returns 404.
Complete source assembly requires private web access. Other repositories remain
public.

The supplied monochrome logo is deployed in the website header, footer, favicon
and download link. Desktop and simulated viewport checks passed at seven widths
in both languages for home, mining and Explorer: 42 layouts locally and 42 on the
public website. Official model download requests were zero. The source is the
readable 500px message preview; original decoding failed, so original-quality
acceptance is not claimed. The retained atlas, model and results were preserved.

The separately requested **flybrainwork / FBW** token is issued on **Solana
Devnet** using the V2 supply/allocation model: 311,833,243 tokens, eight decimals,
and miner/verifier/community pools of 224,519,936 / 56,129,984 / 31,183,323.
Mint: `HCdV49RkqtC7pPwzHCYg5KtkmU8opifjojLbAyZXKgQW`. Both transactions reached
finalized commitment; exact supply, pool balances and Metaplex fungible metadata
were independently read back. Mint authority is revoked; freeze authority is
absent. Metadata update authority remains with the supplied test wallet.

The initial three token accounts were controlled by that wallet. Wallet mining
V3 subsequently adopted the same supply into the program-controlled fixed pools.
The two-FBW Devnet discovery acceptance budget has been paid; this does not
complete service-contract escrow or historical-claim business flows.
Existing production and formal FBW configuration remain unchanged. See the
contract repository's `deploy/fbw-devnet.json` and `tools/fbw-devnet/README.md`
for public receipts and repeatable verification. Private wallet/mint/account keys
and the transaction journal stay outside repositories and website artifacts.

## Wallet mining V3 Devnet acceptance

The prospective finite plan paid two different complete-model discovery units
under one funded miner grant. Each payment atomically wrote a canonical 1024-byte
Result and transferred 100,000,000 atoms (one FBW) to the original miner ATA.
Both transactions are finalized. A holder burned ten atoms between the payments;
the following payment and prior-payment recovery continued without reissuance.

Program: `5yxjnH1PSk8iQKfK3ejG4jfSkewkTKfcpJygojdb6sam`.
The wallet interface is published on the existing website; local and public
Chromium each passed 24 read-only viewport/language/route checks.
The initial two-unit budget is complete; new deposits and paid work stop until a
new prospectively frozen budget and calibrated task supply are available.
The first dedicated Result was closed with the real project signature and two
archive attestations. The second Result remains readable. Actual finalized replay
after closure charged no second rent and paid no duplicate token. The miner
explicitly revoked the grant and withdrew 11,704,320 unused lamports.

Evidence and commands: [wallet mining V3](WALLET_MINING_V3_EXECUTION.md).
Local SBF: 60 main checks and 11 boundaries. Authority: 16 tests. SIWS/session:
15 checks. Durable transport: nine checks. Browser: actual Chromium with seven
mock Wallet Standard/RPC checks. Public Devnet: two complete-model winners,
actual authorized full native replay and four close/refund checks.
These are scripted local signing and mock-wallet browser evidence. Actual
extension-wallet confirmation and physical Android acceptance remain unverified.
One operator controls three verifier/signing identities; independent operation
is not claimed. Mainnet and production funding remain disabled.

## Marketplace progress

The ten-project/five-product catalog, eight draft price templates, additive
database migration and read-only catalog API are implemented. Repeat migration
into nonempty historical state and checked cumulative amount allocation pass
their integration tests.

The shared service financial domain passes host tests for complete asset identity,
legal burn below a verified cap, finite allowances, aggregate shared-vault
coverage, request idempotency, refund limits, cumulative pools/claims, beneficiary
changes and exact inheritance. These tests do not claim a deployed service
contract or a completed FBW API payment loop.

Still required: independent service SBF adapter and actual SPL integration,
budgeted assignment/lease/fencing endpoints, native service workers, real Ridge
training/export/evaluation, immutable version release, finite API authorization,
durable settlement/unknown-state reconciliation, customer refunds and historical
claims, market/playground/wallet views and the complete 52-item acceptance matrix.
The catalog is proposed; prices are draft; formal assets and acquisition routes
are unconfigured. No fake training, external customers, income or accuracy is
created by importing definitions.

## Remaining external and device gates

- Physical Android Chrome, physical GPU, low-memory devices, higher concurrency,
  512-step public runs and simultaneous complete compute/3D performance acceptance.
- Authorized external observations, licenses and a frozen calibration/holdout
  evaluation; biological predictive accuracy has not been established.
- Higher-difficulty calibration, difficulty-family migration and sustainable
  finite target supply.
- Independent operators, installable validator nodes, open admission and staking.
- Formal asset identity, authorities, audited programs, finite operating budgets,
  authorized acquisition inventory/routes and operating agreements.
- Full snapshot disaster recovery and measured archive/queue/cost capacity.

No production issuance, paid service, formal FBW reward or mainnet change is
activated by this repository work.
