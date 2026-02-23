---
Title: "Scientific Analog Product Brochure (2017)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN"]
Year: 2017
Source: "XMODEL_brochure_201706.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: Take Your Analog Models to the Next Level


<!-- Page 2 -->
## Our Products

* **XMODEL** enables fast and accurate simulation of analog/mixed-signal systems entirely in SystemVerilog.
 
* **GLISTER** is a graphical user interface of XMODEL and MODELZEN integrated into Cadence® Virtuoso® Schematic Editor.

* **MODELZEN** can automatically generate XMODEL models from your circuit schematics or netlists.


<!-- Page 3 -->
# XMODEL is for Everyone!

## System Architects
**Explore architectural choices of analog/mixed-signal systems using XMODEL's fast event-driven simulation.**

 * Compose system-level models in schematic forms using GLISTER.
 * Enjoy 10-1OOx faster speed than other analog functional models (Verilog-A/MS or Real Number Verilog).
 * Verify system-level operation including digital HDL models that are ready for synthesis.

*XMODEL as Top-Down Tool*

## Circuit Designers
**Compose or auto-generate models for your circuits easily in a schematic-based analog design environment.**

 * Compose top-down functional models in schematic forms using GLISTER with a rich set of primitives.
 * Express any analog circuit behaviors in SystemVerilog using circuit-level modeling (CLM).
 * Automatically extract models from any circuits using MODELZEN.

*XMODEL as Bottom-Up Tool*

## Verification Engineers
**Verify chip-level functionality of large-scale systems consisting of both digital and analog components.**

 * e.g., RF transceivers with digital calibration, processors with high-speed I/Os, DRAMs with internaI power generation, ...
 * Leverage blazingly fast event-driven simulation in a single simulation platform of SystemVerilog.
 * Seamlessly integrate with existing digital verification flows (e.g. UVM) as well as mixed-signal simulation flows.
 
*XMODEL as Sign-Off Tool*


<!-- Page 4 -->
# XMODEL: Empower SystemVerilog with Event-Driven Analog Models

XMODEL is an extension to your existing SystemVerilog simulator such as VCS, NC-Verilog, and Questa/ ModelSim, enabling fast and accurate simulation of analog/mixed-signal systems with functional models and/or circuit-level models. Since XMODEL can perform analog simulation entirely in SystemVerilog without involving SPICE, it is ideally suited for verifying large, complex mixed-signal systems where the mixture of digital and analog poses challenges to the existing tools such as SPICE, Verilog-AMS, and Real-Number Verilog.

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

XMODEL uses revolutionary, patent-pending algorithms to express analog waveforms in functional expressions and compute them efficiently in an event-driven fashion. As a result, the functional models composed with XMODEL primitives in SystemVerilog can achieve up to 10~100x speed-up over Verilog-AMS or Real-Number Verilog, which must compute all the values on the waveforms for accurate results.

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

In addition to the functional primitives, XMODEL also provides a set of circuit-level primitives such as resistors, capacitors, transistors, and even transmission lines. With these circuit-level primitives, one can easily compose models with various analog effects such as loading, nonlinearity, switching, and multiple driver effects, which are not directly supported by Real-Number Verilog (a.k.a. wreal models). Yet, the simulation still runs entirely in SystemVerilog without invoking SPICE.
 

<!-- Page 5 -->
# GLISTER: Model Circuits in Schematics without Writing Codes

GLISTER is a graphical user interface to XMODEL and MODELZEN integrated into the Cadence® Virtuoso® Design Environment. With GLISTER, you can easily compose analog models in schematic forms and run XMODEL simulations without writing any codes.

## Model Building with XMODEL Primitive Symbols

GLISTER provides the rich set of XMODEL primitives as schematic symbols and can netlist them into SystemVerilog models. Hence, writing models with GLISTER simply means placing primitive symbols on a schematic and connecting them with wires. No coding necessary! Composing models with GLISTER is even easier with the on-line documentations integrated into the Cadence® Design Environment.

## Mixed-Signal Hierarchical Netlisting

GLISTER understands that your schematic models may contain different types of signals connecting digital and analog components, such as wire, real, xbit, and xreal. When netlisting the schematics into SystemVerilog models, GLISTER can automatically determine the proper type of each signal by traversing the design hierarchy and produce models with consistent signal types and required connectors.

