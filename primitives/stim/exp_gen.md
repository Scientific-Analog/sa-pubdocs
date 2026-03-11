---
title: "XMODEL primitive: exp_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: exp_gen
primitive_category: stim
description: "An analog exponential signal generator"
date: 2026-03-11T07:20:43.456588
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE exp_gen
An analog exponential signal generator

The `exp_gen` primitive generates an exponential signal. A set of parameters define the stimulus waveform V(t) as follows:

* For t < delay1 :
```
    V(t) = init_value
```

* For delay1 <= t < delay2:
```
    V(t) = init_value + change*(1-exp(delay1-t)/tau1)
```

* For t >= delay2 :
```
    V(t) = init_value + change*(1-exp(delay1-t)/tau1)
           - change*(1-exp(delay2-t)/tau2)
```

That is, the primitive initially generates a DC signal at `init_value`. At the first onset (t=`delay1`), the primitive starts to generate a signal that exponentially converges towards `init_value`+`change` with a time constant of `tau1`. Then at the second onset (t=`delay2`), the signal starts to exponentially converge back towards `init_value` with a time constant of `tau2`. If the parameter `delay2` is negative, the primitive does not produce the second onset.

The primitive can also repeat the two exponential onsets at the period defined by the parameter `period`, when it has a positive value greater than `delay2-delay1`.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| init_value | real | 0.0 | None | initial value |
| change | real | 0.0 | None | change value |
| delay1 | real | 0.0 | seconds | delay to onset #1 |
| delay2 | real | -1.0 | seconds | delay to onset #2 |
| tau1 | real | 0.0 | seconds | time constant #1 |
| tau2 | real | 0.0 | seconds | time constant #2 |
| period | real | -1.0 | seconds | repetition period |

