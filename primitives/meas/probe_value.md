---
title: "XMODEL primitive: probe_value"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_value
primitive_category: meas
description: "A probe for measuring the values of an xreal-typed signal at triggering events."
date: 2026-03-11T07:20:43.435981
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_value
A probe for measuring the values of an xreal-typed signal at triggering events.

The `probe_value` primitive measures the value of an xreal-typed signal `in` at the specified triggering events and records the results in a table format to a text file named by the parameter `filename`.

The measurement can be triggered either internally or externally depending on the value of the parameter `period`. When `period` is greater than 0, the measurement is triggered internally at a period of `period` after an initial delay of `delay`. When `period` is 0, the change is triggered externally whenever the `trig` input changes to a different value.

The primitive can also measure and record the values of multiple inputs at once. In this case, the parameter `num_in` defines the number of inputs provided to `in`.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | input signal |
| trig | input | xbit | trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "probe_value.dat" | None | output filename |
| num_in | int | 1 | None | number of inputs |
| period | real | 0.0 | seconds | trigger period |
| delay | real | 0.0 | seconds | initial delay |

