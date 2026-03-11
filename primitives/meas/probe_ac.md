---
title: "XMODEL primitive: probe_ac"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_ac
primitive_category: meas
description: "An AC analysis probe for measuring frequency-domain, AC transfer function."
date: 2026-03-11T07:20:43.423354
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_ac
An AC analysis probe for measuring frequency-domain, AC transfer function.

The `probe_ac` primitive measures the frequency-domain transfer function of a circuit by supplying an AC stimulus (`stim`) and measuring the circuit's response (`resp`). That is, one can measure a frequency-domain transfer function by configuring a testbench that feeds the `stim` output of this primitive to the circuit's input and connects the circuit's output to the `resp` input of this primitive.

The stimulus `stim` is a sinusoidal chirp signal with specified DC offset (`stim_dc`) and AC amplitude (`stim_ac`), and with frequency varying from `freq_start` to `freq_stop` over the time `period` after an initial delay `delay`. Over the course of simulation, the `probe_ac` primitive measures the response at each frequency value plus `freq_offset` and records the corresponding transfer function magnitude and phase values in a table format to a text file named by the parameter `filename`. The simulation must be run longer than `delay`+`period` in order for the primitive to collect the entire transfer function.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| stim | output | xreal | stimulus (to circuit) |
| resp | input | xreal | response (from circuit) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "probe_ac.dat" | None | output filename |
| stim_dc | real | 0.0 | None | stimulus DC offset |
| stim_ac | real | 1.0 | None | stimulus AC amplitude |
| freq_start | real | 10.0e6 | Hz | start frequency |
| freq_stop | real | 10.0e9 | Hz | stop frequency |
| freq_offset | real | 0.0 | Hz | frequency offset |
| period | real | 1e-6 | seconds | sweep period |
| delay | real | 0.0 | seconds | initial delay |

