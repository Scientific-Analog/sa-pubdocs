---
title: "XMODEL primitive: integ"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: integ
primitive_category: function
description: "An integration operator for xreal-typed signals."
date: 2026-03-11T07:20:43.362351
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE integ
An integration operator for xreal-typed signals.

The `integ` primitive computes the time-integral of an xreal-typed input signal `in`. It is equivalent to a linear filter with a transfer function of 1/s.

The parameters `init_value` and `scale` specify the output initial value of the integral and the input scale factor, respectively, as shown in the following equation.

```
    out = init_value + scale * integral(from 0 to t) of x(t) dt
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| init_value | real | 0.0 | None | initial output value |
| scale | real | 1.0 | None | input scale factor |

