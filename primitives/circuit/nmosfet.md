---
title: "XMODEL primitive: nmosfet"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: nmosfet
primitive_category: circuit
description: "An n-type MOSFET transistor."
date: 2026-03-11T07:20:43.525093
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE nmosfet
An n-type MOSFET transistor.

The `nmosfet` primitive represents a four-terminal n-channel MOSFET.

The current version implements an approximate EKV transistor model, consisting of two transconductance stages with rectified linear characteristics:

```
    Id1 = Kp * W/L * (Vgs - Vth)    if Vgs > Vth
    Id2 = Kp * W/L * (Vgd - Vth)    if Vgd > Vth
    Ids = Id1 - Id2
```

Each capacitance parameter (Cgs, Cgd, Cgb, Csb, Cdb) is an array of three real-typed values each expressing the capacitance between the corresponding terminals of the transistor operating in cut-off, linear, and saturation region, respectively.

This primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| d | input | xreal | drain |
| g | input | xreal | gate |
| s | input | xreal | source |
| b | input | xreal | bulk |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| W | real | 1e-6 | m | channel width |
| L | real | 1e-6 | m | channel length |
| Kp | real | 1e-3 | A/V | intrinsic transconductance |
| Kp_data | real | '{0.0} | A/V | intrinsic transconductance data |
| Vth | real | 0.0 | V | threshold voltage |
| Ro | real | `INFINITY | ohms | output resistance |
| Cgs | real_array | '{0.0,0.0,0.0} | farad/m | G-to-S capacitance per width (off,lin,sat) |
| Cgd | real_array | '{0.0,0.0,0.0} | farad/m | G-to-D capacitance per width (off,lin,sat) |
| Cgb | real_array | '{0.0,0.0,0.0} | farad/m | G-to-B capacitance per width (off,lin,sat) |
| Csb | real_array | '{0.0,0.0,0.0} | farad/m | S-to-B capacitance per width (off,lin,sat) |
| Cdb | real_array | '{0.0,0.0,0.0} | farad/m | D-to-B capacitance per width (off,lin,sat) |
| m | real | 1.0 | None | multiplicity factor |

