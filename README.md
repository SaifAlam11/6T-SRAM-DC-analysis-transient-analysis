
# 6T SRAM Cell Design and Verification

This repository contains the schematic, custom physical layout, and pre-layout simulation verification for a standard 6-Transistor (6T) SRAM cell designed in Cadence Virtuoso using the GPDK090 (90nm) technology node.
The project covers the complete custom IC design flow, including cross-coupled inverter schematic capture, layout optimization for minimal area, and DC sweep analysis to calculate the Static Noise Margin (SNM).

Project Specifications

* Technology Node: Generic PDK 90nm (GPDK090)
* Supply Voltage (\(V_{DD}\)): 1.8 V
* Cell Topology: Standard 6-Transistor configuration (2 Pull-Up PMOS, 2 Pull-Down NMOS, 2 Pass-Gate NMOS)
* Design Environment: Cadence Virtuoso (IC617)
* Simulator: Spectre

## Design Flow & Implementation


### 1. Schematic Capture

* Implemented the classic cross-coupled inverter latch configuration featuring two access transistors.
* Assigned design variables (Vin) to systematically isolate and characterize individual inverter Voltage Transfer Curves (VTCs).

### 2. Custom Physical Layout

* Compact Footprint: Arranged standard pull-up and pull-down configurations to optimize diffusion share boundaries and routing efficiency.
* Layer Allocation: Used native GPDK090 layers including Poly (gates), Metal 1 (local interconnects/routing), and Contact windows.
* Well Isolation: Properly biased the N-Well region (\(V_{DD}\)) and P-Substrate (\(V_{SS}\)) to prevent latch-up and manage substrate noise.

### 3. Simulation & Analysis

* DC Sweep Configuration: Swept input nodes from 0V to 1.8V using Spectre to observe voltage transitions.
* Butterfly Curve Generation: Manipulated waveform plotting axes within Virtuoso Visualization & Analysis XL to map storage nodes (Q vs Qbar) against each other.
* Stability Verification: Confirmed cell stability by evaluating the distinct closed loops (eyes) of the resulting Butterfly Curve to guarantee robust Static Noise Margin parameters.

## Verification Suite

Physical verification can be run directly inside Cadence Virtuoso using industry-standard tools:

* DRC (Design Rule Check): Executed via Siemens Calibre nmDRC to ensure layout clearance, spacing, and density rules strictly adhere to PDK limits.
* LVS (Layout Versus Schematic): Executed via Siemens Calibre nmLVS to extract layout netlists and check complete equivalence against the source schematic.
