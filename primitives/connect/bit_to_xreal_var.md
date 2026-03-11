---
title: "XMODEL primitive: bit_to_xreal_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: bit_to_xreal_var
primitive_category: connect
description: "A bit-to-xreal connector with variable logic-1 and logic-0 levels."
date: 2026-03-11T07:20:43.475050
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE bit_to_xreal_var
A bit-to-xreal connector with variable logic-1 and logic-0 levels.

The `bit_to_xreal_var` primitive converts a bit-type signal to an xreal-type signal with variable logic-1 and logic-0 levels. The digital level of the input signal is converted to an analog level, defined by the two external inputs: `level0` and `level1`.

The parameters `Rout` and `Cout` specify the optional output resistance and capacitance, respectively. The output resistance effectively sets the driving strength and output capacitance sets the transition time of the connector.

The parameters `valueX` and `valueZ` define the mapped values of logic X and logic Z, respectively. For example, if `valueX` is set to 0, all input values corresponding to logic X are treated as logic 0. Note that by default, the primitive leaves the output floating at its last value when the input has a logic X or logic Z value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | xreal-type output |
| in | input | wire | bit-type input |
| level0 | input | xreal | conversion level for logic 0 |
| level1 | input | xreal | conversion level for logic 1 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width | int | 1 | None | connector bit-width |
| Rout | real | 0.0 | ohms | output resistance |
| Cout | real | 0.0 | farads | output capacitance |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |

