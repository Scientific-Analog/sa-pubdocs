---
title: "XMODEL primitive: temp_to_real"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: temp_to_real
primitive_category: connect
description: "Temperature measurement as a real-type value."
date: 2026-03-11T07:20:43.483723
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE temp_to_real
Temperature measurement as a real-type value.

The `temp_to_real` primitive measures the global temperature (``global_temp`) and drives a real-type output `out` with its value.

The string-type parameter `unit` sets whether the output value is in Celsius (C) or Fahrenheit (F).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | real-type temperature output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| unit | string | "C" | None | temperature unit |

