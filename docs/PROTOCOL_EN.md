# flybrainlabs: verifiable computation and finite settlement budgets V2

Version: 2026-10-12. flybrainlabs is a neural simulation computation network.
Its purpose is to produce verifiable and reusable simulation results.

## Computation and scientific scope

MaleCNS v1.0 supplies anatomical connectivity. The registered graph contains
165,122 neurons and 25,563,197 directed neuron pairs; the latter is not the
original biological synapse count. The frozen numerical model uses integer
point-neuron LIF dynamics: leakage, input accumulation, threshold events,
reset, refractory state and connection propagation. A step represents 1 ms;
256 steps represent a 256 ms model trajectory. Actual execution time is
measured separately. Currents, membrane states and stimulus costs are model
units, not calibrated mV, pA or joules.

Paired A/B runs use the same model, zero initial state and background seed.
Only B adds the specified stimulus; evaluation compares B minus A. Windows
are relative to stimulus termination. Net target events, positive response
cells, absolute off-target change, selectivity and stimulus cost follow the
frozen task. R is the required number of backgrounds, not biological confidence
or the number of independent institutions. The frozen backgrounds do not trigger
the first control pulse. Transmitter-to-sign mapping includes assumptions.
The point model does not solve dendritic compartments; the O32 constraint is
local and cannot establish whole-brain side-effect control.

Task calibration, complete protocol replay, independent implementation
reproduction and external biological validation are separate evidence classes.
No biological predictive accuracy is reported without authorized observations.

## Goal competition and complete verification

Each V2 round freezes the model, stimulus domain, windows, evaluator, seeds and
deadlines. The current product domain has 4 x 3 x 1 x 6 = 72 legal combinations.
Different downstream readouts can reuse the same simulation. Renaming a task,
changing its wallet or using another outer ID does not create scientific supply.
Solved tasks are not cycled for new rewards. Exhaustion waits for a new calibrated
and authorized scientific task.

Miners commit, privately upload complete backgrounds, then reveal. Authorized
verifiers replay every required background. The earliest still-eligible authority
receipt sequence that ultimately verifies wins. Client clocks, upload throughput
and verification completion order do not determine the winner. FBW users participate in validation under the admission and evidence policy
frozen for each task. Participating workers execute the registered complete model
and sign reports binding task identity, output and evaluation. Numerical integrity
and measured operating cost are recorded as separate evidence.

Strictly equivalent numerical optimizations may satisfy the same contract.
Early failure retains only the genuinely completed scope. Cache reuse or a new
readout does not count as a new underlying simulation. Live visualization binds
to the currently executing work; historical viewing reads stored observations
and never automatically starts computation.

## Scientific identities and publication

SimulationID uses the domain `FlyPoW/science-simulation-v1/v2\0` and canonical
JSON to bind dataset, graph, model, parameter roots, numerical rules, initial
state, canonical stimulus, actual seed, timestep and run extent. Wallet, filename,
title, readout and outer round are excluded.

ReadoutID binds a deduplicated sorted SimulationID set, response and off-target
roots, windows, evaluator and eligibility rules. ContributionID binds contributor,
contribution class, scientific references, task, budget and authorization.
AcceptanceID separately binds contribution, frozen acceptance policy, judgement,
evidence and issuer, avoiding circular identifiers. Historical goal, round, claim,
receipt, salt and scientific bytes are preserved without reinterpretation.

The result center exposes only explicitly authorized publications. Private
candidates, salts, paths, signing keys and customer tickets remain private.
Public calibration examples use a dedicated package, new complete native replay
and independent event evaluation. They are calibration examples, not current
round winners or biological discoveries. File delivery uses an allowlist,
expiration, MIME and size checks, SHA-256 and Range recovery. Reproduction is an
explicit action. Raw events and display samples are separate. Viewing does not
upload local history or automatically download the complete model.

## EconomicPolicyV2

The normative policy object is `web/data/economic-policy-v2.json`. The supply
design is 311,833,243 FBW with eight decimals: 31,183,324,300,000,000 atoms.
The fixed issuance pools are 224,519,936 FBW for miners, 56,129,984 for
verification services and 31,183,323 for community and ecosystem. These exact
integers sum to the cap. Amounts use checked integers or decimal strings, never
JavaScript Number accounting. A supply cap is neither circulation nor a price.

