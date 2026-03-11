---
title: "XMODEL primitive: real_to_xbit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: real_to_xbit
primitive_category: connect
description: "A real-to-xbit connector."
date: 2026-03-11T07:20:43.479962
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE real_to_xbit
A real-to-xbit connector.

The `real_to_xbit` primitive converts a real-type signal to an xbit-type signal. The analog level of the input signal is converted to a digital level using the threshold parameters: threshold, thres0, or thres1.

The parameter `threshold` sets the threshold level between logic 0 and logic 1. In other words, the output changes to logic 1 when the input rises above this threshold and to logic 1 when it falls below the threshold.

In addition, by defining the parameters `thres0` and `thres1`, one can set different thresholds for logic 0 and logic 1 (NOTE: not yet implemented).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | xbit-type output |
| in | input | real | real-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.5 | None | threshold level |
| thres0 | real | `NAN | None | threshold level for logic 0 |
| thres1 | real | `NAN | None | threshold level for logic 1 |

