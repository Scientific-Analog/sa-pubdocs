---
title: "XMODEL primitive: log_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: log_func
primitive_category: function
description: "A logarithmic function for an xreal-typed signal."
date: 2026-03-11T07:20:43.368611
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE log_func
A logarithmic function for an xreal-typed signal.

The `log_func` primitive produces an xreal-typed output which is a logarithmic function of an xreal-typed input. That is,

```
    out = log(in).
```

The parameter `base` sets the base of the logarithmic function (default: M_E=2.718282). The parameter `scale` sets the additional scale factor applied to the output.

The primitive approximates the logarithmic function with a piecewise-linear (PWL) function and the parameters `abstol` sets the absolute tolerance of such PWL approximation. Specifically, the parameter `abstol` determines the number of PWL sections per decade.

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| base | real | M_E | None | base of the log function |
| scale | real | 1.0 | None | scale factor |
| abstol | real | 1e-3 | None | absolute tolerance |

