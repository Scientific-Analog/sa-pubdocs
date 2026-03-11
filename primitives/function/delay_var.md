---
title: "XMODEL primitive: delay_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: delay_var
primitive_category: function
description: "A variable transport delay for xreal-typed signals."
date: 2026-03-11T07:20:43.346104
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE delay_var
A variable transport delay for xreal-typed signals.

The `delay_var` primitive models a variable transport delay for xreal-typed signals. In other words, it delays an xreal-typed input `in` to the output `out` by the time amount controlled by another xreal-typed input `delay`.

Note that the `delay` input must satisfy the following two conditions at all times. First, its value must be no less than a unit timestep (no future prediction). Second, its time-derivative must be less than 1.0 (no time-reversal).

For modeling a fixed transport delay for xreal-typed signals, use the `delay` primitive. For modeling a fixed or variable transport delay for xbit-typed signals, use the `delay_xbit` or `delay_to_clk` primitive, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| delay | input | xreal | delay |

