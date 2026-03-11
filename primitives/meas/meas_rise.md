---
title: "XMODEL primitive: meas_rise"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_rise
primitive_category: meas
description: "Measurement of the time instants of xreal-typed signal's rising events."
date: 2026-03-11T07:20:43.417292
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_rise
Measurement of the time instants of xreal-typed signal's rising events.

The `meas_rise` primitive measures the time instants when an xreal-typed signal `in` has the (N+k*P)-th event rising above a given threshold after a specified delay, where k is 0, 1, 2, and so on. The output is a real-typed value indicating the absolute time of each event. The threshold, triggering count N, period P, and delay are defined by the parameters `threshold`, `times`, `period`, and `delay`, respectively. When the parameter `times` is less than or equal to 0, the primitive updates the measurement whenever `in` rises above the threshold after the delay. It is equivalent to the `meas_cross` primitive with the parameter `direction` set to `+1`.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | measurement output |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.0 | None | threshold level |
| delay | real | 0.0 | seconds | triggering delay |
| times | int | 0 | None | triggering count |
| period | int | 0 | None | triggering period |

