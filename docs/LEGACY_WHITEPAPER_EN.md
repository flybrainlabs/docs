> Archived historical FlyHash / local coordinator material. Not the current finite campaign.

# flybrain protocol v0.2 — local testnet implementation

> **Historical FlyHash specification.** Its nonce search, halving and legacy wallet rules are not the new campaign. Current browser whole-network experiment status and its uncalibrated limits are recorded in [RESEARCH_CAMPAIGN_STATUS_ZH.md](RESEARCH_CAMPAIGN_STATUS_ZH.md). No new Solana rewards or FLY mint are active.

The public website at https://flybrain.work is a static research showcase: mining, staking, transfers and rewards are not live there. This brand update does not change existing protocol identifiers, address derivation, signatures or local balances.

flybrain combines a fixed public connectome, deterministic FlyHash work, signed native wallets, bonded validator attestations and a fixed-supply reward ledger. The running service is a **local coordinator**, not an independent P2P mainnet.

## Data and computation

The official MaleCNS v1.0 syn-partners file is downloaded from HHMI Janelia. Its 311,833,243 bulk rows include segmentation fragments; this is not the same scope as the published count of approximately 125 million neuronal connections.

Each row becomes a 40-byte little-endian record containing body_pre, body_post and both 3D endpoints. Every 4,096 records form one domain-separated Merkle leaf. The reproduced root is:

`6841b8dd1f5892afbd9588041b656b26c18843c23f2fed9b2f042bbe9bf98c8d`

Direction-aware 50-dimensional sketches expand to 2,000 FlyHash outputs, each reading six inputs. The strongest 100 outputs survive, with deterministic index-based tie-breaking. A compressed dictionary preserves the same fingerprints and artifact root for all 88,384,522 body IDs.

Every nonce performs 256 serial data-dependent synapse accesses, mixes the endpoint fingerprints, then produces a domain-separated SHA-256 work hash. Wallet mining also binds the network ID, recipient wallet, unique signed authorization, parent hash and proposed height into the block template. Legacy unsigned diagnostic proofs do not earn ledger rewards or campaign points.

The browser brain uses 24,000 deterministic spatial samples from named brain/optic neuropils in the official table. Displayed FlyHash winners are mapped onto sample positions by display bucket; they are **not measured neuronal firing**.

## Wallets and signatures

Native addresses are derived from Ed25519 public keys. The browser encrypts exported PKCS8 key material with AES-256-GCM using PBKDF2-SHA256 (310,000 iterations), a random salt and IV. Private keys are not transmitted. Users must retain the encrypted backup and password; no recovery service exists.

Every account-changing request signs a network-specific message containing the public key, account nonce, expiry, action and exact payload. The backend verifies signatures strictly. Nonces, balances, stakes and accounting records change atomically in SQLite. Amounts are integer atoms: 100,000,000 atoms per FLY.

Transfers currently settle in this local ledger between registered wallets. This is not an interoperable Ethereum wallet or a live external blockchain.

## Monetary policy

- Fixed total: **311,833,243 FLY**.
- Genesis community allocation: **31,183,324.30 FLY (10%)**.
- Mining allocation: **280,649,918.70 FLY (90%)**.
- Target block interval: **60 seconds**.
- Each mining tranche issues exactly **31,183,324.30 FLY**, or 10% of total supply.
- Community distributions spend the existing allocation; they never advance mining-halving progress.

| Stage | Target weeks in stage | Blocks | Approximate FLY per block | Cumulative weeks |
|---|---:|---:|---:|---:|
| 1 | 1 | 10,080 | 3,093.58375992 | 1 |
| 2 | 2 | 20,160 | 1,546.79187996 | 3 |
| 3 | 4 | 40,320 | 773.39593998 | 7 |
| 4 | 8 | 80,640 | 386.69796999 | 15 |
| 5 | 16 | 161,280 | 193.34898499 | 31 |
| 6 | 32 | 322,560 | 96.67449249 | 63 |
| 7 | 64 | 645,120 | 48.33724624 | 127 |
| 8 | 128 | 1,290,240 | 24.16862312 | 255 |
| 9 | 256 | 2,580,480 | 12.08431156 | 511 |

