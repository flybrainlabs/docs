# FBW Marketplace implementation contract

The supplied 2026-10-12 Marketplace specification was read in full: 1,572 lines,
128,137 bytes, SHA-256
`c0958e931c0f2284593e8cda7095e0a1c5ed7459da1f3da73af85ac0167ada02`.
The original user attachment remains outside the public repositories. This English
document records its engineering constraints and current implementation boundary.

## Required products and state

Ten projects cover response, stimulus search, intervention, optic flow, looming,
heading, odor, anomaly, navigation and sparse retrieval. Five product families are
FlyBrain Core, FlyMotion-Lite, FlyHeading-Lite, FlyOdor-3 and FlySparseSearch.
Core includes cache, complete replay and bounded target search as separate SKUs,
not fictitiously separate trained models.

Project, generation, model version, deployment, job, payment and reconciliation
are independent state axes. An imported definition creates no budget, worker,
training, completed work, model, deployment or financial fact. Achieved metrics
and target metrics are separate. Draft prices require measured cost, benchmarks
and explicit approval before becoming active.

## First complete scientific and financial loop

Authorized work must pass complete verification, produce actual training data,
train a small Ridge model, export all weights/bias/normalization and freeze its
share manifest. A finite FBW authorization then pays an actual service call.
Only delivered, settled and mature income becomes historical entitlement. The
original miner can claim it. A second call without new mining must create new
historical earnings, while every retry of the same call must avoid duplicate
charge, refund, allocation or claim.

SimulationID excludes wallet, nonce, display title and downstream readout.
Assignments and attempts are separate from semantic work. Budgets, leases,
sequence, fencing and evidence-backed progress are bounded. Completed status
requires successful durable artifact writes. Native full-graph computation runs
outside SQLite locks and HTTP execution threads. Input features cannot read the
response they predict. Train/validation/test split by underlying trajectory.
Distributed Ridge merges sufficient statistics, never independently trained W.
Controlled shard recomputation checks sample coverage and matrix integrity.

## FBW accounting and storage

FBW is the only new API payment, refund, immediate reward and royalty asset.
Buying FBW is separate from consuming it. There is no fallback API asset.
Eight decimals and the existing 31,183,324,300,000,000 atom cap remain fixed;
service operations cannot mint. Amounts use decimal integer strings and checked
wide arithmetic. Cumulative four-pool floor and cumulative individual floor
retain rounding reserves and permit lifetime turnover above total supply.

One vault must aggregate all mutually exclusive customer, reserved, unmatured,
refund, task and unpaid revenue obligations. Wallet migration never resets claimed
amounts. Legal inheritance paths combine into one stable entitlement; cycles,
duplicate edges and impossible exact coefficients are rejected.

Settlement actions and outbox commit together. Unknown RPC/history states retain
the original locked liability. Blockhash expiry alone proves no nonexecution.
Block height and slot are distinct. FBW issuance evidence is checked; legitimate
burn below the cap must not be rejected as counterfeit issuance.

A new service economy program must preserve old programs and account layouts,
execute real SPL transfers and seal complete small-model content. Chunk order,
length, content, reference count and rent-refund authority are checked. A hash-only
manifest is not a complete on-chain model. Hybrid storage is explicitly labeled.
SOL sponsorship has its own bounded allowlist/budget, never hidden FBW charges.

## Privacy and launch

Private requests, outputs and salts remain customer-scoped. Low-entropy private
inputs use salted commitments, not public bare hashes. Signed gateway receipts
are accountable statements, not general proofs of correct execution. Synthetic
benchmarks and local test mints stay out of production traffic and revenue.
UCI224/322 licensing conflicts remain unresolved until valid rights are obtained.

The current release implements catalog/migration/API and a tested financial
domain. All remaining execution, chain and product gates are tracked in
[STATUS.md](STATUS.md). Missing production configuration blocks activation, not
continued software development and isolated integration.
