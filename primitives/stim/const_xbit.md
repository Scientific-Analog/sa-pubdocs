---
title: "XMODEL primitive: const_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: const_xbit
primitive_category: stim
description: "A constant-value generator with xbit-typed output."
date: 2026-03-11T07:20:43.452549
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE const_xbit
A constant-value generator with xbit-typed output.

The `const_xbit` primitive generates a constant xbit-typed vector output.

The bit-width and value of the constant output are set by the `width` and

`value` parameters, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | constant's bit-width |
| value | logic | 0 | None | constant's value |

