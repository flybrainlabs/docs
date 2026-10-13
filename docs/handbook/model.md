# The scientific model

The source of anatomy is **MaleCNS v1.0**, an official fruit-fly central nervous system connectome. flybrainwork prepares a registered numerical graph from that source, then executes a frozen integer point-neuron model. Dataset anatomy, numerical assumptions and observed biological performance are different parts of the evidence.

## Graph and data counts

| Item | Registered value | Interpretation |
| --- | --- | --- |
| Neurons | 165,122 | Nodes in the prepared execution graph |
| Directed neuron pairs | 25,563,197 | Directed connected pairs; not original biological synapse count |
| Atlas types | 11,751 | Source catalog types used for anatomical browsing |
| Baseline step | 1 ms | Model-time increment |
| Baseline extent | 256 steps | 256 ms numerical trajectory; tasks may declare another frozen extent |

Source rows can include segmentation fragments and multiple observations. Always read a count's definition rather than equating every table row with a biological cell or synapse.

## Integer point-neuron LIF dynamics

The model tracks leakage, input accumulation, threshold events, reset, refractory state and propagation along connections. Integer rules and frozen parameters make the numerical contract replayable across implementations.

This point-neuron representation does not solve dendritic compartments. Currents, membrane states and stimulus cost use **model units**; they are not calibrated mV, pA or joules. Transmitter-to-sign mapping and related parameter choices contain assumptions.

The model's registered graph, parameters, initial state, time step and run extent are part of its identity. A changed parameter profile is a different scientific computation even when a page title stays the same.

## Paired A/B evaluation

A and B use the same model, zero initial state and background seed. B adds the candidate stimulus; A remains the control. The evaluator compares B minus A within windows defined relative to stimulus termination.

Metrics include net target events, positive response cells, absolute off-target change, selectivity and stimulus cost. Their exact windows, thresholds and eligibility rules belong to the frozen task. Local off-target constraints, including the O32 scope, do not establish whole-brain side-effect control.

The required background count R describes the numerical contract. It is not a confidence interval, a count of institutions or an estimate of biological reproducibility.

## What complete replay establishes

Complete replay establishes that submitted output agrees with the frozen numerical rules over all required backgrounds. Independent native/WASM/NumPy byte agreement is implementation reproduction. Neither alone establishes predictive accuracy against a living organism.

External validation requires authorized observations, licensing, a frozen calibration/holdout split, appropriate metrics and scientific review. These are outstanding gates; this project does not publish an established biological predictive accuracy.

## Source and licensing

Read the [official MaleCNS downloads](https://male-cns.janelia.org/download/) for source provenance. The [published connectome LIF methodology](https://www.nature.com/articles/s41586-024-07763-9) is a reference, not a validation result for this exact implementation.

Project source code licensing does not relicense the dataset or third-party assets. Before reusing a package, inspect its source and license disclosures. For the next step, read [Tasks and competition](/docs/tasks/) and [Results and reproduction](/docs/results/).
