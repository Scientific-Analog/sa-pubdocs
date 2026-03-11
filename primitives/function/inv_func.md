---
title: "XMODEL primitive: inv_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: inv_func
primitive_category: function
description: "A multiplicative inverse function (i.e. reciprocal function) for an xreal-typed signal."
date: 2026-03-11T07:20:43.366202
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE inv_func
A multiplicative inverse function (i.e. reciprocal function) for an xreal-typed signal.

The `inv_func` primitive produces an xreal-typed output which is a reciprocal of an xreal-typed input. That is,

```
    out = 1/in.
```

The parameter `scale` sets the additional scale factor applied to the output.

The primitive approximates the 1/x function with a piecewise-linear (PWL) function and the parameters `abstol` and `reltol` set the absolute and relative tolerances of such PWL approximation, respectively. Specifically, the parameter `abstol` determines the smallest input possible (=abstol) and largest input possible (=1/abstol), and the parameter `reltol` determines the interval width of each PWL section.

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
| abstol | real | 1e-12 | None | absolute tolerance |
| reltol | real | 1e-2 | None | relative tolerance |

