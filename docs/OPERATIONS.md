# Node and website operations

The public computation UI is [flybrainlabs mining](https://flybrain.work/mining/).
The public record interface is [Explorer](https://flybrain.work/explorer/).
Actual endpoint identity and readiness come from reviewed public configuration;
SSH credentials and private runtime configuration are not repository inputs.

## Build a reviewed release

Assemble a pinned release using the infrastructure manifest. Build the authority,
complete replay binary and public index/query processes:

```sh
cargo build --locked --release --bin target_authority \
  --bin flypow_explorer_indexer --bin flypow_explorer_query
cargo build --locked --release -p flypow-target-protocol --bin target_trial
npm run build:web
```

Use a distinct release directory. `tools/build_product_release.py` updates an
existing complete static export with a recorded baseline and retains its atlas.
`tools/export_static.py --mode research-app --output /path/to/new-release` is a
fresh build. Full atlas/model generation is an explicit scientific operation,
not a way to repair a retained release. Check each command's actual `--help` and
validate its output with `tools/validate_static_release.py` before publication.

## Persistent service directories

- Install reviewed binaries under an operator-owned release path.
- Keep authority SQLite/WAL, signing identity and candidate archives in a private
  persistent data directory, outside the web root.
- Keep the full model and verifier outputs in separate persistent directories.
- Provide exact frontend HTTPS origins to the authority CORS allowlist and exact
  API origins to the website CSP. Do not enable wildcard credentialed access.
- The query service opens only the public projection and listens on loopback
  behind the reviewed reverse proxy.

The repository includes systemd and nginx examples under `deploy/target-v2/`,
`deploy/explorer-v1/` and `deploy/product-v2/`. These are templates, not installed
production configuration. Provide actual model paths, key locations, runtime,
TLS, archive capacity and reviewed budgets before installation.

For a small host, the serial verifier uses three identities in one process and
replays complete backgrounds sequentially. Do not also start parallel workers
with the same identities. This is still one operator.

## Health, release and rollback

Read signed readiness and verify the expected source revision before connecting
the public frontend. An API response is not a full-computation acceptance test.
Run the controlled browser/complete-replay checks required by the changed release.
Retain backup checksums and exact deployed file hashes. Upgrade tools preserve
keys, SQLite/WAL, private archives, public objects and customer records.

Do not restart into newly generated keys or an empty database. Roll back binaries
and static files using a coherent retained release; verify old-binary compatibility
against a private snapshot before replacing live processes.

## Coherent backup

Stop the authority and replay writers for a coherent snapshot, then privately
archive database, WAL, objects, configuration and identities from the same point.
Read back the archive and verify its checksum before resuming service. A copy of
only a live SQLite main file is not a complete backup. Retain multiple generations
and restore to a separate private directory first. Verify identities, winners,
archive roots, customer tickets and public projection consistency on loopback.

Source maintenance preserves existing live state. The complete disaster-recovery
drill remains a separate pending acceptance item.

## Financial configuration

Formal chain/payment/reward features remain disabled. Do not infer a mint or vault
from the token symbol. Supply, genesis, programs, token program, precision,
authorities, finality, funding and receipt source must all match actual chain
evidence before enabling an authorized payment deployment. Isolated test mints
and local-bank transactions never enter production revenue or customer activity.

RPC timeout, missing history and expired blockhash are not proof that a transfer
did not execute. Retain the original business ID and locked liability until the
original transaction and business account are conclusively reconciled. Use block
height for expiry; a slot is a separate coordinate.
