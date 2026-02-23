---
Title: "Scientific Analog Product Brochure (2019)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2019
Source: "XMODEL_brochure_201905.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: The Best Way to Verify Analog Circuits in SystemVerilog


<!-- Page 2 -->
# What's the Best Way to Verify My Analog Circuits in SystemVerilog?

## Verification Engineers
I want to run faster simulation of analog models in SystemVerilog.

### XMODEL is the fastest way to run analog simulation in SystemVerilog.
Its unique event-driven algorithm and rich set of primitives make it easy to compose analog models that run 10~100x faster than Real-Number Verilog models.

## System Architects
I need to compose analog models but don’t want to write codes.

### GLISTER lets you build top-down analog models in schematic forms.
With GLISTER, writing analog models is simply drawing schematics with XMODEL primitive symbols in Cadence Virtuoso. No coding required!

## Circuit Designers
I need to write SystemVerilog models for my analog circuits.

### MODELZEN can auto-extract bottom-up analog models from your circuits.
With MODELZEN, you can automatically generate correct-by-construction, SPICE-accurate SystemVerilog models from your circuits just with a mouse click.


<!-- Page 3 -->
# XMODEL: Empower SystemVerilog with Event-Driven Analog Models

XMODEL is a plug-in extension to SystemVerilog that enables fast and accurate analog/mixed-signal simulation without SPICE. With its rich set of primitives, it is easy to compose both functional- and circuit-level analog models that run in an event-driven fashion entirely within SystemVerilog. Particularly, XMODEL offers the best way to verify your mixed-signal ICs with Universal Verification Methodology (UVM).

## XMODEL Simulation Flow

```
      Analog/Mixed-Signal Models
                   │
                   ▼
 ┌────────────────────────────────────┐
 │               XMODEL               │
 │                                    │
 │     XMODEL Primitives Library      │
 │                  +                 │
 │      SystemVerilog Simulator       │
 │                  +                 │
 │      XMODEL Simulation Engine      │
 │                                    │
 └────────────────────────────────────┘
                   │
                   ▼
          Simulation Results
```

## Fast and Accurate Analog Simulation in SystemVerilog

XMODEL uses revolutionary, patent-pending algorithms to express analog waveforms in equation forms and compute them efficiently in an event-driven manner. As a result, the SystemVerilog models composed with XMODEL primitives can achieve up to 10~100x speed-up compared to Verilog-AMS or Real-Number Verilog, without sacrificing accuracy.

### XMODEL (Event-Driven)
Can be both fast and accurate thanks to fewer events

```
        □  ← events
       / \
      /   \
  □───     ───□
```

### Other Simulators  
*(SPICE, Verilog-AMS, Real-Number Verilog)*
Must trade speed for accuracy due to more events required

```
      ┌─┐
      │ └─┐
      │   └─┐
  ┌───┘      └───┐
```

## Circuit-Level Simulation in SystemVerilog

Currently, XMODEL is the only solution that enables true circuit-level simulation in SystemVerilog without invoking SPICE. Simply by listing the XMODEL’s circuit-level primitives such as resistors, capacitors, transistors, and transmission lines, you can write analog models with loading effects, nonlinear behaviors, switching effects, and multiple drivers.

## XMODEL-SPICE Co-simulation

The SystemVerilog models built with XMODEL primitives can also interface with SPICE netlists as well as Verilog-AMS or Real-Number Verilog models as supported by the host simulator.

## Automate Simulations with XMULAN

XMULAN is an extensive Python library included in XMODEL. With XMULAN, you can write Python scripts that launch simulations while sweeping parameters, collect results, and post-process them.


<!-- Page 4 -->
# GLISTER: Build Top-Down Analog Models in Schematic Forms

GLISTER is a graphical user interface for using XMODEL and MODELZEN within the Cadence Virtuoso Design Environment. With GLISTER, you can easily compose analog models in schematic forms and run XMODEL simulations without writing any codes.

