---
title: "XMODEL primitive: latch_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: latch_xbit
primitive_category: gate
description: "A transparent latch with xbit-type input/output's."
date: 2026-03-11T07:20:43.567098
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE latch_xbit
A transparent latch with xbit-type input/output's.

The `latch_xbit` primitive models a transparent latch with xbit-typed signals. It is suitable for processing digital signals of which precise timing information must be preserved.

The parameter `delay_dq` defines the propagation delay from the input (`d`) to the output (`q`). The implemented delay is `inertial`, meaning that if a new input event arrives before the previous input event propagates to the output, the output event will be overriden with the one corresponding to the new input event.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| q | output | xbit | data output |
| d | input | xbit | data input |
| clk | input | xbit | clock input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay_dq | real | 0.0 | seconds | d-to-q delay |
| init_value | logic | 1'bx | None | initial value |

