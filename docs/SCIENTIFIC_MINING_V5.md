# Scientific mining V5

Status: implemented and tested in an isolated Solana VM. Public V5 rounds remain
disabled until the original node is installed through its approved maintenance
route, prospective funding is verified, and Devnet/browser acceptance succeeds.
Existing V4 catalogs, signatures, budgets and earned claims keep their rules.

## Experiment and contribution rules

A funded round reserves ten equal places: six distinct qualifying interventions,
two assigned reproductions on new backgrounds, and two registered input stress
tests. Audit assignments and hypotheses are content addressed before commitment.
Correct assigned audit work qualifies whether its scientific outcome is positive
or negative. A negative discovery does not qualify. Wallets do not establish
distinct humans, devices or operators.

Discovery search uses two declared training backgrounds. It interleaves three
cost-ordered choices with one exploration choice, records a Pareto frontier, and
checks candidates with the complete model. This is a bounded search heuristic;
it establishes neither global optimality nor foundational algorithmic novelty.
The browser's current search allowance is finite. An unsuccessful search need not
create a claim or earn a reward.

The complete V5 readout counts every cell outside the registered response set in
the non-target metric. It sums absolute per-cell spike-count changes separately
in each registered window. Stimulus current multiplied by duration is a model
cost proxy, not physical energy or a clinical dose. Parameter profiles and
scientific questions are immutable within a round.

## Commit, challenge, evidence and settlement

1. The authority publishes the complete question, audit assignments, time slots,
   resource limits, analysis identity and reward per place. Initialization reserves
   exactly `10 * reward_atoms` from the existing available project pool. It cannot
   mint tokens or increase the owner's financial authorization.
2. During the commitment window, miners commit an intervention with a salt. The
   commitment binds chain, program, policy, round, miner, beneficiary and role.
3. After commitment closes, anyone can register the first produced Solana slot
   at or after the frozen challenge slot, using the authenticated SlotHashes
   sysvar. Registration expires after 128 slots. This chain beacon has proposer
   bias; it is not an unbiased randomness oracle. Each role/assignment derives
   its declared fresh background seeds from that challenge.
4. The miner executes every required background, retains complete archives,
   publishes their content hashes and the manifest, and reveals the committed
   intervention. Uploads require a scoped wallet signature and a finite claim
   storage allowance. Missing evidence is retryable, not proof of validity.
5. The node derives its own complete event frontier and checks all archive bytes
   and the complete non-target readout. Two of the three frozen verifier keys
   must agree on computational validity and scientific outcome. Two keys of one
   operator are disclosed as one operator. Settlement trusts this quorum; the
   contract does not independently execute the brain model or verify a SNARK.
6. Permissionless resolution follows commitment order within each category.
   Invalid, withheld, duplicate and excess-assignment claims consume no winning
   place. Verification completion order cannot overtake an earlier live claim.
7. Each accepted claim owns one immutable entitlement. Public SPL payment retries
   transfer it once to its frozen beneficiary. Closing releases only unused
   budget; accepted unpaid rewards survive closure and successor rounds. Every
   queued claim must be resolved before closure. A qualifying quorum recorded
   before the deadline remains resolvable afterwards.

Rounds can close partly filled. The miner can move to an approved successor after
acceptance while retaining the older payment context. A new unapproved or
unfunded question is never silently added to the wallet's authorization scope.
The node processes only already registered, configured rounds. Automatic reward
budget expansion, mainnet activation and new issuance are not implemented here.

## Exact complete-model execution

The retained integer LIF reference has threshold 100, leak divisor 8 and a
background tick of either 0 or 10. For any integer subthreshold voltage:

```text
v - floor(v / 8) + background <= 99 - floor(99 / 8) + 10 = 97 < 100
```

The leak map is monotone; refractory ticks reset below threshold. Therefore an
interval without a synaptic or stimulus drive cannot hide a spike. The control
lane starts without drives or spikes and remains silent by induction. This is a
property of the current registered model, not a biological observation.

