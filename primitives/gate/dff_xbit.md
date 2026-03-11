---
title: "XMODEL primitive: dff_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: dff_xbit
primitive_category: gate
description: "A D flip-flop with xbit-type input/output's."
date: 2026-03-11T07:20:43.561824
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE dff_xbit
A D flip-flop with xbit-type input/output's.

The `dff_xbit` primitive models a D flip-flop with a data input `d`, a clock input `clk`, and an output `q`. All the input and output signals are xbit-typed. This primitive is suitable when processing digital signals with precise timing information.

The parameter `trig_edge` specifies whether the D flip-flop is triggered by the positive edge (+1), negative edge (-1), or both edges (0) of the clock `clk`. The parameter `init_value` defines the initial value of the output `q`.

The parameter `delay_cq` defines the propagation delay from the triggering edge of the clock to the output `q`. This delay is inertial, meaning that if a new triggering clock edge arrives before the previous change propagates to the output, the output change will be overriden with the one corresponding to the new triggering clock event.

When the parameter `setup_time` or `hold_time` is specified, the primitive also checks the setup or hold timing constraints, respectively. The parameter `setup_time` defines the amount of time the input `d` must be stable before the triggering edge of the clock and the parameter `hold_time` defines the amount of time the input `d` must be stable after the triggering edge of the clock. The parameter `check_mode` defines the action when a timing constraint is violated, whether the primitive changes its output `q` to a value `x` (1), displays a warning message (2), or does both (3).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| q | output | xbit | data output |
| d | input | xbit | data input |
| clk | input | xbit | clock input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| trig_edge | int | 1 | None | triggering clock edge |
| init_value | logic | 1'bx | None | initial value |
| delay_cq | real | 0.0 | seconds | clk-to-q delay |
| setup_time | real | `NaN | seconds | setup time constraint |
| hold_time | real | `NaN | seconds | hold time constraint |
| check_mode | int | 1 | None | action for violation |

