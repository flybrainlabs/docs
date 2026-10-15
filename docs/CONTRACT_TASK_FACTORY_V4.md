# Contract task factory V4

## Status and scope

Implemented as an opt-in versioned lifecycle on 2026-10-15 and verified on an
isolated local validator. The existing Devnet program was upgraded at finalized
slot `511257144`; task-factory activation is pending. Existing V3 services,
signed formats, financial grants, receipts, archives and OPFS data are retained.
No public V4 task, new FBW reward budget or token issue has been activated.

Actual SBF acceptance is recorded by `contracts` in
`deploy/task-factory-v4/local-sbf-acceptance.json`: 20 checks, 38 successful
transactions, maximum 718 packet bytes and 138409 compute units. Its scientific
roots and signatures are explicit fixtures. Replay fault tests inject native
outcomes. These records do not establish new scientific discoveries, biological
accuracy, independent operators, physical wallets or a funded public release.

The combined verification record is
`TASK_FACTORY_V4_IMPLEMENTATION_ACCEPTANCE.json`. Eight static-export checks
passed using identical immutable resources via local hardlinks; an initial bulk
copy exceeded the small temporary filesystem. No source resource was modified.

## Source publication

The `protocol`, `contracts`, `sdk`, `node`, `miner`, `web` and `docs` source
branches were pushed and their remote commits checked using the dedicated
`flybrainlabs` GitHub SSH identity. The shared branch is
`feat/contract-task-factory-v4-20261015`. CLI/API authentication remains
unconfigured; this Git publication performs no API account operation.
The infrastructure feature branch maintains exact component pins and a
`docs/TASK_FACTORY_V4_PUBLICATION.json` receipt. Source publication does not merge
`main`, activate a public factory or fund new tasks.

## Devnet program deployment

Program `5yxjnH1PSk8iQKfK3ejG4jfSkewkTKfcpJygojdb6sam` now contains the reviewed
404944-byte SBPF v3 executable with SHA-256
`606eac05dda6210fc6cfa68f677060f3545b44aa8118983a1334c44e261a33e8`.
The intended cluster's v3 feature, existing authority and genesis were checked.
The upgrade was simulated before sending, then its finalized bytes were read
back. All 24 existing program-owned accounts retained their data. The preceding
executable and private transport journals were retained outside repositories;
the upload buffer's rent was returned. Historical V3 deployment receipts remain
unchanged. Current evidence is `contracts/deploy/task-factory-v4/devnet-program.json`.

Thirteen verifier source files were installed beside the existing original-node
services. Their import graph and the existing complete native model hashes were
checked. No service was restarted or V4 verifier enabled. A separate read-only
Devnet simulation of factory initialization and first descriptor upload passed
(737 bytes, 83593 CU); it sent no transaction and persisted no factory or budget.
See `infra/docs/TASK_FACTORY_V4_DEPLOYMENT.json` for the combined evidence.

An operator-workstation proposal contains eight distinct downstream readouts,
excluding all 31 historical scientific identities. Each was evaluated on 20
retained complete-model input streams, including eight held-out inputs, with
two fixed public backgrounds. Kernel reuse is explicit and establishes neither
new mining work nor biological accuracy. This catalog is not approved or
registered. The proposed eight-task, eight-FBW Devnet budget requires owner
confirmation before registration or activation.

The deployed product view still selects V3. Public V4 use additionally requires
the approved immutable catalog, finite budget, available content, configured
verifier operators, connected-wallet transaction sender and durable artifact
publisher. Real-wallet/full-model candidate acceptance remains pending. Source
installation and a program upgrade do not complete those activation checks.

## Responsibilities

| Actor | Responsibility |
| --- | --- |
| Scientific operator | Prepare distinct calibrated goals, publish complete specifications/data and approve the finite catalog and budget before activation. |
| Contract | Create/freeze catalog and task accounts, order commitments, check replay quorum, reserve rewards, accept the winner, activate the successor and pay fixed entitlements. |
| Miner | Read authoritative chain state, check content hashes, compute all backgrounds, retain artifacts, commit and reveal with the connected wallet. |
| Verification node | Retrieve committed artifacts and fully replay them. Submit a verdict; never select goals, change difficulty, generate entropy or open rounds. |
| Content providers | Serve content by hash, independently of task authority. Multiple sources are supported. |

