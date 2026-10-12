# Contributor and publication workflow

All new or updated documentation, commit messages, pull requests, issues,
release notes and repository descriptions are written in English. The product
UI remains bilingual. This rule is also recorded in every `AGENTS.md`.

## Checkout and build

```sh
git clone https://github.com/flybrainwork/infra.git flybrain/infra
python3 flybrain/infra/tools/workspace.py checkout --repos flybrain
python3 flybrain/infra/tools/workspace.py verify --repos flybrain
python3 flybrain/infra/tools/workspace.py assemble --repos flybrain --output flybrain-workspace
cd flybrain-workspace
npm ci
npm run build:web
cargo test -p flypow --lib --test target_authority --test product_api --test explorer --test market_catalog
```

Rust 1.90+, Node 22+ and Python 3.11+ are required. Use the locked dependencies.
Build WASM only when the engine changes:

```sh
rustup target add wasm32-unknown-unknown
cargo build --locked --release -p flypow-sim-core --target wasm32-unknown-unknown
mkdir -p web/wasm
cp target/wasm32-unknown-unknown/release/flypow_sim_core.wasm web/wasm/flypow_sim_core.wasm
```

Large static-export tests need a disk-backed temporary directory; a small tmpfs
may not fit the retained full anatomy assets. Set `TMPDIR` to an existing scratch
directory for that test run. Do not delete the anatomy/model cache to make room.

Optional scientific dependencies are listed in `tools/requirements-research.txt`.
Official downloads and full-model runs are deliberate operations; they are not
part of repository checkout. Preserve existing verified model and browser caches.

## Edit a component

`component.json` records the owning repository and path of every assembled file.
Edit in that repository, switch it to an appropriate development branch and
assemble with `--working-tree` for validation. This mode uses reviewed local
changes and does not claim to be a pinned release.

```sh
python3 flybrain/infra/tools/workspace.py assemble --repos flybrain --output flybrain-workspace --working-tree
```

If an intentional edit was made in the assembled layout, first route it back:

```sh
python3 flybrain/infra/tools/workspace.py sync --repos flybrain --output flybrain-workspace
```

Sync rejects concurrent source edits and does not silently remove files. New
files and deletions must be registered in the owning component map. The assembler
rejects duplicate ownership, traversal, stale revisions and unsynchronized changes;
it preserves build outputs and caches on refresh.

## Validate and publish automatically

Run the checks needed for the actual change, then inspect the diff and staged
files. The publication helper accepts only the maintained `flybrainwork` SSH
origins, scans source paths/documentation and uses normal fast forwards:

```sh
python3 flybrain/infra/tools/check_sources.py --repos flybrain
python3 flybrain/infra/tools/publish_components.py --repos flybrain \
  --only node protocol --message "feat(marketplace): validate finite service authorization" \
  --report /private/path/publication.json
```

Do not treat a source scan as a replacement for functional tests. No changes
means no empty commit. Remote changes must be preserved before publishing; the
helper stops on divergence. Update `infra/release-manifest.json` to the verified
new dependency commits and publish that infrastructure update as well. Publishing
does not authorize merging the former draft PR or activating formal funds.

## English documentation and immutable inputs

Use English for explanations, examples and technical comments. Preserve immutable
historical JSON/receipt bytes, even when a display field contains another language.
Document their interpretation separately. User interface translation dictionaries
are product data and remain bilingual. Do not translate a scientific object in
place and silently change its hash.

Legacy document URLs and the `lang=zh` download query remain compatible aliases;
their maintained document content is now English. UI language selection does not
change that documentation policy.

## Local secret storage

Use an external private directory with restricted permissions. Never put wallet
keypairs, SSH private keys, GitHub tokens, node signing keys, customer inputs,
browser profiles or databases in a repository. Publication records include only
public repository names, revisions, hashes and verification outcomes. Do not
write secret contents into a test report or a support message.
