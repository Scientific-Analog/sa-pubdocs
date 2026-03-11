---
title: "XMODEL primitive: transformer"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: transformer
primitive_category: circuit
description: "An ideal transformer circuit element."
date: 2026-03-11T07:20:43.539750
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE transformer
An ideal transformer circuit element.

The `transformer` primitive represents an ideal two-winding transformer. Winding 1 connects terminals `pos1` and `neg1` and has `n1` turns. Winding 2 connects terminals `pos2` and `neg2` and has `n2` turns. An ideal transformer has the following I/V relationships:

```
    v1/v2 = n1/n2
    i1/i2 = -n2/n1
```

To model a physical transformer with the inductance of L1 and L2 and coupling coefficient of k between the two windings, add a parallel inductor Lp=k*L1 between the pos1 and neg1 terminals and series inductors Ls1=L1*(1-k) and Ls2=L2*(1-k) to the windings 1 and 2, respectively. The turn ratio n1/n2 is equal to sqrt(L1/L2). The absolute number of turns of each winding is not important but only the ratio n1/n2.

```
                          n1:n2
                         o     o
   o---Ls1---o pos1 o----) ||| (----o pos2 o---Ls2---o
             |           ) ||| (
             Lp          ) ||| (
             |           ) ||| (
             o neg1 o----) ||| (----o neg2
```

The internal xreal-typed variables V, I, and P measure the voltage across, current through, and power entering the port of winding 1, respectively. The voltage, current, and power of the port of winding 2 can be easily derived using the I/V equations listed above. Note that the ideal transformer itself does not dissipate any power and the power entering the port of winding 1 is always equal to the power leaving the port of winding 2.

Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos1 | input | xreal | positive terminal of winding 1 |
| neg1 | input | xreal | negative terminal of winding 1 |
| pos2 | input | xreal | positive terminal of winding 2 |
| neg2 | input | xreal | negative terminal of winding 2 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| n1 | real | 1.0 | None | number of turns on winding 1 |
| n2 | real | 1.0 | None | number of turns on winding 2 |

