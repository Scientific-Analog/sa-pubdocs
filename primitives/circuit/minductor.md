---
title: "XMODEL primitive: minductor"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: minductor
primitive_category: circuit
description: "An n-port multiple-inductor circuit element."
date: 2026-03-11T07:20:43.522279
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE minductor
An n-port multiple-inductor circuit element.

The `minductor` primitive represents an n-port multiple-inductor element with self/mutual inductances. The number of ports, i.e., the number of self-inductor elements is defined by the parameter `num_port`. Each of the xreal-type vector terminals `pos` and `neg` lists the positive and negative terminals of the ports #1, #2, ..., #N in sequence, respectively. That is:

```
    pos[0:num_port-1] = {pos_1, pos_2, ..., pos_n}
    neg[0:num_port-1] = {neg_1, neg_2, ..., neg_n}
```

The parameter `L` is an one-dimensional real-typed array defining the inductance matrix with self/mutual inductance values (L_ij) in the following format:

```
    L = '{L_11, L_12, ..., L_1N, L_21, L_22, ..., L_2N, ..., L_ij, ..., L_N1, L_N2, ..., L_NN}
```

where L_ii denotes the self inductance and L_ij denotes the mutual inductance between the inductors at port #i and port #j. Note that the inductance matrix must be symmetric, i.e., L_ij = L_ji.

The parameter `ic` is a real-type array that can optionally define the initial conditions of the currents flowing through the ports. Also, the parameters `Cpos` and `Cneg` can optionally define the capacitances between the ports' positive/negative terminals and ground, respectively.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminals of the ports |
| neg | input | xreal | negative terminals of the ports |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_port | int | 2 | None | number of ports |
| L | real array | '{1.0, 1.0, 1.0, 1.0} | henries | inductance matrix |
| ic | real array | '{`NaN, `NaN} | amperes | initial conditions |
| Cpos | real array | '{0.0, 0.0} | farads | pos-to-gnd capacitances |
| Cneg | real array | '{0.0, 0.0} | farads | neg-to-gnd capacitances |
| m | real | 1.0 | None | multiplicity factor |

