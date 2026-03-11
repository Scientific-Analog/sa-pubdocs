---
title: "XMODEL primitive: trig_time"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: trig_time
primitive_category: meas
description: "A trigger generator for timed events."
date: 2026-03-11T07:20:43.448439
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE trig_time
A trigger generator for timed events.

The `trig_time` primitive generates an xbit-typed trigger `out` at specified time instants. For instance, the parameters `delay` and `period` specify that the primitive shall trigger `out` when time is equal to delay + N*period, where N is 0, 1, 2, ... If `delay` is less than 0, the primitive triggers `out` at the end of simulation. If `period` is less than or equal to 0, the primitive triggers `out` only once. Alternatively, one can set the list of time instants at which the primitive shall trigger `out` using the parameter `data`.

The xbit-typed trigger `out` can be used as an input to the measurement primitives to measure the time instants, delays, periods, etc. of the triggering events. The trigger signal is initialized to X and changes to 1 when the first event occurs. The trigger output `out` then toggles to a different value (0 or 1) whenever a subsequent event occurs.

**NOTE**: some SystemVerilog simulators may not allow triggering new events at the end of simulation.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay | real | -1.0 | second | triggering delay |
| period | real | 0.0 | seconds | triggering period |
| data | real_array | '{-1.0} | seconds | list of triggering time instants |

