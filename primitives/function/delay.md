---
title: "XMODEL primitive: delay"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: delay
primitive_category: function
description: "A fixed transport delay for xreal-typed signals."
date: 2026-03-11T07:20:43.343185
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE delay
A fixed transport delay for xreal-typed signals.

The `delay` primitive models a fixed transport delay for xreal-typed signals. It delays an xreal-typed input signal by the time amount defined by the parameter `delay`.

For modeling a variable transport delay for xreal-typed signals, use `delay_var` primitive. For modeling a fixed or variable transport delay for xbit-typed signals, use the `delay_xbit` or `delay_to_clk` primitive, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay | real | 0.0 | seconds | transport delay |

