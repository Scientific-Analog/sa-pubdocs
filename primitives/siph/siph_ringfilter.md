---
title: "XMODEL primitive: siph_ringfilter"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_ringfilter
primitive_category: siph
description: "An optical ring resonator filter."
date: 2026-03-11T07:20:43.585252
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_ringfilter
An optical ring resonator filter.

The `siph_ringfilter` primitive represents an optical ring resonator filter, which splits the incident wave entering the port `in` into two waves leaving the ports `thru` and `drop`, where the transmission gain to the port `thru` and coupling gain to the port `drop` vary with the incident wave's wavelength depending on the presence of resonance in a coupled closed-loop path. A typical silicon microring resonator filter is made of a waveguide that connects between the ports `in` and `thru`, a waveguide that connects between the ports `add` and `drop`, and a ring waveguide that forms a closed loop between these two waveguides and is coupled to them via a pair of directional couplers. The `siph_ringfilter` primitive models the optical ring resonator filter as a reciprocal element that can receive incident waves from any port and propagate waves with the symmetrical transfer characteristics.

```
               in  --------------------- thru
                            ---
                           /   \
                          |     |
                           \   /
                            ---
             drop  --------------------- add
```

The parameter `oplength_cpl` specifies the optical path length of the directional couplers in meters, which is equal to the shortest delay between the ports `in` and `thru` or between the ports `add` and `drop` multiplied by the speed of light in free space (c0=2.99792458e8 meters/sec). The parameters `gain_thru1` and `gain_cpl1` specify the transmission and coupling gains of the directional coupler coupling between the `in`-to-`thru` waveguide and the ring, and the parameters `gain_thru2` and `gain_cpl2` specify the transmission and coupling gains of the directional coupler coupling between the `add`-to-`drop` waveguide and the ring, respectively. For both directional couplers, the wave being coupled to an opposite-side waveguide experiences a -pi/2 phase shift. Note that this primitive does not model the dependencies of the gains `gain_thru` and `gain_cpl` on the light's wavelength or waveguide's length.

The parameter `oplength_ring` specifies the optical path length of the ring, including the optical path lengths of the directional couplers. Therefore, the resonance occurs when the value of the `oplength_ring` is equal to an integer-multiple of the wavelength of the incident wave. The parameter `gain_ring` specifies the additional gain through a round trip of the ring waveguide excluding the transmission gains of the two directional couplers. It is assumed that the two directional couplers are located at the symmetrical positions on the ring.

The parameter `dispersion` specifies the total group delay dispersion (GDD) of the ring waveguide at the center wavelength specified by the parameter `wavelength`. The GDD is defined as the change in the group delay (tg) with respect to the angular frequency (w), which can be measured directly or derived from the dispersion coefficient (D) (in second/meter^2) as:

```
       dtg       (wavelength)^2               (wavelength)^2         (oplength)
GDD = ----- = - ---------------- * D * l = - ---------------- * D * ------------.
       dw            2*PI                         2*PI                   ng
```

Note that such dispersion in the group delay can cause shifts in the periodic patterns of the ring resonator filter's frequency response.

The parameter `Zrel` specifies the waveguides' characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | input port |
| thru | input | xreal | thru port |
| add | input | xreal | add port |
| drop | input | xreal | drop port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| oplength_cpl | real | 38.75u | meters | optical path length of coupler |
| oplength_ring | real | 155u | meters | optical path length of ring |
| gain_thru1 | real | 0.99 | None | transmission gain of coupler #1 |
| gain_cpl1 | real | 0.14 | None | coupling gain of coupler #1 |
| gain_thru2 | real | 0.99 | None | transmission gain of coupler #2 |
| gain_cpl2 | real | 0.14 | None | coupling gain of coupler #2 |
| gain_ring | real | 1.0 | None | additional gain of ring |
| dispersion | real | 0.0 | second^2 | group delay dispersion |
| wavelength | real | 1550n | meters | center wavelength |

