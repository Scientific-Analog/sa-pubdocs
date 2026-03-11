---
title: "XMODEL primitive: inductor"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: inductor
primitive_category: circuit
description: "An inductor circuit element."
date: 2026-03-11T07:20:43.518638
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE inductor
An inductor circuit element.

The `inductor` primitive represents a two-terminal inductor. Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| L | real | 1.0 | henries | inductance |
| ic | real | `NaN | amperes | initial condition |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

