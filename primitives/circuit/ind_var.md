---
title: "XMODEL primitive: ind_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: ind_var
primitive_category: circuit
description: "A variable inductor circuit element."
date: 2026-03-11T07:20:43.517369
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE ind_var
A variable inductor circuit element.

The `ind_var` primitive represents a two-terminal inductor of which inductance varies with the current following from `pos` to `neg`.

The parameter `L` is a real-typed array defining the current-dependent inductance as a piecewise-constant (PWC) function using the following coefficients:

```
    '{L0, V1, L1, V2, L2, V3, L3, ..., LN}.
```

meaning that the inductance L is:

```
    L = L0     for V < V1,
        L1     for V1 <= V < V2,
        L2     for V2 <= V < V3,
        ...
        L(N-1) for V(N-1) <= V < VN,
        LN     for VN <= V.
```

Note that the array has an odd number of elements since it starts with an inductance value (L0) and ends with an inductance value (LN). The piecewise-constant inductance means that the inductor has a piecewise-linear flux-to-I relationship.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| L | real array | '{1.0} | henries | PWC inductance |
| ic | real | `NaN | amperes | initial condition |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

