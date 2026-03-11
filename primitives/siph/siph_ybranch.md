---
title: "XMODEL primitive: siph_ybranch"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_ybranch
primitive_category: siph
description: "An optical Y-shaped branch."
date: 2026-03-11T07:20:43.594404
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_ybranch
An optical Y-shaped branch.

The `siph_ybranch` primitive represents an optical Y-shaped branch, which can serve either as a power splitter or as a power combiner. In other words, the primitive can split the incident wave entering the port `in` into two waves leaving the ports `thru_1` and `thru_2`, or combine the incident waves entering the ports `thru_1` and `thru_2` into a wave leaving the port `in`. The waves experience the delays as they propagate through the Y-branch, which is equal to the optical path length between the port `in` and port `thru_1` or `thru_2` (specified by the parameter `oplength`) divided by the speed of light in free space (c0=2.99792458e8 meters/sec).

```
                 +-------- thru_1
                /
    in --------+
                \
                 +-------- thru_2
```

The parameter `gain_thru` specifies the transmission gain between the port `in` and port `thru_1` or `thru_2` (default: 0.7071). The `siph_ybranch` primitive is a reciprocal element that can receive incident waves from any port and propagate waves with the symmetrical transfer characteristics.

The parameter `oplength` specifies the optical path length between the port `in` and port `thru_1` or `thru_2` in meters, which is equal to the waveguide's propagation delay multiplied by the speed of light in free space (c0). For instance, a quarter-wavelength Y-branch for a 1550nm laser would have an optical path length of 1550nm/4=387.5nm. Note that this primitive does not model the dependency of the gain `gain_thru` on the light's wavelength or waveguide's length.

The parameter `Zrel` specifies the Y-branch's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | input port |
| thru_1 | input | xreal | thru port #1 |
| thru_2 | input | xreal | thru port #2 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |
| oplength | real | 15.5e-6 | meters | optical path length |
| gain_thru | real | 0.7071 | None | transmission gain (in-to-thru) |

