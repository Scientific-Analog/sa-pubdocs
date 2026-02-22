---
Title: "Scientific Analog Product Brochure (2015)"
Company: "Scientific Analog, Inc."
Document_type: "product_brochure"
Products: ["XMODEL"]
Year: 2015
Source: "XMODEL_brochure_201505.pdf"
License: "Copyright (c) Scientific Analog, Inc."
---

<!-- Page 1 -->
# XMODEL: The Best Way to Verify Analog Circuits in SystemVerilog


<!-- Page 2 -->
# INTRODUCING XMODEL

XMODEL is a collection of tools and libraries that can turn your favorite SystemVerilog simulator into a powerful analog/mixed-signal simulator. With XMODEL, you can verify the functionality and estimate the performance of various large-scale mixed-signal systems that require both high accuracy and fast speed, all on a single simulation platform, SystemVerilog.

XMODEL uses revolutionary, patent-pending algorithms to accurately express and quickly compute continuous-time analog waveforms on an event-driven logic simulator. Unlike other analog simulators that use a set of time-sampled points to describe a signal waveform, XMODEL uses a series of events each described by a mathematical, functional expression of the signal. This allows XMODEL to achieve virtually infinite precision without relying on a fine time step, while using only a small number of events. This trait is analogous to the vector fonts that always achieve the best image quality regardless of the display resolution while requiring only a small amount of data.

Furthermore, XMODEL computes these functional expressions for analog signals in a purely event-driven fashion, without involving any time-step integration or numerical iterations. These algorithms make XMODEL both fast and accurate, typically achieving 10~100× speed-up compared to Verilog-AMS or Real-Number Verilog for the same accuracy.


<!-- Page 3 -->
# XMODEL is:

## Fast: 
Its typical speed-up over Verilog-AMS or Real-Number Verilog is 10~100×.

## Accurate: 
The best precision is always achieved without sacrificing the speed.

## Easy: 
Writing models and running simulation is easy both for analog and digital designers.

## Comparison with other analog/mixed-signal behavioral simulators

| Category | XMODEL | Real-Number Models | Verilog-AMS | Matlab®/Simulink® |
|-----------|---------|-------------------|--------------|-------------------|
| **Simulation Algorithm** | Event-driven | Fixed-step | Variable-step | Variable/fixed-step |
| **Baseline Simulator** | SystemVerilog | SystemVerilog | Verilog-AMS | Matlab®/Simulink® |
| **Speed** | Fastest (regardless of time step) | Moderate (varies with time step) | Slow | Fast |
| **Accuracy** | High (regardless of time step) | Moderate (varies with time step) | High | High |
| **Modeling Capability** | Functional and Circuit-level | Functional only | Functional and Circuit-level | Functional only |
| **Statistical Simulation** | Fast (Monte-Carlo + CPDF) | Slow (Monte-Carlo) | Slow (Monte-Carlo) | Slow (Monte-Carlo) |


<!-- Page 4 -->
# XMODEL is for Everyone!

## System Architects
**Explore architectural choices while evaluating their system-level performances.**
e.g. Compare bit-error rates (BERs) and jitter tolerance (JTOL) of a high-speed I/O link with different equalization or timing recovery options.

## Circuit Designers
**Run fast system-level simulation with analog behavioral models.**
e.g. Simulate the convergence behavior and phase noise characteristics of a digitally-controlled phase-locked loop (PLL).

## Verification Engineers
**Verify the functionality of digital controllers in the context of analog.**
e.g. Verify a digital calibration engine for radio-frequency transceivers 


<!-- Page 5 -->
# MAIN FEATURES

## 1. Ultra-Fast Analog/Mixed-Signal Simulation in SystemVerilog

With XMODEL, you can perform purely event-driven behavioral simulation of analog/mixed-signal systems using the commercial available SystemVerilog simulators. Currently, the supported simulators are Synopsys® VCS®, Cadence® NC-Verilog®/Incisive®, and MentorGraphics® ModelSim®/Questa®. XMODEL is particularly suited for verifying large-scale mixed-signal systems for which traditional SPICE, fast SPICE, and Verilog-AMS are too slow and Verilog, VHDL, and Real-Number Verilog models are too crude. Also, its advantage over other model-based simulators such as Matlab/Simulink is that the digital RTL models verified using XMODEL can be turned into implementations directly, without having to rewrite the models.

## 2. Dynamic Waveform Viewing with XWAVE

