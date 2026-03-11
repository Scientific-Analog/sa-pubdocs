---
title: "XMODEL primitive: filter_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_var
primitive_category: function
description: "A variable filter for xreal-typed signals."
date: 2026-03-11T07:20:43.358870
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_var
A variable filter for xreal-typed signals.

The `filter_var` primitive models a linear dynamical system whose gain, poles, and zeros are time-varying, controlled by real-typed inputs, `gain`, `poles`, and `zeros`, respectively.

The `gain` input specifies the DC gain of the filter. The `poles` and `zeros` inputs specify the lists of pole and zero frequencies, respectively, using the following real-typed array format:

```
poles = '{real(fp1),imag(fp1), real(fp2),imag(fp2), ..., real(fpM),imag(fpM)}
zeros = '{real(fz1),imag(fz1), real(fz2),imag(fz2), ..., real(fzN),imag(fzN)}
```

where fp1, fp2, ... are the pole frequencies of the filter in Hz and fz1, fz2, ... are the zero frequencies of the filter in Hz. Note that one must specify both the real and imaginary values of each pole or zero. For instance, to specify a DC pole (i.e., fp=0), the `poles` input must contain '{0.0, 0.0}. Assigning '{`INFINITY, `INFINITY} value to the `poles` or `zeros` input places the corresponding pole or zero at infinity, effectively removing its presence. For instance, a filter_var primitive would have no zero if its `zeros` input is set to '{`INFINITY, `INFINITY} even when its `num_zeros` parameter is set to 1. When the `num_poles` or `num_zeros` parameter is set to 0, the corresponding `poles` or `zeros` inputs must still be fed with an array of two real values such as '{0.0, 0.0}.

The transfer function of this `filter_var` primitive is then defined as the following canonical form:

```
             z(s)         (1+s/(2pi*fz1))(1+s/(2pi*fz2))...(1+s/(2pi*fzN))
H(s) = gain*----- = gain* ------------------------------------------------ ,
             p(s)         (1+s/(2pi*fp1))(1+s/(2pi*fp2))...(1+s/(2pi*fpM))
```

The `filter_var` primitive can also model an ideal all-pass variable-gain amplifier. In this case, the number of poles and the number of zeros should be set to 0, and both the `poles` and `zeros` inputs should be set to '{0.0, 0.0}.

The parameter `delay` sets the transport delay from the input to output in seconds. For synchronization reasons, the transport delay value must be at least a unit timestep.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| gain | input | real | DC gain |
| poles | input | real | pole frequencies |
| zeros | input | real | zero frequencies |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_poles | int | 2 | None | number of poles |
| num_zeros | int | 1 | None | number of zeros |
| delay | real | 0.0 | seconds | transport delay |

