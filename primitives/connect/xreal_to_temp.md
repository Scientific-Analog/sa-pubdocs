---
title: "XMODEL primitive: xreal_to_temp"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: xreal_to_temp
primitive_category: connect
description: "Temperature assignment with an xreal-type value."
date: 2026-03-11T07:20:43.496948
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE xreal_to_temp
Temperature assignment with an xreal-type value.

The `xreal_to_temp` primitive sets the global temperature (``global_temp`) with an xreal-type input `in`.

The string-type parameter `unit` sets whether the input value is in Celsius (C) or Fahrenheit (F) and the parameters `abstol` and `reltol` set the absolute and relative tolerances of updating the temperature value, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | xreal-type temperature input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| unit | string | "C" | None | temperature unit |
| abstol | real | 1.0 | None | absolute tolerance |
| reltol | real | 1e-2 | None | relative tolerance |

