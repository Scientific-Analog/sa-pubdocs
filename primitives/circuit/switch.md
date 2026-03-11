---
title: "XMODEL primitive: switch"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: switch
primitive_category: circuit
description: "A switch circuit element."
date: 2026-03-11T07:20:43.535894
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE switch
A switch circuit element.

The `switch` primitive represents a two-terminal switch with on/off resistances. The parameters `R0` and `R1` define the resistance values when the input `ctrl` is 0 and 1, respectively.

The parameter `ic` defines the initial state of the switch, i.e., the assumed value of `ctrl` before it is initialized. In other words, at time=0, the switch will have the resistance assuming the input `ctrl` has the value of `ic`.

By default, when the input `ctrl` has a logic X or logic Z value, the switch enters an open state with infinite resistance. One can change this behavior by defining the mapped values for logic X and logic Z using the parameters `valueX` and `valueZ`, respectively. For example, if `valueX` is set to 0, the switch will have the resistance of `R0` when its input `ctrl` has a logic X value.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| ctrl | input | xbit | control signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| R0 | real | `INFINITY | ohms | resistance when ctrl=0 |
| R1 | real | 0.01 | ohms | resistance when ctrl=1 |
| ic | logic | 1'bx | None | initial switch state |
| valueX | logic | 1'bx | None | mapped value of logic X |
| valueZ | logic | 1'bz | None | mapped value of logic Z |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

