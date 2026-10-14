# System architecture

The project is maintained as ten repositories under [flybrainlabs](https://github.com/flybrainlabs). Each assembled source file has one owner. A release is identified by the infrastructure commit and its manifest of exact dependency revisions.

## Components and responsibilities

| Repository | Responsibility |
| --- | --- |
| web | Product interface, documentation rendering, atlas and static export |
| node | Authority, archives, complete replay coordination and product/service APIs |
| miner | Native/WASM numerical core, browser workers, storage and mining controls |
| explorer | Public projection, independent query service and record interface |
| protocol | Versioned scientific/financial identity and receipt primitives |
| contracts | Solana programs and public deployment receipts |
| sdk | Codecs, wallet integration, clients and durable transport |
| research | Model preparation, task definitions, calibration and evaluation |
| docs | English technical documentation, bilingual website handbook, protocol explanations and runbooks |
| infra | Dependency pins, assembly, deployment and publication tooling |

The **web repository is private**. Other maintained repositories remain public. Complete source checkout therefore requires authorization to web; public website reading does not.

:::diagram architecture

## Browser boundary

The website serves native HTML and same-origin assets. Mining runs the WebAssembly numerical core inside workers and uses persistent local storage. Wallet integration handles connection, sign-in and scoped authorization separately from model preparation.

Documentation and history reading do not automatically start a simulation. The documentation search index contains only public handbook text; it does not query private candidate or ticket records.

## Authority and replay boundary

The authority owns durable scientific ordering, eligibility, candidate archives and winner selection. Authorized native workers replay the required backgrounds. Operator identity, model files, databases/WAL and private archives remain outside repositories and website exports.

A serial replay process can use three identities on one small host. This is a resource arrangement, not evidence of three independent operators.

## Public query boundary

The Explorer query process reads a public projection rather than the private authority database. It exposes only authorized public fields, stable cursors and evidence links. Private candidate material and customer requests are not recoverable through that API.

## Chain and financial boundary

The V3 extension wraps its explicitly versioned financial operations while preserving old instruction tags, layouts and signature domains. Permanent unit/intent records retain financial uniqueness. A temporary 1,024-byte Result and exact token payment are created atomically for an accepted payable winner.

A relayer transports signed finite actions and reconciles unknown outcomes durably. Scientific terminal state does not discard pending financial liabilities. Program upgrade and Result-close trust remain with the authorized project wallet.

## Compatibility and build boundary

Some internal crate names, schema strings, seed domains and storage keys retain historical `flypow` identifiers. They are compatibility bytes, not the current project name. A branding edit must not change scientific hashes, addresses or historical signatures.

The assembler preserves cross-component paths for those inputs. Use [Build and contribute](/docs/development/) for a reproducible checkout and [Operations and recovery](/docs/operations/) for stateful releases.
