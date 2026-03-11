---
title: "XMODEL primitive: trig_posedge"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: trig_posedge
primitive_category: meas
description: "A trigger generator for an xbit-typed signal's rising transition events."
date: 2026-03-11T07:20:43.445958
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE trig_posedge
A trigger generator for an xbit-typed signal's rising transition events.

The `trig_posedge` primitive generates an xbit-typed trigger `out` when an xbit-typed signal `in` has the (N+k*P)-th rising transition after a specified delay, where k is 0, 1, 2, and so on. The triggering count N, period P, and delay are defined by the parameters `times`, `period`, and `delay`, respectively. When the parameter `times` is less than or equal to 0, the primitive triggers `out` whenever `in` has a rising transition after the delay. This primitive is equivalent to the `trig_edge` primitive with the `direction` parameter set to `+1`.

The xbit-typed trigger `out` can be used as an input to the measurement primitives to measure the time instants, delays, periods, etc. of the triggering events. The trigger signal is initialized to X and changes to 1 when the first event occurs. The trigger output `out` then toggles to a different value (0 or 1) whenever a subsequent event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output trigger |
| in | input | xbit | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay | real | 0.0 | seconds | triggering delay |
| times | int | 0 | None | triggering count |
| period | int | 0 | None | triggering period |

