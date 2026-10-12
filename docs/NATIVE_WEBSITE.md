# FlyPoW native website

This is the initial website delivery record. The current v0.2 release replaces the procedural fly with an official-data 3D brain, adds English/Chinese, wallets, validators, community and economics. See [TESTNET_VERIFICATION.md](TESTNET_VERIFICATION.md) for current checks; the historical results below describe the earlier implementation.

## Delivered routes

| Route | Purpose |
| --- | --- |
| `/` | Monochrome homepage with interactive Three.js fruit-fly specimen |
| `/mining` | Existing full-data mining, proof verification and synapse inspection |
| `/explorer` | Searchable, paginated local candidate-block archive |
| `/explorer/{hash}` | Stored proof details, export and server-side recomputation |
| `/roadmap` | Completed, current and planned milestones |
| `/whitepaper` | Full HTML reader with table of contents |
| `/whitepaper.md` | Downloadable protocol draft |
| `/blog` | Research/engineering notes index |
| `/blog/{slug}` | Three complete project articles |

## Implementation and visual design

- Native server-rendered HTML, shared CSS and vanilla JavaScript. No React/Vue, component framework, CDN runtime or frontend bundler.
- Black, white and neutral grays; restrained borders, editorial typography and consistent navigation.
- Three.js r180 is vendored locally, with its MIT license under `web/vendor/three/`.
- The fruit fly is a procedural **structural illustration**, not a reconstruction of the official electron-microscopy specimen. Geometry includes a head with compound-eye motifs, antennae, thorax, segmented abdomen, three leg pairs, wing pair and halteres.
- Pointer rotation, wheel zoom, keyboard rotation/zoom, two-pointer pinch zoom, wireframe, pause and reset are implemented. Reduced-motion preference is respected.
- CSS includes narrow-screen navigation and stacked content. Desktop browser inspection was completed; no separate physical touchscreen-device check was performed.
- Candidate records are created from actual mined proofs and saved atomically under `data/runtime/blocks/`. Record numbers are not network block heights. No chain confirmations, balances or transactions are fabricated.

## Design-tool result

Stitch project ID: `8460224904550504030`.

The single baseline generation request failed with `Request contains an invalid argument`; listing the project returned no screens. Screen ID: none. Exported Stitch HTML/screenshot paths: none. The implementation was authored directly to the user's explicit native HTML, Three.js and monochrome requirements. No generated Stitch design is represented as having been used or verified.

## Validation

- Release build and strict Clippy completed.
- 19 Rust tests passed, including persistence/reload, duplicate suppression, archive search and details, native page routes, missing article and asset-path rejection.
- Native scripts passed Node syntax checks.
- Browser inspection covered the homepage and Three.js rendering, wireframe, keyboard view adjustment, zoom, pause, six navigation entries, real mining and verification, candidate detail recomputation, roadmap, whitepaper anchors, blog list and article body.
- Actual pointer drag changed the visible view readout from `000°` to `026°`; a wheel event changed zoom from `1.00×` to `0.94×`. Reset restored the default view. Pointer inspection used the browser's documented DOM/CUA path after its selector-evaluation helper timed out.
- A real full-data proof with work hash `00c4aa6a55355bb88b83e41ed7ed63f4f11bc723ab9d7cd55cb7d1b9ee1a8c52` was generated through the mining page, saved to the candidate archive, opened in its detail page and passed all 11 recomputation checks.
- The service remains local at `http://127.0.0.1:8787/`; full data remained loaded during page checks.

The optional pre-existing WebMCP verification hook remains on the mining page. The browser integration provides no callable WebMCP validation context, so that optional hook was not independently exercised.
