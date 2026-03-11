---
title: "XMODEL primitive: delay_sel"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: delay_sel
primitive_category: function
description: "A selectable transport delay for xreal-typed signals."
date: 2026-03-11T07:20:43.344490
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE delay_sel
A selectable transport delay for xreal-typed signals.

The `delay_sel` primitive models a transport delay for xreal-typed signals, which can be selected from a set of delays by a wire-type selection signal `sel`. With this primitive, one can describe a transport delay element of which delay can vary with a set of digital input values.

With the width of the input `sel` equal to k, as specified by the parameter `width_sel`, the primitive can have up to 2^k transport delays to select from. Each transport delay is indexed by an integer ranging from 0 to 2^k-1, which corresponds to the unsigned integer value of the input `sel[k-1:0]`.

The parameters `indices` and `delay` together describe the set of transport delays. First, the parameter `indices` is an integer-type array that lists the indices of the transport delays in the order that they are defined in the parameter `delay`. The indices may be listed in an arbitrary order and may not span a complete set, but each index must be within the range of 0~2^k-1. For example, '{0, 3, 1} is possible when k=2. The special value of '{-1} is equivalent to a complete set of indices listed as '{0, 1, 2, ..., 2^k-1}.

On the other hand, the parameter `delay` is a real-type array listing the transport delay values in seconds, of which indices are listed in the parameter `indices`. For synchronization reasons, the transport delay values must be at least a unit timestep.

For illustration, the following example describes two transport delays with index 0 and 1, respectively. The transport delay with index 0 is 5ns and the transport delay with index 1 is 2.5ns.

```
    indices = '{0, 1}
    data = '{5e-9, 2.5e-9}
```

When the parameter `indices` does not list a complete set of indices, the undefined transport delays are assumed to be 0.0.

When the parameter `filename` is defined, the primitive reads the named file that defines the parameter values in Python format. For the above example, the values of the parameters `indices` and `delay` can be defined within a file as below:

```
    indices = [0, 1]
    data = [5e-9, 2.5e-9]
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | output signal |
| in | input | xreal | input signal |
| sel | input | wire | selection signal (binary-coded) |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| width_sel | int | 1 | None | width of selection bits |
| indices | int array | '{0} | None | list of delay indices |
| delay | real array | '{0.0} | seconds | list of transport delays |
| filename | string | "" | None | parameter definition file |

