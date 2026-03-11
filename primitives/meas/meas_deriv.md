---
title: "XMODEL primitive: meas_deriv"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_deriv
primitive_category: meas
description: "A primitive for measuring the n-th derivative value of an xreal-typed signal at triggering events."
date: 2026-03-11T07:20:43.404331
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_deriv
A primitive for measuring the n-th derivative value of an xreal-typed signal at triggering events.

The `meas_deriv` primitive measures the n-th derivative value of an xreal-typed signal `in` when it is triggered by the input `trig`. The real-typed output `out` indicates the sampled n-th derivative value of the signal at the triggering events. The parameter `order` specifies the order of derivative (default: 1). The output `out` initially takes an 'NaN (not-a-number)' value until the first triggering event occurs, and gets updated to a finite value once a triggering event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | slope |
| in | input | xreal | input signal |
| trig | input | xbit | trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| order | int | 1 | None | order of derivative |

