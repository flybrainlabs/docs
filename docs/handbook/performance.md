# Performance and graphics

The mining interface reports actual neural updates per second, work progress and logs. These measurements help you tune a session. They do not measure biological predictive accuracy and do not independently determine compensation.

## Model time and wall-clock time

The registered baseline step represents 1 ms of model time. A 256-step trajectory represents 256 ms in that numerical model, regardless of how long the device takes to execute it. Wall-clock duration is measured separately.

Throughput can change with worker count, memory bandwidth, browser scheduling, temperature and background activity. Compare runs only when they use the same model, task extent and required background count.

## Tune workers conservatively

Start with a worker setting appropriate to available resources and watch memory, responsiveness and progress. Increasing concurrency can improve throughput until shared memory or scheduling becomes the bottleneck. More threads can also compete with 3D rendering and the rest of the browser.

Keep a saved checkpoint before making a major resource change. A faster trial that omits a required background is not equivalent to a complete one. Exact numerical optimization must preserve the frozen output contract.

## Use the 3D view

The monochrome view shows the brain and the lower neural context in a vertical frame, with slow central rotation where enabled. Display settings are grouped in the top controls. Graphics can be disabled independently so that a session can concentrate on computation.

Anatomical structure, current execution observations and historical samples are separate views. A source skeleton does not depict the activity of every cell, and a display sample does not replace complete scientific output.

## When rendering fails

Use the graphics retry or disable graphics, retain the error and compare with the [Neuron atlas](/atlas/). The atlas is a useful structural control page but uses its own browsing path. A successful atlas view does not by itself prove simultaneous complete-model computation and 3D performance.

Do not clear the model cache to repair a WebGL or display-resource fault. See [Troubleshooting](/docs/troubleshooting/) for a targeted diagnostic sequence.

## Device acceptance

Public WebGL and simulated viewport checks have passed. Physical Android Chrome, physical GPU, low-memory devices, higher concurrency, public 512-step workloads and simultaneous full computation/3D need their actual acceptance records.

A support report should identify browser version, device, available memory if known, worker setting, graphics mode, task/round and the actual stage that stopped. Record whether the same saved work resumes after a targeted retry. Avoid claiming physical-device support from a simulated mobile viewport.
