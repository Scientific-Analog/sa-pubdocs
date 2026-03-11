---
title: "XMODEL primitive: real_to_temp"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: real_to_temp
primitive_category: connect
description: "Temperature assignment with a real-type value."
date: 2026-03-11T07:20:43.478856
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE real_to_temp
Temperature assignment with a real-type value.

The `real_to_temp` primitive sets the global temperature (``global_temp`) with a real-type input `in`.

The string-type parameter `unit` sets whether the input value is in Celsius (C) or Fahrenheit (F).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | real | real-type temperature input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| unit | string | "C" | None | temperature unit |

