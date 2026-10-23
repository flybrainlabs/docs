# flybrainlabs docs

Project documentation for [flybrainlabs](https://flybrain.work/), with English
technical maintenance guides and localized handbook reading editions.
See [project identity](docs/PROJECT_IDENTITY.md) for the required project name,
repository ownership and publication language.

## Scope

Architecture, scientific and financial protocol, component ownership, contributor workflow, acceptance evidence and operations. Technical maintenance documentation uses English; the Chinese handbook is a localized reading edition. Frozen numerical IDs and historical receipt formats are unchanged.

## Source map

- `docs/ARCHITECTURE.md`
- `docs/PROTOCOL_EN.md`
- `docs/DEVELOPMENT.md`
- `docs/OPERATIONS.md`
- `docs/STATUS.md`

Each imported file has one owning repository. `component.json` maps maintained
files into the shared build layout. Dependencies are pinned by commit in the
[infrastructure release manifest](https://github.com/flybrainlabs/infra/blob/main/release-manifest.json).

## Build and test

Use Rust 1.90 or newer (the source uses edition 2024), Node 22 or newer and Python
3.11 or newer. Optional scientific Python dependencies are in
`tools/requirements-research.txt` in the assembled workspace. SBF builds require
the compatible Solana/Agave build tools.

First assemble the exact source revisions:

```sh
git clone https://github.com/flybrainlabs/infra.git flybrainlabs/infra
python3 flybrainlabs/infra/tools/workspace.py checkout --repos flybrainlabs
python3 flybrainlabs/infra/tools/workspace.py assemble --repos flybrainlabs --output flybrainlabs-workspace
cd flybrainlabs-workspace
npm ci
```

Run the applicable checks from the assembled workspace:

```sh
python3 ../flybrainlabs/infra/tools/check_sources.py --repos ../flybrainlabs
```

This transition keeps the existing cross-component import paths intact. Cloning
this repository alone does not supply its external components. The assembler
creates a disposable build layout; all maintained edits belong to the owning
repositories. Use `workspace.py sync` for intentional changes made in that layout,
then review the component diffs and validate them before publication.

Full-model and browser integration checks require existing, verified local
resources and explicit arguments. They do not download a model or reset a
browser profile by default. Isolated chain checks require their own local bank;
production funds and addresses are never substituted.

## Development policy

- Technical documentation, source code, code comments, commit messages, issues,
  PRs and release notes use English. Chinese is allowed only in localized
  handbook prose under `docs/handbook/zh/` and its navigation translation data;
  code examples and comments remain English. Product interfaces may remain
  bilingual.
- Completed, verified updates are committed and pushed automatically to
  `flybrainlabs/docs` using normal fast forwards.
- Keys, wallets, customer inputs, node databases, private artifacts, browser
  profiles and model caches stay outside Git and website exports.
- Production payment and reward configuration remains disabled until its actual
  asset identities, authorities, funds and operating gates are satisfied.

See [AGENTS.md](AGENTS.md), the
[development guide](https://github.com/flybrainlabs/docs/blob/main/docs/DEVELOPMENT.md),
[architecture](https://github.com/flybrainlabs/docs/blob/main/docs/ARCHITECTURE.md)
and [status](https://github.com/flybrainlabs/docs/blob/main/docs/STATUS.md).

## License and provenance

Project code retains the declared `MIT OR Apache-2.0` license. Data descriptors
and third-party assets retain their own source attribution and licenses; this
code license does not relicense MaleCNS data or third-party libraries. The
import preserves numerical/identity fixtures and does not reinterpret existing
scientific or financial records. See [NOTICE](NOTICE).

## Website handbook

Read the [public documentation center](https://flybrain.work/docs/). The handbook
has 26 guides in English and Chinese across eight categories, spanning the project,
mining, wallets, science, economics, Explorer, community, services, development
and support. The website language control switches the full reading experience.

Maintained sources are under [docs/handbook](docs/handbook), with the owner-requested
Chinese product reading edition in [docs/handbook/zh](docs/handbook/zh). Technical
maintenance documentation and publication text continue to use English.
[Documentation maintenance](docs/DOCUMENTATION_CENTER.md) explains the deterministic
web generator, local search, public downloads, validation and scoped publication.
Edit the Markdown and navigation in this repository; generated HTML and browser
assets are maintained by web. Current capabilities and future gates are explicit.
