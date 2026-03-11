---
title: "XMODEL primitive: vinit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vinit
primitive_category: circuit
description: "An initial conditioning element for a node voltage."
date: 2026-03-11T07:20:43.545683
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vinit
An initial conditioning element for a node voltage.

The `vinit` primitive sets the initial condition of a node voltage. In other words, the voltage between the two terminals `pos` and `neg` is set close to the specified value of `ic`.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| ic | real | `NaN | volts | initial condition |
| m | real | 1.0 | None | multiplicity factor |