XWAVE is a full-featured waveform viewer dedicated for displaying event-driven waveforms with infinite precision. Since XMODEL records each signal waveform using a series of functional expressions rather than using a finite set of discrete points, you will never see finite-precision effects while browsing the waveforms. Also, XWAVE can process and display statistical simulation results such as phase noise, jitter, bit-error rates, etc.

## 3. Streamline Your Simulation with XMULAN

XMULAN is a powerful Python library included in the XMODEL package that can streamline your XMODEL simulations and post-process their results. With XMULAN, you can launch a set of simulations while sweeping parameters, collect results, and process them for display or recording. For instance, you can write Python scripts simulating the jitter transfer function of a PLL, jitter tolerance of a CDR, and BER bathtub curve of a high-speed transceiver each of which requires the sweep of jitter frequency, amplitude, and voltage/timing offset, respectively. 


<!-- Page 6 -->
## 4. Hyper-Fast Statistical Simulation

Some key characteristics of analog/mixed-signal systems are statistical in nature. XMODEL has a unique capability of computing the signal’s statistical property while performing time-domain simulation, achieving significant speed-ups over the traditional Monte-Carlo simulations. For instance, XMODEL can measure a 50-point BER bathtub curve measuring down to 10-18 BER in 10 minutes and a jitter tolerance curve with the target BER of 10-12 in only 20 minutes!

# FINALLY, WRITING MODELS IS EASY WITH XMODEL

## 1. Build Models with a Rich Library of XMODEL Primitives

Writing behavioral models for analog circuits is a burden for many circuit designers and verification engineers. XMODEL makes this job easy by providing a rich set of primitive modules that let you build analog models and their testbenches simply by connecting them up as building blocks. Virtually no programming required! The XMODEL package also comes with a variety of examples that illustrate how to model common circuit blocks.


<!-- Page 7 -->
## 2. Use a Schematic Editor and GLISTER to Compose Models Graphically

You can also compose models using a graphical editor such as Cadence® Virtuoso® Schematic Editor.  All the XMODEL primitives are available as schematic symbols. GLISTER is a model netlister that can generate XMODEL sources from the schematic views and also the XMODEL-SPICE co-simulation netlists using the views selected from Cadence® Hierarchical Editor.

## 3. Verify Your Models Against Circuits Using XMODEL-SPICE Co-simulation

Since XMODEL uses SystemVerilog as the core simulation engine, it can run co-simulation on systems with the selected circuit blocks expressed in transistor-level SPICE netlists. With this feature, you can verify whether your model is consistent with its circuit implementation, by comparing their simulation results with the same testbench and stimuli. 

## 4. Use Circuit-Level Models When Signal-Flow Modeling is Difficult

For some circuits, writing signal-flow behavioral models may not be easy. For example, it can be much more straightforward to describe a switched-capacitor DC-DC converter using switches and capacitors rather than deriving its time-averaged model. The XMODEL’s Circuit-Level Modeling (CLM) feature allows you to describe circuits using basic circuit elements like resistors, capacitors, and switches. Still, the simulation is run in the same event-driven fashion, which is faster than traditional SPICE.

## 5. Extract Circuit Parameters with MODELFIT

Replacing analog circuits with their macromodels is an effective way to speed-up the system-level verification including the circuit-level non-idealities. MODELFIT is a Python library that can streamline the processes of extracting common circuit characteristics, such as large-signal DC and small-signal AC characteristics, periodically time-varying characteristics such as PPV and ISF, and statistical characteristics such as variation, mismatch, and noise.


<!-- Page 8 -->
# About Scientific Analog, Inc.

Scientific Analog, Inc. is a spin-off from Seoul National University, Korea, which was founded with a mission to make analog circuit design more productive and less laborious. In particular, we believe that analog design can be as systematic as digital by leveraging its linear system abstraction. For example, XMODEL is a by-product of an effort to make a behavioral simulator that is most suitable for linear dynamical systems. Our aim is to develop design libraries and
verification tools for analog with which designers can make complex analog/mixed-signal systems simply by putting together building blocks without an expertise in transistor-level circuit design.

## Contact Us
For further information on XMODEL or licensing and support, please contact info@scianalog.com or visit us at www.scianalog.com.
* Email: info@scianalog.com
* Website: https://www.scianalog.com

## Disclaimers
All the trademarks used in this document are the property of their respective holders.
