---
title: "XMODEL primitive: bit_to_real"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: bit_to_real
primitive_category: connect
description: "A bit-to-real connector."
date: 2026-03-11T07:20:43.469927
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE bit_to_real
A bit-to-real connector.

The `bit_to_real` primitive converts a bit-type signal to a real-type signal. The digital level of the input signal is converted to an analog level, defined by the conversion level parameters: `level0` and `level1`. The output signal makes instantaneous transitions with zero rise/fall times.

The parameter `delay` specifies the inertial delay of the primitive. In other words, if a new input event arrives before the previous event propagates to the output, the previous event will be cancelled.

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. Note that by default, the primitive ignores the logic X and logic Z values of the input and retains the last output value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | real-type output |
| in | input | wire | bit-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| level0 | real | 0.0 | None | conversion level for logic 0 |
| level1 | real | 1.0 | None | conversion level for logic 1 |
| delay | real | 0.0 | seconds | propagation delay |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

