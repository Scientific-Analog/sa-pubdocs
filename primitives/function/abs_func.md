---
title: "XMODEL primitive: abs_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: abs_func
primitive_category: function
description: "An absolute value function for an xreal-type signal."
date: 2026-03-11T07:20:43.334671
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE abs_func
An absolute value function for an xreal-type signal.

The `abs_func` primitive produces an xreal-typed output which is the absolute value of an xreal-typed input. That is,

```
    out = abs(in) = |in|.
```

The parameter `scale` sets the additional scale factor applied to the output.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | scale factor |

