---
title: "XMODEL primitive: power"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: power
primitive_category: function
description: "A power operator for xreal-typed signals."
date: 2026-03-11T07:20:43.373891
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE power
A power operator for xreal-typed signals.

The `power` primitive computes the xreal-typed input `in` raised to the power of `index`, i.e. `in^index`. For instance, with an index of 2, the primitive returns `in*in` and with an index of 3, it returns `in*in*in`.

Note that only non-negative integer exponentiation indices are supported currently.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| index | real | 2 | None | exponent of power |

