---
title: "XMODEL primitive: meas_cross"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_cross
primitive_category: meas
description: "Measurement of the time instants of xreal-typed signal's crossing events."
date: 2026-03-11T07:20:43.401817
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_cross
Measurement of the time instants of xreal-typed signal's crossing events.

The `meas_cross` primitive measures the time instants when an xreal-typed signal `in` has the (N+k*P)-th event crossing a given threshold after a specified delay, where k is 0, 1, 2, and so on. The output is a real-typed value indicating the absolute time of each event. The threshold, triggering count N, period P, and delay are defined by the parameters `threshold`, `times`, `period`, and `delay`, respectively. When the parameter `times` is less than or equal to 0, the primitive updates the measurement whenever `in` crosses the threshold after the delay. The parameter `direction` specifies whether the primitive detects the rising events only (+1), falling events only (-1), or both (0).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | measurement output |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.0 | None | threshold level |
| direction | int | 0 | None | crossing direction |
| delay | real | 0.0 | seconds | triggering delay |
| times | int | 0 | None | triggering count |
| period | int | 0 | None | triggering period |

