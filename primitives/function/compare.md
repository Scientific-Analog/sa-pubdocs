---
title: "XMODEL primitive: compare"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: compare
primitive_category: function
description: "An analog clocked comparator."
date: 2026-03-11T07:20:43.340242
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE compare
An analog clocked comparator.

The `compare` primitive samples xreal-typed input signals `in` and `in_ref` at each rising edge of an xbit-typed input `trig` and determines whether their difference (i.e., `in`-`in_ref`) is higher or lower than the threshold level. In other words, its xbit-typed output `out` is set to 1 if the difference is higher than the threshold and is set to 0 otherwise. Here the threshold level is defined by the `threshold` parameter. The primitive can also model random decision errors by specifying a non-zero RMS value of the input-referred noise (`noise_in`).

The `compare` primitive can operate in two modes: an ideal comparator model and a finite-aperture comparator model. For the latter mode, the finite sampling aperture of the comparator is modeled by an impulse sensitivity function (ISF).

### 1) Ideal comparator model

In this mode, the `compare` primitive models an ideal clocked comparator behavior. In other words, the comparator samples the instantaneous value of the input difference `in`-`in_ref` at the rising edge of `trig` and outputs 1 if the sampled value is higher than the threshold and 0 otherwise.

An input dead zone can be modeled using the `sensitivity` parameter. In other words, an xbit-typed output `out` is set to 1 if the input difference value is higher than `threshold`+`sensitivity` and is set to 0 if lower than `threshold`-`sensitivity`. If the difference is between `threshold`-`sensitivity` and `threshold`+`sensitivity`, `out` keeps its previous value.

### 2) Finite sampling aperture comparator model

A realistic comparator acts on a weighted average of the input signal over a certain finite time window rather than on an instantaneous value of the input at one particular time point. This finite sampling aperture can be described by an impulse sensitivity function (ISF), which describes the comparator's internal response measured at one chosen observation point (t_obs) to an impulse input arriving at time t.

The finite sampling aperture of most comparators is contributed by two operating phases of the comparator, sampling and regeneration phases. During the sampling phase, the comparator transfers the input signal to its internal node through a finite-bandwidth low-pass filter. The later arriving input has the larger impact to the output, resulting in an ISF whose magnitude decreases as the arrival time t decreases (e.g. left exponential). On the other hand, during the regeneration phase, the signal stored on the internal node grows exponentially over time via a positive feedback. The earlier arriving input has the larger impact to the output, resulting in an ISF whose magnitude decreases as the arrival time t increases (e.g. right exponential).

```
             ISF(t) measured at the observation time
              ^
              | sampling          regeneration
              | time       .      time
              | constant  / \     constant
              |          /    \
              |         /       \
              | -------/          \----------------
              |-------------------------------------> t

              |----------->| sampling instant

              |<-sampling->|<---regeneration------->
```

More description on modeling the finite sampling aperture and noise behavior of clocked comparators can be found in the following publication:

```
- J. Kim, B. S. Leibowitz, M. Jeeradit, "Simulation and Analysis of Random
  Decision Errors in Clocked Comparators," IEEE Trans. Circuits and Systems I,
  pp 1844-1857, Aug. 2009.
```

The `compare` primitive models a typical ISF of the comparator using the following six member parameters listed in the parameter `ISF_params`:

```
    ISF_params[0]: sampling instant (time delay to the peak of ISF)
    ISF_params[1]: sampling gain (when t_obs > 0, it refers to the total area of the ISF function)
    ISF_params[2]: sampling time constant (shape of the left exponential)
    ISF_params[3]: regeneration time constant (shape of the right exponential)
    ISF_params[4]: internal latch threshold (determining metastability)
    ISF_params[5]: observation time (t_obs; optional)
```

When any of `ISF_params[0]`~`ISF_params[4]` is negative (e.g., -1), the `compare` primitive operates in the ideal comparator mode. The interpretation on the sampling gain (=`ISF_params[1]`) is different depending on the observation time parameter `t_obs` (=`ISF_params[5]`). When `t_obs` <= 0, the sampling gain is simply the scale factor applied to the net input (i.e., `in`-`in_ref`-`threshold`) before it goes through sampling and regeneration. On the other hand, when `t_obs` > 0, the sampling gain refers to the total area of the ISF function measured at a particular observation time, `t_obs`. If ISF_params[5] is not specified, it is assumed to be -1.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | digital decision output |
| in | input | xreal | analog input |
| in_ref | input | xreal | reference input |
| trig | input | xbit | trigger input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| threshold | real | 0.0 | None | threshold level |
| noise_in | real | 0.0 | None | RMS value of input-referred noise |
| sensitivity | real | 0.0 | None | input sensitivity |
| ISF_params[0] | real | -1.0 | seconds | sampling instant |
| ISF_params[1] | real | -1.0 | None | sampling gain |
| ISF_params[2] | real | -1.0 | seconds | sampling time constant |
| ISF_params[3] | real | -1.0 | seconds | regeneration time constant |
| ISF_params[4] | real | -1.0 | None | latch threshold |
| ISF_params[5] | real | -1.0 | seconds | observation time (optional) |
| delay | real | 0.0 | seconds | latch delay |
| init_value | logic | 1'bx | None | initial output value |
| trig_mode | int | 1 | None | triggering mode |

