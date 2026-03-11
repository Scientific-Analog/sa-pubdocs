---
title: "XMODEL primitive: meas_ber"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: meas_ber
primitive_category: meas
description: "A primitive for measuring the bit-error rate of a data stream."
date: 2026-03-11T07:20:43.400597
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE meas_ber
A primitive for measuring the bit-error rate of a data stream.

The `meas_ber` primitive measures the bit-error rate of a data stream `in` by comparing it either with the external reference data stream `in_ref` (mode="ext" or "in") or with an internal PRBS reference (mode="int" or "prbs"). In case of using an internal PRBS reference, the parameter `length` defines the LFSR length N, generating a pseudo-random bit sequence with a length of 2^N-1. The value range of `length` is 3~128 (default: 7).

The parameter `trig_mode` defines whether the inputs `in` and `in_ref` are sampled at the positive edge (1), negative edge (-1), or both edges (0) of the input `clk`. By default, the inputs are sampled at the negative edge of `clk` (-1), assuming the data transitions are aligned with the positive edges of `clk`. The parameters `start` and `stop` define when the measurement begins and ends, respectively.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| bit_err | output | reg | bit error indicator |
| prb_err | output | real | bit error probability |
| in | input | xbit | input signal |
| in_ref | input | xbit | reference signal |
| clk | input | xbit | clock signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| mode | string | "ext" | None | reference source |
| length | int | 7 | None | reference LFSR length |
| trig_mode | int | -1 | None | triggering mode |
| start | real | 0.0 | seconds | abs. time to start measurement |
| stop | real | -1.0 | seconds | abs. time to stop measurement |

