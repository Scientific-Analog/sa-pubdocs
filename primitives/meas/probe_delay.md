---
title: "XMODEL primitive: probe_delay"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_delay
primitive_category: meas
description: "A delay probe for a clock signal."
date: 2026-03-11T07:20:43.428295
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_delay
A delay probe for a clock signal.

The `probe_delay` primitive measures the delay of an xbit-typed input (`in`) with respect to a reference input (`trig`) and records its waveform into a file.

The primitive uses a `clk_to_delay` primitive to measure the delay of the rising edge of `in` with respect to the rising edge of `trig`, and the parameters `delay_trig`, `delay_in`, `skip_trig`, and `skip_in` control which rising edges of the two inputs are to be compared with. For more information, refer to the documentation for the `clk_to_delay` primitive.

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). In case of recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| trig | input | xbit | reference trigger to measure the delay from |
| in | input | xbit | input pulse to measure the delay to |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |
| delay_trig | real | 0.0 | seconds | start delay for 'trig' |
| delay_in | real | 0.0 | seconds | start delay for 'in' |
| skip_trig | int | 0 | None | edges to skip for 'trig' |
| skip_in | int | 0 | None | edges to skip for 'in' |

