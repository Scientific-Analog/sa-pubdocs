---
title: "XMODEL primitive: ilo"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: ilo
primitive_category: function
description: "An injection-locked oscillator (ILO)."
date: 2026-03-11T07:20:43.360481
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE ilo
An injection-locked oscillator (ILO).

The `ilo` primitive models an injection-locked oscillator (ILO) based on perturbation projection vector (PPV). An ILO is an oscillator with one or more external inputs which may perturb the phase of the oscillator. A typical ILO has a periodically time-varying sensitivity to the external input, which enables the ILO's phase and frequency to be injection-locked to those of the external input.

The `ilo` primitive first computes the internal phase of the oscillator from the xreal-typed inputs `in` and `ctrl` and then produces xbit-type clock signals `out` according to the computed phase. The number of external inputs that may perturb the internal phase is specified by the parameter `num_in` and the number of output clock phases that uniformly span one clock period is specified by `num_phase`. The phase relationship among the output clocks is the same with that used in the `phase_to_clk` or `freq_to_clk` primitives, where out[i] leads out[i+1] by 1/num_phase of the period.

The `ctrl` input can optionally control the free-running frequency of the oscillator and scale factor for its PPV via the real-array parameters `freq` and `scale`, respectively. In other words, the parameters `freq` and `scale`, each taking the same real-array format with the parameter `data` of the `pwl_func` primitive, can define the piecewise-linear (PWL) functions between the `ctrl` input to the ILO's free-running frequency and PPV's scale factor, respectively. Note that when the parameter `freq` or `scale` has only a single element (e.g. '{1.0e9} or '{1.0}), the corresponding characteristic of the ILO takes a constant value regardless of the `ctrl` input.

The internal phase of the injection-locked oscillator is computed as:

```
    integ(freq(ctrl)*dt) + alpha(t) + alpha_0
```

where `alpha(t)` is the phase deviation caused by the external inputs `in[num_in-1:0]` and `alpha_0` is the initial phase of the oscillator set by the parameter `init_phase` as `init_phase`/(2*M_PI). Here, `alpha(t)` and `alpha_0` are in unit intervals (UIs). When the parameter `init_phase` has a negative value (e.g. -1), the initial phase `alpha_0` is randomized in [0, 1).

The phase deviation `alpha(t)` of the ILO is governed by a nonlinear ordinary differential equation shown below:

```
    dalpha(t)/dt = sum of (ppv_i(integ(freq(ctrl)*dt) + alpha(t) + alpha_0) * freq(ctrl) * scale(ctrl) * in_i(t))
```

where `ppv_i` denotes the normalized PPV with respect to the i-th input `in[i]` scaled by `freq(ctrl)*scale(ctrl)`. For more information about this equation and concept of PPV, please refer to: X. Lai and J. Roychowdhury, "Automated Oscillator Macromodelling Techniques for Capturing Amplitude Variations and Injection Locking", in Proc. ACM/IEEE International Conference on Computer Aided Design (ICCAD), Nov. 2004.

The real-array type parameter `ppv` defines the normalized perturbation projection vector (PPV) in a piecewise-linear form. Its basic format is:

```
    '{ p[0], v[0], p[1], v[1], p[2], v[2], ... }
```

where the phase-value pairs (p,v) describe the PWL approximation of the normalized PPV in units of UI with respect to each input. Note that the first phase point p[0] must be 0.0 and the sequence of phase points (p[0], p[1], p[2], ...) must span a range of [0, 1) in a monotonically increasing order. In case with multiple inputs (num_in > 1), the parameter `ppv` is a linear concantenation of individual PPV parameters as shown below:

```
    '{ ...
       p2[0], v2[0], p2[1], v2[1], p2[2], v2[2], ...    // PPV for in[2]
       p1[0], v1[0], p1[1], v1[1], p1[2], v1[2], ...    // PPV for in[1]
       p0[0], v0[0], p0[1], v0[1], p0[2], v0[2], ...    // PPV for in[0]
    }
```

It is important that the first phase points p0[0], p1[0], p2[0], ... of each PPV must be 0.0 as they also serve as delimiters separating the individual PPVs. For best simulation performance, it is strongly recommended to use a set of phase points uniformly spanning the range [0, 1). In such cases, the following short format omitting the explicit phase points can be used. Each PPV entry starts with a number of phase points N (>=2) followed by a sequence of N value points v[0], v[1], ..., v[N-1].

```
    '{
       ...
       N2, v2[0], v2[1], v2[2], ..., v2[N2-1],   // PPV for in[2]
       N1, v1[0], v1[1], v1[2], ..., v1[N1-1],   // PPV for in[1]
       N0, v0[0], v0[1], v0[2], ..., v0[N0-1]    // PPV for in[0]
    }
```

