---
title: "XMODEL primitive: transition"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: transition
primitive_category: function
description: "An xbit-to-xreal transition filter."
date: 2026-03-11T07:20:43.386550
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE transition
An xbit-to-xreal transition filter.

The `transition` primitive converts an xbit-typed, binary signal to an xreal-typed, analog signal, by assigning analog values to the 0- and 1-levels and optionally making the transition times finite. It can also model additional inertial delay.

The parameters `value0` and `value1` define the corresponding analog values to the input's 0 and 1 values, respectively. The parameters `rise_time` and `fall_time` define the rise and fall times of the 0-to-1 and 1-to-0 transitions, respectively. The parameters `rise_time` and `fall_time` by default have values of 0.0, in which case, the corresponding transition will occur instantaneously. If the parameter `rise_time` or `fall_time` takes a positive value, the value must be greater than the unit simulation time step (i.e. time precision).

The parameter `delay` specifies the optional inertial delay of the primitive applied before the conversion. In other words, if the xbit-typed input `in` changes to a new value before the time equal to `delay` elapses since the previous input value change, the previous input change event will be overriden by the new input change event. When the parameter `rise_time` or `fall_time` has a value greater than 0.0, the parameter `delay` assumes the minimum value equal to the unit simulation timestep (i.e. time precision).

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. Note that by default, the primitive ignores the logic X and logic Z values of the input and retains the last output value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | analog output |
| in | input | xbit | digital input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| value0 | real | 0.0 | None | value for logic 0 |
| value1 | real | 1.0 | None | value for logic 1 |
| rise_time | real | 0.0 | seconds | rise transition time |
| fall_time | real | 0.0 | seconds | fall transition time |
| delay | real | 0.0 | seconds | propagation delay |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

