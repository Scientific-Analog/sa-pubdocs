---
title: "XMODEL primitive: poly_func"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: poly_func
primitive_category: function
description: "A polynomial function for xreal-typed signals."
date: 2026-03-11T07:20:43.371029
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE poly_func
A polynomial function for xreal-typed signals.

The `poly_func` primitive defines a polynomial function for xreal-typed signals. With this primitive, one can define a nonlinear DC transfer function with up to three inputs.

The parameter `num_in` specifies the number of inputs, of which maximum value is 3. The parameter `data` is a real-type array defining the coefficients C0, C1, C2, ... of the input-to-output polynomial equation as listed below depending on the number of inputs:

```
    data = '{C0, C1, C2, C3, ...}
```

### 1) For a single-input polynomial (num_in = 1):

```
    out = C0 + C1*in + C2*in^2 + C3*in^3 + C4*in^4 + ...
```

### 2) For a two-input polynomial (num_in = 2):

```
    out = C0 + C1*in[1] + C2*in[0] +
          C3*in[1]^2 + C4*in[1]*in[0] + C5*in[0]^2 +
          C6*in[1]^3 + C7*in[1]^2*in[0] + C8*in[1]*in[0]^2 + C9]*in[0]^3 +
          C10*in[1]^4 + ...
```

### 3) For a three-input polynomial (num_in = 3):

```
    out = C0 + C1*in[2] + C2*in[1] + C3*in[0] +
          C4*in[2]^2 + C5*in[2]*in[1] + C6*in[2]*in[0] +
          C7*in[1]^2 + C8*in[1]*in[0] + C9*in[0]^2 +
          C10*in[2]^3 + C11*in[2]^2*in[1] + C12*in[2]^2*in[0] + C13*in[2]*in[1]^2 + C14*in[2]*in[1]*in[0] +
          C15*in[2]*in[0]^2 + C16*in[1]^3 + C17*in[1]^2*in[0] + C18*in[1]*in[0]^2 + C19*in[0]^3 +
          C20*in[2]^4 + ...
```

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For example, for the parameter `data`, its real-typed array value can be defined using the following syntax:

```
    data = [3.0, -2.0, 1.0]
```

to describe a single-input polynomial function of x^2 - 2*x + 3, where x is the input.

**NOTE**: for the number of inputs >= 2, this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signals |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int | 1 | None | number of inputs |
| data | real array | '{0.0} | None | polynomial coefficients |
| filename | string | "" | None | parameter definition file |

