# Canonical Result V3 layout

The program owns exactly 1024 bytes with discriminator `FBMRV003`. Fields use
little-endian integers and raw 32-byte public keys/commitments. This is a checked
scientific summary, not the complete spike-event archive or the model itself.
The full response archives are retained under their content commitments.

| Offset | Length | Field |
| --- | --- | --- |
| 0 | 8 | `FBMRV003` discriminator |
| 8 | 2 | Version, 3 |
| 10 | 2 | Reserved, zero |
| 12 | 4 | Total size, 1024 |
| 16 | 800 | 25 ordered bindings below |
| 816 | 8 | Original grant generation |
| 824 | 8 | Project round sequence |
| 832 | 8 | Scientific claim sequence |
| 840 | 8 | Frozen reward atoms |
| 848 | 8 | Actual result rent lamports |
| 856 | 8 | Winner acceptance slot |
| 864 | 8 | Settlement slot |
| 872 | 8 | Settlement Unix time, signed |
| 880 | 2 | Required complete backgrounds |
| 882 | 2 | Actual complete backgrounds |
| 884 | 4 | Simulation steps, 256 |
| 888 | 4 | Model neurons, 165122 for this plan |
| 892 | 4 | Metrics version, 1 |
| 896 | 128 | 16 ordered signed 64-bit metrics below |

Binding `i` begins at `16 + 32*i`: genesis identity, program, frozen policy,
stage, economic task, logical discovery unit (zero), project round, candidate,
claim, stable contribution, model root, graph root, parameter profile,
goal result root, manifest root, complete archive root, miner wallet,
fixed reward wallet, original grant ID, original session key, permanent unit PDA,
original grant PDA, settler policy, complete replay evidence root, final
scientific winner proof.

The metrics are: summed baseline spikes; candidate stimulus cost; first-window
minimum target net spikes, maximum off-target absolute change and minimum
positive-cell count; second-window equivalents; summed actual neuron updates;
summed actual synaptic additions; total full response bytes; distinct complete
replay certificates; complete backgrounds; three reserved zeros.

The first accepted winner certificate freezes the prepared summary. Settlement
fills rent, acceptance/settlement slots and time, computes the final result hash
and stores it in the permanent unit. The transaction creates/writes the Result,
consumes only actual missing rent, updates grant/stage counters and transfers the
frozen reward atom amount atomically. Failed execution retains no business effect;
the transaction fee remains the relayer's separate cost.

The Result is immutable after payment. Only the configured project authority may
close it after retention and two authorized finalized-archive certificates. Rent
returns only to the fixed project recipient. Permanent paid/uniqueness state and
checked archives remain, preventing recreation or another reward. Withdrawal of
unused miner principal is a separate miner-signed instruction.
