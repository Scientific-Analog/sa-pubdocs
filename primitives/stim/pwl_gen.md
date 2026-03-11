---
title: "XMODEL primitive: pwl_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: pwl_gen
primitive_category: stim
description: "An analog piecewise-linear stimulus generator."
date: 2026-03-11T07:20:43.463191
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE pwl_gen
An analog piecewise-linear stimulus generator.

The `pwl_gen` primitive generates an xreal-typed, piecewise-linear (PWL) waveform defined as a series of (time,value) points. The waveform can be described either by using the real-typed array parameter `data` or by feeding a file of which name is defined by the parameter `filename`.

The parameter `data` is formatted as a real-typed array of time-value pairs:

    '{ time1, value1, time2, value2, time3, value3, ... }.

For instance, data = '{1e-9, 0.5, 2e-9, 0.3, 3e-9, 0.7}.

When the parameter `filename` is specified, the primitive reads the named file that defines the parameter values in Python format. For instance, for the parameter `data`, its real-typed array value can be defined within the file as the following:

```
    data = [ time1, value1,
             time2, value2,
             time3, value3,
             ...
           ]
```

The parameter `period` defines the period at which the waveform is repeated. If its value is negative (e.g. -1), the waveform is not repeated. The parameter `repeat_pos` defines the start point of the waveform to repeat (by default, 0.0). The parameter `delay` defines the initial delay for the primitive to wait before generating the waveform.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| data | real array | '{0.0,0.0,1.0e-9,1.0} | None | PWL data series |
| repeat_pos | real | 0.0 | seconds | repetition start position |
| period | real | -1.0 | seconds | repetition period |
| delay | real | 0.0 | seconds | initial delay |
| filename | string | "" | None | PWL data description file |

