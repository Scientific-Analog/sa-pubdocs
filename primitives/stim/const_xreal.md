---
title: "XMODEL primitive: const_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: const_xreal
primitive_category: stim
description: "A constant-value generator with xreal-typed outputs."
date: 2026-03-11T07:20:43.453818
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE const_xreal
A constant-value generator with xreal-typed outputs.

The `const_xreal` primitive generates a vector of constant xreal-typed outputs.

The bit-width and values of the constant outputs are set by the `width` and

`value` parameters, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | constant's bit-width |
| value | real array | '{0.0} | None | constant's values |

