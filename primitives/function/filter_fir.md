---
title: "XMODEL primitive: filter_fir"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: filter_fir
primitive_category: function
description: "A finite impulse response filter."
date: 2026-03-11T07:20:43.356219
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE filter_fir
A finite impulse response filter.

The `filter_fir` primitive is a discrete-time filter with a finite impulse response. It decides the output value based on N previous inputs and its discrete-time impulse response as follows:

```
    out[n] = data[0]*x[n] + data[1]*x[n-1] + ... + data[N-1]*x[n-N+1]

    where x[n] = -0.5 for in[n] = 0
                  0.5 for in[n] = 1
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | analog output |
| in | input | xbit | digital input |
| trig | input | xbit | trigger input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| data | real array | '{1.0} | None | filter coefficients |
| tran_time | real | 0.0 | seconds | transition time |