For tranche budget T and block count B, each reward is floor(T/B) atoms; the first T mod B blocks receive one additional atom. Every tranche therefore sums exactly to T. No oversized final reward or additional mint is needed. The first block receives 3,093.58375993 FLY.

Each block pays floor(80% of subsidy) to its miner, with the remainder forming the validator pool. The first block pays 2,474.86700794 FLY to its miner and 618.71675199 FLY to validators collectively. Validator rounding remainders are assigned deterministically.

First halving targets 10,080 accepted blocks, approximately one week at continuous one-minute production. Subsequent stage durations double. Completing the mining allocation takes 5,150,880 blocks, or 511 target weeks (about 9.8 years). There is no calendar-only mint when miners or validators are absent.

After the mining allocation is exhausted, subsidy is zero. A public-network fee market would be needed for ongoing incentives; the current local ledger does not implement transaction fees.

## Validators and settlement

A validator bonds **10,000 FLY**. Each bonded wallet has one committee seat; larger deposits do not increase its vote. A candidate snapshots up to 21 eligible wallets, selected deterministically from the previous tip, proposed height and addresses. The submitting miner is excluded.

A validator opens an assignment, requests full-data recomputation and signs the verified candidate hash. Duplicate votes, wrong keys, stale nonces and self-validation are rejected. A candidate requires strictly more than two thirds of its snapshotted committee. The local bootstrap committee may contain one eligible validator; this is not a claim of Byzantine resilience.

The coordinator accepts at most one candidate after each 60-second minimum interval. No quorum or no valid PoW means no settlement or subsidy. The accepted miner receives 80%; eligible signed validators share 20% equally. Competing candidates at that height become stale.

Normal unbonding takes seven days. A launch grant locks its principal for 90 days; unbonding that principal also waits for its grant lock. A validator must finish outstanding assigned attestations before beginning unbonding.

The current UI performs computation on the server and collects client wallet signatures. Independent validator clients, P2P consensus, adaptive difficulty, succinct full-index proofs and production Sybil resistance remain future work.

## Community launch

The reserved community budget is proposed as follows:

- 100,000 FLY: ten founding validator seats.
- 5,200,000 FLY: 52 weekly rounds, up to ten new winners per round.
- 9,000,000 FLY: research/developer bounties.
- 8,000,000 FLY: education, ecosystem and community programs.
- 8,883,324.30 FLY: long-term community reserve.

Only the founding and weekly mechanisms are spendable through the current application. There is no general treasury withdrawal endpoint.

A founding seat requires a registered wallet and an actual wallet-bound computation. Each award is 10,000 FLY. Founding and weekly winners may receive only one launch award per wallet. Principal is locked for 90 days but may immediately fund a validator bond.

Verified points:
- Qualified referral: +10, at most ten per wallet per UTC week. The invitee must complete their first wallet-bound computation.
- Computation: +10, at most three per UTC day.
- X/Twitter follow: UI only, prospective +10; not credited.
- X/Twitter share: UI only, prospective +10; not credited.

The referral is immutable after signed registration. Self-referrals and duplicate computation credits are rejected. Weekly ranking orders verified points, qualified invitations, first point time and address. At UTC Monday rollover, up to ten eligible, previously unawarded wallets receive claimable 10,000-FLY awards. Fewer eligible wallets means fewer awards; unused funds stay reserved.

An address is not proof of a unique person. Public launch requires an explicit identity/Sybil-review process; current caps and signatures do not solve multi-wallet farming.

## References

- HHMI Janelia MaleCNS: https://male-cns.janelia.org/download/
- Google Research connectome release: https://research.google/blog/a-connectomics-milestone-mapping-the-complete-male-fruit-fly-brain/
- Dasgupta, Stevens and Navlakha (2017): https://www.science.org/doi/10.1126/science.aam9868
- Fly-LSH reference: https://github.com/tian-kun/Fly-LSH
