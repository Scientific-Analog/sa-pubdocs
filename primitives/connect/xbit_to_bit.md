---
title: "XMODEL primitive: xbit_to_bit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: xbit_to_bit
primitive_category: connect
description: "An xbit-to-bit connector."
date: 2026-03-11T07:20:43.486438
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE xbit_to_bit
An xbit-to-bit connector.

The `xbit_to_bit` primitive converts an xbit-type signal to a bit-type signal.

The parameter `width` sets the bit-width of the input and output signals in case they are vectors. The parameter `strength` sets the driving strength of the bit-type output signal (e.g. 4 for `weak`, 5 for `pull`, 6 for `strong`, and 7 for `supply`).

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. They can be used to suppress the propagation of logic X and Z values.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | wire | bit-type output |
| in | input | xbit | xbit-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | connector bit-width |
| strength | int | 6 | None | driving strength (0~7) |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

