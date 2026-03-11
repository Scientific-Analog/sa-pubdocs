---
title: "XMODEL primitive: vccs"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vccs
primitive_category: circuit
description: "A voltage-controlled current source (VCCS)."
date: 2026-03-11T07:20:43.541012
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vccs
A voltage-controlled current source (VCCS).

The `vccs` primitive represents a dependent current source controlled by a voltage across two circuit terminals. This primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| in_pos | input | xreal | positive reference terminal |
| in_neg | input | xreal | negative reference terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | scale factor |
| m | real | 1.0 | None | multiplicity factor |

