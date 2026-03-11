---
title: "XMODEL primitive: xreal_to_bit_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: xreal_to_bit_var
primitive_category: connect
description: "An xreal-to-bit connector with variable logic-1 and logic-0 levels."
date: 2026-03-11T07:20:43.494396
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE xreal_to_bit_var
An xreal-to-bit connector with variable logic-1 and logic-0 levels.

The `xreal_to_bit_var` primitive converts an xreal-type signal to a bit-type signal with variable logic-1 and logic-0 levels. The threshold level required to convert the analog level of the input `in` to a digital level of the output `out` is computed as a mid-level between the two inputs `level1` and `level0`.

The parameter `strength` defines the driving strength of the bit-type output signal (e.g. 4 for `weak`, 5 for `pull`, 6 for `strong`, and 7 for `supply`).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | wire | bit-type output |
| in | input | xreal | xreal-type input |
| level0 | input | xreal | conversion level for logic 0 |
| level1 | input | xreal | conversion level for logic 1 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | connector bit-width |
| strength | int | 6 | None | driving strength (0~7) |

