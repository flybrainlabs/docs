# Build and contribute

Use owning component repositories for edits and the assembled workspace for builds. The assembler is a build layout, not another source owner. New files must be registered in the appropriate `component.json` map.

## Prerequisites

Use Rust **1.90 or newer**, Node **22 or newer** and Python **3.11 or newer**. Browser tooling uses pinned npm dependencies. WebAssembly builds need the wasm32 target; SBF builds need compatible Solana/Agave tools. Scientific preparation and full-model checks have their own optional dependencies and actual input resources.

The handbook generator uses the pinned Python dependency in `tools/requirements-docs.txt`. Generated HTML is committed, so reading or serving a published release does not require Markdown rendering at runtime.

## Authenticated pinned checkout

```sh
git clone https://github.com/flybrainlabs/infra.git flybrainlabs/infra
python3 flybrainlabs/infra/tools/workspace.py checkout \
  --repos flybrainlabs --transport ssh
python3 flybrainlabs/infra/tools/workspace.py assemble \
  --repos flybrainlabs --output flybrainlabs-workspace
cd flybrainlabs-workspace
npm ci
```

Configure an authorized GitHub SSH identity outside the repositories. Do not embed a token in a URL. The private web repository must be accessible. The infrastructure revision containing the manifest pins the assembler itself; the manifest pins its other components.

## Basic builds and relevant checks

```sh
npm run build:web
cargo check --locked --bin flypow-web
python3 -B -m unittest discover -s tests -p test_static_export.py -v
```

For the numerical WebAssembly core:

```sh
rustup target add wasm32-unknown-unknown
cargo build --locked --release -p flypow-sim-core \
  --target wasm32-unknown-unknown
```

Historical executable/package names are retained compatibility identifiers. Building them does not rename the project back to its historical brand.

## Edit and validate

Edit an owning checkout, register new files, then assemble explicitly with `--working-tree`. That mode uses reviewed local edits and does not claim to be a pinned release. If an intentional edit occurred in assembly, `workspace.py sync` routes it back after checking concurrent changes; review the resulting diffs.

Run checks that address the actual change. Full-model checks require existing verified resources and explicit arguments. Do not clear a model or browser profile to make a static or documentation test easier. Large exports need disk-backed scratch space.

For the public handbook, edit the English `docs/handbook/` and Chinese `docs/handbook/zh/` sources, regenerate using `tools/build_documentation.py`, inspect links/figures and run its consistency check. [Documentation maintenance](https://github.com/flybrainlabs/docs/blob/main/docs/DOCUMENTATION_CENTER.md) describes the source and generation contract.

## English changes and publication

Technical documentation, comments, commits and release text use English. The product interface and public handbook support English and Chinese. Preserve hashed historical content even when a display field contains another language.

After verified changes, scan staged files/history, inspect authorized remote changes, commit and push with normal fast forwards. Update infra pins to the verified component commits and publish the containing infrastructure commit. Do not force-push, merge the old draft PR or publish to retired accounts.

Keys, wallet files, session tokens, node databases, private artifacts, browser profiles and model caches remain outside Git and public releases. Repository publication does not activate production funding.
