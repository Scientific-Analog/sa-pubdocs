---
title: "XMODEL primitive: integ_rst"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: integ_rst
primitive_category: function
description: "An integration with reset operator for xreal-typed signals."
date: 2026-03-11T07:20:43.365016
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE integ_rst
An integration with reset operator for xreal-typed signals.

The `integ_rst` primitive computes the time-integral of an xreal-typed input signal `in`. Its difference with the `integ` primitive is that it resets its output when its xbit-typed input `rst` is asserted. In other words, the integration is performed only when the input `rst` is at 0, according to the following equations:

```
    out = init_value + scale * integral(from 0 to t) of x(t) dt
```

for the output starting from t=0 with `rst`=0 and

```
    out = rst_value + scale * integral(from t_rst to t) of x(t) dt
```

for the output starting from t=`t_rst` with `rst`=0  where `t_rst` is the time when the input `rst` last fell to 0.

The parameter `scale` specifies the scale factor applied to the integral and the parameters `init_value` and `rst_value` specify the initial value and reset value of the integral, respectively.

The parameter `mode` determines the reset behavior of this primitive, namely, the output value when the input `rst` is 1. When `mode` is set to "reset" (by default), the output value is reset to `rst_value` as soon as the input `rst` rises to 1. On the other hand, when `mode` is set to "hold", the output value is held at its last value while `rst` is at 1 and is reset to `rst_value` when `rst` falls back to 0.

```
            +       +                   +---+   +---+
           /|      /|                  /    |  /    |
    out   / |     / |     /     out   /     | /     | /
         /  |    /  |    /           /      |/      |/
            +---+   +---+                   +       +

            +---+   +---+               +---+   +---+
    rst  ---+   +---+   +--     rst  ---+   +---+   +--

         mode = 'reset'              mode = 'hold'
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| rst | input | xbit | reset input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | input scale factor |
| init_value | real | 0.0 | None | output initial value |
| rst_value | real | 0.0 | None | output reset value |
| mode | string | 'reset' | None | reset mode |

