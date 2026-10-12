# Flybrain assembled development workspace

This layout is generated from uniquely owned source components. It is not an
additional maintained monorepo and has no publication remote. See
`docs/ARCHITECTURE.md`, `docs/DEVELOPMENT.md` and the component ownership marker
`.flybrain-workspace.json`.

Use the infrastructure checkout and assembly tools for pinned builds. Use explicit
working-tree mode for edits, route intentional layout changes with `workspace.py
sync`, validate them and publish each owning repository. Never publish generated
models, browser caches, databases or private configuration as source code.

The root Rust package remains `flypow` for API compatibility. The current product
supports real full-graph simulation/replay and public scientific records.
Marketplace training, service settlement and production payment activation have
separate completion gates; see `docs/STATUS.md`.
