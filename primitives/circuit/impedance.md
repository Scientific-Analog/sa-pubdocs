---
title: "XMODEL primitive: impedance"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: impedance
primitive_category: circuit
description: "An impedance circuit element."
date: 2026-03-11T07:20:43.514514
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE impedance
An impedance circuit element.

The `impedance` primitive represents a two-terminal impedance element. The string-type parameters `Z`, `Zpos`, and `Zneg` define the impedances between the ports `pos` and `neg`, between `pos` and ground, and between `neg` and ground, respectively, using the circuit network expressions.

The circuit network expressions describe the impedance as series or parallel combinations of passive R/L/C elements. For example, a string "R50||C1p" describes a parallel combination of a 50-ohm resistance and a 1-pF capacitance, and "R50+L1n" describes a series combination of a 50-ohm resistance and a 1-nH inductance. In a circuit network expression, each R/L/C element is described with a string starting with an `R`, `L`, or `C` prefix followed by its resistance, inductance, or capacitance value, respectively, and an optional unit suffix (e.g. `n` for nano and `p` for pico). An arbitrary network of R/L/C elements can be described using the series operator `+`, parallel operator `||`, and grouping operators `()`.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Z | string | "R1" | ohms | pos-to-neg impedance |
| Zpos | string | "inf" | ohms | pos-to-gnd impedance |
| Zneg | string | "inf" | ohms | neg-to-gnd impedance |
| m | real | 1.0 | None | multiplicity factor |

