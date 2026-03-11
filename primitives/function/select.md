---
title: "XMODEL primitive: select"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: select
primitive_category: function
description: "A signal selector (i.e. multiplexer) for xreal-typed signals."
date: 2026-03-11T07:20:43.381538
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE select
A signal selector (i.e. multiplexer) for xreal-typed signals.

The `select` primitive selects one of the multiple xreal-typed inputs `in` as its output according to an xbit-typed selection signal `sel`. In other words, it serves an analog multiplexer.

When the number of inputs is equal to 2^k, the primary way to specify the width of the `select` primitive is to define the parameter `width_sel`, denoting the bit-width of the selection signal `sel` in the binary format, to k. It will set the parameter `num_in`, denoting the number of input signals, to 2^k as well.

When the number of inputs is not in the form of 2^k, both `width_sel` and `num_in` can be used. Any inconsistencies between the two parameters may result in undesired behaviors, though. For instance, if `num_in` is larger than `2^width_sel`, then the input signals with the higher indices than 2^width_sel-1 cannot be selected. If `num_in` is smaller than `2^width_sel`, the `select` primitive assumes that the unspecified inputs with indices higher than `num_in` are zero-valued signals.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signals |
| sel | input | xbit | selection signals (binary-coded) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width_sel | int | 1 | None | width of selection bits |
| num_in | int | 2 | None | number of inputs |

