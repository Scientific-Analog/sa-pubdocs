---
title: "XMODEL primitive: cap_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: cap_var
primitive_category: circuit
description: "A variable capacitor circuit element."
date: 2026-03-11T07:20:43.502080
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE cap_var
A variable capacitor circuit element.

The `cap_var` primitive represents a two-terminal capacitor of which capacitance varies with the voltage across the two terminals, `pos` and `neg`.

The parameter `C` is a real-typed array defining the voltage-dependent capacitance as a piecewise-constant (PWC) function using the following coefficients:

```
    '{C0, V1, C1, V2, C2, V3, C3, ..., VN, CN}.
```

meaning that the resistance C is:

```
    C = C0     for V < V1,
        C1     for V1 <= V < V2,
        C2     for V2 <= V < V3,
        ...
        C(N-1) for V(N-1) <= V < VN.
        CN     for VN <= V
```

Note that the array has an odd number of elements since it starts with a capacitance value (C0) and ends with a capacitance value (CN). The piecewise-constant capacitance means that the capacitor has a piecewise-linear Q-V relationship.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself.  The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| C | real array | '{1.0} | farads | PWC capacitance |
| ic | real | `NaN | volts | initial condition |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