When the parameter `ppv` is not specified and `num_in` is either 1, 2, or num_phase, the `ilo` primitive assumes an ideal PPV of a multi-stage ring-oscillator which has the highest sensitivity (+1 or -1) when the clock is transitioning and the lowest sensitivity (0) when it is not, while each clock transition time is assumed to be twice the unit stage delay. Specifically, the ideal PPV has the following values depending on whether `num_phase` is even or odd:

### 1) With 'num_phase' = 2, 4, 6, ... (even) and 'num_in' = 'num_phase':

A PPV with respect to an input in[i] can be described by the following sub-sequence in a short format:

```
    '{ num_phase, vi[0], vi[1], ... , vi[num_phase-1] },
```

where

```
    vi[j] = +1      for j = i,
    vi[j] = -1      for j = (i+num_phase/2) mod num_phase,
    vi[j] = 0       otherwise.
```

For example, the ideal PPV when `num_phase` = 4 is:

```
    '{
       4, 0.0, -1.0, 0.0, 1.0,      // PPV for in[3]
       4, -1.0, 0.0, 1.0, 0.0,      // PPV for in[2]
       4, 0.0, 1.0, 0.0, -1.0,      // PPV for in[1]
       4, 1.0, 0.0, -1.0, 0.0       // PPV for in[0]
    }
```

### 2) With 'num_phase' = 1, 3, 5, ... (odd) and 'num_in' = 'num_phase':

A PPV with respect to an input in[i] can be described by the following sub-sequence in a short format:

```
    '{ 2*num_phase, vi[0], vi[1], ... , vi[2*num_phase-1] },
```

where

```
    vi[j] = +1      for j = 2*i,
    vi[j] = -1      for j = (2*i+num_phase) mod 2*num_phase,
    vi[j] = 0       otherwise.
```

For example, the ideal PPV when `num_phase` = 5 is:

```
    '{
       10, 0.0, 0.0, 0.0, -1.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0,    // PPV for in[4]
       10, 0.0, -1.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0,    // PPV for in[3]
       10, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.0, -1.0,    // PPV for in[2]
       10, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.0, -1.0, 0.0, 0.0,    // PPV for in[1]
       10, 1.0, 0.0, 0.0, 0.0, 0.0, -1.0, 0.0, 0.0, 0.0, 0.0     // PPV for in[0]
    }
```

For both cases, when the parameter `num_in` is 1, the parameter `ppv` assumes the ideal PPV for in[0] by default. On the other hand, when `num_in` is 2, `ppv` assumes a complementary PPV of the in[0]'s PPV for in[1]. For instance, when num_phase=5 and num_in=2, the default value for `ppv` is:

```
    ppv[] = '{
       10, -1.0, 0.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 0.0     // PPV for in[1]
       10, 1.0, 0.0, 0.0, 0.0, 0.0, -1.0, 0.0, 0.0, 0.0, 0.0     // PPV for in[0]
    }
```

The `ilo` primitive can also model noise in the output clocks either by specifying the phase noise parameters `PN_fcenter`, `PN_foffset`, `PN_dbc`, `PN_fcorner`, and `PN_floor`, or by specifying the random jitter parameters `RJ_kappa` and `RJ_rms`. These parameters specify the phase noise or random jitter characteristics when the oscillator is free-running.

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
| out | output | xbit | output signals |
| in | input | xreal | input signal |
| ctrl | input | xreal | control signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_in | int array | 1 | None | number of inputs |
| num_phase | int array | 1 | None | number of output phases |
| ppv | real array | '{0.0} | UI | normalized perturbation projection vector |
| scale | real array | '{1.0} | None | input scale as PWL function of ctrl |
| freq | real array | '{1.0e9} | Hz | output frequency as PWL function of ctrl |
| init_phase | real | 0.0 | radian | initial output phase |
| PN_fcenter | real | -1.0 | Hz | phase noise center frequency |
| PN_foffset | real | 0.0 | Hz | phase noise offset frequency |
| PN_dbc | real | -`INFINITY | dBc/Hz | phase noise measured in dBc/Hz |
| PN_fcorner | real | 0.0 | Hz | 1/f^3 phase noise corner frequency |
| PN_floor | real | -`INFINITY | dBc/Hz | phase noise floor measured in dBc/Hz |
| RJ_kappa | real | 0.0 | second | RMS accumulated random jitter after 1 second |
| RJ_rms | real | 0.0 | second | RMS independent random jitter |

