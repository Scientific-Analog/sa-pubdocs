---
title: "XMODEL primitive: tribuf_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: tribuf_xbit
primitive_category: gate
description: "A tri-state buffer with xbit-type input/output's."
date: 2026-03-11T07:20:43.572879
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE tribuf_xbit
A tri-state buffer with xbit-type input/output's.

The `tribuf_xbit` primitive models a tri-state buffer gate with an inertial delay. It is suitable for processing digital signals of which precise timing information must be preserved.

Note that the `tribuf_xbit` primitive does not leave the output at a high-Z state when it is disabled. Since xbit is a variable type (like a reg), the output will retain its previous value when it is not driven.

The propagation delay of the logic gate is specified by the parameter `delay`. The implemented delay is `inertial`, meaning that if a new input event arrives before the previous input event propagates to the output, the output event will be overriden with the one corresponding to the new input event. If a transport delay behavior is desired, use the `delay_xbit` primitive instead.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | inout | xbit | tri-state output signal |
| in | input | xbit | input signal |
| en | input | xbit | enable signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| delay | real | 0.0 | seconds | propagation delay |

