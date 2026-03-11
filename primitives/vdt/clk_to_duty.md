---
title: "XMODEL primitive: clk_to_duty"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: clk_to_duty
primitive_category: vdt
description: "A clock-to-duty domain translator."
date: 2026-03-11T07:20:43.596911
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE clk_to_duty
A clock-to-duty domain translator.

The `clk_to_duty` primitive takes a periodic clock input `in` and produces an output signal `out` that expresses the duty-cycle of the clock. The output signal is an xreal-typed, piecewise-constant signal that is updated at every triggering edge of the input `in`. The parameter `trig_edge` specifies which edges of the input clock trigger the update of the output: positive edges (+1), negative edges (-1), or both (0).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | duty output |
| in | input | xbit | clock input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| trig_edge | int | 1 | None | triggering clock edge |

