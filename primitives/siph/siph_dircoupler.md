---
title: "XMODEL primitive: siph_dircoupler"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_dircoupler
primitive_category: siph
description: "An optical directional coupler."
date: 2026-03-11T07:20:43.580881
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_dircoupler
An optical directional coupler.

The `siph_dircoupler` primitive represents an optical directional coupler, which splits the incident wave entering the port `in` into two waves leaving the ports `thru` and `cpl`. In typical optical directional couplers, the port `thru` is the opposite-side port on the same waveguide with the port `in` and the port `cpl` is the opposite-side port on the coupled waveguide. Both the waves experience the propagation delay through the waveguides, which is equal to the optical path length of each waveguide (specified by the parameter `oplength`) divided by the speed of light in free space (c0=2.99792458e8 meters/sec).

```
               in  ---+             +--- thru
                       \           /
                        +---------+
                        +---------+
                       /           \
    (isolated) iso ---+             +--- cpl (coupled)
```

The parameter `gain_thru` specifies the transmission gain from the port `in` to port `thru` and the parameter `gain_cpl` specifies the coupling gain from the port `in` to port `cpl`. The wave propagating from the port `in` to port `cpl` may also experience an additional phase shift specified by the parameter `phase_cpl` (default: -M_PI/2). The `siph_dircoupler` primitive is a reciprocal element that can receive incident waves from any port and propagate waves with the symmetrical transfer characteristics.

The parameter `oplength` specifies the optical path length of each waveguide in meters, which is equal to the waveguide's propagation delay multiplied by the speed of light in free space (c0). For instance, a quarter-wavelength directional coupler for a 1550nm laser would have an optical path length of 1550nm/4=387.5nm. Note that this primitive does not model the dependencies of the gains `gain_thru` and `gain_cpl` on the light's wavelength or waveguide's length.

The parameter `Zrel` specifies the coupler's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | input port |
| thru | input | xreal | thru port |
| cpl | input | xreal | coupled port |
| iso | input | xreal | isolated port |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| oplength | real | 15.5e-6 | meters | optical path length |
| gain_thru | real | 0.7071 | None | transmission gain (in-to-thru) |
| gain_cpl | real | 0.7071 | None | coupling gain (in-to-cpl) |
| phase_cpl | real | -M_PI/2 | radians | coupling phase shift (in-to-cpl) |

