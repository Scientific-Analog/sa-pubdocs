---
title: "XMODEL primitive: meas_time"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_time
primitive_category: meas
description: "A primitive for measuring the time instants of triggering events."
date: 2026-03-11T07:20:43.420680
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_time
A primitive for measuring the time instants of triggering events.

The `meas_time` primitive measures the time instant of a triggering event in the input `trig`. The real-typed output `out` indicates the time instant of the last trigger events. It initially takes an 'NaN (not-a-number)' value until the first triggering event occurs, and gets updated to a finite value once a triggering event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | value |
| trig | input | xbit | trigger |

