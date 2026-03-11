---
title: "XMODEL primitive: meas_avg"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_avg
primitive_category: meas
description: "A primitive for measuring the average value of an xreal-typed signal within a time interval."
date: 2026-03-11T07:20:43.399151
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_avg
A primitive for measuring the average value of an xreal-typed signal within a time interval.

The `meas_avg` primitive measures the average value of an xreal-typed input signal `in` within a time interval defined by the two trigger signals, `from` and `to`. To properly define the time interval of measurement, the triggering events of `from` and `to` must arrive in pairs and in each pair, the `from` event must come before the `to` event. The output `out` initially takes an 'NaN (not-a-number)' value until the first measurement can be made. It gets updated whenever the `to` event marks the end of time interval, and may become `NaN` again if a `to` event arrives without a pairing `from` event, marking an invalid time interval.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | output value |
| in | input | xreal | input signal |
| from | input | xbit | from trigger |
| to | input | xbit | to trigger |

