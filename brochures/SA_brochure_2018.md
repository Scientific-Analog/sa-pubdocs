---
Title: "Scientific Analog Product Brochure (2018)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2018
Source: "XMODEL_brochure_201806.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: The Most Advanced Way to Model Analog Circuits in SystemVerilog


<!-- Page 2 -->
# What’s the Best Way to Verify My Analog Circuits in SystemVerilog?

## Verification Engineers
I want to run faster simulation of analog models in SystemVerilog.

### XMODEL is the fastest way to run analog simulation in SystemVerilog.
Its unique event-driven algorithm supports both functional- and circuit-level simulation 10~100x faster than Real-Number Verilog.


<!-- Page 3 -->
## System Architects
I need to compose analog models but don’t want to write codes.

### GLISTER is a graphical user interface integrated into Cadence® Virtuoso®.
It lets you build analog models in schematic forms and netlist them in SystemVerilog without writing any codes.

## Circuit Designers
I want to auto-extract SystemVerilog models from my circuits.

### MODELZEN is an automatic model generator for analog circuits.
With MODELZEN, you can extract correct-by-construction, SPICE-accurate SystemVerilog models from your circuits with a mouse click.


<!-- Page 4 -->
# What’s New This Year?

## GLISTER features are integrated into Cadence® Virtuoso® Analog Design Environment (ADE)

GLISTER-ADE integration allows you to choose “XMODEL” as one of the supported simulators from ADE sessions and perform key GLISTER tasks such as composing testbenches, generating netlists, running simulations, and viewing waveforms, all using the familiar ADE menus and commands.

## MODELZEN can auto-generate functional models as well as structural models

MODELZEN initially generated structural models, which guarantee correct-by-construction models without requiring analog expertise. However, for some critical blocks, one may be willing to go the extra mile in describing their key functionalities and extract functional models that run faster. The new MODELZEN integrates the MODELFIT’s capabilities into its streamlined flow, and can generate the selected parts of the circuits as functional models while generating the rest as structural models.


<!-- Page 5 -->
# XMODEL: Empower SystemVerilog with Event-Driven Analog Models

XMODEL is an extension to your existing System Verilog simulator such as VCS, NC-Verilog, and Questa/ModelSim, enabling fast and accurate simulation of analog/mixed-signal systems with functional models and circuit-level models. Since XMODEL can perform analog simulation entirely in SystemVerilog without involving SPICE, it is ideally suited for verifying large, complex mixed-signal systems where the mixture of digital and analog poses challenges to the existing tools such as SPICE, Verilog-AMS, and Real-Number Verilog.

## XMODEL Simulation Flow

```
             Analog Circuit
                   │
                   ▼
 ┌────────────────────────────────────┐
 │               XMODEL               │
 │                                    │
 │     XMODEL Primitives Library      │
 │                  +                 │
 │      SystemVerilog Simulator       │
 │   (VCS®, NC-Verilog®, ModelSim®)   │
 │                  +                 │
 │      XMODEL Simulation Engine      │
 │                                    │
 └────────────────────────────────────┘
                   │
                   ▼
         Analog Waveform Output
```

## Event-Driven Simulation with XMODEL Functional Models

XMODEL uses revolutionary, patent-pending algorithms to express analog waveforms in functional expressions and compute them efficiently in an event-driven fashion.
As a result, the functional models composed with XMODEL primitives in SystemVerilog can achieve up to 10~100x speed-up over Verilog-AMS or Real-Number Verilog, which must compute all the values on the waveforms for accurate results.

### XMODEL (Event-Driven)

```
        □  ← events
       / \
      /   \
  □───     ───□
```

### Other Simulators  
*(SPICE, Verilog-AMS, Real-Number Verilog)*

```
      ┌─┐
      │ └─┐
      │   └─┐
  ┌───┘      └───┐
```

## Circuit-Level Simulation in SystemVerilog with XMODEL

In addition to the functional primitives, XMODEL also provides a set of circuit-level primitives such as resistors, capacitors, transistors, and even transmission lines. With these circuit-level primitives, one can easily compose models with various analog effects such as loading, nonlinearity, switching, and multiple drivers, which is not directly supported by Real-Number Verilog (a.k.a. wreal models). Yet, the simulation still runs entirely in SystemVerilog without invoking SPICE.


