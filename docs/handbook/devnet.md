# FBW Devnet reference

This reference identifies the existing **flybrainwork / FBW** token and completed Wallet Mining V3 acceptance on **Solana Devnet**. It is intended for reading and reconciliation. The completed issuance, adoption, payments and Result close must not be repeated as setup steps.

## Complete public identity

| Field | Value |
| --- | --- |
| Network | Solana Devnet |
| Genesis | `EtWTRABZaYq6iMfeYKouRu166VU2xqa1wcaWoxPkrZBG` |
| Token name | flybrainwork |
| Symbol / decimals | FBW / 8 |
| Mint | `HCdV49RkqtC7pPwzHCYg5KtkmU8opifjojLbAyZXKgQW` |
| Wallet Mining V3 program | `5yxjnH1PSk8iQKfK3ejG4jfSkewkTKfcpJygojdb6sam` |
| Finite stage | `6CcCZodRjRq3WArpAEkpudVgiK4EhpsSaNiDL5zq8x6x` |
| Initial issued atoms | 31,183,324,300,000,000 |
| Initial two-unit budget | 200,000,000 atoms / 2 FBW |

The name and symbol are display fields. Mint, genesis, token program, decimals, authorities and settlement program together identify the applicable asset and environment.

## Issuance and custody

The original supply was issued once under the three-pool model. Wallet Mining V3 adopted that existing supply into its fixed program-controlled pools. It did not issue a second cap.

Mint authority is revoked; freeze authority is absent. Metadata update authority remains with the supplied test wallet. That project wallet also retains program upgrade and authorized Result-close authority, so the deployment has explicit administrative trust.

## Two finalized payments

| Round | Reward | Actual Result rent | Finalized evidence |
| --- | --- | --- | --- |
| 30 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [Payment transaction](https://explorer.solana.com/tx/2ayKE5iZWaPRSmZJ4R3JUHBJvfad7jbGe8VqcfvCp1c8EH2t3G5WyX7hKAy5rcHqzuuLaTUDchJcaSJnKqg7Dvby?cluster=devnet) |
| 31 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [Payment transaction](https://explorer.solana.com/tx/4EcBLHkHA5jTdBWp6TsAVVUMePzgNpx2WVaKjCsNfNXoET7KQ8FZEEVurrs93coi3LaJrqQX9vWPwkgYpEVYkmJU?cluster=devnet) |

Both used actual complete-model scientific work and authorized full native replay under one grant. A holder burned ten atoms between payments. The following payment and prior-payment recovery succeeded without restoring mint authority.

## Result closure and withdrawal

The first dedicated Result was closed after retention, archive rechecking and two authorized archive certificates with the actual project signature. Its rent returned to the fixed project recipient. Permanent economic evidence remains paid.

The second **1,024-byte Result** remains readable at [CUwx4EwnmCQQPpzE2Wkoy5qFL7xdcKJ4mBvFJz7PS8Rv](https://explorer.solana.com/address/CUwx4EwnmCQQPpzE2Wkoy5qFL7xdcKJ4mBvFJz7PS8Rv?cluster=devnet).

After explicit grant revoke, the miner withdrew **11,704,320 unused lamports**. This was a refund of unused principal, not recovery of consumed rent. The public [execution record](https://github.com/flybrainlabs/docs/blob/main/docs/WALLET_MINING_V3_EXECUTION.md) links close and refund receipts.

## Current state and inspection

The initial two units are solved and their budget is fully paid. Their permanent unit and payment evidence remain unchanged.

## Current user task-supply stage

`task-supply-20261013-v1` uses the same Devnet genesis, program, mint, policy and authorities. Its stage is `PKG52R51QHcTS2ENH4jJJUpDawnvEVsUVK1DCNXFHuG`. Two previously unused calibrated downstream populations receive distinct ScientificTaskIds and permanent economic units. The new budget is **200,000,000 atoms / 2 FBW**, reserved before publication: **100,000,000 atoms / 1 FBW per verified winner**. Plan revision 3 opened round 32 and queued the next goal.

The stage and both reservations have finalized receipts in [task-supply initialization](https://github.com/flybrainlabs/contracts/blob/main/deploy/wallet-mining-v3/task-supply-20261013/initialization.json). The operator sent three budget transactions. No replacement mint, miner grant, winning candidate or reward payment was created for this renewal. This leaves the two units available for browser participants. Live remaining supply and funding can change; inspect the mining page before starting work.

Read the [project Explorer](/explorer/), public config and finalized chain accounts together. An RPC fault should preserve already trusted finalized evidence. Do not turn an unavailable balance into a fabricated zero or assume a closed temporary Result means its payment never happened.

This is Devnet acceptance. It does not activate mainnet, formal emission, paid Marketplace services or production funding.
