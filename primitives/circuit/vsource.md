---
title: "XMODEL primitive: vsource"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: vsource
primitive_category: circuit
description: "A voltage source circuit element."
date: 2026-03-11T07:20:43.551021
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE vsource
A voltage source circuit element.

The `vsource` primitive represents a voltage source stand-alone or controlled by an input signal across two circuit terminals. Note that this primitive is a pseudo-module to describe a structural netlist of electrical circuits and not a behavioral model by itself. The XMODEL simulator extracts an event-driven behavioral model at run-time based on the circuit network described by these circuit-level pseudo-modules.

The `vsource` primitive can be used in two different ways: first as a dependent voltage source controlled by an xreal-typed signal from a signal-flow model (mode="in") and second as an independent voltage source supplying a constant DC voltage (mode="dc").

### 1) A dependent voltage source controlled by an input (mode="in")

The default behavior of the `vsource` primitive (mode="in") is to drive a voltage controlled by the input signal `in`  between two circuit nodes. For instance:

```
    xreal       in, A, B;
    sin_gen     #(.amp(5.0), .freq(30.0)) in_ac(in);
    vsource     vin(.pos(A), .neg(B), .in(in));
```

drives a 5V-amplitude, 30Hz AC voltage between A and B.

This primitive provides a way to create a wide variety of voltage sources by combining it with various stimulus generator primitives.  In other words, the primitive `vsource` serves as a gateway that propagates a signal from signal-flow models to a voltage in electrical models.

### 2) An independent voltage source supplying a DC voltage (mode="dc")

When the parameter `mode` is set to "dc", the primitive works as an independent DC voltage source. For instance:

```
    xreal A, B;
    vsource     #(.mode("dc"), .dc(5.0))
                vin(.pos(A), .neg(B), .in(`ground));
```

connects a 5.0V supply between A and B. The terminal connected to the port "in" is ignored. In fact, it is equivalent to:

```
    xreal       in, A, B;
    dc_gen      #(.value(5.0)) in_dc(in);
    vsource     vin(.pos(A), .neg(B), .in(in));
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
| dc | real | 0.0 | volts | DC voltage value |