<!-- Page 6 -->
# GLISTER: Model Circuits in Schematics without Writing Codes

GLISTER is a graphical user interface to XMODEL and MODELZEN integrated into the Cadence® Virtuoso® Design Environment. With GLISTER, you can easily compose analog models in schematic forms and run XMODEL simulations without writing any codes.

## Model Building with XMODEL Primitive Symbols

GLISTER provides the rich set of XMODEL primitives as schematic symbols and can netlist them into SystemVerilog models. Hence, writing models with GLISTER simply means placing primitive symbols on a schematic and connecting them with wires. No coding is necessary! Composing models with GLISTER is even easier with the on-line documentations integrated into the Cadence® Virtuoso® Design Environment.

## Mixed-Signal Hierarchical Netlisting

GLISTER understands that your schematic models may contain different types of signals connecting digital and analog components, such as wire, real, xbit, and xreal. When netlisting the schematics into SystemVerilog models, GLISTER can automatically determine the proper type of each signal and insert type-coercing connectors as necessary.

## Integrated Testbench Management

With GLISTER’s Testbench Editor, you can define XMODEL testbenches as cellviews in the Cadence® design database, specifying the simulation options, hierarchy configurations, extra source files, etc., all using a graphical user interface. Also, each testbench cellview can be exported as a simulation directory containing a Makefile and source files, allowing batch processing from the command line.

## XMODEL-SPICE Co-simulation Support

When both circuit and model views co-exist in the design hierarchy, GLISTER prepares necessary files for XMODEL-SPICE co-simulation, including the SystemVerilog model files, SPICE/Spectre netlists, and mixed-signal simulation control files. The view for each cell or instance can be selected using the Cadence® Hierarchy Editor. The GLISTER Testbench Editor provides a uniform interface to different simulators including Synopsys®’s VCS® and XA and Cadence®’s NCVerilog® and APS.


<!-- Page 7 -->
# MODELZEN: Auto-Extract Analog Models From Circuits

Automatic generation of analog models is not a dream; it’s a reality! MODELZEN is an automatic model generator for analog circuits that can translate any circuit into an equivalent SystemVerilog model using XMODEL primitives.

## MODELZEN Conversion Flow

```
          SPICE Netlist
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

## Quick and Correct-by-Construction Analog Model Generation

Basically, MODELZEN generates structural models of the circuits, leveraging the circuit-level simulation capability of XMODEL. In other words, MODELZEN builds models by first characterizing the individual devices composing the circuits and then connecting the resulting device models according to the topology of the original circuits. This approach does not require any understanding on the circuits’ functionality and guarantees correct-by-construction models. Furthermore, the generated models run fast with the XMODEL’s event-driven simulation. With MODELZEN, you can get your full-chip models ready in just a few hours!

## No Analog Expertise Required!

With MODELZEN, you don’t need to be an analog expert to create high-fidelity models for analog circuits. Thanks to the MODELZEN’s structural modeling approach, a verification engineer can generate models for system-level verification without asking for help from the circuit designer. Also, a circuit designer can effortlessly refresh the models whenever his/her circuits are updated.

## Create Models with a Mouse Click!

When you use MODELZEN with GLISTER, you can auto-generate models directly from Cadence® Virtuoso® schematics just with a mouse click! GLISTER streamlines the preparation steps of model generation including netlist generation and property exporting, and imports the generated models back into the design database.


<!-- Page 8 -->
# About Scientific Analog, Inc.

**Scientific Analog, Inc.** was founded in 2015 with a mission to make analog IC design as systematic and productive as digital design. In particular, we believe that an effective use of analog models within the established digital flows is the key to successful design and verification of today’s mixed-signal ICs. XMODEL, GLISTER, and MODELZEN are our first line of products towards this mission. Currently, more than 30 companies and universities located in U.S.A., Korea, and China are using XMODEL.

## Contact Us
For further information on Scientific Analog, Inc. or licensing and support of its products, please contact info@scianalog.com or visit www.scianalog.com.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
All the trademarks used in this document are the property of their respective holders.
