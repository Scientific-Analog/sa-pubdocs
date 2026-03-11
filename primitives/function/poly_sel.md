---
title: "XMODEL primitive: poly_sel"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: poly_sel
primitive_category: function
description: "A selectable polynomial function for xreal-typed signals."
date: 2026-03-11T07:20:43.372341
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE poly_sel
A selectable polynomial function for xreal-typed signals.

The `poly_sel` primitive computes a polynomial function of xreal-typed inputs `in`, which can be selected from a set of multiple polynomial functions by a wire-type selection signal `sel`. With this primitive, one can describe a nonlinear DC transfer function that varies with a set of digital input values. The `poly_sel` primitive supports up to three inputs, of which number is specified by the parameter `num_in`.

With the width of the input `sel` equal to k, as specified by the parameter `width_sel`, the primitive can have up to 2^k polynomial functions to select from. Each polynomial function is indexed by an integer ranging from 0 to 2^k-1, which corresponds to the unsigned integer value of the input `sel[k-1:0]`.

The parameters `indices` and `data` together describe the set of polynomial functions. First, the parameter `indices` is an integer-type array that lists the indices of the polynomial functions in the order that they are defined by the parameter `data`. The indices may be listed in an arbitrary order and may not span a complete set, but each index must be within the range of 0~2^k-1. For example, '{0, 3, 1} is possible when k=2. The special value of '{-1} is equivalent to a complete set of indices listed as '{0, 1, 2, ..., 2^k-1}.

On the other hand, the parameter `data` is a real-type array defining each of the polynomial functions of which indices are listed in the parameter `indices` using a concatenated set of data values formatted as below (for the number of indices > 1):

```
    data = '{ N0, C0_0, C1_0, C2_0, ...         // polynomial function with index 'indices[0]'
              N1, C0_1, C1_1, C2_1, ...         // polynomial function with index 'indices[1]'
              ...
              Ni, C0_i, C1_i, C2_i, ...         // polynomial function with index 'indices[i]'
              ...
           }
```

Each set of data values describing a single polynomial function starts with the number of coefficients (Ni), followed by a list of coefficient values: C0_i, C1_i, C2_i, .... This set of Ni coefficients describes a polynomial function in the same way that the parameter `data` does for the `poly_func` primitive.

For a single-input polynomial (`num_in` = 1):

```
    out = C0_i + C1_i*in + C2*in^2 + C3_i*in^3 + C4_i*in^4 + ...
```

For a two-input polynomial (`num_in` = 2):

```
    out = C0_i + C1_i*in[1] + C2_i*in[0] +
          C3_i*in[1]^2 + C4_i*in[1]*in[0] + C5_i*in[0]^2 +
          C6_i*in[1]^3 + C7_i*in[1]^2*in[0] + C8_i*in[1]*in[0]^2 + C9_i*in[0]^3 +
          C10_i*in[1]^4 + ...
```

For a three-input polynomial (`num_in` = 3):

```
    out = C0_i + C1_i*in[2] + C2_i*in[1] + C3_i*in[0] +
          C4_i*in[2]^2 + C5_i*in[2]*in[1] + C6_i*in[2]*in[0] +
          C7_i*in[1]^2 + C8_i*in[1]*in[0] + C9_i*in[0]^2 +
          C10_i*in[2]^3 + C11_i*in[2]^2*in[1] + C12_i*in[2]^2*in[0] + C13_i*in[2]*in[1]^2 + C14_i*in[2]*in[1]*in[0] +
          C15_i*in[2]*in[0]^2 + C16_i*in[1]^3 + C17_i*in[1]^2*in[0] + C18_i*in[1]*in[0]^2 + C19_i*in[0]^3 +
          C20_i*in[2]^4 + ...
```

For illustration, the following example describes two single-input polynomial functions with index 0 and 1, respectively. The polynomial function with index 0 computes x-1 for the input x while the polynomial function with index 1 computes (x-1)^2.

```
    indices = '{0, 1}
    data = '{2, -1.0, 1.0, 3, 1.0, -2.0, 1.0}
```

When the parameter `indices` does not list a complete set of indices, the undefined polynomial functions are assumed to be a constant function outputting 0.0. When the parameter `indices` has only one index, the parameter `data` must omit the number of coefficients (Ni) and list the coefficients only.

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For the above example, the values of the parameters `indices` and `data` can be defined within a file as below:

```
    indices = [0, 1]
    data = [2, -1.0, 1.0, 3, 1.0, -2.0, 1.0]
```

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| sel | input | wire | selection signal (binary-coded) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int | 1 | None | number of inputs |
| width_sel | int | 1 | None | width of selection bits |
| indices | int array | '{0} | None | list of function indices |
| data | real array | '{0.0} | None | list of function data |
| filename | string | "" | None | parameter definition file |

