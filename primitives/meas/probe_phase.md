---
title: "XMODEL primitive: probe_phase"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_phase
primitive_category: meas
description: "A phase probe for a clock signal."
date: 2026-03-11T07:20:43.433570
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_phase
A phase probe for a clock signal.

The `probe_phase` primitive measures the phase of an xbit-typed periodic clock input (`in`) and records its waveform into a file.

The primitive uses a `clk_to_phase` primitive to measure the phase of `in`. Its parameter `freq` sets the nominal frequency at which the clock phase is measured. And the parameter `phase_wrap` controls whether the phase output should be wrapped into a range of [-pi, pi) (phase_wrap=1) or not (phase_wrap=0).

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). In case of recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xbit | signal to measure the phase from |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |
| freq | real | 1.0e9 | Hz | nominal clock frequency |
| phase_wrap | int | 1 | None | phase wrapping to [–π, π) |

