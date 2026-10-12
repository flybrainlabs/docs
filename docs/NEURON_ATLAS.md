# Neuron atlas — full source catalogue

Local page: `http://127.0.0.1:8787/atlas`.

This is an anatomical catalogue, not a neuronal firing simulator or a mining algorithm. The initial 20-type delivery has now been expanded by the batch program to **all 11,751 source types**. Every type has a representative official skeleton, normalized 3D geometry and a derived thumbnail.

One source exception is explicitly recorded: the combined page and right-side page for `VP2_adPN` return 404. The source catalogue's registered `VP2_adPN_L.html` page is available and identifies the same type, so its left-side statistics and body `10736` are used. The UI and table captions mark this limited scope; whole-type counts still come from the catalogue. The separately named `VP2+_adPN` is a different type and was not substituted. Thus catalogue coverage is complete, but this one type does not have full bilateral detail statistics.

## Delivered

- Native HTML/CSS/JavaScript matching the existing monochrome site; English default and Chinese toggle.
- Search by type/synonym/FlyWire name, anatomical region, ROI, predicted transmitter, superclass, dimorphism and side filters; twelve cards per page. Cards show enlarged thumbnails with names and compact metadata below; full descriptions remain in the main detail area.
- A distinct preview for each collected type, projected from an actual official SWC skeleton. No generated substitute anatomy or repeated placeholder image is used.
- One representative reconstruction per type rendered locally using Three.js. Pointer rotation, wheel/pinch zoom, keyboard controls, optional auto-rotation and view reset. Preview and detail identify the representative body ID; they do not claim to show every cell in the type. The detail view also overlays the official central brain, left/right optic lobe and VNC reference surfaces, with context/focus modes and outline visibility/opacity controls.
- Per-type descriptions generated mechanically from source annotations, plus explanations of cell counts, prediction uncertainty, classification, ROI, lineage and the difference between synapse sites and anatomical contacts.
- Source-derived summary statistics and 20,611 upstream/downstream/ROI rows across the initial collection. Clicking a collected partner changes the local selection; uncollected partners link to the source website.
- Local catalogue, detail JSON, normalized display geometry and SVG thumbnails. Ordinary catalogue browsing does not fetch the full brain dataset or automatically crawl uncollected types.

## Batch collection — no agent per item

From the project directory:

```bash
# Initial collection / resume the same first 20 types
.venv/bin/python -B tools/prepare_atlas.py --limit 20

# Extend to the first 200 source types, retaining existing collected entries
.venv/bin/python -B tools/prepare_atlas.py --limit 200 --workers 3

# Retry a particular source type without scanning all completed assets
.venv/bin/python -B tools/prepare_atlas.py --only VP2_adPN

# Explicitly collect every available type (can download many GB)
.venv/bin/python -B tools/prepare_atlas.py --all --workers 3
```

The script uses Python's standard library; it does not invoke an LLM, agent or paid inference API. Downloads use a bounded pool of 1–6 workers, reused TLS connections and bounded retries that respect server backoff. Successful source downloads are cached under `data/runtime/atlas-import/`; completed per-type display assets are reused. Re-running retries missing entries and keeps the existing successful catalogue. A smaller limit does not delete a larger existing collection. A process lock prevents concurrent producers from racing index writes. The live catalogue and `progress.json`/`failures.json` are checkpointed every 100 completed types or 45 seconds while progressing (`--progress-every` can change the batch threshold).

Display assets are generated under `web/data/atlas/`, with the index in `web/data/atlas.json`. Refresh the page after collection; a Rust rebuild is not needed for new data assets. The program reports unavailable skeletons rather than substituting fabricated thumbnails. The full collection is run as the transient user service `flypow-atlas-import`; its progress is recorded in `data/runtime/atlas-import/progress.json`.

## Anatomical context and stable selection

`tools/prepare_atlas_context.py` creates the shared `web/data/atlas-context.json` asset. It downloads the official `fullbrain-major-shells` (CB, OL(L), OL(R)) and `vnc-neuropil-shell-v2` meshes, vertex-clusters them on a 4 µm grid, and converts standard Neuroglancer mesh coordinates from nanometers to the same 8 nm voxel frame as the skeletons. The initial context asset has 194,946 triangles and is approximately 6 MB. It is a brain/VNC reference envelope, not a complete fruit-fly exterior with wings or legs.

The viewer reverses each skeleton's display-only normalization before mapping it into that shared context. Both surfaces and neurons then use the same center, scale and axis transform. Context meshes remain loaded when selecting another neuron. Whole-CNS view preserves rotation/zoom across selections; the focus mode frames the selected neuron.

Selecting a card only updates its selected state and the right-side detail; the existing card and image DOM nodes remain attached. Repeated selection does not reload the same completed view. The grid is rebuilt only when the visible page/filter result or language changes. Each page contains up to 12 cards without introductory paragraphs.

## Preview-first redesign — 2026-09-15

Latest card adjustment: the directory uses vertical cards with subtle borders and background selection, with the thumbnail above its name and metadata. Thumbnail display boxes are doubled at each existing breakpoint: 164×124 px on desktop, 140×112 px on tablet, 106×112 px on mobile, and 128×112 px in the narrow single-column layout. The existing compressed 640×400 images are reused without downloading larger assets. The 50/50 workspace, 12-item pagination, original-image fallback, stable selection and right-side profile remain unchanged. Earlier row-style iterations below are historical.

