---
title: "XMODEL primitive: slice"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: slice
primitive_category: function
description: "An analog continuous-time comparator (slicer)."
date: 2026-03-11T07:20:43.384038
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE slice
An analog continuous-time comparator (slicer).

The `slice` primitive continuously compares the difference between the two inputs `in`-`in_ref` with a user-defined threshold and produces an xbit-type output `out`. The primitive is equivalent to a continuous-time 1-bit analog-to-digital converter.

The output value is set to 1 when the input difference is higher than the threshold level and set to 0 otherwise. The threshold level is defined by the `threshold` parameter.

**NOTE**: this primitive adds a unit timestep delay from its input to output for synchronization.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | digital output |
| in | input | xreal | analog input |
| in_ref | input | xreal | reference input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.0 | None | threshold level |

