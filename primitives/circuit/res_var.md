---
title: "XMODEL primitive: res_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: res_var
primitive_category: circuit
description: "A variable resistor circuit element."
date: 2026-03-11T07:20:43.531578
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE res_var
A variable resistor circuit element.

The `res_var` primitive represents a two-terminal resistor of which resistance varies with the voltage across the two terminals, `pos` and `neg`.

The parameter `R` is a real-typed array defining the voltage-dependent resistance as a piecewise-constant (PWC) function using the following coefficients:

```
    '{R0, V1, R1, V2, R2, V3, R3, ..., RN}.
```

meaning that the resistance R is:

```
    R = R0     for V < V1,
        R1     for V1 <= V < V2,
        R2     for V2 <= V < V3,
        ...
        R(N-1) for V(N-1) <= V < VN,
        RN     for VN <= V.
```

Note that the array has an odd number of elements since it starts with a resistance value (R0) and ends with a resistance value (RN). The piecewise-constant resistance means that the resistor has a piecewise-linear I-V relationship.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| R | real array | '{1.0} | ohms | PWC resistance |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

