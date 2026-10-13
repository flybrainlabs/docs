# Glossary

Use these definitions alongside the task, plan or receipt you are reading. A term can identify a precise protocol object without proving that every possible deployment or business flow is active.

## Science and computation

| Term | Plain-language meaning |
| --- | --- |
| Connectome | A map of anatomical neural connectivity from a defined source |
| MaleCNS | The source dataset used for the registered fruit-fly CNS anatomy |
| Directed neuron pair | A directed connection between two prepared graph nodes; distinct from biological synapse count |
| LIF | Leaky integrate-and-fire point-neuron dynamics with threshold, reset and refractory behavior |
| Model time | The simulated time coordinate, separate from execution wall-clock time |
| Background | A frozen control/input environment required by a task |
| A/B run | Paired control and stimulus executions using the same model and background |
| Readout | A defined interpretation of simulation output using windows and an evaluator |
| Off-target change | A task-scoped response outside its target set; not automatically whole-brain side-effect control |
| Calibration | Measurement used to freeze a task or difficulty rule prospectively |
| Holdout | Data reserved for evaluation rather than used to tune the model/rule |
| SimulationID | Identity of the underlying execution inputs and extent, excluding wallet/title/readout |
| ReadoutID | Identity of the specified interpretation of deduplicated simulation records |

## Competition and evidence

| Term | Plain-language meaning |
| --- | --- |
| Task | Frozen model, input, evaluator and acceptance definition |
| Round | Competition schedule and submission process for its task |
| Candidate/claim | A submitted attempt with its original identity and receipt ordering |
| Commitment | Binding record submitted before the private candidate is fully revealed |
| Reveal | Disclosure checked against that commitment under the round rules |
| Complete replay | Actual execution of every required background to compare the submitted result |
| Authority receipt sequence | Server ordering used by the earliest eligible verified winner rule |
| Public projection | Deliberately restricted public record set read by Explorer |
| Publication | Explicit permission to expose a scientific package; separate from private acceptance |
| ContributionID | Identity of a contributor's class of work under a task, budget and authorization |
| AcceptanceID | Identity of the separate acceptance judgement, policy and evidence |

## Wallets and finance

| Term | Plain-language meaning |
| --- | --- |
| Devnet | Solana's test cluster used by the existing FBW acceptance |
| Genesis | Network identifier used to distinguish the intended cluster |
| Mint | The exact token account/program identity; a symbol alone is insufficient |
| Atom | The smallest token unit; one FBW equals 100,000,000 atoms |
| Lamport | The smallest native SOL unit; one SOL equals 1,000,000,000 lamports |
| SIWS | Sign-In With Solana; a scoped message proving account control |
| Wallet generation | Monotonic authorization context used to isolate account/session changes |
| Grant | Finite on-chain authorization and Result-rent principal, with explicit limits |
| Discovery unit | Permanently unique payable task slot with a frozen amount |
| Result | V3 canonical 1,024-byte temporary on-chain settlement summary |
| Rent principal | Native SOL needed for the declared account; separate from reward and network fee |
| Finalized | Chain commitment level required for reported received payment |
| Unknown transaction | A financial action needing reconciliation; not conclusive failure |
| Outbox | Durable transport record coordinated with a business action for safe retry |
| Accepted liability | An obligation established by its actual acceptance rules |
| Entitlement | A stable beneficiary right under a frozen contract/share policy |
| Unused principal | Deposited amount not consumed under the grant; distinct from previously paid rent |

## Storage and development

| Term | Plain-language meaning |
| --- | --- |
| OPFS | Origin Private File System used by supported browsers for persistent site data |
| Snapshot | Compatible saved state at a declared complete step boundary |
| Manifest | Ordered identity/content description used to verify a build or package |
| Component map | Owning repository mapping for each assembled source file |
| Pinned release | Build identified by an infra revision and exact dependency commits |
| Working-tree assembly | Explicit validation build of local edits, not a published pinned release |
| SBF | The Solana program build/execution format used for actual local-bank and Devnet checks |
| SPL | Solana token-program integration needed for real asset transfers |
| Ridge | Proposed regularized linear-model training path requiring genuine data and evaluation |

See [Feature availability](/docs/availability/) for which concepts are deployed, test-only or pending.
