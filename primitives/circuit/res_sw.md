---
title: "XMODEL primitive: res_sw"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: res_sw
primitive_category: circuit
description: "A switchable resistor circuit element."
date: 2026-03-11T07:20:43.530316
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE res_sw
A switchable resistor circuit element.

The `res_sw` primitive represents a two-terminal resistor of which resistance can be controlled by a third input `R`. In other words, the resistance between the two terminals `pos` and `neg` switches to a new value indicated by the real-typed input `R` whenever its value changes.

Since every value-change event of the input `R` triggers a new computation, the `res_sw` primitive is not recommended for modeling resistance that continuously varies with a voltage or current (use a `res_var` primitive for nonlinear, voltage-dependent resistance).  The `res_sw` primitive is intended mainly for resistance that switches between discrete levels (e.g. resistance programmable by digital control).

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| R | input | real | resistance |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

