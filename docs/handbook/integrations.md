# Integration principles

An integration must preserve versioned identities, finite permissions and the distinction between a read request and a financial action. The SDK and reviewed public configuration provide the supported building blocks. This guide describes their responsibilities rather than promising a finished paid Marketplace API.

## Begin with configuration and identity

Read the current reviewed deployment descriptor. Match the model/task roots for computation and the cluster/genesis, program, token program, mint, decimals and policy for financial work. Reject a partial symbol-only asset match.

Scientific domains and canonical byte encodings are compatibility inputs. Do not translate or normalize a hashed object in place. Use the maintained protocol codecs rather than hand-building signature bytes.

## Public product reads

The product interface includes public result/task lists and details, evidence registries and request/account flows. Explorer uses its independent public query surface. Use the clients and their actual pagination contracts; treat absent/unavailable values as unavailable rather than manufacturing zero counts.

Public reads must not require access to private archive paths or signing keys. A result package uses its own delivery authorization, MIME/size/hash checks and expiration. Customer tickets remain scoped to their receipt and permitted operators.

## Mining and wallet writes

Mining V3 requires an origin-bound one-use sign-in challenge, scoped session and finite grant. Wallet connection, authenticated login, active grant and available funded unit are distinct checks.

A candidate's financial intent is durable and finalized before scientific commit. All callbacks, histories and funding actions are wallet/generation scoped. Accepted settlement remains associated with the original beneficiary when the selected wallet changes.

CSRF and exact origin checks accompany authenticated writes. Do not expand an allowlist to wildcard credentialed access to work around a configuration error.

## Retry and idempotency

Keep the same scientific/business identity for a retried action. Persist the original signed transaction bytes and durable outbox state. Unknown RPC/history states retain the original obligation and authorization context.

Block height determines expiry; slot is a different coordinate. An expired blockhash alone does not prove nonexecution. Reconcile the transaction, permanent business record and recipient evidence before another financial attempt.

An already accepted Result/payment cannot be replayed as a new unit after temporary account closure. Infrastructure failures likewise cannot become scientific negative votes.

## Current integration limits

Wallet-mining Devnet integration is implemented and has actual chain evidence. Real wallet extensions and physical devices need their separate confirmation. Installable open validators and staking remain future work.

Marketplace finite paid API authorization, service SPL adapter, genuine trained-model delivery and historical claims remain incomplete. An API catalog definition does not authorize charging a customer. Use [Feature availability](/docs/availability/) and the maintained [status](https://github.com/flybrainlabs/docs/blob/main/docs/STATUS.md) when choosing an integration target.
