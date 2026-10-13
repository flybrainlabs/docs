# Grants, rent and refunds

A mining grant is a finite authorization and native SOL principal account. It allows the protocol to create the necessary Result account for an eligible winning unit without requesting a new miner signature for every candidate. Its limits are frozen and enforced on chain.

## What you review

A grant fixes the miner and reward wallet, session key, wallet generation, expiry, per-result rent limit, cumulative limit and result-count limit. It contains no unrestricted transaction or arbitrary CPI permission, automatic top-up or beneficiary-change permission.

The deposit is **SOL principal for permitted Result rent**, separate from FBW rewards. Grant management rent, relay transaction fees and auxiliary accounts have their own declared funding responsibilities. A deposit is not service revenue or guaranteed earnings.

:::diagram grant

## When rent is consumed

For a payable winner, the final operation validates authorization, charges only the actual missing Result rent, writes the canonical **1,024-byte Result**, transfers the fixed FBW amount to the original wallet's token account and marks the permanent unit paid. These business effects are atomic.

A failed final operation rolls back those business effects. Network transaction fees remain a separate observable cost. Replaying an already paid unit cannot create a second reward or a second rent consumption, including after the temporary Result has been closed.

The 1,024-byte figure describes the Result account data. It is not the size of the complete scientific archive, a transaction packet or the total operating cost.

## Renewal, rebind and revocation

Renewal or funding rebind requires the original miner's transaction authorization. It preserves the original scientific claim, accepted beneficiary, economic uniqueness and payable amount. It cannot turn old work into a new discovery unit.

Revocation explicitly ends the grant's authority for new actions. Applicable withdrawal returns the unused principal to the same wallet. Principal already consumed for an accepted Result's rent is not unused principal.

Changing browser wallets does not change the original grant's refund recipient. Always review the account and generation associated with the grant before using its controls.

## Result closure and archive evidence

The project signer may close an eligible temporary Result only under the declared retention and archive-certificate rules. Its rent goes to the fixed project recipient. This action does not close the permanent payment evidence or replenish the miner's consumed principal.

Archive certification and chain closure are different from erasing scientific history. The documented acceptance retained the second Result and closed a dedicated first Result after archive verification.

## Current finite-plan state

The initial grant deposited 23,408,640 lamports and consumed 11,704,320 for two Results. After explicit revoke, 11,704,320 unused lamports were withdrawn. Each actual Result rent was 5,852,160 lamports in that acceptance; future rent must use its current quoted and frozen limits.

The two-unit budget is completed and rejects new deposits. These figures describe completed Devnet acceptance, not a deposit offer. Read [FBW Devnet reference](/docs/devnet/) to inspect the actual finalized receipts.
