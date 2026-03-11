---
title: "XMODEL primitive: probe_period"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_period
primitive_category: meas
description: "A period probe for a clock signal."
date: 2026-03-11T07:20:43.432276
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_period
A period probe for a clock signal.

The `probe_period` primitive measures the period of an xbit-typed periodic clock input (`in`) and records its waveform into a file. The primitive uses a `clk_to_period` primitive to measure the period of `in`.

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). In case of recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xbit | signal to measure the period from |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |

