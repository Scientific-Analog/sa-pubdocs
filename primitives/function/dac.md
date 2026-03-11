---
title: "XMODEL primitive: dac"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: dac
primitive_category: function
description: "An ideal digital-to-analog converter."
date: 2026-03-11T07:20:43.341696
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE dac
An ideal digital-to-analog converter.

The `dac` primitive continuously converts an xbit-typed digital input to an xreal-typed analog output.

The transfer characteristic of the `dac` primitive is defined in a similar fashion to the `adc` primitive. In other words, the bit resolution is set by the parameter `num_bit` and the value range of the output analog signal is set either by defining `value_min` and `value_max` or by defining `value_min` and `value_lsb`. For the former case, one LSB step (i.e., `value_lsb`) is defined as `(value_max-value_min)/(2^num_bit-1)`.

The analog output value of the `dac` primitive is determined by the following equation:

```
    out = in*value_lsb + value_min.
```

In case the output value range is defined by `value_min` and `value_max` parameters, the `value_lsb` value is determined as:

```
    value_lsb = (value_max - value_min) / (2^num_bit-1).
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | analog output |
| in | input | xbit | digital input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_bit | int | 1 | bits | DAC resolution |
| value_min | real | 0.0 | None | minimum output value (when in=0) |
| value_max | real | `NaN | None | maximum output value (when in=2^num_bit-1) |
| value_lsb | real | `NaN | None | one LSB step |
| tran_time | real | 0.0 | seconds | transition time |

