# flybrainlabs finite neural experiment protocol v1 — development build

A browser Worker computes a deterministic control/stimulus experiment across the full registered MaleCNS graph. Independent processes replay the complete result. A native Solana program records each frozen scientific task once, conditional integer entitlements and storage escrow. Issuance occurs only after all required tasks are accepted, archived and sealed. Failed campaigns never mint and expose permissionless refunds to fixed recipients.

Formal fees, mainnet and formal FLY issuance are disabled. Localnet pilots have separate campaign IDs, mints and test budgets. Several local keys are not independently operated validators. The draft registry and physiological assumptions require scientific review; model predictions are not confirmed biological causality. Historical nonce/FlyHash, fly1 wallets, SQLite settlement, staking and halving rules are archived in [LEGACY_WHITEPAPER_EN.md](LEGACY_WHITEPAPER_EN.md).

## Input identity and full computation

The minimal pinned official v1.0 files total 1,109,008,094 bytes: annotations, aggregate connection weights and transmitter predictions. The declared Traced registry contains 165,122 real neurons and 25,563,197 directed edges with registered endpoints. Coverage exclusions, missing labels and unmeasured unique fragment counts are disclosed. The historical 311,833,243 table rows are not a neuron count.

Every model step updates all registered cells. Control and stimulus share initial state and addressed background; stimulus adds only its canonical target input. Integer i64 checked arithmetic, floor leak, declared membrane bounds, reset/refractory and one-step synaptic delay are deterministic. Physiological signs and scales are assumptions. Full spike archives match byte for byte in native Rust, WASM and an independent NumPy implementation. Preview bundles contain actual target/Top8 spikes, not invented continuous voltages or dendritic propagation.

## Finite tasks and explicit verifier trust

The default development directory contains four real aIPg10 targets, 64 rectangular inputs and four repeat seeds: 1024 tasks, each still executing the complete graph. Target scope, full model N and total task count are distinct. Canonical TaskID and Merkle membership bind campaign, input versions, real target, condition and repeat. Wallets, time, commitment salts or separate output paths never create another scientific task.

Commit/reveal ordering, bounded eight-candidate queues and frozen deadlines permit cleanup and progression after expired or invalid attempts. Two of three policy keys attest the same complete result and available archive. Actual Ed25519 verification, unique key counting and domain binding cover genesis, program, campaign, submission, identities, public roots, scientific summary, result/preview/manifest and a unified expiry. Hashes and PDAs are not execution proofs. Correctness relies on the configured threshold's honesty, and retention signatures are not proofs of permanent storage.

## Receipts, permanent records and conservation

Temporary SubmissionV1 accounts remain exactly 1024 bytes while alive, including an eight-byte discriminator and 1016-byte fixed Borsh body. Scientific fields freeze at reveal, and the program recomputes the actual summary hash. Full models and outputs remain separate. Permanent ResultPage and Entitlement records preserve uniqueness, attribution, archive commitments, conditional quotas, claims and refunds after close.

Clients request the current rent exemption for exactly 1024; programs use current Rent rules. Storage principal, unused refundable advance, disclosed services and executed slash are separate. Permanent record rent is funded by an independent operating pool. Closing moves actual balance and its corresponding liability atomically into a settlement vault. Donations cannot inflate refunds. Accepted principal is protected before SUCCESS; FAILED and losing attempts expose eligible principal/advance refunds, while SUCCESS releases accepted principal under the frozen development-fund rule and preserves unused-advance liabilities.

## Integer budget and one TGE

The draft fixed supply is 311,833,243 whole FLY: 224,519,936 miners, 56,129,984 verifiers and 31,183,323 community. These integer values replace the historical fractional reserve without migrating old balances. For global task k, total M and pool P, allocate `floor((k+1)P/M)-floor(kP/M)` in whole FLY first, then convert to eight-decimal atoms. There is no time emission, block lottery or halving.

DRAFT permits setup; RUNNING freezes rules. SUCCESS requires every frozen task, archive, entitlement and sealed neuron activity. Otherwise anyone can trigger FAILED after the final deadline. SUCCESS permits one atomic TGE: mint budgets into constrained distribution vaults and revoke mint authority. Subsequent claims transfer to fixed recipients' correct token accounts; failed transfers do not consume quotas. No administrator can sweep unclaimed allocations. Test upgrade authority remains explicit.

## Implementation, operations and limitations

See [campaign architecture and threat model](CAMPAIGN_ARCHITECTURE_ZH.md), [experimental specification](EXPERIMENT_V1_ZH.md), [receipt byte schema](SUBMISSION_V1_ZH.md), [localnet operations](CAMPAIGN_LOCALNET_ZH.md) and [measured implementation status](RESEARCH_CAMPAIGN_STATUS_ZH.md). Static research-app builds include WASM, Worker, standard Solana wallets and declared development RPC/archive origins. Official input CORS limitations require direct official download followed by local import; no opaque no-cors success or project input proxy is provided.

Formal launch requires scientific calibration, independently operated replay/archive services, measured browser resources and security review. Results cannot establish browser execution or CPU/GPU fairness. Mainnet, real funds, formal authority revocation, liquidity pools and exchange applications are separate reviewed actions.

References: [MaleCNS](https://male-cns.janelia.org/download/), [aIPg10](https://reiserlab.github.io/celltype-explorer-drosophila-male-cns/types/aIPg10.html), [whole-brain modelling](https://www.nature.com/articles/s41586-024-07763-9), [Solana accounts](https://solana.com/docs/core/accounts/account-structure), [PDA](https://solana.com/docs/core/pda), [dynamic rent RPC](https://solana.com/docs/rpc/http/getminimumbalanceforrentexemption), [minting](https://solana.com/docs/tokens/basics/mint-tokens), [authority](https://solana.com/docs/tokens/basics/set-authority), [Anchor space](https://www.anchor-lang.com/docs/references/space), [constraints](https://www.anchor-lang.com/docs/references/account-constraints).
