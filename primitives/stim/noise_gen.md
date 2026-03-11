---
title: "XMODEL primitive: noise_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: noise_gen
primitive_category: stim
description: "A noise generator"
date: 2026-03-11T07:20:43.457705
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE noise_gen
A noise generator

The `noise_gen` primitive generates a white Gaussian noise with a mean of `mean` and a standard deviation of `stddev`.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | noise output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| mean | real | 0.0 | None | DC value |
| stddev | real | 0.0 | None | RMS value |

