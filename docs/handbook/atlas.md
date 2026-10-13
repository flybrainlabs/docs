# Neuron atlas

The [Neuron atlas](/atlas/) is a structural browsing tool for **11,751 source types**. It helps you relate task targets and anatomical annotations to representative official skeletons. Ordinary browsing loads display resources rather than downloading the complete execution model.

## Find a type

Use type names, aliases or FlyWire names in search. The directory supports filters for anatomical region, ROI, predicted transmitter, superclass, dimorphism and side where the source provides those fields. Reset a restrictive filter when an expected type disappears.

Select a type to update the representative viewer and profile. Pagination limits the visible directory, while selected detail explains the source annotations. A collected partner can link to another local type; other partners may link to the official source.

## Read the representative view

Each type has a source-derived representative skeleton and body ID. The view does not contain every cell in that type. Thumbnails are derived from actual skeleton geometry rather than reused placeholder anatomy.

Rotate with the pointer, zoom with wheel/pinch, use supported keyboard controls, reset the view or enable optional auto-rotation. The context view includes the official central brain, left/right optic lobes and ventral nerve cord envelopes. These reference surfaces are not a complete external fly body with wings and legs.

The shared context and skeleton coordinates are mapped consistently for display. Focus mode frames the selected neuron; the whole-CNS mode preserves spatial context.

## Interpret annotations carefully

| Annotation | How to read it |
| --- | --- |
| Predicted transmitter | A source prediction; inspect its stated uncertainty |
| Cell count | The source scope, which may include side-specific statistics |
| ROI | A region of interest used to describe anatomical coverage |
| Upstream/downstream partners | Source-derived connectivity summaries, not a live causal experiment |
| Representative body | The exact reconstruction used for the displayed shape |
| Dimorphism/classification | Source annotations, with their own completeness and assumptions |

Source descriptions are mechanically derived from annotations. Do not infer observed behavior from a classification label alone. Synapse sites, anatomical contacts and the prepared graph's directed pairs describe different measurements.

## Known source exception

For **VP2_adPN**, the combined and right-side source pages returned 404 during collection. The registered left-side page was available and provided the representative body **10736** and limited detail statistics. Whole-type counts still come from the catalog; detail scope is marked accordingly.

The separately named VP2+_adPN is a different type and was not substituted. Complete catalog coverage therefore does not mean every type has bilateral detail statistics.

## Relate anatomy to computation

Use related response evidence and [Results](/results/) to follow a body or task into a numerical record. Anatomy, live observations and historical samples remain distinct. Selecting a type does not automatically run a simulation or upload your local history.

If 3D fails, retain the error and use the directory/profile information while following [Performance and graphics](/docs/performance/). Physical Android acceptance remains pending even when simulated layouts pass.
