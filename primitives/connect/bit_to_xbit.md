---
title: "XMODEL primitive: bit_to_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: bit_to_xbit
primitive_category: connect
description: "A bit-to-xbit connector."
date: 2026-03-11T07:20:43.472650
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE bit_to_xbit
A bit-to-xbit connector.

The `bit_to_xbit` primitive converts a bit-type signal to an xbit-type signal.

The parameter `width` sets the bit-width of the input and output signals in case they are vectors.

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. They can be used to suppress the propagation of logic X and Z values.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | xbit-type output |
| in | input | wire | bit-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | connector bit-width |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

