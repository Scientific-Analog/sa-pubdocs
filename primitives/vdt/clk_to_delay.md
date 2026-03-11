---
title: "XMODEL primitive: clk_to_delay"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: clk_to_delay
primitive_category: vdt
description: "A clock-to-delay domain translator."
date: 2026-03-11T07:20:43.595766
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE clk_to_delay
A clock-to-delay domain translator.

The `clk_to_delay` primitive takes two periodic inputs `in` and `trig` and produces an output signal `out` that expresses the delay of `in` with respect to `trig`. The output signal is an xreal-typed, piecewise-constant signal that is updated at every triggering edge of the inputs `in` and `trig`. The parameter `trig_edge` specifies which edges of the inputs trigger the update of the output: positive edges (+1), negative edges (-1), or both (0).

The parameters `delay_trig`, `delay_in`, `skip_trig`, and `skip_in` control which edges of the two inputs are to be compared with. For instance, the parameter `delay_trig` specifies the initial period during which edges of the input `trig` are be ignored. Also, the parameter `skip_in` specifies the number of edges of the input `in` to be ignored after its initial period of `delay_in`.

For example, if `delay_trig`=1e-6, `delay_in`=2e-6, `skip_trig`=5, `skip_in`=9, and `trig_edge`=1, then the `clk_to_delay` primitive starts measuring the delay from the 6th rising edge of `trig` since 1usec to the 10th rising edge of `in` since 2usec.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | delay output (from trig to in) |
| in | input | xbit | input pulse |
| trig | input | xbit | reference trigger pulse |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay_trig | real | 0.0 | seconds | start delay for 'trig' |
| delay_in | real | 0.0 | seconds | start delay for 'in' |
| skip_trig | int | 0 | None | number of edges to skip for 'trig' |
| skip_in | int | 0 | None | number of edges to skip for 'in' |
| trig_edge | int | 1 | None | triggering clock edge |

