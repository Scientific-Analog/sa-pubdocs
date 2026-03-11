---
title: "XMODEL primitive: or_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: or_xbit
primitive_category: gate
description: "A multi-input OR gate with xbit-type input/output's."
date: 2026-03-11T07:20:43.571616
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE or_xbit
A multi-input OR gate with xbit-type input/output's.

The `or_xbit` primitive models a multi-input OR logic gate with xbit-typed signals. It is suitable for processing digital signals of which precise timing information must be preserved.

The input to the `or_xbit` primitive is an xbit array, of which length is specified by the parameter `num_in`.

The propagation delay of the logic gate is specified by the parameter `delay`. The implemented delay is `inertial`, meaning that if a new input event arrives before the previous input event propagates to the output, the output event will be overriden with the one corresponding to the new input event. If a transport delay behavior is desired, use the `delay_xbit` primitive instead.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output signal |
| in | input | xbit | input signals |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int | 2 | None | number of inputs |
| delay | real | 0.0 | seconds | propagation delay |

