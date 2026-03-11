---
title: "XMODEL primitive: exp_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: exp_func
primitive_category: function
description: "An exponential function for an xreal-typed signal."
date: 2026-03-11T07:20:43.348325
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE exp_func
An exponential function for an xreal-typed signal.

The `exp_func` primitive produces an xreal-typed output which is an exponential function of an xreal-typed input. That is,

```
    out = exp(in).
```

The parameter `base` sets the base of the exponential function (default: M_E=2.718282). The parameter `scale` sets the additional scale factor applied to the output.

The primitive first approximates the input as a piecewise-linear (PWL) waveform before computing its exponential function output. The parameters `abstol` and `reltol` set the absolute and relative tolerances of such PWL approximation, respectively.

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| base | real | M_E | None | base of the exponential function |
| scale | real | 1.0 | None | scale factor |
| abstol | real | 1e-4 | None | absolute tolerance for input |
| reltol | real | 1e-2 | None | relative tolerance for input |

