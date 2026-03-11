---
title: "XMODEL primitive: buffer"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: buffer
primitive_category: function
description: "A buffer for an xreal-typed signal."
date: 2026-03-11T07:20:43.339001
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE buffer
A buffer for an xreal-typed signal.

The `buffer` primitive drives an xreal-typed output with an isolated, reduced-order version of an xreal-typed input. One usage is to manually partition a circuit network into clusters. The `buffer` primitive also tries to reduce the number of events propagated to the output while keeping the error within the tolerance.

The parameters `abstol` and `reltol` set the absolute and relative tolerances used for this event-filtering, respectively. The parameter `scale` defines the optional scale factor (default: 1.0) and the parameter `init_value` defines the optional initial value of the output at time=0. Also, the parameters `Rin` and `Cin` can optionally set the input resistance and capacitance (i.e. Zin(s) = Rin || (1/sCin)), respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| scale | real | 1.0 | None | scale factor |
| init_value | real | `NaN | None | initial value |
| abstol | real | 1e-6 | None | absolute tolerance for event-filtering |
| reltol | real | 1e-3 | None | relative tolerance for event-filtering |
| delay | real | 0.0 | seconds | delay for event-filtering |
| Rin | real | `INFINITY | ohms | input resistance |
| Cin | real | 0.0 | farads | input capacitance |
| filename | string | "" | None | parameter definition file |

