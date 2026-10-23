# Website documentation center

The public handbook is at [flybrain.work/docs](https://flybrain.work/docs/).
It is written for participants, researchers, customers, developers and operators.
The main navigation, footer and Help page provide entry points.

## Content and information architecture

The bilingual release contains 26 guides in English and Chinese across eight
categories, with 16,006 rendered English words and 25,519 Chinese reading units
(CJK characters and Latin tokens). Eight diagram designs are used in eleven figures. Categories are:

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

## Bilingual layout correction

The release is published at the official documentation URL. Local and public
Chromium each passed 158 bilingual reading/layout cases plus 32 compact and
short-screen cases. Local search-failure and no-JavaScript fallback checks passed.
The deployment verified a coherent replaced-file backup and all 71 object hashes;
HTTP reading matched 65 changed objects and 13 retained execution/configuration
objects. The full retained atlas contains 11,751 types. All 52 localized Markdown
downloads and 3,463 internal links validate, with 177 search sections per language.
Physical-device acceptance remains separate.

`docs-bilingual-20261014-v1` repairs malformed generated landing-card headings.
The live reproduction parsed 26 cards as 52 broken link blocks; balanced headings
and explicit card containment restore the intended structure. The bilingual build
validates canonical heading IDs, navigation order and all source hashes for both
languages. Eight figure designs and eleven instances have Chinese text.

Each native page retains an English reading fallback and an inert Chinese frame.
Only one article, heading and set of IDs is live at a time. The existing website
language control selects the complete frame, persists its preference and keeps
canonical section anchors. Mounted listeners and asynchronous search callbacks
are canceled when a frame changes. Chinese titles, directory, breadcrumbs, TOC,
reading metadata, figure captions, search, feedback and Markdown use the same
language. Index-fetch failure retains category navigation and can be retried.

`--docs-only` on the scoped builder updates reading pages, local search, downloads
and their shared language helper. It preserves live mining, wallet transport,
financial configuration, CSP and science assets from the verified baseline.
The prepared private-RPC source does not become live through a documentation
release. Provider activation and the original mining acceptance remain pending.

## Historical community extension

The V5 handbook adds `/docs/social/`, a practical contribution guide with a
wallet-to-allocation diagram. Its website revision was
`social-community-20261013-v1`; it preserves the mining-session corrections below.
The new guide distinguishes 25,000,000 FBW pool-internal budget from points and
actual transfers. All 27 handbook pages, 26 Markdown sources, 2,117 internal
links and 174 searchable sections validate. See `SOCIAL_COMMUNITY_ACCEPTANCE.json`
for live service, migration and browser acceptance.

## Historical session corrections

The V4 handbook explains silent wallet restoration, same-tab login expiry,
explicit disconnect, and the distinction between a prepared model and task
availability. The related website revision is `mining-session-20261013-v1`.
The mining header shows only the current stage and explains completed supply;
Check for new tasks synchronizes availability without starting computation.
These changes preserve the existing asset, grant keys, model cache and results.
Actual extension and physical-device acceptance remain separate pending gates.

## Maintained source and generated files

The **docs** repository owns `docs/handbook/navigation.json` and the article
Markdown files under `docs/handbook/`, including localized sources and navigation
under `docs/handbook/zh/`. It also owns this English maintenance explanation.
Chinese is allowed in that localized Markdown prose and its navigation labels.
Source code, fenced code examples and technical comments, including HTML
comments inside translated Markdown, continue to use English. The source-policy
check limits the exception to localized Markdown and the navigation JSON; it
does not exempt other file types placed in the translated directory.

The **web** repository owns:

- `tools/build_documentation.py` and pinned `tools/requirements-docs.txt`.
- Generated `web/pages/docs.html`, `web/docs/*.html` and `web/docs/routes.rs`.
- Generated `web/data/docs-manifest-v1.json` and both `docs-search-v1.json`
  and `docs-search-zh-v1.json`.
- `web/docs.css`, `web/docs.js`, shell navigation and native route integration.
- Static export, scoped release builder, link checks and Chromium acceptance.

All new files must be registered in the owning `component.json`. The generated
Rust include embeds the same guide HTML and Markdown downloads into native web
routes; it does not parse Markdown at runtime. Its allowlisted slugs return 404
for unknown articles. Static deployment emits `/docs/<slug>/index.html` and
`/downloads/docs/<slug>.md` and `/downloads/docs/zh/<slug>.md` from the
same maintained sources. Native routes provide the same localized downloads.

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

Use matching H2/H3 heading levels and order in both languages. English canonical
IDs are reused in Chinese so existing links keep their identity. Add a cross-guide link with its actual
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
date, previous/next links and per-section permalinks. Each article declares its
actual language and is excluded from text-by-text shell translation. The normal
website language toggle replaces the complete localized reading frame.

Each localized public search index has 177 title/section entries. It is loaded on an actual
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
rendering at 320/390/768/1024/1280/1440 widths, both content languages and all 26
guides. It checks cards, prose, figures, duplicate IDs, short-screen menus, 125%
text, anchor/refresh persistence, localized search/downloads and print feedback.
The English native fallback remains readable without JavaScript. `--fault-checks` adds isolated local index
failure/recovery checks. These are simulated viewports, not physical-device or
wallet-extension acceptance.

`tools/build_documentation_release.py --docs-only` refreshes an independent
complete retained export for reading-only updates. The broader historical mode
without that flag also updates the shared product shell. It updates shared navigation, public handbook, downloads, search assets,
sitemap and the reviewed wallet-entry/throughput presentation in that historical
mode. The earlier entry revision was `documentation-20261013-v3`. Scientific WASM, worker execution,
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
