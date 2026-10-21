# Continuous V4 mining implementation

## Delivery status

This is a reviewable implementation on `feat/continuous-mining-20261021`.
It is not accepted as a complete live mining release. The matching original
node service has not been activated. The website overlay is staged locally.
The full qualified-candidate handoff timeline and real personal-RPC reward
acceptance remain required gates. V5 stays disabled.

The machine-readable evidence map is
`docs/CONTINUOUS_MINING_V4_20261021_ACCEPTANCE.json` in the infrastructure
repository. It distinguishes fixture tests, actual PostgreSQL/SBF transactions,
complete-model browser work and unobserved live behavior.

## Implemented flow

1. Create or unlock the dedicated mining wallet, complete backup and explicitly
   consent to automatic chain costs for this unlocked session.
2. Configure a personal supported RPC key. The existing network, deployment,
   account and canonical transaction checks remain mandatory.
3. Start once. Model preparation and nonactivating session preparation run
   together. Only after model readiness does the browser select/recover a task,
   acquire an input lease and dispatch computation. Preparation can be paused.

Start and signing authority remain memory-only. A refresh restores encrypted
wallet records, saved RPC preferences, source/model caches and scientific
results; it does not restore unlock authority or authorize new payments.
Available balances contain finalized SOL and FBW assets, never pending rewards.

## Independent work and result processing

The existing V4 rule remains one ACTIVE task per factory. A signed pool supplies
multiple independently funded factories. Scientific production, catalog
registration, keeper operations, native replay and payment use separate lanes.
The existence of old replay work no longer gates all catalog production.

Each execution captures its original client, store, submission handler,
network and configuration. A completed qualified candidate is saved before its
outbox handoff; its Worker can then accept other legal work. The outbox scans
retained contexts independently of task selection. Current-task pending
candidates direct new work toward other open tasks. Old uploads and payment
Promises are not awaited by the task-selection lane.

Candidate state, ordered trial completion receipts and the original archives
are authoritative. A journaled derived OPFS index accelerates history and
records aggregate count/bytes. Crash recovery validates actual side files and
hashes, recomputes metrics and restores only a durable ordered prefix. The
index does not replace the evidence. Unsaved in-memory bytes cannot survive a
forced browser termination; the recovery UI retains those bytes while memory
still exists and provides original-store save/export operations.

## Control and transaction boundaries

Pause stops new computation and Commit. Previously committed results may finish
necessary Reveal while the original unlocked authorization remains valid.
Stop, wallet lock, payment revocation and identity changes prevent subsequent
new signatures and sends. Already broadcast receipts remain recoverable.
A capacity pause preserves intent; an explicit user Pause cancels that intent.
Late Resume/RPC callbacks cannot reactivate a stopped session.

Candidate locks coordinate submission/reconciliation/payment. A wallet lock and
priority lane serialize financial work through finality; urgent Reveal has
priority over pending ordinary Commit within that lane. Existing salts, journal
keys, raw signed packets, blockhash bounds and canonical account policies are
retained. This release does not claim that two real browser tabs with scarce
funds have completed the full financial acceptance matrix.

## Finite supply and operational limits

The example runtime remains disabled and contains no credentials. New FBW
allocation requires both the existing finite authorization and actual funded
balance. Previously allocated/reserved/unpaid rewards cannot be reused.
Only an observed on-chain refund reduces allocated authorization accounting.
Scientific deduplication and permanent chain markers remain intact.

Keeper defaults are minimum 1, target 2, maximum 4, idle target 0, minimum useful
claim window 90 seconds and authenticated demand TTL 120 seconds. Full, paused
or expired ACTIVE catalogs also count toward the separate active safety ceiling. New
advance/expire operations recheck shared capacity under a database advisory
lock. Existing packets are reconciled rather than replaced to evade capacity.
A protected valid-quorum finalization may open its protocol-defined successor;
that protocol effect is not suppressed by a new-payment or production gate.
These policy values are configuration, not consensus rules.

The browser outbox defaults to 2 active operations, 32 candidates and 1 GiB.
Retries have persisted bounded exponential delay, capped at about 60 seconds.
Local storage and actual remaining browser quota also constrain admission.
The server uses replay time/work estimates, outstanding input leases, background
count, upload/confirmation margins and deadlines. Defaults are bootstrap
estimates; they are not measured production P95 guarantees.

Calibration sharing the sole native lane must yield after a complete kernel.
Checkpoint identity binds the preregistration, policy, inventory and existing
authorization. Kernel timeout is bounded; changing the tool hash requires the
existing operator policy review, not an automatic private authorization edit.
Reward, signer, fee and storage exhaustion preserve jobs and accrued rights.

## Storage and historical rights

Upload grants expire after 1,800 seconds by default and can be renewed for the
same frozen object set. A cleanup lease protects renewal/upload races. Known
expired partials become eligible after 24 hours; each cleanup pass is bounded.
Immutable evidence and unknown orphan directories are preserved and counted.
Replay temporary copies are removed in `finally`; crash-created temporary
leftovers still require an explicitly reviewed retention procedure.

Serving, draining and retired catalog states bound the active manifest without
removing permanent scientific inventory. Historical catalog statements have a
separate signature domain, scope and expiration. Renewed history does not roll
back the active manifest. Unpaid original rights retain their original context.
History with no persisted original wallet binding remains preserved rather than
being assigned to whichever wallet is currently unlocked.

## Actual evidence and limits

- Thirteen coordinator, wallet, storage, gateway and RPC regression suites passed.
- Actual PostgreSQL plus retained SBF/SPL integration executed 22 isolated
  transactions, opened two independent catalogs before verification and paid
  each original reward once. Native scientific decisions in that suite are
  explicitly fixtures.
- A separate PostgreSQL test retains 132 catalog lifecycle fixtures, renews a
  bounded signed active manifest and signed old history, and preserves unknown
  immutable packets while recovering active capacity. It does not claim 132
  on-chain deployments or an actual historical token transfer.
- The complete 165,122-neuron model ran in browser Workers after one Start,
  then ran in another signed catalog. Warm first progress was 44.9 seconds.
- An empty isolated profile automatically fetched and checked 1,109,008,097
  official source bytes, built the complete model and reached real computation
  in 399.4 seconds. Download transport was a controlled service of retained
  files matching the frozen hashes; public-network cold download remains unrun.
- Calibration checkpoint/restart equivalence passed across 29 yielding slices
  using retained complete-model streams. It does not establish new native-kernel
  scheduling capacity while actual verification competes for CPU/RAM.

These measurements establish their stated paths, not universal speed, sustained
utilization, completed qualified multi-catalog submission, live rewards or a
24–72 hour soak. The acceptance map records the remaining gates explicitly.
