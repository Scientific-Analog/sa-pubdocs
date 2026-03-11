---
title: "XMODEL primitive: bit_to_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: bit_to_xreal
primitive_category: connect
description: "A bit-to-xreal connector."
date: 2026-03-11T07:20:43.473821
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE bit_to_xreal
A bit-to-xreal connector.

The `bit_to_xreal` primitive converts a bit-type signal to an xreal-type signal. The digital level of the input signal is converted to an analog level, defined by the conversion level parameters: `level0` and `level1`.

The parameters `level0` and `level1` define the conversion levels of logic 0 and logic 1, respectively. The parameters `rise_time` and `fall_time` define the finite rise and fall times of the 0-to-1 and 1-to-0 transitions, respectively.

The parameter `delay` specifies the inertial delay of the primitive. In other words, if a new input event arrives before the previous event finishes its transition, the new event's transition will override the current transition.

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. Note that by default, the primitive ignores the logic X and logic Z values of the input and retains the last output value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | xreal-type output |
| in | input | wire | bit-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | connector bit-width |
| level0 | real | 0.0 | None | conversion level for logic 0 |
| level1 | real | 1.0 | None | conversion level for logic 1 |
| rise_time | real | 0.0 | seconds | rise transition time |
| fall_time | real | 0.0 | seconds | fall transition time |
| delay | real | 0.0 | seconds | propagation delay |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

