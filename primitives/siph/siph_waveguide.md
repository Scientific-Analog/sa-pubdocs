---
title: "XMODEL primitive: siph_waveguide"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_waveguide
primitive_category: siph
description: "An optical waveguide element."
date: 2026-03-11T07:20:43.592746
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_waveguide
An optical waveguide element.

The `siph_waveguide` primitive represents an optical waveguide that guides the propagation of optical waves. Particularly, this primitive models the optical waveguide as an equivalent transmission line that internally propagates the equivalent voltage and current waves carrying the total optical power.

The parameter `Zrel` specifies the waveguide's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

The parameter `oplength` specifies the optical path length of the waveguide in meters, which is equal to the waveguide's group delay at the wavelength of interest multiplied by the speed of light in free space (c0=2.99792458e8 meters/sec). For instance, a quarter-wavelength waveguide of a 1550nm laser has an optical path length of 1550nm/4=387.5nm. It is also equal to the physical length (l) of the waveguide multiplied by the group refractive index (ng) at the wavelength.

The parameter `gain` specifies the total gain through the waveguide. For example, a 5-km optical waveguide with an attenuation constant of 0.2dB/km would have a total gain equal to 10^(-0.2*5/20)=0.891. The parameter `dispersion` specifies the total group delay dispersion (GDD) of the waveguide at the center wavelength specified by the parameter `wavelength`. The GDD is defined as the change in the group delay (tg) with respect to the angular frequency (w), which can be measured directly or derived from the dispersion coefficient (D) (in second/meter^2) as:

```
       dtg       (wavelength)^2               (wavelength)^2         (oplength)
GDD = ----- = - ---------------- * D * l = - ---------------- * D * ------------.
       dw            2*PI                         2*PI                   ng
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| port_1 | input | xreal | optical port #1 |
| port_2 | input | xreal | optical port #2 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| oplength | real | 15.5e-6 | meters | optical path length |
| gain | real | 1.0 | None | gain |
| dispersion | real | 0.0 | second^2 | group delay dispersion |
| wavelength | real | 1550e-9 | meters | center wavelength |

