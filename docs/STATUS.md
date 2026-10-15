# Implementation and acceptance status

Updated: 2026-10-15. Repository organization does not change production capability.

## Immediate task supply events (server deployment verified)

Node commit `006b875` on `fix/immediate-task-supply-20261015` is installed on the
original node following the owner's explicit deployment request. Its installed
SHA-256 is `ec9c33e5602e4774369eca4eb3f85d016fdff5a2b604efdcd3daf02128b6930c`.
Independent SSH verification at 2026-10-15 04:22:01 UTC confirmed that the ten-second
event filter is absent and the replacement wakeup helper is present.

The dispatcher processes relevant signed events immediately. It coalesces bursts,
retains a follow-up during an in-flight check and handles recovered outbox events.
The one-minute recovery poll, finite budgets, verification and storage bounds,
signed cursors and idempotent publication retain their existing behavior.

The existing 27 scheduler checks, nine evaluator checks and actual loopback SSE
regression passed before deployment. The server import graph and source hash
also passed. The scoped upgrade replaced one source and restarted only the wallet
gateway once. Coherent SQLite backups and the previous source are retained;
historical rows and private configuration were verified unchanged. Authority,
verifier and community process identities were retained, and all four services
were active with zero unexpected systemd restarts during acceptance.

During that recorded verification, the original node reported 31 solved goals,
zero pending or unopened goals,
event sequence 244 and dispatcher state `waiting-approved-tasks`. No new task,
funded stage, grant renewal or reward payment was created by deployment. An empty
catalog still needs distinct approved calibrated work and finite finalized funding.
This acceptance does not establish sustained mining capacity or a paid live task.
This is a historical acceptance of the former node dispatcher. Contract-owned
successor scheduling has since replaced task generation on the original node;
the current V4 deployment is described below.

The dispatcher commit is included in the remotely verified source branch
`feat/contract-task-factory-v4-20261015`. Publication used the existing dedicated
SSH identity, authenticated as `flybrainlabs`. CLI/API authentication remains
unconfigured and no API account operation was performed. Exact source revisions
are recorded by the infrastructure feature branch. External public HTTP
verification was not repeated for this update. Read-only loopback HTTP checks on
the original node passed, including the wallet configuration endpoint.

See infrastructure `docs/IMMEDIATE_TASK_SUPPLY_DEPLOYMENT.json`,
[continuous supply](CONTINUOUS_TASK_SUPPLY_PLAN.md) and
[the 30-day incentive plan](MINING_INCENTIVE_STAGE_30D_PLAN.md).

## Community page refinement with Stitch

Release `social-stitch-refinement-20261014-v1` is deployed at `/social/`. Actual
Google Stitch screen `35bc362868e741a386d51f833aabb5a3` supplied the design
reference. My Community is immediately above Community Leaderboard in the
right-side desktop column, with matching document order on compact screens.
Graphite surfaces, fine borders, faint orbital artwork and bounded task cards
retain the website's monochrome identity and existing typography.

Bound accounts no longer expose a GitHub reconnect control or instruction.
Authorization-unavailable bindings keep their identity and records with an
honest status. The initial binding and the three repository Open GitHub/Verify
flows remain available. Existing backend refresh, points, private configuration,
wallets, mining, administration and complete atlas resources are retained.

Acceptance passed 52 isolated GitHub Chromium checks, 40 existing Social browser
checks, 44 local UI checks and 59 read-only public UI checks. All 12 changed
public HTTP hashes, both languages, responsive order, keyboard opening,
reduced motion and all 11,751 atlas types were verified. The website update
required no production backend change, service restart, database migration,
credential replacement, fixture account or chain transaction. Actual user
wallet-extension and physical-device acceptance remain separate.
See the infrastructure `STITCH_COMMUNITY_REFINEMENT_ACCEPTANCE.json` and the web
component's `docs/STITCH_COMMUNITY_REFINEMENT.md`.

## GitHub Star opening and verification

Release `github-star-flow-20261014-v1` separates Star verification from points.
The three selected repositories retain individual **Open GitHub** buttons. With
a signed-in wallet and bound GitHub identity, opening one repository enables
only its **Verify** button. Language rerenders preserve the prerequisite; wallet
changes, disconnect and refresh reset it. The server verifies the actual bound
identity and public repository relationship, so opening the tab proves nothing.

Successful checks with rewards paused are retained as immutable audit evidence,
shown as **Verified** and included in the three-repository progress on refresh.
They add no points and consume no reward receipt. Historical credits, identities,
private configuration and snapshots are retained. Star points remain off under
the existing platform review; GitHub identity binding retains its 50-point reward.

