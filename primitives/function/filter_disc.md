---
title: "XMODEL primitive: filter_disc"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_disc
primitive_category: function
description: "A discrete-time filter for xreal-typed signals."
date: 2026-03-11T07:20:43.353656
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_disc
A discrete-time filter for xreal-typed signals.

The `filter_disc` primitive models a discrete-time filter with an xreal-typed input. The primitive samples the input `in` at the rising edge of the trigger signal `trig` and processes the sampled signal with the following z-domain transfer function to produce the output `out`:

```
             a0 + a1*z^(-1) + a2*z^(-2) + ... + aN*z^(-N)
    H(z) = ------------------------------------------------
             b0 + b1*z^(-1) + b2*z^(-2) + ... + bM*z^(-M)
```

where the numerator coefficients a0, a1, ..., aN are defined by the parameter array `num` (i.e., num[0:N] = '{a0, a1, ..., aN}) and the denominator coefficients b0, b1, ..., bM are defined by the parameter array `den` (i.e., den[0:M] = '{b0, b1, ..., bM}). The value of the coefficient b0 (i.e., den[0]) must not be zero.

If the order of the denominator is 0 (i.e., M=0), the primitive models a discrete-time filter with a finite impulse response (FIR). Otherwise, the primitive models a discrete-time filter with an infinite impulse response. The parameter `init_value` specifies the initial output value of the filter.

The parameters `num`, `den`, `init_value` can be alternatively defined by a parameter definition file named `filename` in the following Python format:

```
    num = [a0, a1, a2, ..., aN]
    den = [b0, b1, b2, ..., bM]
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| trig | input | xbit | trigger signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num | real array | '{1.0} | None | numerator coefficients |
| den | real array | '{1.0} | None | denominator coefficients |
| init_value | real | `NaN | None | initial output value |
| filename | string | "" | None | parameter definition file |

