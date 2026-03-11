---
title: "XMODEL primitive: probe_ber"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: probe_ber
primitive_category: meas
description: "A probe for measuring the bit-error rate of a data stream."
date: 2026-03-11T07:20:43.424598
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE probe_ber
A probe for measuring the bit-error rate of a data stream.

The `probe_ber` primitive measures the bit-error rate of a data stream `in` by comparing it either with an external reference data stream `in_ref` (with mode="ext" or "in") or with an internal PRBS reference (with mode="int" or "prbs"). In case of using an internal PRBS reference, the parameter `length` defines the LFSR length N, generating a pseudo-random bit sequence with a length of 2^N-1. The value range of `length` is 3~128 (default: 7). The primitive can also verify a parallel stream of M-bit pseudo-random sequences, where the bit-width M is set by the parameter `width`.

The parameter `trig_mode` defines whether the inputs `in` and `in_ref` are sampled at the positive edge (1), negative edge (-1), or both edges (0) of the input `clk`. By default, the inputs are sampled at the negative edge of `clk` (-1), assuming the data transitions are aligned with the positive edges of `clk`.

The parameter `filename` sets the name of the waveform file, of which extension determines the waveform format (e.g. ".jez" for JEZ and ".fsdb" for FSDB). In case of recording in JEZ format, the parameter `format` defines whether the data are recorded in a binary ("jezbinary") or ascii ("jezascii") format. The parameters `start` and `stop` define when the recording begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| in | input | xbit | input data |
| in_ref | input | xbit | reference data |
| clk | input | xbit | clock |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| filename | string | "xmodel.jez" | None | output filename |
| format | string | "jezbinary" | None | format version |
| start | real | 0.0 | seconds | abs. time to start recording |
| stop | real | -1.0 | seconds | abs. time to stop recording |
| mode | string | "ext" | None | reference source |
| length | int | 7 | None | reference LFSR length |
| width | int | 1 | None | input bit-width |
| trig_mode | int | -1 | None | triggering mode |