## Lifecycle

```mermaid
flowchart LR
  P[Approved scientific catalog] --> U[Upload and seal on chain]
  U --> A[Public Advance activates first task]
  A --> C[Miner computes and commits]
  C --> R[Publish artifacts and reveal]
  R --> V[Nodes fully replay and attest]
  V --> Q[Contract checks 2 of 3 and ordering]
  Q --> E[Durable winner and reward entitlement]
  E --> N[Activate next frozen task]
  E --> Pay[Separate retryable token payment]
  N --> C
```

`Append` creates all scheduled task accounts during catalog upload. `Seal`
freezes the complete ordered catalog. Preallocating accounts removes successor
rent funding and task-content generation from the acceptance transaction.

The second valid vote for the earliest eligible commitment atomically accepts
that winner and activates the supplied successor. A later verified candidate
waits behind an earlier live commitment. After that earlier candidate is rejected
or expires, anyone can call `Finalize`. No privileged relayer or successful-task
minimum interval exists in V4.

Acceptance can persist without a successor account; anyone can recover using
`Advance`. Invalid supplied accounts fail the transaction and can be omitted on
retry. Payment is separate: failure cannot erase acceptance or task advancement.
All operations require transactions; the contract is not a background scheduler.

## Frozen catalog and science

Descriptors bind scientific identity, goal ID, canonical content hash, model and
graph roots, parameter profile, calibration and input-domain hashes, reward atoms,
claim/reveal/verification windows, finite attempts and 2/4/8/16 distinct seeds.
The complete content object has schema `flybrainlabs-scientific-task-v4`, an
existing complete `GoalSpec` in `goal`, and `seeds` as sixteen-character lowercase
hexadecimal u64 strings. Model bytes and complete result archives stay off chain.

Seeds are fixed prospectively and publicly available. They permit precomputation;
this version provides neither a VRF nor fresh verifier-generated randomness.
Unpredictable challenges require a separately reviewed randomness extension.

Scientific identity matches the existing `science-task-v1` fields and domain in
`node/src/product_identity.rs`. Renaming, changing calibration labels, campaign
IDs or seeds does not create distinct science. Permanent V4 registration markers
reject duplicate catalog inclusion. The compiler also requires a historical
exclusion inventory because the contract cannot infer the private V3 database.

The ordered catalog starts with 32 zero bytes and repeatedly applies:

`SHA256("Flybrain/task-catalog/v4\0" || previous || index_u32_le || descriptor_borsh)`

Initialization fixes its final hash/count. Upload is authority-controlled and
checks order, uniqueness and total rewards; sealing requires the exact root and
count. Compact descriptors are stored directly on chain, up to 4096 tasks. This
implementation does not include a Merkle-catalog mode. A hash cannot guarantee
content availability or scientific validity; the approved source material and
calibration must be retained and available independently.

Task and registration records are not deleted on closure. Failed or abandoned
registrations cannot be disguised as new paid discovery in another campaign.
Review the complete compiled catalog before upload: this version has no descriptor
editing or administrative registration-marker reset.

## Replay, ordering and recovery

- At most eight eligible submissions occupy a task queue. This bounds verification
  capacity rather than pacing successful tasks. It does not establish Sybil
  resistance, slashing or permissionless independent verifier admission.
- Commitments bind the program, chain, policy, task/attempt, miner, beneficiary,
  candidate, result root, manifest, archive index and salt. Reveal requires a later
  slot. Copying a reveal cannot acquire an earlier eligible commitment.
- Replay signatures additionally bind the descriptor, submission PDA, commitment
  sequence/slot, verdict, report hash and complete-trial count. Distinct keys may
  vote in any order; duplicate votes count once and equivocation is rejected.
- Both positive and negative scientific votes require complete native replay of
  every required background. Missing artifacts, wrong model bytes, partial replay,
  process failure and network faults create no scientific vote.
- Verifier keys are frozen at initialization. Two admitted keys are a trusted
  quorum, not evidence of independent operators. The contract does not run the
  scientific model itself.
