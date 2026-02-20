---
Title: "Scientific Analog Product Brochure (2025)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL", "GLISTER", "MODELZEN", "EQCHECK"]
Year: 2025
Source: "XMODEL_brochure_202506.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: The Best Way to Verify Analog Circuits in SystemVerilog


<!-- Page 2 -->
# What's the Best Way to Verify My Analog Circuits in SystemVerilog?

## For Verification Engineers, looking for a faster way to simulate analog models in SystemVerilog
**XMODEL is the fastest way to run analog simulation in SystemVerilog**
XMODEL's event-driven algorithm and rich set of primitives make it easy to build analog models that run significantly faster than
Real-Number Model.

## For System Architects, exploring architectures through top-down modeling of analog circuits
**GLISTER lets you build top-down analog models in schematic forms**
With GLISTER, describing system-level models of your analog circuits is as easy as drawing schematics with XMODEL primitive symbols. Zero coding, quick results.

## For Circuit Designers, seeking high-fidelity SystemVerilog models for their analog circuits
**MODELZEN can auto-extract bottom-up analog models from your circuits**
With MODELZEN, you can auto-generate correct-by-construction, SPICE-accurate SystemVerilog models from mouse click.


<!-- Page 3 -->
# XMODEL: Simulate Analog Circuits in SystemVerilog

XMODEL is a plug-in extension to SystemVerilog, enabling fast and accurate analog/mixed-signal simulation without SPICE. Its rich set of primitives makes it easy to build functional- and circuit-level models of analog circuits that run event-driven entirely within SystemVerilog. XMODEL is ideal for verifying analog circuits with digital control or calibration, using UVM testbenches.

## Fast and Accurate Event-Driven Simulation of Analog Models

XMODEL employs revolutionary algorithms that represent continuous-time analog waveforms using equations instead of points and compute them efficiently in an event-driven manner. XMODEL
can deliver up to 10-100x faster speed compared to Verilog-AMS or Real Number Verilog, without sacrificing accuracy.

## True Kirchhoff's Law-Based Simulation in SystemVerilog

Yet, XMODEL remains the only solution that simulates voltages and currents in analog circuits directly described with primitives for resistors, capacitors, and transistors, and more-without invoking SPICE. It offers the most straightforward way to model multiple-driver, loading, nonlinear, and switching effects.

## Verifying Analog/Mixed-Signal Systems with UVM

Universal Verification Methodology (UVM) is a standardized library for building reusable testbenches for digital systems. With XMODEL, you can now extend UVM to verify analog/mixed-signal circuits, using techniques such as coverage-driven and assertion-based verification with constrained-random inputs. All you need is a fixture module that encapsulates the device under verification (DUV) along with instrumentation units that generate stimuli and measure responses, all described using XMODEL primitives.


<!-- Page 4 -->
# GLISTER: Build Top-Down Analog Models in Schematic Forms

GLISTER is a plug-in for OpenAccess-based schematic editors, including Cadence Virtuoso and Synopsys Custom Compiler, providing a graphical interface to compose SystemVerilog models of analog circuits in schematic form and run XMODEL simulations-without writing code. GLISTER serves as a top-down modeling tool, enabling circuit designers to explore and refine ideas prior to implementation.

## No-Code Model Building with XMODEL Primitive Symbols

GLISTER provides a symbol library for XMODEL primitives, allowing you to build analog models simply by drawing schematics and netlisting them. Its intuitive user interface, especially tailored for analog designers, makes analog modeling a breeze.

## Integrated and Unified Testbench Management

The GLISTER Testbench Editor offers a unified interface for configuring testbenches, launching simulations, and viewing waveforms, as well as preparing netlists and control files for XMODEL-SPICE co-simulation from a hierarchy configuration.

## Modeling Silicon Photonics Systems in SystemVerilog

XMODEL's event-driven simulation extends seamlessly to optical domains, where signal frequencies reach hundreds of terahertz. In addition to over 200 primitives for electrical circuits, XMODEL provides dedicated primitives for silicon photonic elements, including optical waveguides, couplers, branches, laser sources, photodetectors, Mach-Zehnder modulators, micro-ring modulators, and more. With XMODEL, SystemVerilog becomes a unified platform for verifying heterogeneous systems that integrate digital, analog, and photonic components.


<!-- Page 5 -->
# MODELZEN: Auto-Extract Analog Models from Circuits

With MODELZEN, automatic model generation for analog circuits is not a dream; it's reality! MODELZEN is a bottom-up model extractor that converts any analog circuit into an equivalent SystemVerilog model described using XMODEL primitives. The extracted models support thorough and efficient validation of large-scale mixed-signal chips, leveraging the power of XMODEL and UVM.

## Quick, Correct-by-Construction Structural Model Generation

By default, MODELZEN generates structural models using XMODEL's circuit-level primitives. It maps each device in the circuit to an equivalent primitive, fits parameters via SPICE simulation, and connects the primitives according to the circuit topology. The result? Correct-by-construction models, generated with a mouse click.

## Functional Model Generation with User-Defined Models (UDMs)

To achieve faster simulation speeds, MODELZEN can also generate functional models for selected parts of the circuits using predefined templates called User-Defined Models (UDMs). If you've been writing bottom-up models manually, the UDM interface can capture your expertise and automate the model generation process.

## EQCHECK: Auto-Checking Circuit-Model Equivalence

EQCHECK is our new product, designed to streamline the validation of SystemVerilog models against SPICE-level circuits. Given a SPICE-simulated waveform file, it auto-generates a SystemVerilog testbench that replays the circuit's input/output waveforms. The testbench feeds the inputs to the model, compares its outputs to those from the circuit, and uses checkers to flag discrepancies. Once validated, you can confidently use the models of your analog circuits for system-level verification.


<!-- Page 6 -->
# About Scientific Analog, Inc.

Scientific Analog, Inc. was founded in 2015 with a mission to make analog IC design as systematic and productive as digital. In particular, we believe that an effective use of analog models within the established digital flows is the key to successful design and verification of today's mixed-signal ICs.

XMODEL, GLISTER, and MODELZEN are our first line of products towards this mission. Currently, more than 70 companies and universities worldwide are using XMODEL.

## Contact Us
For further information on Scientific Analog, Inc. or licensing and support of its products, please contact info@scianalog.com or visit https://www.scianalog.com.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Try Our Online Interactive Demos!
* Top-down Modeling with GLISTER: https://www.scianalog.com/glister_demo
* Bottom-up Modeling with MODELZEN: https://www.scianalog.com/modelzen_demo

## Disclaimers
XMODEL, GLISTER, MODELZEN, XWAVE, XMULAN, and EQCHECK are trademarks of Scientific Analog, Inc. Other product and company names referenced in this document may be the trademarks of their respective owners.

