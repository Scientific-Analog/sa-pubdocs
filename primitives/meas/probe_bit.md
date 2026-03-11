---
title: "XMODEL primitive: probe_bit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_bit
primitive_category: meas
description: "A probe for a bit-typed signal."
date: 2026-03-11T07:20:43.425888
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_bit
A probe for a bit-typed signal.

The `probe_bit` primitive records the waveform of a bit-typed signal into a file.

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). In case of recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | bit | signal to record |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |

