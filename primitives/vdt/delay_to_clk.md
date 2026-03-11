---
title: "XMODEL primitive: delay_to_clk"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: delay_to_clk
primitive_category: vdt
description: "A delay-to-clock domain translator."
date: 2026-03-11T07:20:43.601589
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE delay_to_clk
A delay-to-clock domain translator.

The `delay_to_clk` primitive delays an input xbit-typed signal `trig` (usually a clock) to an output xbit-typed signal `out` by the delay amount expressed by an xreal-typed input `in`.

The delay expressed by `in` must be greater than a unit simulation time step. If the delay changes while the input edge is still propagating to the output, the time-average of the input delay during the transition period will determine the overall delay.

The `delay_to_clk` primitive can also add random jitter or phase noise to the output signal. The added random jitter can contain independent jitter as well as accumulated jitter, each of which is specified by the parameter `RJ_rms` and `RJ_kappa`, respectively. The parameter `RJ_rms` defines the RMS value of the independent random jitter, which has fixed statistics regardless of the delay. On the other hand, the parameter `RJ_kappa` defines the RMS value of the accumulated random jitter, which increases as a square-root function of the delay. The total RMS value of the random jitter added to the output signal can be expressed as:

```
        Total RMS value of random jitter (RJ) = sqrt(RJ_rms^2 + RJ_kappa^2 * delay).
```

Alternatively, the added phase noise of the output clock can be specified using the phase noise parameters `PN_fcenter`, `PN_foffset`, `PN_dbc`, `PN_fcorner`, and `PN_floor`. Defining these phase noise parameters is equivalent to defining the random jitter parameters satisfying the following relationships:

```
        RJ_rms = 10^(PN_floor/20) / (2π*sqrt(PN_fcenter)),
        RJ_kappa = 10^(PN_dbc/20) * PN_foffset / PN_fcenter.
```

Note that the random jitter parameters `RJ_rms` and `RJ_kappa` cannot describe the 1/f noise (e.g. flicker noise) being accumulated over the delay, while the phase noise parameters can (`PN_fcorner`). For more information on these phase noise parameters, please refer to the documentation on the `clk_gen` primitive. These parameters typically describe the phase noise of an oscillator producing a clock at a certain frequency.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | clock output |
| trig | input | xbit | trigger input |
| in | input | xreal | delay input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| RJ_kappa | real | 0.0 | second | RMS accumulated random jitter after 1 second |
| RJ_rms | real | 0.0 | second | RMS independent random jitter |
| PN_fcenter | real | -1.0 | Hz | phase noise center frequency |
| PN_foffset | real | 0.0 | Hz | phase noise offset frequency |
| PN_dbc | real | -`INFINITY | dBc/Hz | phase noise measured in dBc/Hz |
| PN_fcorner | real | 0.0 | Hz | 1/f^3 phase noise corner frequency |
| PN_floor | real | -`INFINITY | dBc/Hz | phase noise floor measured in dBc/Hz |

