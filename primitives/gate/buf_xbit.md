---
title: "XMODEL primitive: buf_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: buf_xbit
primitive_category: gate
description: "A logic buffer gate with xbit-typed input/output's."
date: 2026-03-11T07:20:43.553994
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE buf_xbit
A logic buffer gate with xbit-typed input/output's.

The `buf_xbit` primitive models a logic buffer gate with an inertial delay. It is suitable for processing digital signals of which precise timing information must be preserved.

The propagation delay of the logic gate is specified by the parameter `delay`. The implemented delay is `inertial`, meaning that if a new input event arrives before the previous input event propagates to the output, the output event will be overriden with the one corresponding to the new input event. If a transport delay behavior is desired, use the `delay_xbit` primitive instead.

The parameter `init_value` defines the initial output value at time=0.

The parameters `valueX` and `valueZ` define the mapped input values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. They can be used to suppress the propagation of logic X and Z values.

The parameter `twostate` is provided for legacy support. When set to 1, the primitive enforces a 2-state output by producing logic 0 outputs whenever the input has a logic X or logic Z value. For the `buf_xbit` primitive, this is equivalent to setting both `valueX` and `valueZ` to 0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output signal |
| in | input | xbit | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay | real | 0.0 | seconds | propagation delay (inertial) |
| init_value | logic | 1'bx | None | initial output value |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |
| twostate | bit | 0 | None | enforce 2-state output |

