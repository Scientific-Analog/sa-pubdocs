---
title: "XMODEL primitive: siph_phshifter"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_phshifter
primitive_category: siph
description: "An optical phase shifter element."
date: 2026-03-11T07:20:43.583788
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_phshifter
An optical phase shifter element.

The `siph_phshifter` primitive represents an optical phase shifter, which propagates the optical waves with a variable delay controlled by the xreal-typed input 'delay. For optical waves, this delay is equivalent to a phase shift equal to delay*2*PI*c0/wavelength, where c0 is the speed of light in free space.

The parameter `Zrel` specifies the phase shifter's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

The parameter `gain` and `dispersion` specifies the total gain and group delay dispersion (GDD) through the phase shifter. For more information on these parameters, please refer to the documentation on the `siph_waveguide` primitive.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| port_1 | input | xreal | optical port #1 |
| port_2 | input | xreal | optical port #2 |
| delay | input | xreal | group delay |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| gain | real | 1.0 | None | gain |
| dispersion | real | 0.0 | second^2 | group delay dispersion |
| wavelength | real | 1550e-9 | meters | center wavelength |

