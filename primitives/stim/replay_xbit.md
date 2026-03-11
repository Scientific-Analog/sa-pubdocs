---
title: "XMODEL primitive: replay_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: replay_xbit
primitive_category: stim
description: "A reproducer of an xbit-type signal stored in a waveform file"
date: 2026-03-11T07:20:43.464452
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE replay_xbit
A reproducer of an xbit-type signal stored in a waveform file

The `replay_xbit` primitive replays an xbit-typed signal stored in a waveform file. This primitive is useful when composing a testbench that feeds the previously-collected simulation results as inputs to a new device-under-test (DUT).

For instance, to replay a signal with a hierarchical name of `X1.Y1.a` stored in a waveform file named `mywaves.fsdb`, you can instantiate this `replay_xbit` primitive with the parameters `filename` and `signal` defined as below:

```
    xbit a;
    replay_xbit #(.filename("mywaves.fsdb"), .signal("X1.Y1.a")) inst_a (.out(a));
```

In case the waveform file stores the signal as a multi-bit vector, you must connect the primitive's output to an equal-width xbit vector and specify its bit width using the parameter `width`. For instance, the following example replays an 8-bit vector signal `X1.Y1.b[7:0]` stored in the waveform file.

```
    xbit [7:0] b;
    replay_xbit #(.filename("mywaves.fsdb"), .signal("X1.Y1.b[7:0]"), .width(8)) inst_b (.out(b));
```

Instead of replaying the whole waveform, you can replay a selected part of the waveform, of which start and stop time positions are defined by the parameters `start` and `stop`, respectively. For instance, if the parameter `start` is 100e-9 and `stop` is 200e-9, the `replay_xbit` primitive reproduces the waveform starting from the 100ns-position to the 200ns-position of the waveform, starting from the simulation time of zero. If the parameter `start` has a negative time value or the parameter `delay` has a positive time value, the primitive does not start replay until the simulation time of abs(start)+delay is elapsed and outputs a value defined by the parameter `init_value` or the initial value of the waveform at time=0 until then. On the other hand, when the primitive stops replay because it reaches the end of the waveform or a positive time value defined by the parameter `stop`, the primitive outputs a value defined by the parameter `final_value` or holds the last value of the waveform until the simulation ends.

**NOTE**: The current release supports the replay of waveforms only in FSDB-format files.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "" | None | waveform filename |
| signal | string | "" | None | signal name |
| width | int | 1 | None | signal bit-width |
| start | real | 0.0 | seconds | waveform time position to start replay |
| stop | real | -1.0 | seconds | waveform time position to stop replay |
| delay | real | 0.0 | seconds | initial delay before replay starts |
| init_value | logic | 1'bz | None | initial value before replay starts |
| final_value | logic | 1'bz | None | final value after replay stops |
| finish | int | 0 | None | finish simulation when replay stops |