```
 ┌──────────────────────────────────────────────────────────┐
 |  Draw model schematics with XMODEL primitive symbols.    |
 |                           │                              |
 |                           ▼                              |
 |  And GLISTER can netlist them into SystemVerilog models. |
 └──────────────────────────────────────────────────────────┘
```

## Model Building with XMODEL Primitive Symbols

With GLISTER, writing models simply means placing the XMODEL primitive symbols on a schematic view and connecting them with wires. No coding is necessary! Also, the intuitive user interface friendly to analog designers makes analog modeling a breeze.


## Mixed-Signal Hierarchical Netlisting

GLISTER understands that your schematic models may contain different types of signals connecting digital and analog components. GLISTER is the only SystemVerilog netlister that can automatically detect the type of each signal and insert type-coercing connectors as necessary.

## Integrated Testbench Management

The GLISTER Testbench Editor provides a consistent interface for configuring testbenches, launching simulations, and viewing waveform results, as well as for preparing netlists and control files for XMODEL-SPICE co-simulation from a hierarchy configuration.

## Integration with Cadence Analog Design Environment (ADE)

The GLISTER-ADE integration allows you to choose XMODEL as one of the supported simulators from the ADE sessions and perform key GLISTER tasks such as configuring testbenches, generating netlists, running simulations, and viewing waveforms, all using the familiar ADE menus and commands.


<!-- Page 5 -->
# MODELZEN: Auto-Extract Analog Models From Circuits

With MODELZEN, automatic generation of analog models is not a dream; it’s a reality! MODELZEN is a bottom-up model extractor that can translate any analog circuit into an equivalent SystemVerilog model using XMODEL primitives.

## MODELZEN Conversion Flow

```
      SPICE/Spectre Netlist
                │
                ▼
┌──────────────────────────────┐
│           MODELZEN           │
│                              │
│  1. Input Netlist Parsing    │
│  2. Topology Analysis        │
│  3. Device Model Fitting     │
│  4. Output Model Generation  │
│                              │
└──────────────────────────────┘
                │
                ▼
         XMODEL Netlist
```

## Quick, Correct-by-Construction Structural Model Generation

By default, MODELZEN generates structural models of the circuits, using the circuit-level primitives of XMODEL. In other words, MODELZEN builds models by first characterizing the individual devices composing the circuits and connecting the resulting device models according to the topology of the original circuits. This approach guarantees correct-by-construction models without requiring analog expertise and gets your full-chip models ready in just a few hours!

## Functional Model Generation with User-Defined Models (UDMs)

In addition to circuit-level models, MODELZEN can also generate higher-abstraction models that enable faster simulation speeds. With the MODELZEN’s new user-defined model (UDM) interface, you can map any selected parts of the circuits to custom functional models populated with SPICE-calibrated parameters. If you have been writing bottom-up models manually, the UDM interface is a great way to capture your expertise and automate the model generation flow.

## Create Models from Circuit Schematics Just with a Mouse Click!

The GLISTER support for MODELZEN provides a user-friendly interface for generating SystemVerilog models directly from Cadence Virtuoso schematics. When initiated by a mouse click, GLISTER streamlines the whole steps of model generation with MODELZEN, including extracting circuit netlists, exporting MODELZEN properties, generating SystemVerilog models, and importing the models back to the design database.


<!-- Page 6 -->
# About Scientific Analog, Inc.

Scientific Analog, Inc. was founded in 2015 with a mission to make analog IC design as systematic and productive as digital. In particular, we believe that an effective use of analog models within the established digital flows is the key to successful design and verification of today’s mixed-signal ICs.

XMODEL, GLISTER, and MODELZEN are our first line of products towards this mission. Currently, more than 40 companies and universities worldwide are using XMODEL.

## Contact Us
For further information on Scientific Analog, Inc. or licensing and support of its products, please contact info@scianalog.com or visit www.scianalog.com.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
XMODEL, GLISTER, MODELZEN, XWAVE, and XMULAN are trademarks of Scientific Analog, Inc.
Other product and company names referenced in this document may be the trademarks of their respective owners.
