---
title: "XMODEL primitive: siph_ringres"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_ringres
primitive_category: siph
description: "An optical ring resonator."
date: 2026-03-11T07:20:43.588404
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_ringres
An optical ring resonator.

The `siph_ringres` primitive represents an optical ring resonator, which exhibits varying transmission between the ports `in` and `thru` depending on the presence of resonance in a coupled closed-loop path. A typical silicon microring resonator is made of a main waveguide that connects between the ports, a ring waveguide that forms a closed loop, and a directional coupler that couples these two waveguides. This `siph_ringres` primitive models the optical ring resonator as a reciprocal element that can receive incident waves from any port and propagate waves with the symmetrical transfer characteristics.

```
               in  --------------------- thru
                            ---
                           /   \
                          |     |
                           \   /
                            ---
```

The parameter `oplength_cpl` specifies the optical path length of the directional coupler in meters, which is equal to the shortest delay between the ports `in` and `thru` multiplied by the speed of light in free space (c0=2.99792458e8 meters/sec). The parameters `gain_thru` and `gain_cpl` specify the transmission and coupling gains of the directional coupler, respectively. The wave being coupled to an opposite-side waveguide experiences a -pi/2 phase shift. Note that this primitive does not model the dependencies of the gains `gain_thru` and `gain_cpl` on the light's wavelength or waveguide's length.

The parameter `oplength_ring` specifies the optical path length of the ring, including the optical path length of the directional coupler. Therefore, the resonance occurs when the value of the `oplength_ring` is equal to an integer-multiple of the wavelength of the incident wave. The parameter `gain_ring` specifies the additional gain through a round trip of the ring waveguide excluding the transmission gain of the directional coupler.

The parameter `dispersion` specifies the total group delay dispersion (GDD) of the ring waveguide at the center wavelength specified by the parameter `wavelength`. The GDD is defined as the change in the group delay (tg) with respect to the angular frequency (w), which can be measured directly or derived from the dispersion coefficient (D) (in second/meter^2) as:

```
       dtg       (wavelength)^2               (wavelength)^2         (oplength)
GDD = ----- = - ---------------- * D * l = - ---------------- * D * ------------.
       dw            2*PI                         2*PI                   ng
```

Note that such dispersion in the group delay can cause shifts in the periodic patterns of the ring resonator's frequency response.

The parameter `Zrel` specifies the main waveguide's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | input port |
| thru | input | xreal | thru port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| oplength_cpl | real | 38.75u | meters | optical path length of coupler |
| oplength_ring | real | 155u | meters | optical path length of ring |
| gain_thru | real | 0.99 | None | transmission gain of coupler |
| gain_cpl | real | 0.14 | None | coupling gain of coupler |
| gain_ring | real | 0.99 | None | additional gain of ring |
| dispersion | real | 0.0 | second^2 | group delay dispersion |
| wavelength | real | 1550n | meters | center wavelength |