The executor seeds a complete stimulus frontier, reconstructs exact dormant
membrane/refractory/background histories before each driven update, and follows
every outgoing edge of every actual spike in canonical sender order. A receiver
is retained even when signed inputs cancel. It preserves Euclidean division,
checked intermediate arithmetic, clamping, delays, traces and archive bytes.
The validator never trusts a miner's proposed list of relevant cells.

When more than a quarter of the registry is in the next frontier, it reconstructs
all remaining dormant states and resumes the retained dense loop. Observational
counters count that reconstruction when it actually happens. The native report
separates `verificationMethod: exact-events-v1` from its actual backend, which can
be `dense-fallback-v1`. A legacy dense oracle remains available. Unsupported
background profiles do not receive the sparse admission certificate.

Correctness follows by induction over the complete driven-event frontier and
the no-hidden-spike invariant. Dense equivalence tests support this argument;
tests are not a cryptographic proof of an arbitrary future model. Dense network
activity can require processing nearly the entire graph.

## Identities and evidence

- Computation context: model, graph, metadata, parameters, initial state,
  transition, RNG, horizon and time step.
- Computation identity: that context, actual challenge-derived background
  context, intervention and background count. It excludes wallet and goal name.
- Analysis identity: the frozen readout and complete non-target coverage.
- Claim identity: the chain/program/round, beneficiary, role and salted input
  commitment. Permanent computation markers prevent paying the same computation
  under another wallet or readout in this V5 program.

Archives are existing canonical FBRP bytes; manifests and V5 accounts have new
schemas and disjoint PDA domains. The economic program appends instruction tag
12 without changing previous tags or layouts. User OPFS, model caches, wallets,
database journals and old entitlements are retained.

## Current acceptance and limits

The 2026-10-20 implementation acceptance includes deterministic signed/cyclic
small-graph oracle comparisons, real native/WASM session checks, and 94 actual
SBF transactions in LiteSVM. Six-cell simulation evidence passes through the
miner orchestrator, scoped mnemonic wallet, signed HTTP upload, PostgreSQL
journal, node verification, restart recovery and SPL payment. It includes a
changed archive, an earlier invalid commitment, duplicate computation, negative
stress outcomes, ten paid places, and payment idempotency.

Actual Chromium/Worker/WASM acceptance also matches native archive hashes and
complete non-target metrics for both the six-cell fixture and the retained
165,122-cell model. OPFS output and a Blob stored through a fresh IndexedDB
journal remain readable. Chain reads in that browser test are explicit isolated
SBF fixtures, and graphics are disabled for its CPU/WASM check. This does not
establish a real personal-RPC wallet flow or public finality.

Complete retained-model performance was also measured locally on 165,122 cells:

| Workload | Measured result | Scope |
| --- | --- | --- |
| 20 silent stress inputs, warm validator | p50 2.47 ms; p95 3.51 ms | Negative scientific outcomes; not qualifying discoveries |
| 3 strong stimuli with dense fallback | 9.95–15.79 s | Matches retained complete archive bytes |
| Same strong input, dense oracle | 15.73 s | One comparison on the same local host |
| First request including model startup | 2.94 s | Measured round trip for the first silent input |
| Peak child RSS in this mixed run | 311,316 KiB | Local process, not the original node |

These observations exclude upload, queueing, contract confirmation and public
finality. They do not establish original-node throughput, ten concurrent miners,
physical device capacity, biological validity, broad robustness or universal
instant verification. The small retained-background sample is an execution test,
not a statistical robustness claim. A dense-only first prototype was slower
than dense replay; the measured fallback addresses that concrete regression.

Real Devnet activation, a real user's personal-RPC browser flow, and independent
scientific/operator acceptance remain separate gates. The public configuration
must remain disabled until those deployment and funding checks are satisfied.
