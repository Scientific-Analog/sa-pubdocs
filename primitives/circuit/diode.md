---
title: "XMODEL primitive: diode"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: diode
primitive_category: circuit
description: "A diode circuit element."
date: 2026-03-11T07:20:43.509239
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE diode
A diode circuit element.

The `diode` primitive represents a two-terminal diode. Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

The `diode` primitive can model diodes in three ways: using an ideal model (`ideal`),  exponential model (`exp`), or piecewise-linear model (`pwl`).

### 1) Ideal diode model (model = 'ideal')

The diode turns on when the voltage across the two terminals (pos and neg) is higher than the specified turn-on voltage (`Von`) and turns off otherwise. The parameters `Ron` and `Roff` define the turn-on and turn-off resistances, respectively.

### 2) Exponential diode model (model = 'exp')

The diode current (Id) is an exponential function of the voltage (Vd = V(pos) - V(neg)) according to the following equation:

```
    Id = Is * (exp((Vd-Id*Rs)/(N*VT)) - 1)
    where VT = kT/q (25.695mV at 25C)
```

In this equation, `Is` and `VT` change with the global parameter ``global_temp`, defining the temperature in Celsius (default: 25C). Specifically, the thermal voltage `VT` is proportional to the absolute temperature and the transport saturation current `Is` is proportional to exp(-VG0/VT), where VG0 is assumed to be 1.205V for silicon.

The parameters `abstol` and `reltol` set the error tolerance approximating these equations.

### 3) Piecewise-linear diode model (model = 'pwl')

Using this model, the diode can have an arbitrary piecewise-linear I-V characteristic. In this case, the diode is equivalent to a nonlinear resistor (the `res_var` primitive). The parameter `R_data` describes the piecewise-constant resistance values across different voltage intervals, using the same format as the `R` parameter in the `res_var` primitive.

For all the diode models, the parameter `C` defines the linear capacitance across the terminals and the parameters `Cpos` and `Cneg` define the linear capacitance of the terminals `pos` and `neg` to the ground, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| model | string | "ideal" | None | diode model |
| Von | real | 0.0 | volts | turn-on voltage |
| Ron | real | 0.01 | volts | turn-on resistance |
| Roff | real | `INFINITY | volts | turn-off resistance |
| Is | real | 1e-16 | ampere | saturation current |
| N | real | 1.0 | None | emission coefficient |
| Rs | real | 0.0 | ohms | series resistance |
| abstol | real | 1e-9 | A | absolute tolerance |
| reltol | real | 0.1 | None | relative tolerance |
| R_data | real array | '{1.0} | ohms | PWC resistance |
| C | real | 0.0 | farads | pos-to-neg capacitance |
| Cpos | real | 0.0 | farads | pos-to-gnd capacitance |
| Cneg | real | 0.0 | farads | neg-to-gnd capacitance |
| m | real | 1.0 | None | multiplicity factor |

