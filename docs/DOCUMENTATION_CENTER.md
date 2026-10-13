# Website documentation center

The public handbook is at [flybrain.work/docs](https://flybrain.work/docs/).
It is written for participants, researchers, customers, developers and operators.
The main navigation, footer and Help page provide entry points.

## Content and information architecture

The current release contains 26 English guides in eight categories and 15,177
rendered words. Eight diagram designs are used in eleven figures. Categories are:

1. Start here: project overview, first session and feature availability.
2. Mining and wallets: workflow, cache/recovery, sign-in, grants and performance.
3. Science and evidence: model, tasks, verification, atlas and reproduction.
4. Economics and Explorer: policy, FBW Devnet reference and public evidence.
5. Community contributions: X identity, points, ranking and future allocations.
6. Services and Marketplace: scoped requests and the proposed service roadmap.
7. Developers and operators: architecture, builds, integration and operations.
8. Support and reference: troubleshooting, privacy/security and glossary.

Guides explain practical actions, terminology, state transitions and limitations.
Source coverage includes the maintained protocol, product/chain descriptors,
atlas provenance, Marketplace specification summary, Wallet Mining V3 execution
and deployment receipts. The availability reference distinguishes deployed
features, finite Devnet acceptance, pending real-device/extension evidence and
planned work. A completed test budget is never described as an open reward offer.

The project name remains flybrainlabs. The existing test asset remains
flybrainwork / FBW on Devnet. Current issuance, payment, Result-close and refund
effects are documentation inputs; no transaction driver is part of this build.

## Community extension

The V5 handbook adds `/docs/social/`, a practical contribution guide with a
wallet-to-allocation diagram. Current website revision is
`social-community-20261013-v1`; it preserves the mining-session corrections below.
The new guide distinguishes 25,000,000 FBW pool-internal budget from points and
actual transfers. All 27 handbook pages, 26 Markdown sources, 2,117 internal
links and 174 searchable sections validate. See `SOCIAL_COMMUNITY_ACCEPTANCE.json`
for live service, migration and browser acceptance.

## Current session corrections

The V4 handbook explains silent wallet restoration, same-tab login expiry,
explicit disconnect, and the distinction between a prepared model and task
availability. The related website revision is `mining-session-20261013-v1`.
The mining header shows only the current stage and explains completed supply;
Check for new tasks synchronizes availability without starting computation.
These changes preserve the existing asset, grant keys, model cache and results.
Actual extension and physical-device acceptance remain separate pending gates.

## Maintained source and generated files

The **docs** repository owns `docs/handbook/navigation.json` and the article
Markdown files under `docs/handbook/`. It also owns this maintenance explanation.
The **web** repository owns:

- `tools/build_documentation.py` and pinned `tools/requirements-docs.txt`.
- Generated `web/pages/docs.html`, `web/docs/*.html` and `web/docs/routes.rs`.
- Generated `web/data/docs-manifest-v1.json` and `docs-search-v1.json`.
- `web/docs.css`, `web/docs.js`, shell navigation and native route integration.
- Static export, scoped release builder, link checks and Chromium acceptance.

All new files must be registered in the owning `component.json`. The generated
Rust include embeds the same guide HTML and Markdown downloads into native web
routes; it does not parse Markdown at runtime. Its allowlisted slugs return 404
for unknown articles. Static deployment emits `/docs/<slug>/index.html` and
`/downloads/docs/<slug>.md` from the same maintained sources.

## Regenerate from an assembled workspace

Use the pinned source assembly and an external Python environment:

```sh
python3 -m venv /path/to/documentation-python
/path/to/documentation-python/bin/python -m pip install \
  -r tools/requirements-docs.txt
/path/to/documentation-python/bin/python tools/build_documentation.py
/path/to/documentation-python/bin/python tools/build_documentation.py --check
```

For direct edits to owning checkouts, pass `--source` to the docs repository's
`docs/handbook` and `--web` to the web repository's `web` directory. Generation is
deterministic under Markdown 3.8.2. The exporter checks article source hashes
before writing their public derivatives. Register a new slug in both source and
generated ownership maps; review and assemble before publication.

Use H2 headings for stable section links. Add a cross-guide link with its actual
`/docs/<slug>/` route. Tables are wrapped for narrow-screen scrolling. A standalone
`:::diagram <name>` marker selects a reviewed HTML/CSS figure, with an ordered
text sequence and caption. Diagram content must preserve its scientific or
financial scope. There is no diagram CDN, runtime Markdown dependency or remote
image generator in the reading path.

## Reader functionality

The desktop layout has a category directory, readable article column and section
navigation. Narrow layouts collapse the directory and section navigation using native
disclosures. Open panels and search results remain in normal document flow, and
only one compact navigation panel is expanded at a time. Guides have breadcrumbs, calculated reading time, update
date, previous/next links and per-section permalinks. The article subtree declares
English and is excluded from automatic interface translation. The shell can
retain its normal language toggle.

The public search index has 162 title/section entries. It is loaded on an actual
search; queries are filtered in the browser and are not sent to the authority or
a third-party search engine. Keyboard navigation, highlighted snippets, no-result
messages and recoverable index-fetch errors use native elements and text nodes.
Escape from a result restores input focus and closes the list without reopening
it. Slash focuses search outside editable fields.

Markdown download and ordinary navigation work without JavaScript. Print/save-PDF
and copy-page-link are explicit enhanced actions. Print CSS uses a light paper
layout, hides navigation and retains the prose, tables and figures. Clipboard
failure provides an address-bar fallback rather than claiming a successful copy.

## Validation and deployment

```sh
python3 tools/check_documentation.py /path/to/complete-release
python3 tools/validate_static_release.py /path/to/complete-release
python3 -B -m unittest discover -s tests -p test_static_export.py -v
cargo check --locked --bin flypow-web
```

The full research-export test needs disk-backed temporary storage; set `TMPDIR`
to an existing dedicated scratch directory when `/tmp` is too small. Do not
delete model, atlas or browser caches to make that test pass.

Chromium reading acceptance is `tests/documentation_site.py`. It checks real
rendering at 320/390/768/1280/1440 widths, both shell languages, all 25 guides,
full-text/keyboard search, print layout, native navigation without JavaScript and
home/mining navigation compatibility. `--fault-checks` adds isolated local index
failure/recovery checks. These are simulated viewports, not physical-device or
wallet-extension acceptance.

`tools/build_documentation_release.py` refreshes an independent complete retained
export. It updates shared navigation, public handbook, downloads, search assets,
sitemap and the reviewed wallet-entry/throughput presentation. The current
revision is `documentation-20261013-v3`. Scientific WASM, worker execution,
candidate submission and frozen financial configuration stay byte-identical;
11 checked execution/configuration assets are retained. The research-app and
wallet-interface wrappers change deliberately to implement wallet-first entry.
Current public token labels and whitepaper downloads use FBW. The existing
policy JSON and all chain/scientific identities remain byte-identical; the supply
view renders a display reference from the published policy without depending on
live API availability. Compact headers move the existing language button into
the menu, preserving its listeners and desktop placement.

Its scoped hash report is consumed by the existing verified-backup deployment
tool. No authority upgrade, model download, financial transaction or browser
profile reset is required.

After public acceptance, publish the changed web/docs commits using normal
authorized fast forwards, update the infra manifest pins and publish the
containing infrastructure commit. Retain the public acceptance summary in the
infra repository; private operator journals and keys remain outside all sources.

## Compact-layout regression

`tests/mobile_documentation.py` uses real Chromium mobile emulation at
320/360/390/768 widths. It checks compact header placement, a working language
switch, menu/document separation, mutually exclusive directory/section panels,
prose reflow at 125% zoom, table/figure containment and the unchanged supply/pool
values displayed as FBW in both shell languages. It is a layout/interaction check,
not a claim of physical Android acceptance.

## Wallet entry and throughput regression

The primary mining entry opens the wallet selector before model preparation or
computation and then requires sign-in. Pending artifact recovery and pause
controls remain usable without a wallet. A disconnected wallet cannot start or
resume new mining through the primary entry. The completed finite plan remains
closed; connection does not create another task or reward budget.

An idle rate displays **Not running** without a unit. A session without a usable
sample displays **Measuring**; a finite measured rate alone displays the updates
per second unit. The label and value share one aligned row.

`tests/wallet_entry_gate.mjs` checks nine wallet/task/control states without
transactions. `tests/mining_wallet_entry.py` checks the real wallet-selector
entry and idle presentation at 320/390/1440 pixels in both shell languages.
Six cases passed locally and on the public website. The idle presentation panel
is revealed for its layout check; no model or simulated computation is run.
These checks do not replace actual extension-wallet confirmation.
