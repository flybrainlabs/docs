# First 30-day mining incentive plan

Planning record: 2026-10-14. This document records the owner's clarified targets
and a candidate reward design. It is not an executable funded stage, a new wallet
grant, or an activated emission schedule.

## Owner-confirmed targets

- The first incentive phase lasts **30 days**, replacing the earlier proposed
  90-day opening phase.
- The activity target is **100 SOL in aggregate miner expenditure per day across
  the network**, or **3,000 SOL across 30 days** if sustained.
- This is a participation target, not a mandatory charge, a verified balance, or
  an instruction to spend project funds. Current execution remains on Devnet.
- Increase early rewards while preserving finite budgets, scientific uniqueness,
  and the existing node resource and verification limits.
- On 2026-10-15 the owner removed the artificial task-speed limit. Eligible
  approved work may advance as soon as verified results and available resources
  permit. There is no target-time cooldown between successful tasks; Solana's
  own block production and transaction capacity remain network properties.

The start timestamp is not configured. Freeze the start and end before eligible
participation; the phase lasts 30 consecutive 24-hour windows from that start.

## What counts as miner expenditure

Count finalized Result-rent debits and finalized transaction fees actually paid
by miners. Exclude unused refundable grant principal, deposits merely moved into
a grant, project-paid auxiliary account rent, relayer-paid fees, and repeated
observations of the same transaction. Reconcile by permanent economic unit and
transaction identity; uncertainty is not a second charge.

Miner expenditure and project receipts have different timing and destinations.
Result rent initially resides in the Result account. Eligible closure sends it
to the fixed project recipient. Network fees do not become project receipts.

The deployed V3 settlement consumes only the actual missing rent for a canonical
1,024-byte Result belonging to a payable verified winner. Rejected or losing
candidates do not consume Result rent; wallet-signed actions can still incur their
own transaction fees. Existing grant limits and refund rights remain unchanged.

Sources: [execution evidence](WALLET_MINING_V3_EXECUTION.md) and
[grants, rent and refunds](handbook/grants.md).

## Candidate first-phase rewards

The owner's duration and SOL target are confirmed. The following reward and
allocation amounts are **recommendations**, not separately approved funding.
They replace the earlier illustrative 200-FBW opening reward for this higher
activity scenario; already funded historical unit amounts retain their bytes.

| Item | Recommended amount | Integer amount |
| --- | --- | --- |
| Standard payable task winner | 50 FBW | 5,000,000,000 atoms |
| Maximum daily miner allocation | 860,000 FBW | 86,000,000,000,000 atoms |
| Maximum 30-day miner allocation | 25,800,000 FBW | 2,580,000,000,000,000 atoms |

The stage ceiling is **11.491184%** of the original 224,519,936-FBW miner pool.
The initial pool allocation is not a fresh verified available balance. Verification
services have their own pool and need a separate measured budget and operating-cost
cap; their work is not funded by assuming this miner allocation covers it.

Each reward must be frozen for a unique eligible task before participation.
Track reservations, accepted liabilities, in-flight payments and finalized
payments as mutually exclusive states of each obligation. Allocate at most
17,200 standard 50-FBW units per day and 516,000 across this phase, including
unpaid reserved units. These are financial ceilings, not validated throughput or
instructions to publish that many tasks. Units must fit both daily and phase limits.

Publish daily tranches prospectively. Unused daily allocation does not cause extra
work to be generated or retroactively alter a reward; a later funded phase may
use remaining allocation under its separately frozen rules. No later phase rate,
automatic halving, token price, or SOL-to-FBW exchange rate is established here.

## Illustrative task volume

The finalized historical Devnet acceptance consumed **5,852,160 lamports**, or
**0.00585216 SOL**, for each winning Result. That is historical evidence, not a
current quote. A read-only public RPC quote attempt during this planning turn was
unavailable; activation needs a fresh positive quote and current grant checks.

Ignoring miner-paid wallet fees and any prepaid Result balance:

`100 SOL / 0.00585216 SOL = approximately 17,087.708 successful units per day`.

Rounding to 17,088 distinct paid units yields 100.00171008 SOL in historical-rate
Result debits per day. Actual expenditure also depends on the current rent quote,
miner-paid wallet actions and any prepaid balances.

| Reward per winner | FBW/day at 17,088 units | FBW over 30 days | Original miner-pool share |
| --- | --- | --- | --- |
| 50 FBW | 854,400 | 25,632,000 | 11.416358% |
| 100 FBW | 1,708,800 | 51,264,000 | 22.832716% |
| 200 FBW | 3,417,600 | 102,528,000 | 45.665433% |

The 50-FBW candidate leaves 168,000 FBW below the proposed phase ceiling in
this illustration. The higher activity target makes the earlier 200-FBW candidate
much more expensive than the previous unmeasured 1,000-task/day illustration.

## Capacity and activation

Approximately 17,088 successful units/day implies one distinct paid winner every
5.056 seconds on average, before considering losing candidates, full-model
replays and archival work. This ratio is a cost illustration, not a minimum
interval, a five-second timer, or a required completion rate. Existing evidence
does not establish that capacity.
Reward adjustments alone cannot ensure either this expenditure target or more
scientific work without additional node load.

Keep the deployed bounded dispatcher: one current plus four future goals,
refill below two unopened goals, verifier-backlog/readiness gates, storage reserves
and finite finalized funding. No per-block Solana listener, shortened polling,
automatic wallet top-up or enlarged permission is introduced by this plan.

The next executable tranche still needs genuinely distinct calibrated goals,
held-out evidence, a measured replay/storage cost, an explicit finite operating
cap, and verified available miner/verifier funding. The existing funded-stage
workflow supports 1-128 units; do not substitute this phase-level projection for
an oversized executable stage. Prospectively funded tranches must share a durable
phase ledger so multiple stages cannot independently consume the full ceiling.

Increase supply only inside measured capacity. If the 100-SOL participation target
is missed, retain the resource limits and unused allocation; do not pad archives,
charge unsuccessful attempts as Result rent, repeat solved science, or add an
undisclosed service fee to reach the target.

[Continuous task supply](CONTINUOUS_TASK_SUPPLY_PLAN.md) is already deployed; its
latest recorded catalog is empty and no new finite stage has been funded by this
planning work. Its catalog hot-loads when actual approved work and finalized
funding exist. This document performs no deployment, restart, catalog admission,
funding transaction, grant renewal, or reward payment.
