---
title: "XMODEL primitive: probe_dc"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_dc
primitive_category: meas
description: "A DC analysis probe for measuring DC transfer function."
date: 2026-03-11T07:20:43.427078
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_dc
A DC analysis probe for measuring DC transfer function.

The `probe_dc` primitive measures the DC transfer function of a circuit by supplying a DC stimulus (`stim`) and measuring the circuit's response (`resp`). That is, one can measure a DC transfer function by configuring a testbench that feeds the `stim` output of this primitive to the circuit's input and connects the circuit's output to the `resp` input of this primitive.

The `probe_dc` primitive produces a DC signal for its `stim` output, stepping from `start` to `stop` at an increment of `step`. The change in `stim` can be triggered either internally or externally depending on the value of the parameter `period`. When `period` is greater than 0, the change is triggered internally at a period of `period` after an initial delay of `delay`. When `period` is 0, the change is triggered externally whenever the `trig` input changes to a different value. Before making each change to `stim`, the `probe_dc` primitive takes a measurement on the `resp` input and records the results in a table format to a text file named by the parameter `filename`. For desired results, the triggering period must be set long enough for the circuit to reach its final DC response. Also, the simulation must be run longer than `delay+period*(stop-start+step)/step` in order for the primitive to collect the entire transfer function.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| stim | output | xreal | stimulus (to circuit) |
| resp | input | xreal | response (from circuit) |
| trig | input | xbit | trigger input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "probe_dc.dat" | None | output filename |
| start | real | 0.0 | None | start value |
| stop | real | 1.0 | None | stop value |
| step | real | 0.1 | None | step value |
| period | real | 0.0 | seconds | trigger period |
| delay | real | 0.0 | seconds | initial delay |

