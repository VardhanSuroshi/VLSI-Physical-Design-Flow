# About the project 
This project offers an immersive tutorial experienced within the context of the VSD Advanced Physical Design workshop, focusing on the utilization of OpenLANE.

OpenLANE represents a revolutionary automated RTL to GDSII flow, integrating essential components such as OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor, and custom methodology scripts. It is under the Apache License 2.0, reflecting its commitment to the open-source ethos. The primary objective of OpenLANE is to deliver pristine GDSII layouts autonomously, eliminating the need for human intervention. OpenLANE is fine-tuned for the Skywater 130nm open-source PDK and serves as a powerful tool for creating both hard macros and complete chips.




### Skills Gained

- **Automated ASIC Design**: Proficiency in leveraging automated RTL to GDSII flows.
- **Open-Source Toolchain**: Mastery of open-source tools such as Yosys, Magic, and Netgen.
- **Design Exploration**: Skill in using custom methodology scripts for design exploration and optimization.
- **Skywater 130nm PDK**: Expertise in working with the Skywater 130nm open-source Process Design Kit.
- **Hands-On Chip Development**: Experience in producing hard macros and complete chips autonomously.



## Why Open Source Tools for ASIC Development?

The hope for open-source ASIC flows like OpenLane is to provide multiple benefits:

- **Innovation Unleashed**: They empower you to explore unconventional approaches and foster creativity in ASIC design.

- **Vertical Integration**: These tools expand your capabilities for seamless integration, giving you greater control over your projects.

- **AI and Software-Driven Workflows**: Open source tools promote AI-assisted, software-driven workflows, making ASIC development more intelligent and efficient.

- **Cost-Efficient Scalability**: Harness the limitless scalability of the cloud without being burdened by licensing costs. Your potential knows no bounds.

# OpenLane Design Stages

OpenLane flow consists of several stages. By default, all flow steps are run in sequence. Each stage may consist of multiple sub-stages. OpenLane can also be run interactively as shown here.

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/c216442f-36bd-45e4-8659-2de69d4945d8)






1. Synthesis

- **yosys/abc**: Perform RTL synthesis and technology mapping.
- **OpenSTA**: Performs static timing analysis on the resulting netlist to generate timing reports.

2. Floorplaning

- **init_fp**: Defines the core area for the macro as well as the rows (used for placement) and the tracks (used for routing).
- **ioplacer**: Places the macro input and output ports.
- **pdngen**: Generates the power distribution network.
- **tapcell**: Inserts welltap and decap cells in the floorplan.

3. Placement

- **RePLace**: Performs global placement.
- **Resizer**: Performs optional optimizations on the design.
- **OpenDP**: Performs detailed placement to legalize the globally placed components.

4. Clock Tree Synthesis (CTS)

- **TritonCTS**: Synthesizes the clock distribution network (the clock tree).

5. Routing

- **FastRoute**: Performs global routing to generate a guide file for the detailed router.
- **TritonRoute**: Performs detailed routing.
- **OpenRCX**: Performs SPEF extraction.

6. Tapeout

- **Magic**: Streams out the final GDSII layout file from the routed def.
- **KLayout**: Streams out the final GDSII layout file from the routed def as a back-up.

7. Signoff

- **Magic**: Performs DRC Checks & Antenna Checks.
- **KLayout**: Performs DRC Checks.
- **Netgen**: Performs LVS Checks.
- **CVC**: Performs Circuit Validity Checks.
  
---

OpenLane integrated several key open source tools over the execution stages:

- **RTL Synthesis, Technology Mapping, and Formal Verification**: yosys + abc
- **Static Timing Analysis**: OpenSTA
- **Floor Planning**: init_fp, ioPlacer, pdn, and tapcell
- **Placement**: RePLace (Global), Resizer, OpenPhySyn (formerly), and OpenDP (Detailed)
- **Clock Tree Synthesis**: TritonCTS
- **Fill Insertion**: OpenDP/filler_placement
- **Routing**: FastRoute or CU-GR (formerly) and TritonRoute (Detailed) or DR-CU
- **SPEF Extraction**: OpenRCX or SPEF-Extractor (formerly)
- **GDSII Streaming out**: Magic and KLayout
- **DRC Checks**: Magic and KLayout
- **LVS check**: Netgen
- **Antenna Checks**: Magic
- **Circuit Validity Checker**: CVC
Everything in Floorplanning through Routing is done using **OpenROAD** and its various sub-utilities.
---
**OpenLane Output**

All output run data is placed by default under `./designs/design_name/runs`. Each flow cycle will output a timestamp-marked folder containing the following file structure:
```
<design_name>
├── config.json/config.tcl
├── runs
│   ├── <tag>
│   │   ├── config.tcl
│   │   ├── {logs, reports, tmp}
│   │   │   ├── cts
│   │   │   ├── signoff
│   │   │   ├── floorplan
│   │   │   ├── placement
│   │   │   ├── routing
│   │   │   └── synthesis
│   │   ├── results
│   │   │   ├── final
│   │   │   ├── cts
│   │   │   ├── signoff
│   │   │   ├── floorplan
│   │   │   ├── placement
│   │   │   ├── routing
│   │   │   └── synthesis
To delete all generated runs under all designs: `make clean_runs`
```
