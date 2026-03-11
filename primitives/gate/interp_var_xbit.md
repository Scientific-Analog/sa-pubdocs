---
title: "XMODEL primitive: interp_var_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: interp_var_xbit
primitive_category: gate
description: "A delay-interpolating buffer between two xbit-typed signals with variable delay."
date: 2026-03-11T07:20:43.563342
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE interp_var_xbit
A delay-interpolating buffer between two xbit-typed signals with variable delay.

The `interp_var_xbit` primitive is similar to the `interp_xbit` primitive, which takes two xbit-typed inputs and produces an xbit-typed output whose delay is referenced to a weighted average of the two inputs' arrival times. However, the difference is that the propagation delay of the `interp_var_xbit` primitive can be varied by the input `delay`, while that of the `interp_xbit` primitive is fixed.

The propagation delay of the `interp_var_xbit` primitive determines the maximum delay difference allowed between the two inputs. In other words, the primitive cannot interpolate two input pulses of which arrival times are apart by more than the propagation delay. If the second edge does not arrive until this delay after the arrival of the first edge, then the primitive may drive the output into an indeterminate state (1'bx). For instance, the difference between the arrival times of the two inputs, t0 and t1 are spaced by more than `delay` (i.e. t1-t0 > delay), then the output will have 1'bx during the period of t0+delay ~ t1+delay. The parameter `max_warn` sets the maximum warning message count for consecutive clock edges that violate this constraint. Setting it to 0 suppresses all warning messages and setting it to -1 displays them all.

The interpolation weight is controlled by the input `weight`, which spans the range from 0 to 1. For instance, if the rising edge of the first input `in_0` arrives at t0 and the rising edge of the second input `in_1` arrives at t1, the `interp_var_xbit` primitive produces a rising edge of its output at t_out:

```
    t_out = t0*(1-weight) + t1*weight + delay.
```

The `interp_var_xbit` primitive models an inertial delay, meaning that if a new input event arrives before the previous input event propagates to the output, the output event will be overridden with the one corresponding to the new input event.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output signal |
| in_0 | input | xbit | input signal 0 |
| in_1 | input | xbit | input signal 1 |
| weight | input | real | weighting signal |
| delay | input | xreal | propagation delay |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| max_warn | int | -1 | None | maximum warning count |

