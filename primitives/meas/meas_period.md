---
title: "XMODEL primitive: meas_period"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_period
primitive_category: meas
description: "A primitive for measuring the time difference between two consecutive events of one trigger."
date: 2026-03-11T07:20:43.413716
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_period
A primitive for measuring the time difference between two consecutive events of one trigger.

The `meas_period` primitive measures the time difference between two consecutive events occurring for one trigger input `trig`. The real-typed output `out` indicates the time difference between the last two trigger events of the input. It initially takes an 'NaN (not-a-number)' value until the first time difference measurement can be made.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | value |
| trig | input | xbit | trigger |

