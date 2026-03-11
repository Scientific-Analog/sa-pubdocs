---
title: "XMODEL primitive: meas_freq"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_freq
primitive_category: meas
description: "A primitive for measuring the frequency of a trigger."
date: 2026-03-11T07:20:43.407926
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_freq
A primitive for measuring the frequency of a trigger.

The `meas_freq` primitive measures the frequency of a trigger input `trig`, by measuring the time difference between its two consecutive events. The real-typed output `out` indicates the frequency measured from the last two trigger events of the input. It initially takes an 'NaN (not-a-number)' value until the first frequency measurement can be made.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | value |
| trig | input | xbit | trigger |

