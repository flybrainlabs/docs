# Local Web verification record — 2026-09-14

This records the original full-data verification workflow. The later signed-wallet, validator and emission release is documented separately in [TESTNET_VERIFICATION.md](TESTNET_VERIFICATION.md).

Endpoint: `http://127.0.0.1:8787/`. User service: `flypow-web.service`.

## Full official data

- Official Feather MD5 matched `58efcf712f8c4d4de5f2ad51e97def76`.
- Canonical rows: 311,833,243; bytes: 12,473,329,720.
- Python and Rust full-file Merkle calculations agreed on `6841b8dd1f5892afbd9588041b656b26c18843c23f2fed9b2f042bbe9bf98c8d`.
- All 88,384,522 body IDs, including segmentation fragments, were indexed.
- Compact index: 2,742,389,584 bytes; 4,204,438 distinct winner codes.
- Artifact root: `076f90991fcbcca9082faa342f17736fbdf27a869f1fd8c62db7bbf2a5528561`.
- First, middle and final canonical records matched the corresponding original Arrow rows.

The news article's approximately 125 million synapses and 166,000 neurons are not the raw bulk table's row/body counts. This service preserves all bulk rows.

## Checks completed

- 18 Rust tests passed, including compact/reference fingerprint equality, streaming Merkle odd-leaf handling, HTTP work generation, proof tampering, origin checks and input limits.
- Two Python converter tests passed, including official-source enforcement, multi-batch conversion, rejected non-integer columns and preservation of existing outputs.
- Release build, strict Clippy and JavaScript syntax checks passed.
- In the real browser, generated a proof from the full dataset, recomputed it successfully, then changed one work-hash character and observed rejection.
- Read a real synapse through the page: row 155,916,621, body 516559 → 29742, agreeing with the official source.
- Started and cancelled a mining task through the page.
- Restarted the service, fully rechecked every persisted fingerprint against the construction receipt and confirmed that a pre-restart proof still passed all 11 checks. Reload took approximately 88 seconds in this run.
- Final page contains a fresh successful proof; the service remained active and `ready: true`.

Optional WebMCP registration is feature-detected. No callable WebMCP validation context was available in this browser integration, so those optional tools were not verified; normal browser/API verification was tested as above.

The service replays PoW against its locally constructed, trusted full-data index. It does not implement a succinct proof of index construction or measure the scientific retrieval quality of the index.
