---
title: "XMODEL primitive: sample"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: sample
primitive_category: function
description: "A sample-and-hold function for xreal-typed signals."
date: 2026-03-11T07:20:43.378113
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE sample
A sample-and-hold function for xreal-typed signals.

The `sample` primitive models a sample-and-hold function, which samples the value of the input signal `in` at the trigger event of the input `trig` and holds the value until the next trigger event.

The parameter `trig_mode` defines whether the primitive is triggered by the positive edge (1), negative edge (-1), or both edges (0) of the input `trig` (default: 1). The parameter `init_value` defines the initial output value before the first trigger event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| trig | input | xbit | trigger signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| init_value | real | `NaN | None | initial output value |
| trig_mode | int | 1 | None | triggering mode |

