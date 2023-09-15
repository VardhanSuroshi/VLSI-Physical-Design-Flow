<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_asic_class/assets/132068498/84c06100-dffc-48a1-9b48-fd86f53942bd" alt="Image" width="900">
</p>



# About the project 
This project offers an immersive tutorial experienced within the context of the VSD Advanced Physical Design workshop, focusing on the utilization of OpenLANE.

OpenLANE represents a revolutionary automated RTL to GDSII flow, integrating essential components such as OpenROAD, Yosys, Magic, Netgen, Fault, OpenPhySyn, SPEF-Extractor, and custom methodology scripts. It is under the Apache License 2.0, reflecting its commitment to the open-source ethos. The primary objective of OpenLANE is to deliver pristine GDSII layouts autonomously, eliminating the need for human intervention. OpenLANE is fine-tuned for the Skywater 130nm open-source PDK and serves as a powerful tool for creating both hard macros and complete chips.

### Skills Gained

- **Automated ASIC Design**: Proficiency in leveraging automated RTL to GDSII flows.
- **Open-Source Toolchain**: Mastery of open-source tools such as Yosys, Magic, and Netgen.
- **Design Exploration**: Skill in using custom methodology scripts for design exploration and optimization.
- **Skywater 130nm PDK**: Expertise in working with the Skywater 130nm open-source Process Design Kit.
- **Hands-On Chip Development**: Experience in producing hard macros and complete chips autonomously.


---
# Table of Contents

