---
title: "XMODEL primitive: trig_call"
document_type: reference
reference_type: primitive
product: XMODEL
primitive: trig_call
primitive_category: meas
description: "A trigger generator for called events."
date: 2026-03-11T07:20:43.439538
company: "Scientific Analog, Inc."
license: "Copyright (c) Scientific Analog, Inc."
---

# PRIMITIVE trig_call
A trigger generator for called events.

The `trig_call` primitive generates an xbit-typed trigger `out` when its `trigger()` task is called. This primitive is convenient if one wants to trigger events using a procedural statement within an `initial` or `always` block.

For instance, the following example shows how to trigger `trig1` whenever the `clk` signal has a positive-edge transition:

```
    xbit trig1;
    trig_call U1(trig1);

    always @(posedge clk) begin
        U1.trigger();
    end
```

The prototype of the `trigger()` task is listed below. The `trigger()` task can schedule a trigger event at an advanced time by providing the first optional argument `delay`, which indicates the absolute time delay measured from the current time. By default, the task assumes a pure transport delay, scheduling a new event while keeping all the pending events. However, with its second optional argument `inertial` set to 1, the task assumes an inertial delay, cancelling all the pending events before scheduling a new one.

```
    task trigger(input real delay=0.0, input int inertial=0);

Note that the `trig_call` primitive cannot generate more than one trigger events in a given timestep and may suppress the excess events. The parameter `max_warn` sets the maximum warning message count for such excess trigger events. Setting it to 0 suppresses all warning messages and setting it to -1 displays them all.

The xbit-typed trigger `out` can be used as an input to the measurement primitives to measure the time instants, delays, periods, etc. of the triggering events. The trigger signal is initialized to X and changes to 1 when the first event occurs. The trigger output `out` then toggles to a different value (0 or 1) whenever a subsequent event occurs.

## Input/Output Terminals
| Name | I/O | Type | Description |
|:-----|:----|:-----|:------------|
| out | output | xbit | output trigger |

## Parameters
| Name | Type | Default | Unit | Description |
|:-----|:-----|:--------|:-----|:------------|
| max_warn | int | -1 | None | maximum warning count |

