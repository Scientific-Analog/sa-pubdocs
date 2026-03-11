---
title: "XMODEL primitive: prbs_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: prbs_gen
primitive_category: stim
description: "A digital PRBS generator."
date: 2026-03-11T07:20:43.460458
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE prbs_gen
A digital PRBS generator.

The `prbs_gen` primitive generates a pseudo-random bit sequence (PRBS) with a length of 2^N-1 to an xbit-typed output when triggered by the input `trig`. The LFSR length N is set by the parameter `length`. The valid range of `length` is 3~128 (default: 7).

The primitive can also generate a parallel stream of M-bit pseudo-random sequences, where the bit-width M is set by the parameter `width`. The parameter `seq_mode` defines whether the parallel stream is a MSB-first sequence (1) or LSB-first sequence (0). Its default value is 1 (MSB-first).

The parameter `trig_mode` defines whether the primitive is triggered by the positive edge (1), negative edge (-1), or both edges (0) of the input `trig` (default: 1).

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | signal output |
| trig | input | xbit | trigger input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| length | int | 7 | None | LFSR length |
| width | int | 1 | None | output width |
| seq_mode | int | 0 | None | sequence mode |
| trig_mode | int | 1 | None | triggering mode |