The default issuance path uses one global account, one mint, atomic issuance to
three constrained vaults and revocation of mint authority. Issuance markers and
CPI occur in the same transaction. Nonzero initial supply, invalid authority,
retries or another campaign cannot issue a second cap. Adopting an existing mint
uses a separate supply/vault verification path. Upgrade and settlement authority
trust remains explicit.

Continuous targets are funded by finite stages. Before participation, stages
and task slots freeze funding source, amount, weights, deadline, beneficiary,
acceptance and treatment of remaining funds. New allocations normally use atoms.
Cumulative allocation can use `floor((k+1)*P/M)-floor(k*P/M)` in atoms; this differs
from V1's whole-token allocation. No unreserved task promises a reward. Additional
tasks enter a new stage without delaying previously established rights.

Discovery pays a unique economic task/slot. Coverage requires a separate frozen
unit and budget. Verification has reserved service orders and may pay a correct
rejection according to its contract. Additional readout and curation have separate
contracts. Reported throughput, thread count, time, failure logs, a different
wallet, receipt or policy version cannot duplicate compensation.

## Ledgers, finality and commercial records

Scientific outcomes, contribution rights and funds are linked by stable IDs.
A scientific win is not a deposited balance. Reservation, accepted liability,
in-flight transfer and finalized payment are mutually exclusive financial states.
Transactions transfer budget between them. Business-level uniqueness and
message-event idempotency are separate. Database events are append-only, chained
and accompanied by a persistent outbox. The program independently verifies asset,
vault, beneficiary, limits and durable business consumption identifiers.

A submitted claim locks its amount. RPC timeout or missing history is unknown;
funds remain locked. Only conclusive evidence that the original action did not
execute and cannot subsequently execute permits release or retry. Partial claims
cannot exceed accepted entitlement. Only finalized payment is displayed as
received. Stage failure or cancellation does not erase unconditional accepted
rights. Refundable remainder excludes accepted obligations, in-flight payments
and service liabilities and goes to the frozen recipient. There is no arbitrary
administrative sweep of unclaimed rights.

Quotes disclose execution, replay, archive, transport, transaction fees, account
principal, deposits and prepayments separately. The 1,024-byte rule applies only
to the original Submission receipt; it is not the total storage or operating
cost. New deposits and unused prepayments are refundable by default unless a
different explicit agreement applies. Different assets are reconciled separately.
Without a real price, profit conversion is unknown. Issuance is not sales revenue,
deposits are not profit, prepayments are not completed revenue and sponsorship
cannot be counted twice.

## Services and retention

Services have explicit stimulus-search, response-comparison, public sponsorship,
retrieval and delivery scopes. Forms are validated, rate-limited, idempotent and
durably stored before a private ticket is issued. Signed operations record quote
confirmation, funding, execution and delivery separately. Customer text is never
executed as code. Restricted requests require review; confidential public-miner
execution is not promised without actual isolation and access control. Request
fields are removed after at most 365 days; audit and contract retention is
separately disclosed.

## Current deployment and preserved history

Website computation, persistent full replay, result publication and private
tickets have deployment acceptance records. Formal asset identity, issuance
authorization, funding, independent chain observation and operating approval are
not configured. Isolated local-chain acceptance is not a production transaction.
Actual machine/network identity remains accurate even when compact product UI
omits decorative network badges.

Frozen V1 campaigns continue under their original task catalog, issuance, fee and
principal rules. Their English documentation remains under `docs/history/v1/`.
Wallets and historical rights are not automatically migrated.

## Sources

- [MaleCNS official downloads](https://male-cns.janelia.org/download/)
- [Model evaluation reference](https://www.nature.com/articles/s41586-024-07763-9)
  (a methodological reference, not evidence of this project's accuracy)
- [Tasks](https://flybrain.work/tasks/), [Results](https://flybrain.work/results/)
  and [Methods](https://flybrain.work/methods/)

Every artifact identifies its specific source, roots, versions and license;
different fly datasets are not assumed to share a license.
