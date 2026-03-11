---
title: "XMODEL primitive: vlimit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vlimit
primitive_category: circuit
description: "A voltage limiting element."
date: 2026-03-11T07:20:43.546864
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vlimit
A voltage limiting element.

The `vlimit` primitive represents a shunt resistor element that keeps the voltage difference between `pos` and `neg` within the specified limits. The parameters `Vmax` and `Vmin` define the maximum and minimum limits, respectively.

When the voltage difference V is within the limits, the element has a high shunt resistance, defined by the parameter `Rpass`, passing V as-is. On the other hand, when V is about to exceed one of the limits, the element switches to a low shunt resistance, defined by the parameter `Rstop`, stopping V at the corresponding limit. For effective voltage limiting, `Rstop` must be sufficiently small compared to the output resistance of the circuit driving the voltages.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Vmax | real | `INFINITY | V | maximum voltage limit |
| Vmin | real | -`INFINITY | V | minimum voltage limit |
| Rpass | real | `INFINITY | ohms | shunt resistance while passing |
| Rstop | real | 0.01 | ohms | shunt resistance while limiting |
| m | real | 1.0 | None | multiplicity factor |

