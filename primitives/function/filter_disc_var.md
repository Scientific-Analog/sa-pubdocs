---
title: "XMODEL primitive: filter_disc_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_disc_var
primitive_category: function
description: "A variable discrete-time filter for xreal-typed signals."
date: 2026-03-11T07:20:43.354798
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_disc_var
A variable discrete-time filter for xreal-typed signals.

The `filter_disc_var` primitive models a discrete-time filter with an xreal-typed input, of which transfer function can be time-varying, controlled by real-typed inputs.

The primitive samples the input `in` at the rising edge of the trigger signal `trig` and processes the sampled signal with the following z-domain transfer function controlled by the inputs `num` and `den` to produce the output `out`:

```
             a0 + a1*z^(-1) + a2*z^(-2) + ... + aN*z^(-N)
    H(z) = ------------------------------------------------
             b0 + b1*z^(-1) + b2*z^(-2) + ... + bM*z^(-M)
```

where the numerator coefficients a0, a1, ..., aN are set by the real-typed array input `num` (i.e., num[0:N] = '{a0, a1, ..., aN}) and the denominator coefficients b0, b1, ..., bM are set by the real-typed array input `den` (i.e., den[0:M] = '{b0, b1, ..., bM}). The value of the coefficient b0 (i.e. den[0]) must not be zero at all times. The parameters `order_num` and `order_den` specify the order of the numerator (N) and the order of the denominator (M) of the transfer function, respectively.

If the order of the denominator `order_den` is 0 (i.e., M=0), the primitive models a discrete-time filter with a finite impulse response (FIR). Otherwise, the primitive models a discrete-time filter with an infinite impulse response. The parameter `init_value` specifies the initial output value of the filter.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| trig | input | xbit | trigger signal |
| num | input | real | numerator coefficients |
| den | input | real | denominator coefficients |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| order_num | int | 0 | None | order of numerator |
| order_den | int | 0 | None | order of denominator |
| init_value | real | `NaN | None | initial output value |

