---
title: "XMODEL primitive: filter"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter
primitive_category: function
description: "An analog linear filter for xreal-typed signals."
date: 2026-03-11T07:20:43.349539
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter
An analog linear filter for xreal-typed signals.

The `filter` primitive models a linear dynamical system, described by a Laplace s-domain transfer function and a transport delay.

The transport delay is set by the `delay` parameter. The transfer function of the primitive `filter` can be defined using one of the following two methods:

### 1) Specifying the DC gain, poles, and zeros of the filter

The first method specifies the transfer function with the following canonical form using the three parameters: `gain`, `poles`, and `zeros`.

```
               z(s)          (1+s/(2*pi*fz1))(1+s/(2*pi*fz2))...(1+s/(2*pi*fzN))
H(s) = gain * ----- = gain * ------------------------------------------------ ,
               p(s)          (1+s/(2*pi*fp1))(1+s/(2*pi*fp2))...(1+s/(2*pi*fpM))
```

where fz1, fz2, ... are the zero frequencies of the filter in Hz and fp1, fp2, ... are the pole frequencies of the filter in Hz.

The `gain` parameter specifies the DC gain of the filter. The `poles` and `zeros` parameters specify the lists of pole and zero frequencies, respectively, using the following real array format:

```
poles = '{real(fp1),imag(fp1), real(fp2),imag(fp2), ..., real(fpM),imag(fpM)}
zeros = '{real(fz1),imag(fz1), real(fz2),imag(fz2), ..., real(fzN),imag(fzN)}
```

Note that both the real and imaginary parts of each pole/zero frequency must be specified. For instance, to specify a DC pole (i.e., fp=0), the `poles` parameter must contain '{0.0, 0.0}. As a special case, the `zeros` parameter with a value of '{0} implies that the filter has no zeros (i.e. z(s) = 1).

The parameters `gain`, `poles`, `zeros`, and `delay` can be alternatively defined by a parameter definition file named `filename` in the following Python format:

```
poles = [real(fp1),imag(fp1), real(fp2),imag(fp2), ..., real(fpM),imag(fpM)]
zeros = [real(fz1),imag(fz1), real(fz2),imag(fz2), ..., real(fzN),imag(fzN)]
```

### 2) Specifying the coefficients of the partial fraction decomposition form

The second method specifies the transfer function in a partial fraction decomposition form (i.e. a sum of rational forms). The method is only supported in the parameter definition file:

```
           b1_real + j*b1_imag                 bN_real + j*bN_imag
H(s) = ---------------------------- + ... + ---------------------------- ,
       (s + a1_real + j*a1_imag)^m1         (s + aN_real + j*aN_imag)^mN
```

The coefficients `ai_real`, `ai_imag`, `bi_real`, `bi_imag`, and `mi` shall be listed in the file named `filename` in the following Python format:

```
    data = [ a1_real, a1_imag, b1_real, b1_imag, m1,
             a2_real, a2_imag, b2_real, b2_imag, m2,
             ...
             aN_real, aN_imag, bN_real, bN_imag, mN,
           ]
```

For both cases, the complex poles must be specified as conjugate pairs, otherwise an error will be reported.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| gain | real | 1.0 | None | DC gain |
| poles | real array | '{1.0e9, 0.0} | Hz | pole frequencies |
| zeros | real array | '{0.0} | Hz | zero frequencies |
| delay | real | 0.0 | seconds | transport delay |
| filename | string | "" | None | parameter definition file |

