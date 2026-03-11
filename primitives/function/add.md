---
title: "XMODEL primitive: add"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: add
primitive_category: function
description: "A multiple-input adder for xreal-typed signals."
date: 2026-03-11T07:20:43.337709
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE add
A multiple-input adder for xreal-typed signals.

The `add` primitive produces an xreal signal which is a sum of multiple

xreal-typed inputs. Using the parameters `num_in` and `scale`, one can

set the number of input signals to be added and their respective scale

factors.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signals |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int | 2 | None | number of inputs |
| scale | real array | '{1.0, 1.0} | None | input scale factors |

