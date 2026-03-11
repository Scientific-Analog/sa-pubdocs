---
title: "XMODEL primitive: freq_to_clk"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: freq_to_clk
primitive_category: vdt
description: "A frequency-to-clock domain translator."
date: 2026-03-11T07:20:43.604483
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE freq_to_clk
A frequency-to-clock domain translator.

The `freq_to_clk` primitive takes an xreal-typed input `in` expressing a frequency and produces xbit-typed clock signals `out` with the corresponding frequency. The primitive can also produce multiple clocks with uniformly-spaced phases as well as clocks with phase noise or random jitter.

The parameter `num_phase` sets the number of output clock phases and the parameter `init_phase` sets the initial phase of the clock at t=0, where a negative value (e.g. -1) implies that the initial phase is to be randomized.

The phase noise of the output clocks can be specified using the phase noise parameters `PN_fcenter`, `PN_foffset`, `PN_dbc`, `PN_fcorner`, and `PN_floor`, assuming the phase noise spectrum of a typical oscillator consisting of 1/f^3 noise, 1/f^2 noise, and noise floor (ref: D. B. Leeson, "A Simple Model of Feedback Oscillator Noise Spectrum," in Proceedings of the IEEE, vol. 54, Feb. 1966, pp. 329–330). These phase noise parameters take effects only when the parameter `PN_fcenter` has a positive value (default: -1.0).

```
  log(PN) | \
          |  \ 1/f^3 noise
          |   \
          |    \
          |     `` 1/f^2 noise
          |       ``          noise floor
          |         ``---------- (=PN_floor)
          +----+------------------ log(f)
           PN_fcorner
```

The parameter `PN_fcorner` defines the 1/f^3 phase noise corner frequency, i.e., the offset frequency at which the 1/f^3 noise and 1/f^2 noise have equal levels (default: 0.0). The parameter `PN_floor` defines the phase noise floor, i.e. the minimum phase noise level in dBc/Hz at all frequencies (default: -`INFINITY). When the parameters `PN_fcorner` and `PN_floor` have their default values (0.0 and -`INFINITY, respectively), the output clock has only 1/f^2 phase noise.

The 1/f^2 phase noise characteristics can be defined by specifying its phase noise level in dBc/Hz (`PN_dbc`) measured at one offset frequency (`PN_foffset`) from the center frequency (`PN_fcenter`, which is equal to `freq` by default) using the parameters `PN_dbc`, `PN_foffset`, and `PN_fcenter`, respectively. To avoid confusion, it is recommended to use the `PN_foffset` value greater than the `PN_fcorner` value and the `PN_dbc` value greater than the `PN_floor` value to define the 1/f^2 phase noise level. Otherwise, the total phase noise level produced by the primitive at the offset frequency `PN_foffset` might not be equal to the specified `PN_dbc` due to the additional 1/f^3 phase noise or phase noise floor.

Alternatively, the phase noise of the output clocks can be specified using the random jitter parameters `RJ_kappa` and `RJ_rms`. The parameter `RJ_kappa` defines the RMS value of the accumulated random jitter, which increases as a square-root function of time due to the 1/f^2 phase noise. On the other hand, the parameter `RJ_rms` defines the RMS value of the independent random jitter, which has fixed statistics regardless of time. Defining these random jitter parameters is equivalent to defining the phase noise parameters satisfying the following relationships:

```
        RJ_kappa = 10^(PN_dbc/20) * PN_foffset / PN_fcenter.
        RJ_rms = 10^(PN_floor/20) / (2π*sqrt(PN_fcenter)),
```

Note that the random jitter parameters `RJ_kappa` and `RJ_rms` cannot specify the 1/f^3 phase noise.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | clock output |
| in | input | xreal | frequency input |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_phase | int | 1 | None | number of phases |
| init_phase | real | 0.0 | radian | initial clock phase |
| PN_fcenter | real | -1.0 | Hz | phase noise center frequency |
| PN_foffset | real | 0.0 | Hz | phase noise offset frequency |
| PN_dbc | real | -`INFINITY | dBc/Hz | phase noise measured in dBc/Hz |
| PN_fcorner | real | 0.0 | Hz | 1/f^3 phase noise corner frequency |
| PN_floor | real | -`INFINITY | dBc/Hz | phase noise floor measured in dBc/Hz |
| RJ_kappa | real | 0.0 | second | RMS accumulated random jitter after 1 second |
| RJ_rms | real | 0.0 | second | RMS independent random jitter |

