---
title: "XMODEL primitive: xreal_to_real"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: xreal_to_real
primitive_category: connect
description: "An xreal-to-real connector."
date: 2026-03-11T07:20:43.495729
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE xreal_to_real
An xreal-to-real connector.

The `xreal_to_real` primitive converts an xreal-type signal to a real-type signal.

The parameter `mode` specifies whether the resulting real-type waveform is updated at fixed time intervals (`fixed`), at variable time intervals assuming piecewise-linear representation (`variable`, `pwl`, or `variable:pwl`), or at variable time intervals assuming piecewise-constant representation (`pwc` or `variable:pwc`). By default, the variable time intervals assuming piecewise-linear representation are used, meaning that the real-value events are generated so that the the piecewise-linear waveform connecting the real-value events closely track the input xreal-type waveform within the specified tolerance.

The parameter `period` determines how often the original xreal-type waveform is sampled. In other words, it sets the minimum time interval. If the parameter `period` is 0, then the primitive uses the current simulation time step as the minimum sampling period. If it is a non-integer multiple value of the simulation time step, the primitive will use the nearest integer multiple value instead.

When the variable-interval sampling mode is used, the primitive makes best efforts to minimize the number of events generated for the output signal, while keeping the error within the absolute and relative error bounds. These error bounds are set by the parameters `abstol` and `reltol`, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | real | real-type output |
| in | input | xreal | xreal-type input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| mode | string | "variable" | None | timestep mode |
| period | real | 0.0 | seconds | unit timestep |
| abstol | real | 1e-4 | None | absolute tolerance |
| reltol | real | 1e-2 | None | relative tolerance |

