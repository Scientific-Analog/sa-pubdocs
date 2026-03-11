---
title: "XMODEL primitive: meas_delay"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_delay
primitive_category: meas
description: "A primitive for measuring the time difference between two triggering events."
date: 2026-03-11T07:20:43.403044
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_delay
A primitive for measuring the time difference between two triggering events.

The `meas_delay` primitive measures the time difference between the trigger events of two inputs `from` and `to`. The real-typed output `out` indicates the time difference between the last trigger events of the two inputs. If the parameter `strict_order` is set to 1 (default), it is assumed that the `from` event always occurs before the `to` event and the primitive updates the time difference measurement `out` only when the `to` input is triggered. If the parameter `strict_order` is 0, then no ordering between the `from` and `to` events is assumed and the primitive updates `out` whenever either the `from` or `to` input is triggered. The output `out` initially takes an 'NaN (not-a-number)' value until the first time difference measurement can be made.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | value |
| from | input | xbit | from trigger |
| to | input | xbit | to trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| strict_order | int | 1 | None | option for strict ordering |

