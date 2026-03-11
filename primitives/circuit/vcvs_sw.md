---
title: "XMODEL primitive: vcvs_sw"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vcvs_sw
primitive_category: circuit
description: "A switchable voltage-controlled voltage source (VCVS)."
date: 2026-03-11T07:20:43.544489
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vcvs_sw
A switchable voltage-controlled voltage source (VCVS).

The `vcvs_sw` primitive represents a dependent voltage source controlled by a voltage across two circuit terminals. Its scale factor is set by the real-typed input `scale`.

This primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| in_pos | input | xreal | positive reference terminal |
| in_neg | input | xreal | negative reference terminal |
| scale | input | real | scale factor |