Acceptance passed 67 GitHub backend checks, 50 GitHub Chromium checks, 45 existing
Social backend checks and 29 daily/invitation checks. Type checking, syntax,
complete-export validation for all 11,751 atlas types and source/history secret
scanning passed. Fifteen public Chromium checks and all 12 changed HTTP object
hashes also passed. The scoped node update repeats no migration and restarts only
the community service for the flow update and the subsequent one-file success
audit classification correction. No other service is restarted. Public
verification and publication evidence are
recorded in the infrastructure `GITHUB_STAR_FLOW_ACCEPTANCE.json`.

## GitHub selected repository tasks

Release `github-task-selection-20261014-v1` is deployed at `/social/`. The public
interaction list contains only `Star miner`, `Star infra` and `Star node`, in
that order, and its progress denominator is three. GitHub identity binding
retains its independent once-only 50-point reward. The current configured maximum
is 53 points, with Star rewards remaining unavailable under the documented
platform review outcome.

The v2 repository manifest preserves the original v1 manifest and stable task
keys. The public API excludes Follow and the other seven repository tasks;
stale or forged direct requests for them are rejected. Stored task definitions,
historical completions, points, snapshots, credentials and private configuration
are preserved. The narrow source update backed up SQLite coherently and restarted
only the community process once. It repeated no migration and left scientific
and financial process identities unchanged.

Acceptance passed 61 backend checks, including retired-task history retention,
42 GitHub Chromium checks, 14 read-only public Chromium checks and the hashes of
all ten changed public objects. Complete-export validation and community type
checking passed. The preceding availability-only update remains recorded below.
See `COMMUNITY_GITHUB.md` and the infrastructure task-selection acceptance record.

## GitHub verification availability follow-up

Release `github-verification-state-20261014-v1` clarifies unavailable interaction
verification at `/social/`. The original production node still enables binding
and disables Follow/Star rewards. A completed binding and its 50-point credit
were observed through aggregate counts, consistent with the owner's report.
This is separate from physical-device or wallet-extension acceptance.

The platform review has not approved the current reward-incentivized Follow/Star
configuration under GitHub's Acceptable Use Policies, section 4. The interface
now labels those buttons as unavailable, places a summary before the task list
and supplies visible, accessible reasons beside each affected task in English
and Chinese. Unavailable tasks no longer advertise claimable points. Existing
completion records and enabled-task verification remain intact.

Acceptance passed 42 isolated GitHub Chromium checks, 57 existing GitHub backend
checks, 13 read-only public Chromium checks and all 12 changed public HTTP object
hashes. The complete static export, its reviewed OAuth bridge and 11,751 atlas
types also passed validation. This scoped website update required no production
database migration, service restart, credential change or token transfer.

## GitHub community tasks

Release `community-github-20261014-v1` is deployed at `/social/`. It reuses the
existing SIWS sessions, SQLite/WAL, immutable community ledger, ranking and
allocation snapshots. GitHub binding is configured for a once-only 50-point
reward. Follow is configured for 10 points and ten public repository Star tasks
for one point each; interaction rewards remain disabled pending the owner's
required platform review. The `examples` auxiliary repository is public and has
original integration examples. The `web` repository remains private.

The third additive migration preserves the first two migration hashes and all
historical community rows. A coherent database backup and separate raw WAL/SHM
copies were retained. Only the community process was restarted, including one
subsequent gate-hardening update; scientific and financial process identities
were unchanged. Website updates matched 28 original scoped objects and two
subsequent callback-header correction objects. Model, wallet/RPC, mining and
anatomy resources retain their original hashes.

Acceptance includes 57 GitHub/SIWS/SQLite fixture checks, 23 provider-contract
checks, 74 existing backend checks, 31 GitHub Chromium checks, 40 existing Social
Chromium checks, 10 wallet Chromium checks, eight export tests, five workspace
safety tests, native compilation, bilingual documentation and public route/hash
checks. These do not establish an actual user's OAuth consent or wallet-extension
confirmation. The owner confirmed the exact application callback URL:
`https://flybrain.work/api/auth/github/callback`. The deployed callback has a
verified `no-referrer` policy. Managed-host callback query-log redaction requires
hosting configuration verification; application and node callback logs contain
no OAuth code/token output.

See `COMMUNITY_GITHUB.md` for routes, private configuration, privacy boundaries,
task identities and operation. A read-only mining investigation found exhausted
plan revision 3 with no current or pending goals and 36 historical rounds.
`CONTINUOUS_TASK_SUPPLY_PLAN.md` records the proposed bounded, event-driven task
pipeline. No new scientific plan, calibration, budget or mining behavior was
activated by that investigation.

## Mining presentation and foreground depth

