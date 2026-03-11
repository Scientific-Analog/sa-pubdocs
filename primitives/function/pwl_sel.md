---
title: "XMODEL primitive: pwl_sel"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: pwl_sel
primitive_category: function
description: "A selectable piecewise-linear (PWL) function for xreal-typed signals."
date: 2026-03-11T07:20:43.376773
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE pwl_sel
A selectable piecewise-linear (PWL) function for xreal-typed signals.

The `pwl_sel` primitive computes a piecewise-linear (PWL) function of an xreal-type input `in`, which can be selected from a set of multiple PWL functions by a wire-type selection signal `sel`. With this primitive, one can describe a nonlinear DC transfer function that varies with a set of digital input values.

With the width of the input `sel` equal to k, as specified by the parameter `width_sel`, the primitive can have up to 2^k PWL functions to select from. Each PWL function is indexed by an integer ranging from 0 to 2^k-1, which corresponds to the unsigned integer value of the input `sel[k-1:0]`.

The parameters `indices` and `data` together describe the set of PWL functions. First, the parameter `indices` is an integer-type array that lists the indices of the PWL functions in the order that they are defined by the parameter `data`. The indices may be listed in an arbitrary order and may not span a complete set, but each index must be within the range of 0~2^k-1. For example, '{0, 3, 1} is possible when k=2. The special value of '{-1} is equivalent to a complete set of indices listed as '{0, 1, 2, ..., 2^k-1}.

On the other hand, the parameter `data` is a real-type array defining each of the PWL functions of which indices are listed in the parameter `indices` using a concatenated set of data values formatted as below (for the number of indices > 1):

```
    data = '{ N0, in1_0, out1_0, in2_0, out2_0, ...     // PWL function with index 'indices[0]'
              N1, in1_1, out1_1, in2_1, out2_1, ...     // PWL function with index 'indices[1]'
              ...
              Ni, in1_i, out1_i, in2_i, out2_i, ...     // PWL function with index 'indices[i]'
              ...
           }
```

Each set of data values describing a single PWL function starts with the number of PWL data points (Ni), followed by a list of (input, output) pairs: in1_i, out1_i, in2_i, out2_i, .... When the PWL function describes a constant function, use Ni of 0 followed by a single output value, i.e. 0, out1_i. Otherwise, Ni must be at least 2.

For illustration, the following example describes two PWL functions with index 0 and 1, respectively. The PWL function with index 0 is described with 3 data points, outputting 10*|x| when the input x satisfies |x| < 1 and outputting 10.0 otherwise. The PWL function with index 1 is described with 0 data points, outputting a constant value of 0.0.

```
    indices = '{0, 1}
    data = '{3, -1.0, 10.0, 0.0, 0.0, 1.0, 10.0, 0, 0.0}
```

When the parameter `indices` does not list a complete set of indices, the undefined PWL functions are assumed to be a constant function outputting 0.0.  When the parameter `indices` has only one index, the parameter `data` must omit the number of PWL data points (Ni) and list the PWL data points only.

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For the above example, the values of the parameters `indices` and `data` can be defined within a file as below:

```
    indices = [0, 1]
    data = [3, -1.0, 10.0, 0.0, 0.0, 1.0, 10.0, 0, 0.0]
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
| width_sel | int | 1 | None | width of selection bits |
| indices | int array | '{0} | None | list of function indices |
| data | real array | '{-1.0,-1.0,1.0,1.0} | None | list of function data |
| filename | string | "" | None | parameter definition file |

