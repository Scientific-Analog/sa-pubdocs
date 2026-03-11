---
title: "XMODEL primitive: sin_gen"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: sin_gen
primitive_category: stim
description: "An analog sinusoid generator"
date: 2026-03-11T07:20:43.467183
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE sin_gen
An analog sinusoid generator

The `sin_gen` primitive generates a sinusoidal signal that can optionally be exponentially decaying or frequency/amplitude-modulated.

The generated stimulus waveform V(t) is defined as follows:

* For t < delay:
```
    V(t) = offset + amp * (AM_offset + AM_amp*sin(AM_phase)) * sin(init_phase)
```

* For t >= delay:
```
    V(t) = offset + amp * exp(-damp(t-delay)) *
           (AM_offset + AM_amp*sin(2*PI*AM_freq*(t-delay) + AM_phase) *
           sin(2*PI*freq*(t-delay) + FM_index*sin(2*PI*FM_freq*(t-delay)) + init_phase)
```

In the last expression, the first, second, and third lines express the exponentially-decaying amplitude, amplitude modulation, and frequency modulation of the generated sinusoidal signal, respectively. The sinusoidal signal may have an arbitrary DC offset (`offset`) and start with an arbitrary initial phase (`init_phase`).

Some examples of generating a simple sinusoid, a sinusoid with exponentially-decaying amplitude, a sinusoid with single-frequency frequency modulation (FM), and a sinusoid with single-frequency amplitude-modulation (AM) are shown below:

* A simple sinusoid (damp=0, AM_offset=1, AM_amp=0, AM_freq=0, AM_phase=0, FM_index=0, FM_freq=0):
```
    V(t) = offset + amp * sin(2*PI*freq(t-delay)+init_phase)
```

  for t >= delay

* A sinusoid with exponentially-decaying amplitude (AM_offset=1, AM_amp=0, AM_freq=0, AM_phase=0, FM_index=0, FM_freq=0):
```
    V(t) = offset + amp * exp(-damp*(t-delay)) * sin(2*PI*freq*(t-delay)+init_phase)
```

  for t >= delay

* Figure 1: An example of the sin_gen primitive generating a damped sinusoid.
* A sinusoid with single-frequency amplitude modulation (AM) (damp=0, FM_index=0, FM_freq=0, init_phase=0):
```
    V(t) = offset + amp * (AM_offset+AM_amp*sin(2*PI*AM_freq*(t-delay)+AM_phase)) *
           sin(2*PI*freq*(t-delay))
```

  for t >= delay

* A sinusoid with single-frequency frequency modulation (FM) (damp=0, AM_offset=1, AM_amp=0, AM_freq=0, AM_phase=0, init_phase=0):
```
    V(t) = offset +
           amp * sin(2*PI*freq*(t-delay)+FM_index*sin(2*PI*FM_freq*(t-delay)))
```

  for t >= delay

**NOTE**: for frequency modulation, the narrowband FM is assumed. In other words, the modulation index, `FM_index`, which is defined as (max. deviation frequency) / (max. modulation frequency), is assumed to be << 1.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xreal | signal output |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| offset | real | 0.0 | None | offset |
| amp | real | 1.0 | None | amplitude |
| freq | real | 1.0e9 | Hz | frequency |
| delay | real | 0.0 | seconds | initial delay |
| damp | real | 0.0 | 1/sec | damping factor |
| init_phase | real | 0.0 | radian | initial phase |
| AM_offset | real | 1.0 | None | AM offset |
| AM_amp | real | 0.0 | None | AM amplitude |
| AM_freq | real | 0.0 | Hz | AM frequency |
| AM_phase | real | 0.0 | radian | AM phase |
| FM_index | real | 0.0 | None | FM index |
| FM_freq | real | 0.0 | Hz | FM frequency |

### Example 1
The following `sin_gen` module generates a 1-GHz sinusoidal signal with an amplitude of 1.0, offset of 0.5, and initial phase offset of 90-degrees (0.5*PI). Also, the signal's amplitude decays with a time constant of 1/0.1e9.



```
sin_gen     #(.freq(1e9), .amp(1.0), .offset(0.5), .init_phase(0.5*M_PI), .damp(0.1e9))

            inst1 (sig1);

```



### Example 2
The following `sin_gen` module generates a 1-GHz sinusoidal signal with an amplitude of 1.0, offset of 0.5, and initial phase offset of 90-degrees (0.5*PI). This time, the signal is single-frequency amplitude-modulated with a modulation amplitude of 0.1 and frequency of 100-MHz.



```
sin_gen     #(.freq(1e9), .amp(1.0), .offset(0.5), .init_phase(0.5*M_PI),

              .AM_offset(1.0), .AM_amp(0.1), .AM_freq(0.1e9))

            inst2 (sig2);

```