Release `mining-depth-20261014-v2` is live at `/mining/`. Preparation and pending
actions show a loading indicator with a disabled primary button and repeated
click protection. Explicit preparation pause remains available. Animated progress
uses the actual native progress value; unknown progress does not invent a percent.
The console and brain use equal desktop columns and stack on narrow screens.

White scrolling logs use existing preparation and computation observations.
Qualified candidates and confirmed wins have distinct bold labels. The original
accessible log remains available. Dark foreground backing reuses the actual brain
and lower nerve cord surfaces, so background characters cannot show through the
transparent anatomy. It follows rotation, pan, zoom and part visibility without
replacing geometry or changing neuron propagation. Graphics and reduced-motion
controls retain their behavior.

Acceptance passed 11 presentation checks, 30 isolated Chromium checks and 23
read-only public Chromium checks, including four framebuffer checks per browser
run after rotation and zoom. Both languages, five viewport sizes, the complete
11,751-type atlas and foreground detail were verified. The incremental correction
matched all 12 changed server objects and 21 changed/retained public HTTP objects.
The earlier presentation deployment and its verified backup remain in the private
publication archive. Scientific execution, wallet/RPC configuration, community v2,
databases and cached results are retained; this release introduces no backend
restart, model download, budget or chain transaction.

These are software Chromium and simulated viewport checks. Physical Android,
extension-wallet and full-model mining acceptance remain separate. The requested
private RPC provider remains inactive. See
[Mining presentation and motion](MINING_PRESENTATION_MOTION.md) and
`infra/docs/MINING_PRESENTATION_MOTION_ACCEPTANCE.json`.

## Community daily contributions and invitations

Release `community-daily-invites-20261014-v1` is live at `/social/`. Public ranking
uses full-length wallet displays with eight middle characters masked and no
wallet-copy action or X username option. The leaderboard is on the desktop
right column; narrow screens stack all sections. The requested allocation
disclaimer is removed from Social and its English/Chinese guide.

New X bindings earn 10 points. Daily authenticated check-in earns one point.
Original X posts earn one point each, up to three per UTC day, using bound-author
and original-body challenge verification. Invitation links fix attribution on
first community registration; inviters earn 10 points only after a distinct
invitee completes X verification, with no per-inviter count cap.

Version 2 is an additive, separately hashed migration. Existing earned points,
bindings, ledgers, snapshots and allocation/budget receipts retain their bytes.
A coherent database backup and integrity check passed. Only the community
service restarted; the private runtime and other services stayed unchanged.

Acceptance passed 45 backend regressions, 29 daily/referral checks, 40 isolated
Chromium interaction checks, 46 local layout/wallet checks, 20 read-only public
checks and eight export tests. All 11,751 atlas types remain in the complete
export. Verified deployment matched 21 website objects and four backend objects;
public HTTP matched 23 changed/retained objects. Actual extension-wallet,
human live X challenge and physical-device acceptance remain separate.

See [Community daily contributions and invitations](COMMUNITY_DAILY_INVITES.md)
and `infra/docs/COMMUNITY_DAILY_INVITES_ACCEPTANCE.json`. This release retains
the existing mining/RPC configuration and does not resolve the earlier mining
failure or activate the pending private RPC provider.

## Stitch Social and wallet presentation

`stitch-social-wallet-20261014-v1` implements three actual Google Stitch design
references on the existing website: desktop Social, mobile Social and wallet
connection/sign-in. The allocation and personal cards now share a compact
desktop grid and stack on narrow screens; conflicting inherited hero styles are
scoped explicitly. Existing task verification, real profile metrics, empty
leaderboard, point history, privacy and community administration are retained.
The supplied Logo, flybrainwork branding and monochrome appearance remain in use.

The wallet modal shows eligible detected providers, genuine missing-provider
guidance, official install links and Check again. Late registration is visible
without refreshing. Real connection advances to an explicit message-signature
action; rejected connection remains visible in the dialog. No automatic signature,
deposit or grant is added. Native dialogs have bounded short-screen scrolling,
a visible close header, keyboard cycling and restored trigger focus. Chinese
includes the existing `zh-CN` document language and open connection controls.

Acceptance passed 46 local UI checks, 41 read-only public UI checks, 32 isolated
SQLite/Ed25519 community checks, 18 public community checks, 24 public cross-route
wallet layouts and eight static-export tests. Complete static validation retains
all 11,751 atlas types. Deployment verified its backup and all 69 scoped object
hashes; public HTTP matched 63 changed and eight retained objects, with the
unchanged CSP independently verified over SSH. English design/integration notes
and the infrastructure acceptance record describe the delivery.

