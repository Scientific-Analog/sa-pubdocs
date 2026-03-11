---
title: "XMODEL primitive: limit"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: limit
primitive_category: function
description: "A limiting operator for xreal-typed signals."
date: 2026-03-11T07:20:43.367457
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE limit
A limiting operator for xreal-typed signals.

The `limit` primitive produces a bounded range of output by limiting the input signal `in` to the range specified by the parameters `upper_limit` and `lower_limit`. In other words, the output signal `out` is set according to the following equation:

```
    out = lower_limit   for in < lower_limit
          in            for lower_limit <= in < upper_limit
          upper_limit   for in >= upper_limit
```

To pose the lower limit only, the parameter `upper_limit` can be set to `INFINITY. Similarly, the pose the upper limit only, the parameter `lower_limit` can be set to -`INFINITY.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| upper_limit | real | 1.0 | None | upper-limit level |
| lower_limit | real | -1.0 | None | lower-limit level |

