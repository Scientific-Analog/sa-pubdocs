---
title: "XMODEL primitive: probe_xreal"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_xreal
primitive_category: meas
description: "A probe for an xreal-typed signal."
date: 2026-03-11T07:20:43.438356
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_xreal
A probe for an xreal-typed signal.

The `probe_xreal` primitive records the waveform of an xreal-typed signal into a file.

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). When recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. When recording in FSDB format, the parameters `abstol` and `reltol` set the error tolerance of recording the true waveform as an approximate piecewise-linear waveform. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xreal | signal to record |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |
| abstol | real | 1e-4 | None | absolute tolerance |
| reltol | real | 1e-2 | None | relative tolerance |

