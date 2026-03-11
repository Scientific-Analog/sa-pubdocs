---
title: "XMODEL primitive: pwl_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: pwl_func
primitive_category: function
description: "A piecewise-linear (PWL) function for xreal-typed signals."
date: 2026-03-11T07:20:43.375387
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE pwl_func
A piecewise-linear (PWL) function for xreal-typed signals.

The `pwl_func` primitive defines a piecewise-linear function of xreal-typed signals. With this primitive, one can define an arbitrarily nonlinear DC transfer function.

The piecewise-linear function is described by a set of PWL data points, which can be specified either inline using the parameter `data` or within a file of which name is specified by the parameter `filename`.

The parameter `data` is formatted as a real-type array of (input, output) pairs with at least two data points: '{in1, out1, in2, out2, ...}. For instance, if the value of `data` is provided as '{-1.0, -10.0, 1.0, 10.0}, the `pwl_func` primitive realizes a function of which output is:

```
    -10.0       for input < -1.0
    10*input    for -1.0 <= input < 1.0
    +10.0       for input >= 1.0
```

In a special case when the primitive needs to describe a constant function, define the parameter `data` as a single-element list containing the constant output value. For instance, the parameter `data` set to '{1.0} describes a function with a constant output of 1.0.

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For instance, for the parameter `data`, its real-typed array value can be defined as following:

```
    data = [ in1, out1,
             in2, out2,
             in3, out3,
             ...
           ]
```

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| data | real array | '{-1.0, -1.0, 1.0, 1.0} | None | PWL data points |
| filename | string | "" | None | parameter definition file |

