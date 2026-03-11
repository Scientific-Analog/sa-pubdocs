---
title: "XMODEL primitive: siph_cwlaser"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_cwlaser
primitive_category: siph
description: "A continuous-wave laser source element."
date: 2026-03-11T07:20:43.578079
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_cwlaser
A continuous-wave laser source element.

The `siph_cwlaser` primitive represents a multi-wavelength, continuous-wave laser source.

The parameter `wavelength` specifies the list of wavelengths, and the parameters `power` and `init_phase` specify the power and initial phase of the corresponding wavelength components, respectively. If the parameter `power` or `init_phase` has only one element, it is assumed that all the wavelength components have the same power or initial phase, respectively.

The parameter `Zrel` specifies the relative characteristic impedance of the optical waveguide feeding the laser to the output port `out`. The value of `Zrel` is relative to a reference impedance (Z0) of your choice. The use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

When the parameter `filename` is defined, the primitive reads the named file that defines the same named parameters in Python format. For instance, the real-typed array values of the parameters `wavelength` and `power` can be defined as following:

```
    wavelength  = [ 1550e-9, 1630e-9, 1710e-9, 1790e-9 ]
    power = [ 1.0, 0.9, 0.8, 0.95 ]
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | input | xreal | optical output port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| wavelength | real array | '{1550e-9} | meters | list of wavelengths |
| power | real array | '{1.0} | watts | list of power values |
| init_phase | real array | '{0.0} | radian | list of initial phases |
| Zrel | real | 1.0 | None | relative characteristic impedance |
| filename | string | "" | None | parameter definition file |

