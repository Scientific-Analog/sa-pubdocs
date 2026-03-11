---
title: "XMODEL primitive: sqrt_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: sqrt_func
primitive_category: function
description: "A square-root function for an xreal-typed signal."
date: 2026-03-11T07:20:43.385316
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE sqrt_func
A square-root function for an xreal-typed signal.

The `sqrt_func` primitive produces an xreal-typed output which is a square-root of an xreal-typed input. That is,

```
    out = sqrt(in).
```

The parameter `scale` sets the additional scale factor applied to the output.

The primitive approximates the square-root function with a piecewise-linear (PWL) function and the parameters `abstol` and `reltol` set the absolute and relative tolerances of such PWL approximation, respectively. Specifically, the parameter `abstol` determines the width of the first PWL section and the parameter `reltol` determines how the widths of the subsequent PWL sections scale progressively.

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | scale factor |
| abstol | real | 1e-4 | None | absolute tolerance |
| reltol | real | 1e-2 | None | relative tolerance |

