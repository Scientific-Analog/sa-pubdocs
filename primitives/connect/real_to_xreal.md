---
title: "XMODEL primitive: real_to_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: real_to_xreal
primitive_category: connect
description: "A real-to-xreal connector."
date: 2026-03-11T07:20:43.482322
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE real_to_xreal
A real-to-xreal connector.

The `real_to_xreal` primitive converts a real-type signal to an xreal-type signal. The primitive can also perform event filtering. That is, output events are suppressed when the input change is less than the absolute tolerance (parameter `abstol`). Additional low-pass filtering can be applied to the input change, where the parameter `delay` determines the time constant of this filter.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | xreal-type output |
| in | input | real | real-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| abstol | real | 0.0 | None | absolute tolerance for event filtering |
| delay | real | 0.0 | seconds | delay for event filtering |

