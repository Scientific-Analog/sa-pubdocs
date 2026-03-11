---
title: "XMODEL primitive: step_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: step_gen
primitive_category: stim
description: "An analog step generator"
date: 2026-03-11T07:20:43.468547
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE step_gen
An analog step generator

The `step_gen` primitive generates an xreal-typed step signal. In other words, it generates a signal that changes from `init_value` to `init_value+change` after `delay` from time 0.

```
   init_value+change                 +-----------------------------------
                                     |
   init_value         ---------------+
                      ^              ^
                      |              |
   time               0            delay
```

The primitive can also generate a pulse with finite duration when its parameter `width` is defined with a positive value.

```
   init_value+change                 +--------+
                                     |        |
   init_value         ---------------+        +--------------------------
                      ^              ^        ^
                      |              |        |
   time               0            delay delay+width
```

And the primitive can repeat this finite-duration pulse when the parameter `period` is defined with a positive value greater than the value of the parameter `width`.

```
   init_value+change                 +--------+            +--------+
                                     |        |            |        |
   init_value         ---------------+        +------------+        +---- ...
                      ^              ^        ^            ^
                      |              |        |            |
   time               0            delay delay+width  delay+period
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| init_value | real | 0.0 | None | initial value |
| change | real | 0.0 | None | step change |
| delay | real | 0.0 | seconds | delay |
| width | real | -1.0 | seconds | step pulse width |
| period | real | -1.0 | seconds | repetition period |