The local Stitch skill and its credential-free client are validated; credentials
and raw design responses stay outside repositories and public builds. This UI
update retains the deployed RPC bundle, financial configuration, CSP, scientific
execution, cached results and bilingual handbook. It introduces no chain
transaction, model download, budget, backend restart or production fixture user.
Actual wallet-extension, physical-device and earlier mining/RPC acceptance remain
open.

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


## Continuous task supply and retained participation — 2026-10-14

Release `continuous-task-supply-20261014-v1` installs a bounded, durable task
supplier in the original wallet gateway and publishes explicit browser standby.
The existing authority, serial verifier and community service remain running;
scientific identities, previous result evidence, wallet defaults and funding
fields are retained.

The dispatcher uses the signed authority outbox/SSE with a shared one-minute
fallback. It announces at most one current plus four future goals, replenishes
below two unopened eligible goals, and checks finalized finite funding, verifier
readiness, replay backlog and storage reserves before publication. Prepared
requests and signed receipts recover without duplicate goal issuance. Already
registered scientific work cannot be reintroduced by renaming it.

The browser preserves explicit participation while waiting, dispatches no
simulation in standby, and checks live identity/grants before continuing after a
new round or transient connection failure. Explicit pause/stop, wallet changes,
foreground restrictions and resource limits continue to require user control.
Normal standby refreshes and telemetry are reduced to approximately one minute.

The first gateway deployment encountered a missing installed RPC dependency.
Its rollback retained the database but needed correction of the restored runtime
file owner. The previous gateway was recovered; the completed upgrade now
includes that dependency, retains rollback ownership and verifies the full Node
import graph before stopping the service. No funding, reward payment, model
download, scientific task or production fixture was created by either attempt.

Current source verification found 31 solved scientific goals, 36 historical rounds
and no pending goal. The dispatcher is installed with an empty reserve and
reports `waiting-approved-tasks`. A new approved calibrated task catalog and a
finite Devnet funding amount are still required to resume real competition.
Continuous full-model campaign, physical-device and independent-operator
acceptance remain pending. See `CONTINUOUS_TASK_SUPPLY_PLAN.md` and the
infrastructure `CONTINUOUS_TASK_SUPPLY_ACCEPTANCE.json` for the implemented
boundaries and retained evidence.


## First 30-day mining incentive planning — 2026-10-14

The owner clarified an initial 30-day phase and a target of 100 SOL/day in
aggregate miner expenditure, not project operating expenditure or guaranteed
project receipts. The previous 90-day opening schedule was illustrative and was
never activated. A candidate 50-FBW standard winner reward, 860,000-FBW daily
ceiling and 25,800,000-FBW phase ceiling are recorded for review in
[the planning document](MINING_INCENTIVE_STAGE_30D_PLAN.md).

Using the documented historical 0.00585216-SOL Result rent, the daily target
would require approximately 17,088 distinct successfully settled units, excluding
miner-paid wallet fees and prepaid Result balances. This throughput is unmeasured;
a current public RPC quote was unavailable. The reward recommendation and ceiling
are not funded or active. New scientific work, measured replay/archive capacity,
verified balances and a separate verifier/operating budget remain prerequisites.
No payment, grant change, task publication, server restart or deployment was
performed for this planning record.

## Contract task factory V4 — 2026-10-15

The versioned implementation now includes an immutable on-chain catalog, public
advancement, ordered commit/reveal, frozen 2-of-3 replay quorum and durable
entitlements with separate retryable payment. Nodes validate predefined work.
An isolated SBF run passed 20 checks across 38 transactions (718 maximum packet
bytes; 138409 maximum compute units). Browser and replay orchestration tests use
explicit fixtures and do not establish new scientific or physical-wallet acceptance.
The existing Devnet program was upgraded at finalized slot 511257144, preserving
all 24 existing program-owned account data records at upgrade time. The original
node and official website now select the approved eight-task catalog, with
200 FBW per winner and a finite 1,600 FBW Devnet budget. The old node task
generator and verifier are disabled; shared wallet sessions and historical V3
data, grants and receipts are retained.

Two fresh complete-model candidates passed both public backgrounds and
two complete native node replays each. Both 200 FBW payments are finalized;
the miner ATA increased by exactly 400 FBW and task 3 is active. An idle node
restart retained all logical work and journals, with no duplicate payment or
change to finalized balances. The public RPC produced intermittent 429/503
errors during acceptance; private-provider configuration remains pending. Current evidence is
`TASK_FACTORY_V4_LIVE_ACCEPTANCE.json`; the initial inactive installation record
is historical. Signing uses a restricted external scripted wallet and two
trusted verifier keys controlled by one operator. Extension confirmation,
physical devices, independent operators and biological accuracy are unverified.
Mainnet, formal issuance and production payments remain disabled. See
[the implementation and operation guide](CONTRACT_TASK_FACTORY_V4.md).