## Integrated Testbench Management

With GLISTER's Testbench Editor, you can define XMODEL testbenches as cellviews in the Cadence® design database, specifying the simulation options, hierarchy configurations, extra source files, etc., using a graphical user interface. Also, each testbench cellview can be exported as a simulation directory containing a Makefile and source files, allowing batch processing from the command line.

## XMODEL-SPICE Co-simulation Support

When both circuit and model views co-exist in the design hierarchy, GLISTER prepares necessary files for XMODEL-SPICE co-simulation, including the SystemVerilog model files, SPICE/Spectre netlists, and mixed-signal simulation control files. The cellview to be used for each cell or instance can be selected using the Cadence® Hierarchy Editor. The GLISTER Testbench Editor provides a uniform interface to different simulators including Synopsys®'s VCS® and XA and Cadence®'s NCVerilog® and APS.


<!-- Page 6 -->
# MODELZEN: Create Analog Models with Peace of Mind

Automatic generation for analog models is not a dream; it's a reality! MODELZEN is an automatic model generator for analog circuits that can translate any circuit into an equivalent SystemVerilog model using XMODEL primitives.

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

Basically, MODELZEN generates structural models of given circuits, leveraging the circuit-level simulation capability of XMODEL. In other words, MODELZEN builds models by first characterizing the individual devices composing the circuits and then connecting the resulting device models mimicking the topology of the original circuits. This approach does not require any understanding on the circuits' functionality and guarantees correct-by-construction models. Furthermore, the generated models run fast with the XMODEL's event-driven simulation. With MODELZEN, you can get your full-chip models ready in just a few hours!

## No Analog Expertise Required!

With MODELZEN, you don't need to be an analog expert to create high-fidelity models for analog circuits. Thanks to MODELZEN's structural modeling approach, a verification engineer can generate models for system­ level verification without asking for help from the circuit designer. Also, a circuit designer can effortlessly refresh models whenever his/her circuits are updated.

## Create Models with a Mouse Click!

When you use MODELZEN with GLISTER, you can auto-generate models directly from Cadence® Virtuoso® schematics just with a mouse click! GLISTER streamlines the preparation steps of model generation including netlist generation and property exporting and imports the generated models back into the design database, maintaining them up-to-date.


<!-- Page 7 -->
# Take Your Analog Models to the Next Level

## Top-Down Modeling with XMODEL Primitives

With a rich set of XMODEL primitives, it is easy to describe your ideas into functional models and test their operation before starting the circuit design.

## Bottom-Up Modeling with MODELZEN/MODELFIT

After the circuit design is done, you can expedite the system-level verification by using models extracted from your circuits using MODELZEN or MODELFIT.
 * **MODELZEN** translates any circuit netlist into an equivalent XMODEL circuit-level model.
 * **MODELFIT** calibrates the parameters of your functional models against SPICE simulaon.

## Fast System-Level Verification with XMODEL

Either with top-down or with bottom-up models, XMODEL delivers the fastest event-driven simulation in SystemVerilog with co-simulation support with SPICE.

## IC Design Flow with XMODEL

```
          1. Idea             ┐
              │               | Top-Down
              ▼               | Modeling
     2. Functional Model      ┘ 
              │
              ▼
 3. Circuit Implementation    ┐
              │               | Bottom-Up
              ▼               | Modeling
    4. Verification Model     ┘
              │
              ▼
       5. IC Product
```


<!-- Page 8 -->
# About Scientific Analog, Inc.

**Scientific Analog, Inc.** was founded in 2015 with a mission to make analog IC design as systematic and productive as digital design. In particular, we believe that an effective use of analog models within the established digital flows is the key to successful design and verification of today's mixed-signal ICs. XMODEL, GLISTER, and MODELZEN are our first line of products towards this mission. Currently, more than 25 companies and universities located in U.S.A., Korea, China, and India are using XMODEL.

## Contact Us
For further information on Scientific Analog, Inc. or licensing and support of its products, please contact info@scianalog.com or visit www.scianalog.com.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
All the trademarks used in this document are the property of their respective holders.
