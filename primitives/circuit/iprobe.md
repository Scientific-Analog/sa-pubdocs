---
title: "XMODEL primitive: iprobe"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: iprobe
primitive_category: circuit
description: "A current probe circuit element."
date: 2026-03-11T07:20:43.519718
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE iprobe
A current probe circuit element.

The `iprobe` primitive measures a current across a circuit branch and drives its output signal with that result. In other words, this primitive serves as a gateway to propagate a signal from circuit-network models to behavioral models.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model during run-time, based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

