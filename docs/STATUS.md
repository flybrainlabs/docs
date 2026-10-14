# Implementation and acceptance status

Updated: 2026-10-14. Repository organization does not change production capability.

## Bilingual handbook layout correction

`docs-bilingual-20261014-v1` provides all 26 guides in English and Chinese across
eight categories. The generated landing-card headings are balanced; the earlier
26-card layout no longer becomes 52 broken browser link blocks. Full translated
prose, directory, TOC, diagrams, local search, reading metadata and 52 Markdown
downloads use the selected language. Canonical section IDs survive switching,
refresh retains the preference, and print/copy feedback follows the article.

Local and public real-Chromium acceptance each passed 158 bilingual reading/layout
cases and 32 compact/short-screen cases. The verified deployment matched all 71
changed server objects; public HTTP matched 65 changed and 13 retained objects. Generation, source/download hashes, 3,463 internal
links, 177 search sections per language, eight static export tests, five workspace
safety tests and native library compilation passed. These are simulated browser
viewports; physical Android acceptance remains separate. Public deployment and
acceptance are recorded in the infrastructure bilingual acceptance file.

The scoped reading release preserves all executable mining and wallet modules,
financial descriptors, CSP and scientific resources from the verified live
baseline. It introduces no chain transaction or model download. The requested
private RPC provider remains unconfigured and mining acceptance remains pending.

## Private wallet RPC transport prepared

The owner's latest browser log confirms HTTP 429 from the public Devnet RPC.
Sources now support a credential-free authenticated gateway backed by a private
provider endpoint, with independent Devnet genesis checks, finite RPC scope,
bounded requests, reviewed grant submission and finalized HTTP polling. Failed
rent reads cannot become a zero-cost admission quote. RPC admission faults retain
the original candidate for explicit retry; no chain write was introduced by
these checks.

The requested Helius credential is unavailable in the current private inputs.
Activation is pending; the live mining interface and runtime still use the
existing public RPC and mining-module revision `mining-start-20261013-v1`. The 24 transport, 41 gateway and 10
Chromium fixture checks do not verify an actual Helius key or real-device mining.
See [transport and activation](WALLET_RPC_V3.md).

## Mining admission and prepared-worker diagnostics

`mining-start-20261013-v1` is published. Live signed supply still showed open
round 32 and one queued goal at verification, and the existing funded Devnet
stage was retained. Prepared model workers and an open goal are now displayed
separately from wallet login, balance synchronization and finite rent permission.
The primary control offers grant review or device renewal when required, with
structured English/Chinese explanations. Opening or canceling a review does not
start computation or sign a transaction.

An isolated reproduction confirmed that a signed-in wallet without usable credit
previously received Start mining followed by a generic error. The original user's
exact technical failure remains unconfirmed. Admission transport faults retain
the selected candidate for explicit retry and surface their original diagnostics.

