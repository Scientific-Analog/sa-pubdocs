---
title: "XMODEL primitive: cccs_sw"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: cccs_sw
primitive_category: circuit
description: "A switchable current-controlled current source (CCCS)."
date: 2026-03-11T07:20:43.505711
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE cccs_sw
A switchable current-controlled current source (CCCS).

The `cccs_sw` primitive represents a dependent current source controlled by a current across a circuit branch. Its scale factor is set by the real-typed input `scale`.

This primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| in_pos | input | xreal | positive reference terminal |
| in_neg | input | xreal | negative reference terminal |
| scale | input | real | scale factor |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| m | real | 1.0 | None | multiplicity factor |

