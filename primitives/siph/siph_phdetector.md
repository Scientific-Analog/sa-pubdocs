---
title: "XMODEL primitive: siph_phdetector"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_phdetector
primitive_category: siph
description: "A photodetector element."
date: 2026-03-11T07:20:43.582360
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_phdetector
A photodetector element.

The `siph_phdetector` represents a photodetector element that generates an electrical current proportional to the incident optical power.

The parameter `R` specifies the responsivity, the ratio of the generated current to the incident optical power. It is formatted as a real-type array of (wavelength, responsivity) pairs defining the responsivity as a piecewise-linear (PWL) function of the optical wavelength:

```
    '{L1, R1, L2, R2, L3, R3, ..., LN, RN}.
```

For instance, a parameter value of `R` set to '{600e-9, 0.0, 1600e-9, 0.1, 1800e-9, 0.0} would describe a photodetector with the following wavelength-dependent responsivity:

```
    Responsivity  0.1                -+-
                                  ---   -
                               ---       -
                            ---           -
                  0   ----+-               +-----
                        600nm      1600nm 1800nm   Wavelength
```

On the other hand, if the parameter `R` has only a single element (e.g. '{R0}), its value (R0) specifies a uniform responsivity independent of the wavelength.

The parameter `bandwidth` specifies the response bandwidth of the photodetector. The parameter `Zrel` specifies the effective impedance that the photodetector presents at its optical input port relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0. The parameters `abstol` and `reltol` set the absolute and relative tolerances used for this event-filtering, respectively.

When the parameter `filename` is defined, the primitive reads the named file that defines the same named parameters in Python format. For instance, for the parameter `R`, its real-typed array value can be defined as following:

```
    R = [ L1, R1, L2, R2, L3, R3, ..., LN, RN ].
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| in | input | xreal | optical input port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| R | real array | '{1.0} | amperes/watt | responsivity data |
| bandwidth | real | `INFINITY | Hz | response bandwidth |
| Zrel | real | 1.0 | None | relative characteristic impedance |
| abstol | real | 1e-6 | None | absolute tolerance for event-filtering |
| reltol | real | 1e-3 | None | relative tolerance for event-filtering |
| filename | string | "" | None | parameter definition file |

