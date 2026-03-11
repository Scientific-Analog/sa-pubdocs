---
title: "XMODEL primitive: mtline"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: mtline
primitive_category: circuit
description: "A multi-conductor, multi-port transmission line."
date: 2026-03-11T07:20:43.523731
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE mtline
A multi-conductor, multi-port transmission line.

The `mtline` primitive models a multi-conductor, multi-port transmission line with a characteristic impedance of `Z0` and propagation delay of `delay`. The port terminals of the M transmission lines are named as shown below:

```
    pos_1[0], neg_1[0]     ----o======line #0======o---- pos_2[0], neg_2[0]
    pos_1[1], neg_1[1]     ----o======line #1======o---- pos_2[1], neg_2[1]
                                        ...
    pos_1[M-1], neg_1[M-1] ----o=====line #M-1=====o---- pos_2[M-1], neg_2[M-1]
```

where the number of transmission lines M is defined by the parameter `num_line`.

The real-array parameters `ports` and `data` together can define the frequency-dependent transfer characteristics between any selected source and destination ports of the transmission line. For instance, if the transmission or reflection coefficient from line L1, port P1 to line L2, port P2 can be described as the following s-domain transfer function H(s) having total of N partial fraction terms:

```
               b1_real + j*b1_imag                 bN_real + j*bN_imag
    H(s) = ---------------------------- + ... + ---------------------------- ,
           (s + a1_real + j*a1_imag)^m1         (s + aN_real + j*aN_imag)^mN
```

the parameter `ports` shall contain the following entries for the source and destination port indices:

```
    ports = '{ ..., L1.P1, L2.P2, ... }
```

where the port index takes a real value in the format of "<line index>.<port index>". For example, the index for the port #2 of the line #1 is 1.2. And at the corresponding position, the parameter `data` shall have the 5*N+1 entries:

```
    data = '{ ...,
             N,                                             // number of terms
             a1_real, a1_imag, b1_real, b1_imag, m1,        // partial fraction term #1
             a2_real, a2_imag, b2_real, b2_imag, m2,        // partial fraction term #2
             ...
             aN_real, aN_imag, bN_real, bN_imag, mN,        // partial fraction term #N
             ...
           }
```

The parameters `ports` and `data` can be alternatively defined by a parameter definition file named `filename` which defines the same named parameters in Python format. For any transmission characteristics not specified, the primitive assumes the reciprocal characteristics from the ones defined and ideal characteristics for the rest (i.e. no transmission loss and no crosstalk).

This primitive is a pseudo-module describing a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos_1 | input | xreal | positive terminal of port #1 |
| neg_1 | input | xreal | negative terminal of port #1 |
| pos_2 | input | xreal | positive terminal of port #2 |
| neg_2 | input | xreal | negative terminal of port #2 |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_line | int | 1 | None | number of transmission lines |
| Z0 | real | 50.0 | ohms | characteristic impedance |
| delay | real | 0.0 | seconds | line propagation delay |
| ports | real array | '{0.0} | None | source/destination ports |
| data | real array | '{0.0} | None | transfer characteristics data |
| filename | string | "" | None | parameter definition file |
| abstol | real | 1e-3 | None | absolute tolerance for event-filtering |
| reltol | real | 1e-2 | None | relative tolerance for event-filtering |
| m | real | 1.0 | None | multiplicity factor |

