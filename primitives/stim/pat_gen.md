---
title: "XMODEL primitive: pat_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: pat_gen
primitive_category: stim
description: "A digital pattern generator."
date: 2026-03-11T07:20:43.459127
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE pat_gen
A digital pattern generator.

The `pat_gen` primitive generates a stream of digital data pattern to an xbit-typed output. In other words, the primitive sequentially outputs each bit defined in the array parameter `data` when triggered by the input `trig`. The parameter `trig_mode` defines whether the primitive is triggered by the positive edge (1), negative edge (-1), or both edges (0) of the input `trig` (default: 1).

The data pattern can be repeated over time as a whole or in part. The parameters `repeat_pos` and `repeat_num` define this repetition behavior. For instance, if the parameter `repeat_pos` is 3 and `repeat_num` is 2 for the data pattern `data` of '{1,0,0,1,1,0}, the output bit sequence is:

```
    1-0-0-1-1-0-1-1-0-1-1-0
                ^     ^
                |     |
                |     +-- second repetition starting from data[3]
                +-- first repetition starting from data[3]
```

If the `repeat_num` value is -1, the pattern will be repeated indefinitely.

When the parameter `filename` is defined, the primitive reads in the named file that defines the parameter values in Python format. For example, the content of a parameter file corresponding to the above case would be:

```
    data = [ 1, 0, 0, 1, 1, 0 ]
    repeat_pos = 3
    repeat_num = 2
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | signal output |
| trig | input | xbit | trigger input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| data | bit array | '{0} | None | data pattern |
| repeat_pos | int | 0 | None | repetition start position |
| repeat_num | int | 0 | None | number of repetitions |
| trig_mode | int | 1 | None | triggering mode |
| filename | string | "" | None | parameter definition file |

