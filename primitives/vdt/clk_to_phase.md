---
title: "XMODEL primitive: clk_to_phase"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: clk_to_phase
primitive_category: vdt
description: "A clock-to-phase domain translator."
date: 2026-03-11T07:20:43.600416
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE clk_to_phase
A clock-to-phase domain translator.

The `clk_to_phase` primitive takes a periodic clock input `in` and produces an output signal `out` that expresses the phase of the clock, computed according to the nominal frequency specified by the parameter `freq`. The output signal is an xreal-typed, piecewise-constant signal that is updated at every triggering edge of the input `in`. The parameter `trig_edge` specifies which edges of the input clock trigger the update of the output: positive edges (+1), negative edges (-1), or both (0).

The parameter `phase_wrap` controls whether the output phase is wrapped to the range of [-pi, pi). When `phase_wrap` is 1, wrapping is enabled (default); when `phase_wrap` is 0, the phase is allowed to grow without wrapping.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | phase output |
| in | input | xbit | clock input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| freq | real | 1.0e9 | Hz | nominal clock frequency |
| phase_wrap | int | 1 | None | enable phase wrapping within [-pi, pi) |
| trig_edge | int | 1 | None | triggering clock edge |

