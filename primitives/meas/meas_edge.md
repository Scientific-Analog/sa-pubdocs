---
title: "XMODEL primitive: meas_edge"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_edge
primitive_category: meas
description: "Measurement of the time instants of an xbit-typed signal's transition events."
date: 2026-03-11T07:20:43.405544
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_edge
Measurement of the time instants of an xbit-typed signal's transition events.

The `meas_edge` primitive measures the time instants when an xbit-typed signal `in` has the (N+k*P)-th transition after a specified delay, where k is 0, 1, 2, and so on. The output is a real-typed value indicating the absolute time of each event. The triggering count N, period P, and delay are defined by the parameters `times`, `period`, and `delay`, respectively. When the parameter `times` is less than or equal to 0, the primitive updates the measurement whenever `in` has a transition after the delay. The parameter `direction` specifies whether the primitive detects the rising events only (+1), falling events only (-1), or both (0).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | measurement output |
| in | input | xbit | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| direction | int | 0 | None | crossing direction |
| delay | real | 0.0 | seconds | triggering delay |
| times | int | 0 | None | triggering count |
| period | int | 0 | None | triggering period |

