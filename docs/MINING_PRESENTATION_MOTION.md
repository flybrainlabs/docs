# Mining presentation and motion

Release: `mining-depth-20261014-v2`.

The desktop mining console and anatomical panel use equal grid tracks with a
bounded gap. Narrow screens retain a single column. Both normal desktop and
short-screen desktop rules use the same equal-width layout.

## Loading and progress

The primary action has a persistent loading indicator, an accurate stage label,
`aria-busy` and a disabled state during preparation or a pending action. Its event
handler also rejects repeated clicks. Preparation cancellation has a separate
visible button next to the primary action. It uses the existing cancellation
controller and retains downloaded blocks and saved results.

Progress styling follows the native progress element's actual `value` and `max`.
The semantic native element remains in the DOM. A display layer interpolates
changes and moves monochrome stripes inside the measured portion. Unknown
progress uses an indeterminate animation without inventing a percentage. Idle
progress does not advance. Reduced motion removes decorative animation.

## Logs behind anatomy

The transparent anatomical renderer stays above a white monospace log layer.
Opaque dark backing uses the actual displayed anatomical surfaces, underneath
the original anatomy shading and neuronal lines. It blocks characters inside
the brain and lower nerve cord without obscuring their foreground details.
The backing shares existing geometry and follows its parent visibility,
rotation, pan, zoom and whole-CNS/brain-only framing. It adds no geometry
download, GPU readback or change to scientific computation. Log display waits
for foreground protection; disabling the anatomical outline or falling back
to a 2D trace retains the original accessible logs without overlaying text on
the scientific view.
Pointer events and selection remain with the original brain view. The backdrop
reads actual preparation stages, actual progress observations and existing
computation/candidate records. It does not generate arbitrary characters,
invent participants or advance counters. The existing accessible raw log and
download action remain available.

Only approved fields are formatted: stage, completed steps, neuron updates,
synaptic additions, elapsed observation time and shortened candidate identities.
Raw diagnostic details, session values and wallet fields are excluded. The
projection retains at most 36 records and formats them using the current UI
language. Decorative scrolling repeats the same timestamped records; it never
creates new observations or modifies the source log.

Complete locally qualified candidates are bold and labeled as awaiting
verification. Confirmed winners have their own bold state. Reward receipt is
displayed only with the existing finalized financial evidence and winner state.
A completed background or failed save does not become a claimed candidate win.

Scrolling pauses when the document or backdrop is off screen. Turning graphics
off removes the backdrop immediately. Reduced motion removes the scrolling
effect. Source computation, worker scheduling, progress counters, wallet
authorization and scientific identity are unchanged.

## Packaging and evidence

The complete export retains the scientific resources and the completed
community v2 release. Immutable resources may share hardlinks with the prior
export because available disk is smaller than another complete export. The
builder atomically replaces every changed artifact, verifies the original
baseline hash after each replacement and checks retained asset hashes. Do not
use an in-place writer on these retained hardlinks.

Browser acceptance exercises actual primary-button event wiring with a local
preparation fixture, native progress values, equal desktop columns, Chinese and
English, real software WebGL anatomy, layering and graphics/reduced-motion
controls. Log qualification/winner examples are isolated fixtures.
Framebuffer checks after rotation, pitch and zoom verify opaque protection
inside the anatomy, visible foreground detail, clear surrounding pixels and
protection of the lower nerve cord. The backdrop remains underneath the
foreground in both language and narrow-screen layouts. No official model is
downloaded, no scientific model is executed and no wallet funding is
performed by this presentation acceptance. Physical Android and extension-wallet
acceptance remain separate.

The existing RPC/mining failure is outside this presentation release. The
retained RPC configuration does not activate the pending private provider.
