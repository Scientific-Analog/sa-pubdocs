---
title: "XMODEL primitive: vprobe"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vprobe
primitive_category: circuit
description: "A voltage probe circuit element."
date: 2026-03-11T07:20:43.549852
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vprobe
A voltage probe circuit element.

The `vprobe` primitive measures a voltage across two circuit terminals and drives its output signal with that result. In other words, this primitive serves as a gateway to translate a voltage in electrical models to a signal in signal-flow models.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

