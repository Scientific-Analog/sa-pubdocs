---
title: "XMODEL primitive: scale"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: scale
primitive_category: function
description: "A scaler for an xreal-typed signal."
date: 2026-03-11T07:20:43.379211
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE scale
A scaler for an xreal-typed signal.

The `scale` primitive produces an xreal-typed output which is a scaled version of an xreal-typed input. The parameter `scale` determines the scale factor.

For passband signals, the `scale` primitive can also add a phase shift specified by the parameter `phase`. For basebase signals, this parameter has no effects.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | scale factor |
| phase | real | 0.0 | radians | phase shift |

