---
title: "XMODEL primitive: adc"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: adc
primitive_category: function
description: "An ideal analog-to-digital converter."
date: 2026-03-11T07:20:43.336526
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE adc
An ideal analog-to-digital converter.

The `adc` primitive continuously digitizes an xreal-typed, continuous-time analog signal into an xbit-typed, digital signal. Therefore, the primitive is basically a multi-level slicer.

The bit resolution of the `adc` primitive is specified by the parameter `num_bit`. The value range of the input signal is set either by defining `value_min` and `value_max` or by defining `value_min` and `value_lsb`.  For the former case, one LSB step (i.e., `value_lsb`) is defined as `(value_max-value_min)/(2^num_bit-1)`.

The input-to-output transfer characteristic of this `adc` primitive is defined as the following:

```
    out = 0     for in < value_min + 0.5*value_lsb
    out = 1     for value_min + 0.5*value_lsb <= in < value_min + 1.5*value_lsb
    out = 2     for value_min + 1.5*value_lsb <= in < value_min + 2.5*value_lsb
        ...
    out = k     for value_min + (k-0.5)*value_lsb <= in < value_min + (k+0.5)*value_lsb
        ...
    out = 2^num_bit-1 for value_max - 0.5*value_lsb <= in
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | digital output |
| in | input | xreal | analog input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_bit | int | 1 | bits | ADC resolution |
| value_min | real | 0.0 | None | minimum nominal input for out=0 |
| value_max | real | `NaN | None | maximum nominal input for out=2^num_bit-1 |
| value_lsb | real | `NaN | None | one LSB step |