The local and public runs each passed 17 admission checks and 37 wallet/session
checks. Twenty-three funding predicates, 28 action-policy checks, 18 approved
budget cases, scheduler fault/resume regression and eight static-export tests
passed. Server backup/baseline verification and all 82 updated object hashes
passed; public HTTP matched 70 changed and nine retained objects. The tests used
fixture wallets, rent/grant responses and prepared-worker presentation. No new
budget, transaction, paid candidate, model download or cache reset was introduced.
Actual extension confirmation and full mining on the owner's device remain open.
See [diagnosis and implementation](MINING_START_DIAGNOSTICS.md) and
[acceptance](https://github.com/flybrainlabs/infra/blob/main/docs/MINING_ADMISSION_ACCEPTANCE.json).

## Renewed finite Devnet task supply

`task-supply-20261013-v2` restores actual task availability. Two previously unused
and preregistered/calibrated downstream goals have distinct scientific/economic
identities. A separate two-FBW stage reserves one FBW per verified winner before
publication. Three budget transactions finalized; the existing mint, initial
paid stage, authorities and fixed pool policy were retained.

Scientific plan revision 3 opened round 32 and queued the next goal. Signed
current-round/readiness responses, full round validation, active funded-unit
membership and public Chromium task reading passed. The page displayed Current
goal open and Round 32, with the wallet-first gate and no automatic computation.
The operator did not consume the new units for another paid acceptance run.

Eighteen budget-adoption cases and 37 isolated wallet/session checks passed.
Actual extension confirmation and physical-device acceptance remain open.
SQLite and its coherent backup passed integrity checks; historical business
counts were retained and two new funded-goal registrations were added. The
authority/verifiers, model cache and private archives were retained.
See [task renewal](TASK_SUPPLY_RENEWAL.md) and
[acceptance](https://github.com/flybrainlabs/infra/blob/main/docs/TASK_SUPPLY_ACCEPTANCE.json).

## Public UI name and immediately visible language control

The official website is published as `public-ui-20261013-v1`. Its public UI name
is **flybrainwork**; source ownership and GitHub publication remain **flybrainlabs**.
All 56 rendered page shells use the selected name. The compact menu places the
single language button first, outside its bounded scrolling links. It remains
visible immediately on short portrait and landscape screens, including when
Resources is expanded. Documentation and desktop navigation remain in normal flow.

The local and public runs each passed 24 document layouts and eight short-screen
cases in both languages. Four branding tests, eight static-export tests, nine
candidate reconciliation cases and native library compilation passed. Deployment
verified a backup and all 80 scoped object hashes; public HTTP comparison matched
70 changed uncompressed objects and nine retained core/configuration objects.
Physical-device and actual extension confirmation retain their separate gates.

The pinned signed authority responses confirmed `RESEARCH_STAGE_COMPLETE`, no
open round and exhausted supply. The related services were active. A missing
unreceipted claim in a signed closed round is now recorded as not admitted and
removed from automatic polling while keeping local outputs. No new tasks, budgets,
payments, database migrations or model downloads were introduced.
See [delivery and diagnosis](PUBLIC_UI_UPDATE.md) and the
[acceptance record](https://github.com/flybrainlabs/infra/blob/main/docs/PUBLIC_UI_ACCEPTANCE.json).

## Social community participation

[Social](https://flybrain.work/social/) and its authorized administration page are
published as `social-community-20261013-v1`. The separate loopback service uses
8791; the existing authority on 8790 and financial gateway on 8789 are preserved.
The additive checksummed schema V1 shares existing SIWS sessions and SQLite/WAL.
A coherent database backup, integrity check, migration checksum, unchanged
private runtime and historical business counts were verified.

The first task verifies original public X body/author evidence and awards its
initial 100 community points atomically. Evidence failures remain in durable
review; refresh recovers binding, completion, real ranking and point history.
Known identity/post reuse and repeated requests cannot earn the first reward
again. Username visibility is optional. Administration includes audited review,
point corrections, task configuration, immutable ranking snapshots and rules,
candidate allocation, internal budget approval/cancellation and CSV/JSON export.

The 25,000,000 FBW budget belongs to the existing 31,183,323 FBW community pool;
6,183,323 FBW remains for other ecosystem uses. Points are not tokens, and this
module announces no conversion, guaranteed personal amount or payout date.
Approved unexecuted allocations count against the cap. No transfer route,
issuance, real distribution, paid scientific task or financial driver was added.
The public ranking was genuinely empty at deployment; no fixture users were
installed. Live X oEmbed returned official public evidence (HTTP 200, no redirect)
on a historical-post probe; actual human X/wallet-extension acceptance and OAuth
remain separate. Physical-device and independent-operator gates remain open.

Acceptance: 45 SQLite/Ed25519 backend checks, 31 isolated Chromium checks,
18 read-only public Chromium checks, 24 native library tests and eight static
export tests passed. New API/provider/client type checks, syntax lint and browser
bundling passed. All 78 scoped deployment objects and 70 changed uncompressed
public HTTP objects matched. Read the [technical delivery](social-community-system.md),
[human guide](handbook/social.md) and [acceptance](SOCIAL_COMMUNITY_ACCEPTANCE.json).

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
with 26 English and Chinese guides, eight categories, 16,006 rendered English
words, eight diagram designs in eleven figures per language and 177 searchable
title/section entries in each localized index. Header/footer
navigation and Help link to the handbook. Categories cover project introduction,
mining, storage, wallets/grants, scientific model/tasks/replay, atlas/results,
economics/Explorer, community contributions, services/Marketplace, development/operations and support.

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

The Social extension now validates 27 documentation pages, 2,117 internal links
and 26 checksum-matched Markdown downloads. Earlier reading acceptance included
26 documentation pages and 1,964 links; eight export tests and native web compilation passed.
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
