# Economic model

The economic design funds verifiable scientific work through **finite stages**. A stage publishes its funding source, reserved amount, task units, acceptance rules, deadlines, beneficiary and treatment of remaining funds before participation.

A supply cap describes an asset's issuance design. It does not create a price, circulating value, guaranteed income or an unlimited mining budget.

## Supply and fixed issuance allocation

EconomicPolicyV2 specifies eight decimals and **311,833,243 tokens**, or **31,183,324,300,000,000 atoms**. Its exact allocation is:

| Pool | Tokens | Atoms | Purpose |
| --- | --- | --- | --- |
| Miner | 224,519,936 | 22,451,993,600,000,000 | Finite eligible contribution budgets |
| Verification services | 56,129,984 | 5,612,998,400,000,000 | Reserved verification-service work |
| Community/ecosystem | 31,183,323 | 3,118,332,300,000,000 | Defined community/ecosystem allocations |
| Total | 311,833,243 | 31,183,324,300,000,000 | Exact initial cap |

The project token is **flybrainwork / FBW**. The existing Devnet asset uses these exact supply and allocation values. Its existence does not configure a production asset or activate the future Marketplace's payment routes.

Mint authority is revoked for the existing test asset, and freeze authority is absent. A legitimate holder burn can reduce current supply below the verified initial cap without making it counterfeit or authorizing another issuance.

## Finite tasks and allocation

A payable discovery uses a unique task/unit with a prospectively reserved amount. Coverage, verification, additional readout and curation need their own frozen contracts and budgets. A successful trial outside an eligible budget is not an automatic debt.

Allocation uses checked integer atoms. For cumulative distribution, a policy may use `floor((k + 1) × P / M) − floor(k × P / M)`, where P is the pool and M the number of units. Do not substitute JavaScript floating-point accounting or historical whole-token rules.

New stages can admit additional tasks without delaying already established rights. Solved semantic tasks cannot be recycled for another discovery payment by changing a wallet or display name.

## Three linked ledgers

:::diagram ledgers

**Science** records execution, replay and the outcome. **Rights** records an accepted, authorized entitlement. **Funds** records the reservation, accepted liability, in-flight transfer and finalized payment. These financial states are mutually exclusive representations of the same obligation.

A scientific win is not a deposited token balance. The interface reports received assets only after finalized payment evidence.

## Principal, fees and refunds

Quotes and plans separate execution, replay, archive, transport, network fees, account rent principal, deposits and prepayments. Result data length does not represent total cost.

Refundable remainder excludes accepted obligations, in-flight payments and service liabilities. It returns to the frozen recipient under the plan. Unclaimed accepted rights are not arbitrary administrative sweep funds. New deposits and unused prepayments are refundable by default unless a different explicit agreement applies.

RPC timeout, missing history or blockhash expiry cannot alone establish that a transfer did not execute. The original liability remains locked while durable reconciliation determines the actual outcome.

## Revenue and historical rights

Issuance is not sales revenue; deposits are not profit; prepayments are not completed revenue. Different assets retain separate ledgers, and a missing exchange price means a valuation is unknown rather than zero.

The proposed Marketplace requires cumulative historical entitlement, claims, refund limits and exact inheritance. Those host-tested primitives do not mean a deployed paid service exists. Read [Marketplace roadmap](/docs/marketplace/) for the remaining loop.


## Community budget and points

Within the existing 31,183,323 FBW Community & Ecosystem Pool, 25,000,000 FBW is budgeted for future community airdrops and 6,183,323 FBW remains for other ecosystem uses. The approximately 80.17% share refers to this pool, not total supply. Community points and rankings are contribution records; they are not tokens, carry no fixed conversion and do not guarantee a personal amount or date. Frozen approved snapshots and published rules precede any separately authorized distribution. This budget does not change frozen EconomicPolicyV2 bytes or issue additional tokens. Read [Social](/social/) and the [community guide](/docs/social/).
