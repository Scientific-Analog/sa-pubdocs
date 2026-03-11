---
title: "XMODEL primitive: ilimit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: ilimit
primitive_category: circuit
description: "A current limiting element."
date: 2026-03-11T07:20:43.511925
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE ilimit
A current limiting element.

The `ilimit` primitive represents a series resistor element that keeps the current flowing from `pos` to `neg` within the specified limits. The parameters `Imax` and `Imin` define the maximum and minimum limits, respectively.

When the current I is within the limits, the element has a low series resistance, defined by the parameter `Rpass`, passing I as-is. On the other hand, when I is about to exceed one of the limits, the element switches to a high series resistance, defined by the parameter `Rstop`, stopping I at the corresponding limit. For effective current limiting, `Rstop` must be sufficiently large compared to the output resistance of the circuit driving the current.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Imax | real | `INFINITY | A | maximum current limit |
| Imin | real | -`INFINITY | A | minimum current limit |
| Rpass | real | 0.01 | ohms | series resistance while passing |
| Rstop | real | `INFINITY | ohms | series resistance while limiting |
| m | real | 1.0 | None | multiplicity factor |

