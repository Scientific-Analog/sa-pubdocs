---
title: "XMODEL primitive: trig_cross"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: trig_cross
primitive_category: meas
description: "A trigger generator for an xreal-typed signal's crossing events."
date: 2026-03-11T07:20:43.440703
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE trig_cross
A trigger generator for an xreal-typed signal's crossing events.

The `trig_cross` primitive generates an xbit-typed trigger `out` when an xreal-typed signal `in` has the (N+k*P)-th event crossing a given threshold after a specified delay, where k is 0, 1, 2, and so on. The threshold, triggering count N, period P, and delay are defined by the parameters `threshold`, `times`, `period`, and `delay`, respectively. When the parameter `times` is less than or equal to 0, the primitive triggers `out` whenever `in` crosses the threshold after the delay. The parameter `direction` specifies whether the primitive detects the rising events only (+1), falling events only (-1), or both (0).

The xbit-typed trigger `out` can be used as an input to the measurement primitives to measure the time instants, delays, periods, etc. of the triggering events. The trigger signal is initialized to X and changes to 1 when the first event occurs. The trigger output `out` then toggles to a different value (0 or 1) whenever a subsequent event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output trigger |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.0 | None | threshold level |
| direction | int | 0 | None | crossing direction |
| delay | real | 0.0 | seconds | triggering delay |
| times | int | 0 | None | triggering count |
| period | int | 0 | None | triggering period |

