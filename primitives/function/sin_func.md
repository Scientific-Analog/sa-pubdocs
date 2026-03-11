---
title: "XMODEL primitive: sin_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: sin_func
primitive_category: function
description: "A sinusoidal function for an xreal-typed signal."
date: 2026-03-11T07:20:43.382800
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE sin_func
A sinusoidal function for an xreal-typed signal.

The `sin_func` primitive produces an xreal-typed output which is a sinusoidal function of an xreal-typed input. That is,

```
    out = f(in),
```

where the function f() can be either sin() or cos() function, depending on the parameter `mode`. Set the parameter `mode` to "sin" for sin() function and "cos" for cos() function. The parameter `scale` sets the additional scale factor applied to the output.

The primitive first approximates the input as a piecewise-linear (PWL) waveform before computing its sinusoidal function output. The parameters `abstol` and `reltol` set the absolute and relative tolerances of such PWL approximation, respectively.

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| mode | string | 'sin' | None | function type ("sin" or "cos") |
| scale | real | 1.0 | None | scale factor |
| abstol | real | 1e-4 | None | absolute tolerance for input |
| reltol | real | 1e-2 | None | relative tolerance for input |