Previous iteration: the desktop workspace was split equally between the list and preview (50% / 50%), with two columns of borderless rows. The current card update retains the equal split and 12 items per page; the right side still stacks the figure above the full profile. The figure is not sticky, so it cannot obscure the profile while scrolling. Small-screen directory behavior remains responsive. `node tests/atlas_layout.mjs` checks these layout invariants. The narrow-rail design described below records an earlier iteration.

The page now uses a 190–240 px directory rail and a dominant, unboxed detail workspace. On wide screens the main area contains a large 3D figure and a separate readable profile column; connection tables stay within that main area below the figure. The tall title block, full-width filter form and bordered thumbnail cards were removed from this presentation.

Search remains in the rail. Filters and secondary display settings use compact disclosures; the explanatory guide and detailed provenance are collapsed by default. All underlying annotations, source links and the scoped-source warning remain available. On small screens, a Browse types control reveals the directory while the figure stays primary. The 12-item paging, stable selected image/DOM nodes, shared anatomy, focus/overview modes and English/Chinese behavior are retained.

The new stylesheet is `web/atlas-workbench.css`; the older `web/atlas.css` is retained but no longer loaded by `/atlas`. No data collection or changes to mining rules, balances or the data model were performed for this redesign. The interaction fixture checks the mobile directory toggle as well as selection and view controls. The new route, required assets, dictionary keys and unique control IDs passed HTTP/source checks, and the redesigned page was opened in the existing browser environment. This redesign record does not claim a separate visual or physical-device QA run.

`node tests/atlas_interaction.mjs` verifies card/image identity preservation, 12-item pagination, omitted card introductions, rapid-selection races and outline controls using a fixture DOM. `node tests/atlas_context.mjs` checks the four official mesh surfaces and the neuron/context coordinate transform. A browser check confirmed the four-part outline renders, a different neuron can be selected, and focus mode responds.

The input source snapshot is cached for reproducibility. The collector extends that snapshot; it is not a live annotation-update service. Existing catalogue/geometry files belong to this display importer and should not be edited manually during collection.

If a primary page returns 404/410, the importer may use a side page registered for that exact type in the source index. It checks the page's own type identity and records `source_scope` plus `resolved_source_path`; it does not silently merge a similarly named type. The live progress record describes the last invocation and separately reports full catalogue coverage and partial-source count.

## Sources, attribution and transformations

- Reiser Lab Cell Type Explorer: https://reiserlab.github.io/celltype-explorer-drosophila-male-cns/types.html
- Source snapshot: `male-cns:v1.0`, generated `2026-09-09 18:56:13`.
- Neuron type details and annotations are parsed from the source pages; source JavaScript is not executed or copied into the website.
- Representative body IDs are taken from each source page's selected Neuroglancer neurons.
- Coarse skeletons come directly from the official `flyem-male-cns` Google Cloud Storage bucket, using the download location published by the source explorer.
- The type catalogue and morphology data are used under CC BY 4.0. Attribution: Reiser Lab Cell Type Explorer; HHMI Janelia FlyEM, Cambridge and Google Research. Source projects do not endorse FlyPoW.
- Geometry is centered and uniformly scaled for display, with axes transformed to x, -z, y. Previews are orthographic projections of that same skeleton. These are visualization derivatives, not an official synapse-data mirror or a complete cell-type population model.
- SHA-256 source digests and source URLs are stored with the catalogue, details and geometry.

## Validation

Full-collection validation passed for **11,751 distinct previews and 3D geometries**, including body identity and local-file checks, and **7,828,735 source connection/ROI table rows**. All source types are present; the single scoped source exception is described above. Nine Python tests now cover the importer, persistent downloader/retries and same-type side-page fallback. The stable-selection and anatomical-context JavaScript tests also passed. The browser confirmed the explicit left-side warning for `VP2_adPN`, and the final view was restored to the full catalogue.

`node tests/atlas_data.mjs` checks the collected thumbnails/geometries, body identities, connection-table structure, description translation, filter/pagination behavior and external-link constraints. `.venv/bin/python -B -m unittest discover -s tests -v` includes source-parser, omitted HTML table-tag, single-side type, malformed SWC and shape-transformation tests. `cargo test --release` includes the new page route and regression tests for the existing ledger workflow.

Use `node tests/atlas_data.mjs 11751` to verify the full delivery's exact count. Omit the number to validate the current catalogue or supply a different expected count; no code edit is required.

The initial release passed 23 Rust tests, strict Clippy, five Python tests, wallet/validator regressions and the atlas data tests. HTTP checks returned success for `/atlas`, all 60 collected display assets and all required scripts. Resume testing reused all 20 completed entries without any fetch. The existing service was restarted and left active; its full-data load completed in 99.38 seconds, the saved mining proof still passed 11 checks, and network/account/issuance/candidate summaries were unchanged. The atlas page was opened in the local browser; this report does not claim an interactive browser QA run for the new page.

## Design-tool record

Stitch project: `8460224904550504030`. One atlas baseline request returned `Request contains an invalid argument`; there was no screen ID, exported HTML or exported screenshot. The page was implemented directly against the existing site design system. No generated Stitch design or preview is claimed as verified.

For the 2026-09-15 preview-first redesign, one new baseline request reused that same project. It again failed with `Request contains an invalid argument` (and transport abort messages), so there is no new screen ID or exported HTML/screenshot. The explicit layout requirements were implemented directly in native HTML/CSS while preserving the existing interactions.

The existing local Rust service is retained. Sites' 128 MB hosted runtime cannot hold this project's existing full-data computation service; this change does not migrate the backend, publish a separate cloud site or modify mainnet/memory-lock settings.
