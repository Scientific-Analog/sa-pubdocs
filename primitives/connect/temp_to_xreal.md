---
title: "XMODEL primitive: temp_to_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: temp_to_xreal
primitive_category: connect
description: "Temperature measurement as an xreal-type value."
date: 2026-03-11T07:20:43.485025
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE temp_to_xreal
Temperature measurement as an xreal-type value.

The `temp_to_xreal` primitive measures the global temperature (``global_temp`) and drives an xreal-type output `out` with its value.

The string-type parameter `unit` sets whether the output value is in Celsius (C) or Fahrenheit (F) and the parameter `abstol` sets the absolute tolerance of measuring the temperature value.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | xreal-type temperature output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| unit | string | "C" | None | temperature unit |
| abstol | real | 1.0 | None | absolute tolerance |

