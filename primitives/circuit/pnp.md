---
title: "XMODEL primitive: pnp"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: pnp
primitive_category: circuit
description: "An PNP-type bipolar junction transistor."
date: 2026-03-11T07:20:43.529133
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE pnp
An PNP-type bipolar junction transistor.

The `pnp` primitive represents a three-terminal PNP-type bipolar junction transistor. It implements an approximate Ebers-Moll transistor model described below:

```
    Ic = Is*(exp(-Vbe/(N*VT))-1) - (1+1/Br)*Is*(exp(-Vbc/(N*VT))-1)
    Ie = (1+1/Bf)*Is*(exp(-Vbe/(N*VT))-1) - Is*(exp(-Vbc/(N*VT))-1)
    Ib = Ie - Ic
    where VT = kT/q (25.695mV at 25C)
```

In the equations above, `Is` and `VT` change with the global parameter ``global_temp`, defining the temperature in Celsius (default: 25C). Specifically, the thermal voltage `VT` is proportional to the absolute temperature and the transport saturation current `Is` is proportional to exp(-VG0/VT), where VG0 is assumed to be 1.205V for silicon.

The parameters `abstol` and `reltol` set the error tolerance approximating these equations.

This primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| c | input | xreal | collector |
| b | input | xreal | base |
| e | input | xreal | emitter |
| s | input | xreal | substrate |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Is | real | 1e-16 | A | transport saturation current at T=25C |
| N | real | 1.0 | None | emission coefficient |
| Bf | real | 100.0 | None | forward beta |
| Br | real | `INFINITY | None | reverse beta |
| Va | real | `INFINITY | V | Early voltage |
| Cbe | real | 0.0 | farad | base-emitter capacitance |
| Cbc | real | 0.0 | farad | base-collector capacitance |
| Ccs | real | 0.0 | farad | collector-substrate capacitance |
| Cbs | real | 0.0 | farad | base-substrate capacitance |
| Ces | real | 0.0 | farad | emitter-substrate capacitance |
| abstol | real | 1e-9 | A | absolute tolerance |
| reltol | real | 0.1 | None | relative tolerance |
| m | real | 1.0 | None | multiplicity factor |