1. [About the Project](#about-the-project)
2. [Overview from Application to Hardware](#overview-from-application-to-hardware)
3. [Why Do We Need a Chip?](#why-do-we-need-a-chip)
   + [Components of a Chip](#components-of-a-chip)
   + [Key Components Needed for ASIC Development](#key-components-needed-for-asic-development)
   + [Why Open-Source Tools for ASIC Development?](#why-open-source-tools-for-asic-development)
4. [About OpenLane](#about-openlane)
   + [OpenLane Integrated Tools](#openlane-integrated-tools)
   + [OpenLane Output](#openlane-output)
5. 




---

## Overview from Application to Hardware
<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_asic_class/assets/132068498/dd018703-3b2e-464d-8653-d7deb3c9dd6f" alt="Image" width="800">
</p>





- **Apps**: Application software, often referred to as "apps," performs specific tasks or functions for end-users.

- **System Software**: This category acts as an intermediary between hardware components and user-facing applications. It provides essential services, manages resources, and enables application execution.

- **Operating System**: The fundamental software managing hardware resources and offering services for users and applications. It controls memory, processes, files, and interfaces (e.g., Windows, macOS, Linux, Android).

- **Compiler**: Translates high-level programming code( C ,C++ , java etc... ) into assembly-level language.

- **Assembler**: Converts assembly language code into machine code ( 10101011100 ) for direct processor execution. 

- **RTL (Register Transfer Level)**: Represents digital circuit behavior using registers and data transfer operations.

- **Hardware**: Physical components of a computer system or electronic device enabling various tasks.


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_asic_class/assets/132068498/e72cab48-7bad-409c-bb50-033d6b07816f" alt="Image" width="500">
</p>







## Why do we need a Chip?

Consider the Arduino Uno, a versatile development board used for various projects. At its core lies the ATmega328P microcontroller, a crucial component. Here's why we need this chip:

The Arduino Uno is powered by the ATmega328P microcontroller. This chip serves as the brain of the board and is responsible for executing user-programmed code. It contains program memory (Flash), RAM, EEPROM, and various hardware peripherals. The microcontroller handles input, output, and data processing, making it the central processing unit (CPU) of the Arduino Uno. It operates at a clock speed of 16 MHz, ensuring precise timing for program execution.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/c49db320-68d1-4d28-8f9b-28e8e6866ffc" alt="Image" width="600">
</p>




 ### Components of a Chip:


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/55fc637c-2bb4-4f3f-891d-5d252fded3da" alt="Image" width="600">
</p>




A chip comprises several key components:

- **Macros**: Predefined, reusable digital circuit blocks, like standard cells, simplifying complex chip design.

- **Foundry IPs (Intellectual Property)**: Pre-designed, verified circuit elements (e.g., analog blocks, memory cores) licensed from semiconductor foundries for custom chip integration.

- **IO Pads and Pins**: IO pads are physical interfaces connecting the chip to the external world. IO pins facilitate electrical connections between these pads and the internal circuitry for input and output communication.




# Overview of RTL to GDS Flow:

The RTL to GDS (Register-Transfer Level to Graphic Data System) flow is a complex process that transforms a high-level chip design into a physical layout ready for manufacturing. Here are the key steps involved:

 1. RTL Design
- Creation of a high-level chip functionality description using HDL (Hardware Description Language) like VHDL or Verilog.
- Captures the behavior and logic of the design.

 2. Functional Verification
- Subject the RTL design to functional verification to ensure it adheres to specifications.
- Use simulation and test benches to validate functionality and performance.

 3. RTL Synthesis
- Transform RTL code into a gate-level representation using a synthesis tool.
- Maps RTL onto a library of standard cells, optimizing for area, power, and timing.

 4. Technology Mapping
- Map the synthesized gate-level netlist to the target technology library.
- Replace generic gates with technology-specific counterparts (e.g., NAND, NOR, XOR).

 5. Physical Design
- Transform the gate-level netlist into a manufacturable physical layout.
  a. **Floorplanning**: Determine the chip's area and organize the placement of major components.
  b. **Placement**: Assign specific gate and flip-flop locations, optimizing for metrics like wire length and performance.
  c. **Clock Tree Synthesis (CTS)**: Create a clock distribution network to ensure uniform clock signals with minimal skew.
  d. **Routing**: Establish physical interconnections using metal and polysilicon layers. Includes global and detailed routing.
  e. **Physical Verification**: Check layout against design rules, including timing, power, signal, and rule violations.
 6. GDS Generation
- Generate the GDS (Graphic Data System) file.
- This binary file format represents the complete chip layout, including geometric details and interconnections.

7.Signoff
- Encompasses verification and validation steps.

The RTL to GDS flow is a critical process in chip design, ensuring the translation of high-level design into a manufacturable physical layout.















### Key Components Needed for ASIC Development


To develop an ASIC efficiently, you need three key components:

1. **RTL IPs**: Source from platforms like GitHub, OpenCores, and LibreCores for pre-designed RTL blocks.

2. **PDK Data**: Process Design Kit (PDK) data is needed to get the Design Fabricated.

3. **EDA Tools**: Use Electronic Design Automation (EDA) tools for RTL synthesis, layout design, and verification.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/5be0a2b3-31d8-4428-a67c-f369305f4c64" alt="Image" width="600">
</p>






## Why Open-Source Tools for ASIC Development?

The hope for open-source ASIC flows like OpenLane is to provide multiple benefits:

- **Innovation Unleashed**: They empower you to explore unconventional approaches and foster creativity in ASIC design.

- **Vertical Integration**: These tools expand your capabilities for seamless integration, giving you greater control over your projects.

- **AI and Software-Driven Workflows**: Open source tools promote AI-assisted, software-driven workflows, making ASIC development more intelligent and efficient.

- **Cost-Efficient Scalability**: Harness the limitless scalability of the cloud without being burdened by licensing costs. Your potential knows no bounds.




# About OpenLane 

OpenLane is an open-source automated toolchain for designing Application-Specific Integrated Circuits (ASICs) from RTL (Register-Transfer Level) to GDSII (Graphic Data System II) layout. It streamlines the ASIC design process by integrating various open-source tools, allowing for efficient chip development and tape-out without human intervention.


### OpenLane Integrated Tools
OpenLane flow consists of several stages. By default, all flow steps are run in sequence. Each stage may consist of multiple sub-stages. OpenLane can also be run interactively.

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

OpenLane integrated several key open-source tools over the execution stages:

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

# DAY 1: OpenLane and SKYWATER-130 
The Skywater PDK files we are working with are described under ```pdks```


1. **SKYWATER-PDK**: This directory contains essential PDK files provided by the foundry, serving as the foundation for ASIC development.

2. **Open_pdks**: In this directory, you'll find scripts that bridge closed-source and open-source PDKs, ensuring compatibility with various Electronic Design Automation (EDA) tools. These scripts facilitate seamless integration.

3. **Sky130A**: Specifically tailored for Skywater, this directory houses open-source-compatible PDK files. They are designed to work harmoniously with open-source EDA tools, empowering users to develop ASICs without reliance on proprietary software.


![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e5ad6085-ab88-42a8-9da5-e378b0f8d73b)

---
All the designs, we are going to use in this lab are present under the design directory :

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/d4c8f8c4-0c0e-4435-bbe9-3fbe58978d02)

---


### Design Folder Hierarchy :



In each design hierarchy, you will find two distinct components:

1. **Src Folder**: This directory contains Verilog files (`.v`) and SDC (Synopsys Design Constraints) files (`.sdc`). Verilog files describe the digital logic of your design, while SDC files specify timing constraints for your design.

2. **Config.tcl Files**: These are design-specific configuration files used by OpenLANE. They include switches and settings that tailor the ASIC design flow for your specific project. 

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ac2dc627-8ced-4a78-ab35-d65b6744edd4)

here is the comparsion between ```config.tcl``` and ```sky130A_sky130_fd_sc_hd_congfig.tcl```

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/cc021a4b-9ce4-4820-9a61-c2bdf1d1a8a7)


## Hands-on OpenLane Flow :

### Setting Up OpenLane

1. Navigate to the OpenLane directory in your terminal.

2. Type the following command:
OpenLane provides the flexibility to run the entire flow in one go or to use an interactive mode for a more detailed step-by-step process 

```
./flow.tcl -interactive
 ```



3. Software Dependencies for OpenLane

To ensure that OpenLane functions correctly, you need to manage software dependencies. You can import these dependencies into the OpenLane tool by using the following command:

```
package require openlane 0.9
```

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/03f058c6-071a-4d14-94fb-214a39747cec)




4. Preparing the Design in OpenLane

In OpenLane, the "prep" step is crucial for setting up the file structure and merging essential technology and cell information.

+ **File Structure Setup**: Create a structured directory in your project's design folder. 

+ **Configurations**: The "config.tcl" file generated in this folder contains critical parameters used by OpenLane for your specific run. These configurations tailor the OpenLane flow to your design.

+ **Merging Technology and Cell Data**: The command merges essential technology LEF data, which includes layer definitions and design rules needed for Place-and-Route (PnR). Additionally, it combines cell LEF data, reducing Design Rule Check (DRC) errors during the PnR process.

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/c9661546-4ddd-43e7-a871-3e3bbfac5d34)




Prepare design command :
```
prep -design <design_name> -tag <tag>

```


After running the ```prep``` command, you'll find a well-structured project directory with all the necessary information and configurations, ready for the OpenLane flow.


![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/aca81212-fdd9-414e-a450-ce1715793378)



### Synthesis 


To access the reports generated during the synthesis step in OpenLane, navigate to the following directory: ```runs/workshop/report```


Inside this directory, you'll find various reports specific to the tools used in the synthesis process. These reports provide detailed insights and analysis of your design at this stage.


![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ed942b85-817c-4ad4-b0c0-84a1bff79b9d)




**Fixing Timing Violation:**

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ce558ea3-a100-4a9a-b4ef-97cb0f608d52)




In the timing report, if you encounter a slack violation (e.g., -24.89), it indicates that the delay in the critical path is causing an increase in arrival time. To resolve this issue, you can adjust the required time by changing the clock (CLK) period in the `config.tcl` file for your design.

- Slack Violation Formula: `slack = Required time - Arrival time`

By modifying the CLK period, you can effectively manage the timing constraints and address slack violations in your OpenLane project.

how setting the CLK Period: 55 slack violation was reduced to 0 

Note : Reducing Slack Violation is an iterative process 





