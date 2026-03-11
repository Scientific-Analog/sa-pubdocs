---
title: "XMODEL primitive: filter_comb"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_comb
primitive_category: function
description: "An analog comb filter for xreal-typed signals."
date: 2026-03-11T07:20:43.350720
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_comb
An analog comb filter for xreal-typed signals.

The `filter_comb` primitive models a continuous-time comb filter, which can be described by the following Laplace s-domain transfer function:

```
            a0 + a1*exp(-s*T)
    H(s) = -------------------
            b0 + b1*exp(-s*T)
```

where the numerator coefficients a0 and a1 are defined by the parameter array `num_data` (namely, num_data[0] and num_data[1], respectively), and the denominator coefficients b0 and b1 are defined by the parameter array `den_data` (namely, den_data[0] and den_data[1], respectively). The value of the coefficient b0 (i.e. den_data[0] value) must not be zero.

Such comb filters are typically realized by combining the input signal in(t) or output signal out(t) and their delayed signals (in(t-T) or out(t-T), respectively) in a feedforward or feedback manner:

```
    Feedforward type : out(t) = a0*in(t) + a1*in(t-T)
    Feedback type    : out(t) = (a0*in(t) - b1*out(t-T))/b0
```

and this primitive can express both types of comb filters. The delay T is defined by the parameter `delay`.

Note that the transfer function of a comb filter basically describes a discrete-time system with a sampling period of T. To avoid a series of discrete-time events being generated and slowing down the simulation, the `filter_comb` primitive computes its response using an approximate, equivalent continuous-time transfer function instead.

Optionally, one can also describe the deviation of the delay from its nominal value set by the parameter `delay` as a function of frequency f, using the parameter array `delay_data`. This parameter `delay_data` defines the coefficients of a single-input polynomial function in the same way that the parameter `data` does for the primitive `poly_func`. For instance, setting `delay_data` to '{d0, d1} implies that the delay T would vary as a linear function with the frequency f:

```
    T(f) = delay + (d0 + d1*f).
```

Such variation in the delay can cause shifts in the periodic patterns of the comb filter's frequency response.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_data | real array | '{1.0, 0.0} | None | numerator coefficients (a0, a1) |
| den_data | real array | '{1.0, 0.0} | None | denominator coefficients (b0, b1) |
| delay | real | 1n | seconds | delay (T) |
| delay_data | real array | '{0.0} | seconds | delay variation data |
| filename | string | "" | None | parameter definition file |

