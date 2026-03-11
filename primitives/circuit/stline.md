---
title: "XMODEL primitive: stline"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: stline
primitive_category: circuit
description: "A generalized multi-conductor, multi-port transmission line with per-port characteristic impedance and split-delay transfer functions."
date: 2026-03-11T07:20:43.534383
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE stline
A generalized multi-conductor, multi-port transmission line with per-port characteristic impedance and split-delay transfer functions.

The `stline` primitive models a generalized multi-conductor, multi-port transmission line. That is, each of its ports can have a different characteristic impedance defined with a circuit network expression and each of its port-to-port couplings can be defined with multiple transfer functions split with different delays. The parameter `num_port` defines the number of ports of the transmission line, and the primitive has a set of terminals `pos[1:num_port]` and `neg[1:num_port]`, where `pos[i]` and `neg[i]` denote the positive and negative terminals of the port #i, with i ranging from 1 to `num_port`.

The string-array parameter `Z0` defines the individual characteristic impedances of the ports using the circuit network expressions. For example, a string "R50||C1p" describes a parallel combination of a 50-ohm resistance and a 1-pF capacitance, and "R50+L1n" describes a series combination of a 50-ohm resistance and a 1-nH inductance. In this circuit network expression, each R/L/C element is described with a string starting with an `R`, `L`, or `C` prefix followed by its resistance, inductance, or capacitance value, respectively, and an optional unit suffix (e.g. `n` for nano and `p` for pico). The characteristic impedance of each port can be then described as an arbitrary network of R/L/C elements using the series operator `+`, parallel operator `||`, and grouping operators `()`. If the string-array parameter `Z0` has only one expression, it implies that all the ports share the same circuit network expression for their characteristic impedances.

The integer-array parameter `ports` and real-array parameters `delay` and `delay` together define the frequency-dependent transfer characteristics between any selected source and destination ports of the transmission line. For instance, if the transmission or reflection coefficient from port P1 to port P2 can be described as the following s-domain transfer function H(s) having a total of N partial fraction terms and a transport delay of D:

```
                 b1_real + j*b1_imag                 bN_real + j*bN_imag
    H(s) = ( ---------------------------- + ... + ---------------------------- ) * exp(-s*D),
             (s + a1_real + j*a1_imag)^m1         (s + aN_real + j*aN_imag)^mN
```

the parameter `ports` shall contain the following entries for the source and destination port indices:

```
    ports = '{ ..., P1, P2, ... }
```

And at the corresponding position, the parameter `data` shall have the 5*N+1 entries defining the coefficients of the N partial fraction terms:

```
    data =  '{ ...,
              N,                                            // number of terms
              a1_real, a1_imag, b1_real, b1_imag, m1,       // partial fraction term #1
              a2_real, a2_imag, b2_real, b2_imag, m2,       // partial fraction term #2
              ...
              aN_real, aN_imag, bN_real, bN_imag, mN,       // partial fraction term #N
              ...
            }
```

and the parameter `delay` shall have an entry defining the transport delay:

```
    delay = '{ ..., D, ... }
```

Note that the parameters `ports`, `data`, and `delay` may define multiple sets of transfer function and delay for the same pair of source and destination ports, allowing the definition of a port-to-port coupling with multiple transfer functions split with different delays.

The parameters `Z0`, `ports`, `data`, and `delay` can be alternatively defined by a parameter definition file named `filename` which defines the same named parameters in Python format. For any transmission characteristics not specified, the primitive assumes the reciprocal characteristics from the ones defined and ideal characteristics for the rest (i.e. no transmission loss and no crosstalk).

This primitive is a pseudo-module describing a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminals of ports |
| neg | input | xreal | negative terminals of ports |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| num_port | int | 2 | None | number of ports |
| Z0 | string array | '{"R50"} | ohms | characteristic impedance |
| ports | int array | '{0} | None | source/destination ports |
| data | real array | '{0.0} | None | transfer characteristics data |
| delay | real array | '{0.0} | seconds | line propagation delay |
| filename | string | "" | None | parameter definition file |
| abstol | real | 1e-3 | None | absolute tolerance for event-filtering |
| reltol | real | 1e-2 | None | relative tolerance for event-filtering |
| m | real | 1.0 | None | multiplicity factor |

