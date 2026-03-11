---
title: "XMODEL primitive: siph_cwlaser_var"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_cwlaser_var
primitive_category: siph
description: "A tunable continuous-wave laser source element."
date: 2026-03-11T07:20:43.579586
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_cwlaser_var
A tunable continuous-wave laser source element.

The `siph_cwlaser_var` primitive represents a multi-wavelength, continuous-wave laser source with adjustable wavelengths. The input `wavelen` controls the wavelength of each component.

The parameter `num_wavelen` specifies the number of wavelength inputs, and hence the number of wavelength components produced by the laser source. The parameters `power` and `init_phase` specify the power and initial phase of the corresponding wavelength components, respectively. If the parameter `power` or `init_phase` has only one element, it is assumed that all the wavelength components have the same power or initial phase, respectively. The parameter `scale` specifies the scale factor applied to the input `wavelen`, of which default value is 1e-9 so that the wavelength inputs can be specified in nanometers (nm). The parameters `abstol` and `reltol` set the absolute and relative tolerances controlling the wavelength values, respectively.

The parameter `Zrel` specifies the relative characteristic impedance of the optical waveguide feeding the laser to the output port `out`. The value of `Zrel` is relative to a reference impedance (Z0) of your choice. The use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | input | xreal | optical output port |
| wavelen | input | xreal | wavelength input port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_wavelen | int | 1 | None | number of wavelength inputs |
| power | real array | '{1.0} | watts | list of power values |
| init_phase | real array | '{0.0} | radian | list of initial phases |
| scale | real | 1e-9 | None | wavelength scale factor |
| abstol | real | 1e-12 | meters | wavelength absolute tolerance |
| reltol | real | 1e-6 | None | wavelength relative tolerance |
| Zrel | real | 1.0 | None | relative characteristic impedance |

