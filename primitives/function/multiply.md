---
title: "XMODEL primitive: multiply"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: multiply
primitive_category: function
description: "A multiple-input multipler for xreal-typed signals."
date: 2026-03-11T07:20:43.369857
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE multiply
A multiple-input multipler for xreal-typed signals.

The `multiply` primitive produces an xreal signal which is a product of multiple xreal-typed inputs. The parameter `num_in` specifies the number of input signals which form an array for the input `in`.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signals |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int | 2 | None | number of inputs |

