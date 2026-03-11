---
title: "XMODEL primitive: resistor"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: resistor
primitive_category: circuit
description: "A resistor circuit element."
date: 2026-03-11T07:20:43.533145
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE resistor
A resistor circuit element.

The `resistor` primitive represents a two-terminal resistor. Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| R | real | 1.0 | ohms | resistance |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

