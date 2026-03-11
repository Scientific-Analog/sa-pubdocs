---
title: "XMODEL primitive: chirp_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: chirp_gen
primitive_category: stim
description: "An analog chirp generator"
date: 2026-03-11T07:20:43.449721
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE chirp_gen
An analog chirp generator

The `chirp_gen` primitive generates a chirp signal, which is a sinusoidal signal of which frequency varies with time. Depending on the parameter `mode`, the frequency can vary linearly (mode="linear") or exponentially (mode="exp") with time. The parameters `freq_start` and `freq_stop` define the start and stop frequencies, respectively, and the parameter `period` defines the time it takes for the frequency to change from `freq_start` to `freq_stop`.

The parameter `delay` defines when the chirp starts and parameter `init_phase` defines its initial phase then. The parameter `amp` and `offset` define the amplitude and offset of the output sinusoid, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| offset | real | 0.0 | None | offset |
| amp | real | 1.0 | None | amplitude |
| freq_start | real | 1.0e6 | Hz | start frequency |
| freq_stop | real | 10.0e9 | Hz | stop frequency |
| period | real | 1e-6 | seconds | sweep period |
| mode | string | "linear" | None | sweep mode |
| delay | real | 0.0 | seconds | initial delay |
| init_phase | real | 0.0 | radian | initial phase |

