---
title: "XMODEL primitive: deriv"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: deriv
primitive_category: function
description: "A derivative operator for xreal-typed signals."
date: 2026-03-11T07:20:43.347258
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE deriv
A derivative operator for xreal-typed signals.

The `deriv` primitive computes the derivative of an xreal-typed signal `in`. For instance, if the input signal x(t) is cos(wt+phi), then the primitive will return an output dx(t)/dt equal to w*sin(wt+phi).

The parameter `scale` specifies an additional input scale factor, i.e.,

```
    out = scale * d(in)/dt
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | input scale factor |

