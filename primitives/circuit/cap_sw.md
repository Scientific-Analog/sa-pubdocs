---
title: "XMODEL primitive: cap_sw"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: cap_sw
primitive_category: circuit
description: "A switchable capacitor circuit element."
date: 2026-03-11T07:20:43.500753
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE cap_sw
A switchable capacitor circuit element.

The `cap_sw` primitive represents a two-terminal capacitor of which capacitance can be controlled by a third input `C`. In other words, the capacitance between the two terminals `pos` and `neg` switches to a new value indicated by the real-typed input `C` whenever its value changes. The total charge stored on the capacitor is preserved before and after each switching event.

Since every value-change event of the input `C` triggers a new computation, the `cap_sw` primitive is not recommended for modeling capacitance that continuously varies with a voltage or current (use a `cap_var` primitive for nonlinear, voltage-dependent capacitance).  The `cap_sw` primitive is intended mainly for capacitance that switches between discrete levels (e.g. capacitance programmable via digital control).

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| C | input | real | capacitance |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| ic | real | `NaN | volts | initial condition |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

