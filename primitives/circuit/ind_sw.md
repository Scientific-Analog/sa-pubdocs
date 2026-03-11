---
title: "XMODEL primitive: ind_sw"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: ind_sw
primitive_category: circuit
description: "A switchable inductor circuit element."
date: 2026-03-11T07:20:43.515978
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE ind_sw
A switchable inductor circuit element.

The `ind_sw` primitive represents a two-terminal inductor of which inductance can be controlled by a third input `L`. In other words, the inductance between the two terminals `pos` and `neg` switches to a new value indicated by the real-typed input `L` whenever its value changes. The total flux stored on the inductor is preserved before and after each switching event.

Since every value-change event of the input `L` triggers a new computation, the `ind_sw` primitive is not recommended for modeling inductance that continuously varies with a voltage or current (use a `ind_var` primitive for nonlinear, current-dependent inductance).  The `ind_sw` primitive is intended mainly for inductance that switches between discrete levels (e.g. inductance programmable via digital control).

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| L | input | real | inductance |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| ic | real | `NaN | amperes | initial condition |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

