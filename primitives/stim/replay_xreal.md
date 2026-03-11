---
title: "XMODEL primitive: replay_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: replay_xreal
primitive_category: stim
description: "A reproducer of an xreal-type signal stored in a waveform file"
date: 2026-03-11T07:20:43.465811
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE replay_xreal
A reproducer of an xreal-type signal stored in a waveform file

The `replay_xreal` primitive replays an xreal-typed signal stored in a waveform file. This primitive is useful when composing a testbench that feeds the previously-collected simulation results as inputs to a new device-under-test (DUT).

For instance, to replay a signal with a hierarchical name of `X1.Y1.a` stored in a waveform file named `mywaves.fsdb`, you can instantiate this `replay_xreal` primitive with the parameters `filename` and `signal` defined as below:

```
    xreal a;
    replay_xreal #(.filename("mywaves.fsdb"), .signal("X1.Y1.a")) inst_replay (.out(a));
```

The `replay_xreal` primitive tries to reduce the number of events generated while keeping the error within the tolerance specified. The parameters `abstol` and `reltol` set the absolute and relative tolerances for this event-filtering, respectively.

Instead of replaying the whole waveform, you can replay a selected part of the waveform, of which start and stop time positions are defined by the parameters `start` and `stop`, respectively. For instance, if the parameter `start` is 100e-9 and `stop` is 200e-9, the `replay_xreal` primitive reproduces the waveform starting from the 100ns-position to the 200ns-position of the waveform, starting from the simulation time of zero. If the parameter `start` has a negative time value or the parameter `delay` has a positive time value, the primitive does not start replay until the simulation time of abs(start)+delay is elapsed and outputs a value defined by the parameter `init_value` or the initial value of the waveform at time=0 until then. On the other hand, when the primitive stops replay because it reaches the end of the waveform or a positive time value defined by the parameter `stop`, the primitive outputs a value defined by the parameter `final_value` or holds the last value of the waveform until the simulation ends.

**NOTE**: The current release supports the replay of waveforms only in FSDB-format files.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "" | None | waveform filename |
| signal | string | "" | None | signal name |
| abstol | real | 1e-4 | None | absolute tolerance for event-filtering |
| reltol | real | 1e-2 | None | relative tolerance for event-filtering |
| start | real | 0.0 | seconds | waveform time position to start replay |
| stop | real | -1.0 | seconds | waveform time position to stop replay |
| delay | real | 0.0 | seconds | initial delay before replay starts |
| init_value | real | `NaN | None | initial value before replay starts |
| final_value | real | `NaN | None | final value after replay stops |
| finish | int | 0 | None | finish simulation when replay stops |

