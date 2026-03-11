---
title: "XMODEL primitive: meas_value"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_value
primitive_category: meas
description: "A primitive for measuring the values of an xreal-typed signal at triggering events."
date: 2026-03-11T07:20:43.421925
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_value
A primitive for measuring the values of an xreal-typed signal at triggering events.

The `meas_value` primitive measures the value of an xreal-typed signal `in` at the specified triggering events. The real-typed output `out` indicates the sampled value of the signal at the triggering events. The output `out` initially takes an 'NaN (not-a-number)' value until the first triggering event occurs, and gets updated to a finite value once a triggering event occurs.

The measurement can be triggered either internally or externally depending on the value of the parameter `period`. When `period` is greater than 0, the measurement is triggered internally at a period of `period` after an initial delay of `delay`. When `period` is 0, the change is triggered externally whenever the `trig` input changes to a different value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | value |
| in | input | xreal | input signal |
| trig | input | xbit | trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| period | real | 0.0 | seconds | trigger period |
| delay | real | 0.0 | seconds | initial delay |

