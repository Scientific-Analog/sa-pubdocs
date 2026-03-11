---
title: "XMODEL primitive: check_period"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: check_period
primitive_category: meas
description: "A primitive for checking the period of an xbit-type clock input."
date: 2026-03-11T07:20:43.393684
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE check_period
A primitive for checking the period of an xbit-type clock input.

The `check_period` primitive measures the period of an xbit-type clock input `in` and checks whether its value falls within a specified range. The parameter `range` defines the valid range of period, using a two-element real-typed array formatted as '{min_value, max_value}. The parameter `trig_edge` specifies which edges of the input clock trigger checking: positive edges (+1), negative edges (-1), or both (0). Violations are checked only when the input `enable` is high (1).

The primitive also supports a set of parameters that control how violations are detected and reported. The parameter `tgrace_init` defines an initial grace period starting at t=0 during which violations are ignored. The parameter `ngrace_init` specifies the number of initial violations to ignore. The parameter `severity` controls the reporting severity level using an integer value (0: none, 1: info, 2: warning, 3: error, 4: fatal).

The primitive produces a logic-typed output named `out`, which reports the checker status and can be used by user-defined assertion checks. The parameter `value_pass` specifies the value driven on `out` when the checker passes (i.e., when the monitored value is within the valid range). For example, if `value_pass` is set to 1 (default), then `out` = 1 indicates a pass and `out` = 0 indicates a failure (i.e., the value is outside the valid range). When out is `x`, it indicates that checking has not yet started (for example, due to the initial grace period or grace count).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xbit | input signal |
| enable | input | wire | enable signal |
| out | output | logic | output flag (by default, 1: pass, 0: fail) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| range | real array | '{0.0, 0.0} | None | valid range of period [min, max] |
| trig_edge | int | 1 | None | triggering clock edge |
| tgrace_init | real | 0.0 | seconds | initial period to ignore violations |
| ngrace_init | int | 0 | None | number of initial violations to ignore |
| value_pass | bit | 1 | None | output flag value for a pass |
| severity | int | -1 | None | severity level of reporting |

