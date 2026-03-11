---
title: "XMODEL primitive: integ_mod"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: integ_mod
primitive_category: function
description: "An integration with modulo operator for xreal-typed signals."
date: 2026-03-11T07:20:43.363786
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE integ_mod
An integration with modulo operator for xreal-typed signals.

The `integ_mod` primitive computes the time-integral of an xreal-typed input signal `in`. Its difference with the `integ` primitive is that it produces a bounded output ranging from `offset` to 'offset + modulus' via a modulo operation.

As with the `integ` primitive, the parameters `init_value` and `scale` specify the output initial value of the integral and the input scale factor, respectively, the equation governing the output signal `out` is as follows:

```
    out = modulo(init_value-offset + scale*integral(from 0 to t) of x(t) dt)
          + offset
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
| init_value | real | 0.0 | None | output initial value |
| modulus | real | 1.0 | None | output modulus |
| offset | real | 0.0 | None | output offset |