- Timeout retries the same task within its frozen maximum. Exhaustion records
  failure, returns the unused reservation and advances. Failure is not discovery.
- A verified valid candidate survives a missed deadline and must be finalized;
  timeout cannot discard it. Pause stops new commitments/activation but permits
  reveals, votes, acceptance and existing payout. Resume/Advance recover progress.

## Money and retained compatibility

Initialization reserves only an explicitly approved finite amount from the
existing miner pool. Every transition enforces:

`remaining + reserved + accepted_unpaid + paid + refunded = original_budget`

Activation reserves the exact descriptor reward. Acceptance fixes one immutable
winner/beneficiary and records an unpaid entitlement. Anyone can submit `Pay`,
which transfers only from the miner pool to that beneficiary's token account.
Retry pays once. Closing returns only unused funds; accepted rewards remain payable.

V4 uses explicit wallet transactions and submission-account rent. It does not
consume/renew existing V3 session grants. The operator provisions task-account
rent upfront; a miner or explicit payer funds a 768-byte submission account.
Permanent records remain on chain in this version. Rent exemption deposits are
not automatically project revenue or irreversible fees. V3's historical
1024-byte Result rent is not the V4 cost; intended-cluster costs need measurement.

The 30-day stage and aggregate 100-SOL/day miner expenditure remain planning
targets, not funds, guaranteed demand or an FBW budget. Without successful-task
pacing, a finite catalog/budget can finish before day 30. This work changes no
existing reward, grant, public spending setting or emission allocation.

## Tools and integration

Run from the assembled workspace:

```sh
cargo test --locked -p flybrainlabs-mining-v3
cargo check --locked -p flypow-economy-v2-program
node tools/build_browser.mjs
node tests/task_factory_v4.mjs
node tests/factory_storage_v4.mjs
```

`compile_task_catalog_v4.mjs APPROVED_PLAN.json NEW_DIRECTORY` prepares content
and instruction bytes without signing/sending. Plans require schema
`flybrainlabs-task-catalog-plan-v4`, an approval evidence hash, factory ID, decimal
atom budget, deadline, historical exclusion inventory and task entries specifying
`specification`, `approvedCalibrationHash` and frozen `rules`. Approval metadata
is an operator declaration, not independent proof. The compiler does not create
or calibrate goals. Objects use `<sha256>.bin`, including canonical JSON content.

`sdk/tools/task_factory_v4_client.mjs` exports the PDA/transaction adapter and a
strict finalized-chain reader. `miner/web/factory-mining-v4.mjs` connects the
existing complete-model runner, separate V4 candidate store, chain reader and
commit/reveal flow. The application supplies a connected wallet, standard wallet
transaction sender and durable content publisher. Browser Solana dependencies
are included in the generated `factory-wallet-v4.mjs` bundle. Before computing,
the Worker checks `task-factory-deployment-v4.json` against finalized chain state.
No enabled public V4 configuration is added; the existing V3 view remains selected.

`FactoryContentStoreV4` supports multiple sources, finite byte limits and an
injected authorized uploader, with hash checks and retrieval verification.
`LocalFactoryContentStore` reads retained local files for native replay. Other
providers use the same hash-addressed interface. Public bundles contain no
private write credentials.

`factory_verifier_v4.mjs PRIVATE_RUNTIME.json SUBMISSION_ADDRESS` verifies one
submission. Without explicit `submitVotes: true` it sends no transaction. With
`--watch`, it coalesces chain notifications, replays serially, skips already signed
work and backs off infrastructure faults. Watch mode requires a finite
`maxVoteTransactions` per-process allowance. Its one-minute fallback is recovery,
not task pacing. Native binary, verified model, content/output directories and
verifier key paths are private runtime inputs, never repository files.

Deployment objects require schema `flybrainlabs-task-factory-deployment-v4`,
explicit enablement, `localnet`/`devnet`, approved RPC URL, genesis hash, program ID,
policy hash, factory PDA/ID and catalog root. Readers check these bindings,
ownership, discriminators, account sizes and PDAs. Public activation still needs
an approved unused calibrated catalog, available content, finite funding, actual
verifier operators and prospective wallet/cluster acceptance.
