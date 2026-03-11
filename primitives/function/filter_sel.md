---
title: "XMODEL primitive: filter_sel"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_sel
primitive_category: function
description: "A selectable analog linear filter for xreal-typed signals."
date: 2026-03-11T07:20:43.357405
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_sel
A selectable analog linear filter for xreal-typed signals.

The `filter_sel` primitive models a continuous-time linear filter, of which Laplace s-domain transfer function can be selected from a set of multiple transfer functions by a wire-type selection signal `sel`. With this primitive, one can describe a linear AC transfer function that varies with a set of digital input values.

With the width of the input `sel` equal to k, as specified by the parameter `width_sel`, the primitive can have up to 2^k linear filters to select from. Each linear filter is indexed by an integer ranging from 0 to 2^k-1, which corresponds to the unsigned integer value of the input `sel[k-1:0]`.

The parameters `indices` and `data` together describe the set of linear filters. First, the parameter `indices` is an integer-type array that lists the indices of the linear filters in the order that they are defined by the parameter `data`. The indices may be listed in an arbitrary order and may not span a complete set, but each index must be within the range of 0~2^k-1. For example, '{0, 3, 1} is possible when k=2. The special value of '{-1} is equivalent to a complete set of indices listed as '{0, 1, 2, ..., 2^k-1}.

On the other hand, the parameter `data` is a real-type array defining each of the linear filters of which indices are listed in the parameter `indices` using a concatenated set of data values formatted as below (for the number of indices > 1):

```
    data = '{ ...
              // linear filter with index 'indices[i]'
              N,                                        // number of partial fraction terms
              a1_real, a1_imag, b1_real, b1_imag, m1,   // partial fraction term #1
              a2_real, a2_imag, b2_real, b2_imag, m2,   // partial fraction term #2
              ...
              aN_real, aN_imag, bN_real, bN_imag, mN,   // partial fraction term #N
              ...
           }
```

Each set of data values describing a single linear filter starts with the number of partial fraction terms (N), followed by a list of 5*N coefficients describing the N partial fraction terms. These coefficients describe an s-domain transfer function H(s) as expressed below:

```
               b1_real + j*b1_imag                 bN_real + j*bN_imag
    H(s) = ---------------------------- + ... + ---------------------------- ,
           (s + a1_real + j*a1_imag)^m1         (s + aN_real + j*aN_imag)^mN
```

For illustration, the following example describes two linear filters index 0 and 1, respectively. The linear filter with index 0 describes a first-order filter with a single pole at 1GHz, while the linear filter with index 1 describes a second-order filter with complex poles at -4000+j*3000 and -4000-j*3000 rad/s. Both the filters have a gain of 1.

```
    indices = '{0, 1}
    data = '{1, 2*M_PI*1e9, 0.0, 2*M_PI*1e9, 0.0, 1,
             2, 4000, 3000, 0.0, 4167, 1, 4000, -3000, 0.0, -4167, 1}
```

When the parameter `indices` does not list a complete set of indices, the undefined linear filters are assumed to be a constant function outputting 0.0. When the parameter `indices` has only one index, the parameter `data` must omit the number of partial fraction terms (N) and list the coefficients only.

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For the above example, the parameters `indices` and `data` can be defined within a file as below:

```
    indices = [0, 1]
    data = [1, 6.283e9, 0.0, 6.283e9, 0.0, 1, 2, 4000, 3000, 0.0, 4167, 1, 4000, -3000, 0.0, -4167, 1]
```

The parameter `delay` sets the transport delay from the input to output in seconds. For synchronization reasons, the transport delay value must be at least a unit timestep.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| sel | input | wire | selection signal (binary-coded) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width_sel | int | 1 | None | width of selection bits |
| indices | int array | '{0} | None | list of filter indices |
| data | real array | '{0.0} | None | list of filter data |
| delay | real | 0.0 | seconds | transport delay |
| filename | string | "" | None | parameter definition file |

