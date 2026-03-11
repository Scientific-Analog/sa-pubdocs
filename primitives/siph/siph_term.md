---
title: "XMODEL primitive: siph_term"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: siph_term
primitive_category: siph
description: "An optical termination element."
date: 2026-03-11T07:20:43.591415
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE siph_term
An optical termination element.

The `siph_term` primitive represents an optical termination element that absorbs all the energy at the end of the optical waveguide without causing reflections. It is modeled with an equivalent resistor of which resistance value is matched to the characteristic impedance of the optical waveguide.

The parameter `Zrel` specifies the waveguide's characteristic impedance relative to a reference impedance (Z0) of your choice. Note that the use of this relative impedance allows one to determine the amount of reflections at impedance discontinuities without having to know the absolute values of the characteristic impedances. While the choice of the reference impedance (Z0) can be arbitrary, it must be consistent across all the silicon-photonic components used in a system. In other words, all the equivalent circuit elements describing the impedance relationships at the optical ports must use the impedance values relative to the same Z0.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | optical input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| Zrel | real | 1.0 | None | relative characteristic impedance |

