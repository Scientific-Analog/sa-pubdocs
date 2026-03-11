---
title: "XMODEL primitive: dc_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: dc_gen
primitive_category: stim
description: "An analog DC generator"
date: 2026-03-11T07:20:43.455406
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE dc_gen
An analog DC generator

The `dc_gen` primitive generates a DC signal. It can also generate white

Gaussian noise.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| value | real | 0.0 | None | DC value |
| noise | real | 0.0 | None | RMS noise |

