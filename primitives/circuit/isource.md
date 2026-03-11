---
title: "XMODEL primitive: isource"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: isource
primitive_category: circuit
description: "A current source circuit element."
date: 2026-03-11T07:20:43.520872
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE isource
A current source circuit element.

The `isource` primitive represents a current source stand-alone or controlled by an input signal across two circuit terminals. Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

The `isource` primitive can be used in two different ways: first as a dependent current source controlled by an xreal-typed signal from a signal-flow model (mode="in") and second as an independent current source supplying a constant DC current (mode="dc").

### 1) A dependent current source controlled by an input (mode="in")

The default behavior of the `isource` primitive (mode="in") is to drive a current controlled by the input signal `in`  between two circuit nodes. For instance:

```
    xreal       in, A, B;
    sin_gen     #(.amp(5.0), .freq(30.0)) in_ac(in);
    isource     iin(.pos(A), .neg(B), .in(in));
```

drives a 5A-amplitude, 30Hz AC current into a branch between A and B.

This primitive provides a way to create a wide variety of current sources by combining it with various stimulus generator primitives.  In other words, the primitive `isource` serves as a gateway that propagates a signal from signal-flow models to a current in electrical models.

### 2) An independent current source supplying a DC current (mode="dc")

When the parameter `mode` is set to "dc", the primitive works as an independent DC current source. For instance:

```
    xreal A, B;
    isource     #(.mode("dc"), .dc(5.0))
                iin(.pos(A), .neg(B), .in(`ground));
```

connects a 5.0A supply between A and B. The terminal connected to the port "in" is ignored. In fact, it is equivalent to:

```
    xreal       in, A, B;
    dc_gen      #(.value(5.0)) in_dc(in);
    isource     iin(.pos(A), .neg(B), .in(in));
```

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| pos | input | xreal | positive terminal |
| neg | input | xreal | negative terminal |
| in | input | xreal | input control signal |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| mode | string | "in" | None | mode of operation |
| dc | real | 0.0 | amperes | DC current value |
| m | real | 1.0 | None | multiplicity factor |

