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

4. [Overview of RTL to GDS Flow](#overview-of-rtl-to-gds-flow)
5. [About OpenLane](#about-openlane)
   + [OpenLane Integrated Tools](#openlane-integrated-tools)
   + [OpenLane Output](#openlane-output)
6. [DAY 1: OpenLane and SKYWATER-130](#day-1-openlane-and-skywater-130)
   + [Setting Up OpenLane](#setting-up-openlane)
   + [Synthesis](#synthesis)

7. [Day 2: Floorplanning](#day-2-floorplanning)
   + [Floorplan using OpenLane](#floorplan-using-openlane)
   + [Viewing Floorplan in Magic](#viewing-floorplan-in-magic)

   + [Placement in Chip Design](#placement-in-chip-design)
   + [Viewing Placement in Magic](#viewing-placement-in-magic)

   + [Standard Cell Design and Characterization](#standard-cell-design-and-characterization)
   + [Cell Design Flow](#cell-design-flow)
   + [Design Steps](#design-steps)
   + [Characterization Flow](#characterization-flow)

8. [Day 3: Design of Cell Library](#day-3-design-of-cell-library)
   + [SPICE Deck Creation & Simulation](#spice-deck-creation-and-simulation)
   + [SPICE Simulation Using Ngspice](#spice-simulation-using-ngspice)
   + [SPICE Deck for Transient Analysis](#spice-deck-for-transient-analysis)
   + [Fabrication Process for a CMOS Inverter](#fabrication-process-for-a-cmos-inverter)
   + [Final Structure](#final-structure)
   + [Introduction to Magic Tool Options and DRC Rules](#introduction-to-magic-tool-options-and-drc-rules)
   + [SkyWater SKY130 PDK](#skywater-sky130-pdk)
   + [Layout Designing using Magic](#layout-designing-using-magic)

9. [DAY 4: LEF Extraction and Standard Cell Guidelines](#day-4-lef-extraction-and-standard-cell-guidelines)
   + [LEF Extraction and Standard Cell Guidelines](#lef-extraction-and-standard-cell-guidelines)
   + [Including Custom Cells in OpenLANE](#including-custom-cells-in-openlane)
   + [Optimizing Timing Constraints in VLSI Design](#optimizing-timing-constraints-in-vlsi-design)
   + [Clock Tree Synthesis (CTS) and Post-CTS STA Analysis](#clock-tree-synthesis-cts-and-post-cts-sta-analysis)
   + [Fine-Tuning Post CTS-STA Analysis](#fine-tuning-post-cts-sta-analysis)

10. [Day 5: Power Distribution Network, Routing, and SPEF Extraction](#day-5-power-distribution-network-routing-and-spef-extraction)
   + [Power Distribution Network (PDN) Generation](#power-distribution-network-pdn-generation)
   + [Routing in Two Stages](#routing-in-two-stages)
   + [Initiating Routing with OpenLANE](#initiating-routing-with-openlane)
   + [SPEF Extraction for Parasitic Information](#spef-extraction-for-parasitic-information)




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





---

## Why do we need a Chip?

Consider the Arduino Uno, a versatile development board used for various projects. At its core lies the ATmega328P microcontroller, a crucial component. 

**Here's why we need this chip:**
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




---

# Overview of RTL to GDS Flow:




<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/cd68124d-2274-4a3f-8ae3-6e868245f64f" alt="Image" width="600">
</p>


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
 + a. **Floorplanning**: Determine the chip's area and organize the placement of major components.
 + b. **Placement**: Assign specific gate and flip-flop locations, optimizing for metrics like wire length and performance.
 + c. **Clock Tree Synthesis (CTS)**: Create a clock distribution network to ensure uniform clock signals with minimal skew.
 + d. **Routing**: Establish physical interconnections using metal and polysilicon layers. Includes global and detailed routing.
 + e. **Physical Verification**: Check layout against design rules, including timing, power, signal, and rule violations.
  6. GDS Generation
- Generate the GDS (Graphic Data System) file.
- This binary file format represents the complete chip layout, including geometric details and interconnections.

7. Signoff
- Encompasses verification and validation steps.

The RTL to GDS flow is a critical process in chip design, ensuring the translation of high-level design into a manufacturable physical layout.













---

### Key Components Needed for ASIC Development


To develop an ASIC efficiently, you need three key components:

1. **RTL IPs**: Source from platforms like GitHub, OpenCores, and LibreCores for pre-designed RTL blocks.

2. **PDK Data**: Process Design Kit (PDK) data is needed to get the Design Fabricated.

3. **EDA Tools**: Use Electronic Design Automation (EDA) tools for RTL synthesis, layout design, and verification.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/9e49ecfe-b9d1-4695-8b84-d56565633d1e" alt="Image" width="600">
</p>




---

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

![image](https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e773cf4e-5e90-4458-a05d-35c64b858a84)





1. Synthesis

- **yosys/abc**: Perform RTL synthesis and technology mapping.
- **OpenSTA**: Performs static timing analysis on the resulting netlist to generate timing reports.

2. Floorplanning

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
- **KLayout**: Streams out the final GDSII layout file from the routed def as a backup.

7. Signoff

- **Magic**: Performs DRC Checks & Antenna Checks.
- **KLayout**: Performs DRC Checks.
- **Netgen**: Performs LVS Checks.
- **CVC**: Performs Circuit Validity Checks.

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



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e5ad6085-ab88-42a8-9da5-e378b0f8d73b" alt="Image" width="900">
</p>



---
All the designs, we are going to use in this lab are present under the design directory :


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/7d8e18ed-4d2f-4a3f-96ba-bb8acc55e60a" alt="Image" width="900">
</p>




---


### Design Folder Hierarchy :



In each design hierarchy, you will find two distinct components:

1. **Src Folder**: This directory contains Verilog files (`.v`) and SDC (Synopsys Design Constraints) files (`.sdc`). Verilog files describe the digital logic of your design, while SDC files specify timing constraints for your design.

2. **Config.tcl Files**: These are design-specific configuration files used by OpenLANE. They include switches and settings that tailor the ASIC design flow for your specific project. 



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/2a114436-5f3c-467d-8644-27ac0f955faf" alt="Image" width="900">
</p>





here is the comparsion between ```config.tcl``` and ```sky130A_sky130_fd_sc_hd_congfig.tcl```


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/2b5b7b54-1cdc-4fcd-ace3-de1ff7792124" alt="Image" width="900">
</p>






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


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/03f058c6-071a-4d14-94fb-214a39747cec" alt="Image" width="900">
</p>






4. Preparing the Design in OpenLane

In OpenLane, the "prep" step is crucial for setting up the file structure and merging essential technology and cell information.

+ **File Structure Setup**: Create a structured directory in your project's design folder. 

+ **Configurations**: The "config.tcl" file generated in this folder contains critical parameters used by OpenLane for your specific run. These configurations tailor the OpenLane flow to your design.

+ **Merging Technology and Cell Data**: The command merges essential technology LEF data, which includes layer definitions and design rules needed for Place-and-Route (PnR). Additionally, it combines cell LEF data, reducing Design Rule Check (DRC) errors during the PnR process.


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/059d8a39-f5fe-4a0a-a3aa-640985ccb858" alt="Image" width="900">
</p>






Prepare design command :
```
prep -design <design_name> -tag <tag>

```


After running the ```prep``` command, you'll find a well-structured project directory with all the necessary information and configurations, ready for the OpenLane flow.




<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/eb50acff-e559-4cd1-9b18-98f1ec428af6" alt="Image" width="900">
</p>



## Synthesis 


To access the reports generated during the synthesis step in OpenLane, navigate to the following directory: ```runs/workshop/report```


Inside this directory, you'll find various reports specific to the tools used in the synthesis process. These reports provide detailed insights and analysis of your design at this stage.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/0e8ff9c5-a00c-4587-ad08-653e0a867ae1" alt="Image" width="900">
</p>





**Fixing Timing Violation:**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/86f8a1c4-8380-42ef-bb58-07911ea0061b" alt="Image" width="900">
</p>



In the timing report, if you encounter a slack violation (e.g., -24.89), it indicates that the delay in the critical path is causing an increase in arrival time. To resolve this issue, you can adjust the required time by changing the clock (CLK) period in the `config.tcl` file for your design.

- Slack Violation Formula: `slack = Required time - Arrival time`

By modifying the CLK period, you can effectively manage the timing constraints and address slack violations in your OpenLane project.


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/14c3bf7d-e5d1-43d5-9351-86522e734bd8" alt="Image" width="900">
</p>



now setting the CLK Period to 55, the slack violation was reduced to 0. 

**Note: Reducing Slack Violations is an iterative process**


Results at the end of the synthesis process: 
1. Optimized RTL
2. Technology mapped netlist 
3. Estimated approx core area/gate count 
4. Operating frequency and respective timing reports


a snap of the netlist : 


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/1abe69c2-91ae-412f-8d50-c483334b2fe4" alt="Image" width="900">
</p>


# Day 2: Floorplanning


Floorplanning is a critical phase in chip design that establishes the initial chip layout and organization, ensuring efficient use of resources and meeting design goals.
In the Floorplanning phase, the following key actions are typically performed:

1. **Die Area**: Define the total area of the chip's semiconductor material.

2. **Core Area**: Specify the area within the die that contains the primary logic and functional components.

3. **Core Utilization**: Determine the utilization factor, representing the ratio of the area occupied by the netlist to the core area (usually 50%-70%).

4. **Aspect Ratio**: Establish the aspect ratio, which is the ratio of height to width (1 for square, other values for rectangles).

5. **Place Macros**: Arrange pre-designed macros such as memories, clock gating cells, comparators, muxes, etc., within the core area.

6. **Power Distribution Network**: Set up the power distribution network, which may include power straps and taps (although this is sometimes done later in tools like OpenLANE).

7. **Place Input and Output Pins**: Determine the locations for input and output pins, optimizing for signal integrity, power consumption, and timing considerations.



---

## Key Aspects of Floorplanning in Chip Design


### 1. Utilization Factor and Aspect Ratio

- **Utilization Factor**: This represents the amount of die core area occupied by standard cells. It's typically maintained within the range of 50%-70% (utilization factor of 0.5-0.7). This range ensures optimal placement and feasible routing within the chip, promoting efficient use of resources.

- **Aspect Ratio**: The aspect ratio defines the shape of the chip and is calculated by dividing the height of the core area by its width. An aspect ratio of 1 indicates a square chip. Aspect ratio choices influence the chip's physical dimensions and layout.

### 2. Preplaced Cells (MACROs)

- Preplaced cells, often referred to as MACROs, play a crucial role in enabling hierarchical chip design. They allow VLSI engineers to modularize larger designs. In floorplanning, preplaced cells are assigned specific locations within the core area. Blockages are also defined to ensure that standard cells are not placed in the preplaced cell regions.

### 3. Decoupling Capacitors

- Decoupling capacitors are strategically placed near preplaced cells during Floorplanning. They address voltage drops caused by interconnecting wires, which can disrupt noise margins or induce an indeterminate state in circuits. These capacitors charge up to the power supply voltage over time and act as reservoirs of charge. When the circuit requires a transition, they supply the needed charge, effectively decoupling the circuit from the main power supply and stabilizing operation.

### 4. Power Planning

- Power planning is a vital aspect of Floorplanning aimed at reducing noise in digital circuits due to voltage droop and ground bounce. Coupling capacitance forms between interconnect wires and the substrate. During transitions on a net, the charge associated with coupling capacitors may be dumped to the ground. Sufficient ground taps and a robust power distribution network (PDN) with multiple power strap taps are essential to lower resistance, maintain ground voltage stability, and enhance noise margins.

### 5. Pin Placement

- Pin placement optimization is crucial for minimizing buffering, improving power efficiency, and managing timing delays. It involves determining the specific locations along the I/O ring where pins should be placed, guided by the connectivity information of the HDL netlist. Well-optimized pin placement can reduce buffering requirements and subsequently lower power consumption. Blockages are often introduced to distinguish between the core and I/O areas, ensuring proper isolation.

---


## Floorplan using OpenLane 

OpenLane has many commands that can used to customize Floorplan design. A compressive list of those commands can be found in the ```openlane/configuration/readme``` file. 


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/3ca5e353-9a40-484c-805a-e165454be0f4" alt="Image" width="900">
</p>




To get a details list of commands head over to OpenLane docs [here](https://openlane.readthedocs.io/en/latest/reference/openlane_commands.html#floorplan-commands)



we initiate the Floorplan in OpenLane using the command 
```
run_floorplan
```
we can see the following message on successful floorplan execution :




<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/3d305975-d598-45b7-b9d2-8844c3968b5b" alt="Image" width="900">
</p>


### Viewing Floorplan in Magic
To view our floorplan in Magic we need to provide three files as input:

1. Magic technology file (sky130A.tech)
2. Def file of floorplan
3. Merged LEF file

head over to the following directory to view the results of floorplan using Magic : 
```
cd /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/run_1/results/floorplan
```
To invoke magic use the command :
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

Magic has the following GUI interface and a console window to execute commands



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/222ada54-011b-4976-a0cb-67ea64734587" alt="Image" width="600">
</p>

if we zoom in a little we can see that some of the micro, IO pad, and tap-cells have been placed appropriately. 

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/22d9ebfe-e9c2-46d4-b2bf-edfce70a3f00" alt="Image" width="600">
</p>


---

## Placement in Chip Design

### 1. Netlist Binding

Netlist binding is the process of mapping the logical representation of a digital design onto standard cell shapes from a library. Each component in the netlist is mapped to a specific shape defined in the library.

### 2. Initial Placement Design

In this phase, components from the netlist are placed within the chip's core area. Key considerations include:

1. **Proximity to Pins**: Components are strategically placed based on their distance from input and output pins to minimize signal delays.

2. **Signal Optimization**: Signals requiring rapid propagation, such as FF1 to FF2, are placed close together. Buffer cells may be added for signal integrity.

3. **Wire-Length and Capacitance Estimation**: Wire length and capacitance estimates guide placement optimization, factoring in signal delay, power consumption, and integrity.

### 3. Final Placement Optimization

The final placement phase fine-tunes the component layout within the chip, optimizing for performance. It assumes an ideal clock and aims to minimize signal delays, conserve power, and meet design constraints.



---

The next step in the Digital ASIC design flow after floorplanning is placement. The synthesized netlist has been mapped to standard cells and the floorplanning phase has determined the standard cells rows, enabling placement. OpenLane does placement in two stages:

1. **Global Placement** - Optimized but not legal placement. Optimization works to reduce wirelength by reducing half parameter wirelength
2. **Detailed Placement** - Legalizes placement of cells into standard cell rows while adhering to global placement

To do a placement in OpenLane:
```
run_placement
```

For placement to converge the overflow value needs to be converging to 0. At the end of placement cell legalization will be reported:


### Viewing Placement in Magic
To view placement in Magic the command mirrors viewing floorplanning, go to the results/floorplan directory and use the command:
```
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/410ff07d-c7b5-48ad-8452-e32920659ec4" alt="Image" width="600">
</p>



zoomed view of the core with all the standard cells placed in between power can ground rail 

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/3f6eff27-45f2-4dab-bfec-6c3306c65162" alt="Image" width="600">
</p>

---






## Standard Cell Design and Characterization :



Libraries and characterization are fundamental pillars in the IC design process. Libraries offer standardized building blocks that enhance design efficiency and reusability. Characterization, on the other hand, provides critical data for accurately modeling and simulating component behavior. This ensures that the final design aligns with performance, power, and reliability objectives.


Standard cell library contains a description of different variety of cells 


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/4a5f81a6-4e04-4b3a-89f7-026e680881fb)" alt="Image" width="600">
</p>



### Cell design flow : 



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/0bc7fd70-b7cc-488f-8996-7bdc3ce43b86" alt="Image" width="400">
</p>


---
### 1. Inputs

**PDK and spice models**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/855541eb-9323-4666-a719-c8e8ba1d83ea alt="Image" width="600">
</p>


---

**User-Defined parameters**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/b0fec785-7f8f-4e2c-9371-e84bd4f4b666 alt="Image" width="600">
</p>

---

### 2. Design steps 

**Circuit Design**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/bd0464ee-57a8-46e8-8a55-9d17b6cca1d7" alt="Image" width="600">
</p>



---

**Layout Design**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e9b8419a-fe76-4fbe-846d-136b1586085d" alt="Image" width="600">
</p>

![Screenshot 2023-09-17 200713]()

---


### 3.Characterization Flow

To perform characterzation  [GUNA tool](https://www.paripath.com/Products/Guna)  is used : 



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e9b8419a-fe76-4fbe-846d-136b1586085d" alt="Image" width="600">
</p>


---

Additionally, we need to define the timing definition such as :


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/9f0e77dd-ba2a-4d23-a44d-0deac2af57e9" alt="Image" width="600">
</p>


---

# Day 3: Design of Cell Library

## SPICE Deck Creation & Simulation

A SPICE deck is a crucial component in the IC design process, containing essential information for circuit simulation. Below, we describe a sample SPICE deck for a PMOS and NMOS transistor circuit, along with steps for simulation using Ngspice.

### SPICE Deck Components

1. **Model Descriptions**: Defines the characteristics of components in the circuit.
2. **Netlist Description**: Lists the circuit's components, connections, and values.
3. **Simulation Type and Parameters**: Specifies the type of simulation and its parameters.
4. **Libraries Included**: Links external libraries with component models.

### Sample SPICE Deck

```spice
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***

M1 out in vdd vdd pmos W=0.375u L=0.25u   ; PMOS transistor M1 with width (W) of 0.375u and length (L) of 0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u   ; NMOS transistor M2 with width (W) of 0.375u and length (L) of 0.25u

cload out 0 10f   ; Capacitor load (cload) connected between node 'out' and ground (0) with a value of 10 femtofarads (10f)

Vdd vdd 0 2.5   ; Voltage source Vdd connected between node 'vdd' and ground (0) with a voltage of 2.5 volts
Vin in 0 2.5   ; Voltage source Vin connected between node 'in' and ground (0) with a voltage of 2.5 volts

*** SIMULATION Commands ***

.op   ; Perform a DC operating point analysis

.dc Vin 0 2.5 0.05   ; Perform a DC sweep of Vin from 0 to 2.5 volts in steps of 0.05 volts

*** include tsmc_025um_model.mod ***   ; Include the model file 'tsmc_025um_model.mod'

.LIB "tsmc_025um_models.mod" CMOS_MODELS   ; Link the library 'tsmc_025um_models.mod' and define it as 'CMOS_MODELS'

.end   ; End of the SPICE netlist

```



## SPICE Simulation Using Ngspice

Follow these steps for simulation:

1. Source the circuit file in Ngspice using `source <file_name>.cir`.
2. Execute the simulations using the `run` command.
3. Use `setplot` to prepare for plotting.
4. For DC analysis (as indicated in the .cir file), use `dc1` to prepare the DC plot.
5. Display available vectors using `display`.
6. Plot specific vectors, e.g., `plot vout vs vin`, to visualize the circuit behavior.


## SPICE Simulation using Ngspice


Follow these steps for SPICE simulation:

Source the circuit file in Ngspice using the command: source <file_name>.cir

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e56b25fd-a645-4417-816c-0e60ef2144fa" alt="Source Circuit File" width="600">
</p>
Once the .cir file is loaded, execute the simulations by typing: run

To prepare for plotting, use the setplot command.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/fd6b1c68-b60a-4843-b656-1b0ad3c9cc0d" alt="Set Plot" width="600">
</p>


Since we are performing a DC analysis, use dc1 to prepare the DC plot.

To see all the available vectors for plotting, type: display

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/6b0229ef-7cea-4dea-b35e-6f185ffda868" alt="Display Vectors" width="600">
</p>

To plot Vout vs. Vin, use the command: plot vout vs vin

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/79eec2df-f932-4ab0-ad3d-4a07f43852e" width="600">
</p>


To obtain a symmetric DC plot, you can scale the aspect ratio of PMOS by 2.5 times.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/8d55b2de-6ec6-4083-92e4-23daf21c1c22" alt="Symmetric DC Plot" width="600">
</p>



The Vin = Vout point is crucial as it indicates when both transistors are active, leading to peak power consumption.

<p align="center">
  <img src="(https://github.com/VardhanSuroshi/pes_pd/assets/132068498/c842b8d6-fa87-4a66-ae3c-713f3b5c2b1b" alt="Vin = Vout Point" width="600">
</p>

You can vary the CMOS inverter threshold value to make it symmetric and robust.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/72954c80-a83f-4262-b512-c4dc5842d6a5" alt="Threshold Variation" width="600">
</p>

These steps guide you through the SPICE simulation process using Ngspice, enabling you to visualize and analyze the behavior of your circuit.





The symmetric DC plot can be achieved by adjusting the PMOS aspect ratio.


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/2dda74a3-3575-466b-900c-6ef343277a57" alt="Threshold Variation" width="600">
</p>


The Vin = Vout point is crucial, as it signifies when both transistors are active, leading to peak power consumption.





### SPICE Deck for Transient Analysis
For transient analysis, the following SPICE deck can be used:
```
spice
Copy code
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***

M1 out in vdd vdd pmos W=0.375u L=0.25u   ; PMOS transistor M1 with width (W) 0.375u and length (L) 0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u   ; NMOS transistor M2 with width (W) 0.375u and length (L) 0.25u

cload out 0 10f   ; Capacitive load (cload) between node out and ground (0) with a value of 10 femtofarads (10f)

Vdd vdd 0 2.5   ; Voltage source Vdd with a value of 2.5V, connected between node vdd and ground (0)
Vin in 0 0 pulse 0 2.5 0 10p 10p 1n 2n   ; Voltage source Vin with a pulse waveform

*** SIMULATION Commands ***

.op   ; Operating point analysis

.trans 10p 4n   ; Transient analysis from 10 picoseconds to 4 nanoseconds

*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS   ; Include the library file "tsmc_025um_models.mod" for CMOS models

.end   ; End of the SPICE netlist


```


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e6eb8010-bdfc-4d3c-9afd-fbce22f1c338" width="400">
</p>



## Fabrication Process for a CMOS Inverter

Fabrication of CMOS Inverter is a 16-mask process

### 1. Selecting the substrate 

- P-type substrate with resistivity around (5-50 ohm) doping level (10^15 cm^-3) and orientation (100).
- Note that substrate doping should be less than well doping (used to fabricate NMOS and PMOS)

### 2. Create active resistance

This step creates pockets for NMOS and PMOS
1. Grow SiO2(~40nm) on Psub
2. deposit ~80nm Si3N4 on SiO2
3. deposit 1um layer of photoresist(used to define regions)
4. photolithography
5. etch out Si3N4 and SiO2 using a suitable solvent
6. Place the obtained structure in an oxidation furnace due to which field oxide is grown.This process is called ```LOCOS``` that is ```Local oxidation of silicon```
7. Etch out Si3N4 using hot phosphoric acid

### 3.NWel and PWel formation

- Apply photoresist, apply a mask that covers NMOS
- Expose to UV, Wash, remove the mask, and apply boron(p-type) using Ion Implantation at an energy of 200 Kev(for diffusion)
- repeat it for the other half using phosphorous @400Kev because phosphorous is heavier
- Wells have been created but the depth is low. Therefore subject it to high high-temperature furnace which increases the well depth.

### 4. Formation of Gate

- We repeat step 3 but at low energy with a p-type implant as boron @60Kev and an n-type implant as Arsenic.
- Due to this The SiO2 is damaged as the dopants penetrate through it.
- Therefore original SiO2 is etched out using dilute HF solution and regrown to give high-quality oxide(~10 nm thin)
- Finally for the gate to form, apply N-type ion implants for low gate resistance.
- Now mask on small width of Nwell and PWell above SiO2  and perform photolithography
- Gate Formation is Done

### 5. Lightly Doped Drain Formation(LDD Formation)

- On the surface of SiO2 corresponding to NWell, apply photoresist, mask it, and put phosphorous to make N-Implant on p-well(N-)
- Similarly do it for the other side using boron that forms (p-) implant
- This LDD has to be protected from further process
- so, Deposit 0.1um thick SiO2 on the full structure and etch out using plasma anisotropic etching that results in the formation of sidewall spacers.

### 6. Source and Drain Formation

- Mask Nwell structure, deposit arsenic @75KeV that forms an N+ implant on Pwell
- use boron for P+ implant formation on Nwell
- Subject it to high high-temperature furnace that results in the required thickness of N+, P+, N-, and P- implants.

### 7. Steps to form contacts and interconnects

- Etch thin SiO2 oxide in HF solution
- Deposit Titanium of wafer surface using sputtering all over the structure
- Wafer heated at 600-700 degrees in ambient N2 environment for 60 sec that results in low resistance TiSi2 where the gate of both MOS is present.
- At the other places, TiN is formed that's used for local communication
- Etch off TiN on and half around the gate structure of both MOS using RCA Cleaning

### 8. Higher-level metal formation

- On the resulting structure, deposit a thick layer of (1um) SiO2 doped with P/B known as phosphoborosilicate glass
- To make the added surface plain, use CMP (Chemical Metal Polishing)
- For the creation of contact pins, proper holes with contacts have to be made
- This can be done using Al, W, and TiN layer depositions.
- Deposit a layer of Si3N4 that acts as a dielectric to protect the chip.

### 9. Final Structure


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/be303336-1553-4b9a-b8df-885998f5f6d9" alt="Magic Layer Details" width="600">
</p>


# Introduction to Magic Tool Options and DRC Rules

Magic is a venerable VLSI layout tool, written in the 1980s at Berkeley by John Ousterhout, now famous primarily for writing the scripting interpreter language Tcl. Due largely in part to its liberal Berkeley open-source license, magic has remained popular with universities and small companies. The open-source license has allowed VLSI engineers with a bent toward programming to implement clever ideas and help magic stay abreast of fabrication technology. However, it is the well-thought-out core algorithms that lend to magic the greatest part of its popularity. Magic is widely cited as being the easiest tool to use for circuit layout, even for people who ultimately rely on commercial tools for their product design flow.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/e508c52a-9f9a-49f5-9f2d-880c4225dabd" alt="Magic Tool" width="600">
</p>



Download the files required for this lab from:

```
https://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
```

### SkyWater SKY130 PDK

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/5326f145-526e-46ea-9f07-cef5a6d8d028" alt="SKY130 PDK" width="600">
</p>

SKY130 is a mature 180nm-130nm hybrid technology developed by Cypress Semiconductor that has been used for many production parts. SKY130 is now available as a foundry technology through SkyWater Technology Foundry.

The technology is the 8th generation SONOS technology node (130nm).

The technology stack consists of:

- 5 levels of metal (p - penta)
- Inductor or Inductor-Capable (i)
- Poly resistor (r)
- SONOS shrunken cell (s)
- Supports 10V regulated supply (10R)

Details about SKY130 PDK can be found [here](https://skywater-pdk.readthedocs.io/en/main/).

Every design rule has a code that can be used to refer to the documentation.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ff9389e1-e594-49a3-9bb1-73fe5052e46b" alt="Design Rule Codes" width="600">
</p>

Select a particular layer (hover over the layer and click S) and type `drc why` to know what the DRC violation is.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/931a060e-ddd0-406e-928d-c8e16f3eac6e" alt="DRC Violation" width="600">
</p>

To add contact cuts, add `met3` contact by selecting an area and clicking on `m3contact` using the middle mouse button. Then type `cif see VIA2` in Tkcon prompt.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/2c2e9ca1-b828-40a2-9e74-a4d84ecb7ef3" alt="Adding Contact Cuts" width="600">
</p>


Magic techfile is under development and there may be some DRC violations that might not get reflected such violations are marked under incomplete DRC rules. Let's look at an example of a DRC violation and try correcting the rule file to capture the DRC error. Here is a violation 

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/7cc71eac-1ff4-4f41-925b-ce240b86844e" alt="Fixing Errors" width="400">
</p>



here is the description of the violation from the sky130 water PDK documentation under DRC rules : 
<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/98677f46-9550-4d56-a0a2-20b3a277dd6d" alt="Error" width="900">
</p>



To fix the error, open the `sky130A.tech` file using an editor search for `poly.9` and make the changes.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/57b4b982-8648-45ee-b1b9-486f9730974a" alt="Fix Error in sky130A.tech" width="900">
</p>




Now load the `sky130A.tech` file again and type the command `drc check` to reflect the changes made in the tech file. Post-editing the DRC violation will highlight the error

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/98f117d4-8942-4b35-a92b-759f23b704b6" alt="Run DRC Check" width="900">
</p>





# Layout Designing using Magic

Clone the following repository in the openlane directory to build all the dependencies:

```bash
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```

To invoke the layout of the inverter, use the following command:

```bash
magic -T sky130A.tech sky130_inv.mag &
```

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/6e3ec31f-f7a1-4061-acef-c8d27e963d76" alt="Inverter Layout" width="600">
</p>


Hover over the region for which you want more details and select the region by pressing `s`. Then type `what` in the console window to get information about the layer.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/8950b191-3831-403f-b800-43033fce1f59" width="600">
</p>


For a detailed guide on designing the inverter layout from scratch, visit this [repository](https://github.com/nickson-jose/vsdstdcelldesign).

## DRC Checks in Magic

DRC check in Magic happens in real time. Any DRC errors are immediately reflected in the DRC icon on the toolbar.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/f1b02222-95d3-4746-b184-542fea6b9cd6" alt="DRC Checks" width="600">
</p>


Extract Parasitics in Magic:

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/b2e1a688-1246-4058-b573-381c866856db" alt="Extract PEX" width="600">
</p>


This creates a spice deck for simulation with all the parasitics.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/d06563e2-5552-4bb9-81ee-a8dd4132e866" alt="Spice Deck" width="600">
</p>


The above file has details of the inverter netlist, but the sources and their values are not specified. Modify the file as follows:

- The grid size from the layout is 0.01u.
- Specify the library for MOS.
- Create VDD, VSS, Input pulse Va.
- Specify the type of analysis to be done.

Modified SPICE Deck:

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/92010826-fc38-47cc-813c-d6939d9831bc" alt="Modified Spice Deck" width="600">
</p>


To run the spice netlist simulation, use the command on the terminal:

```bash
ngspice sky130_inv.spice
```

Plot the transient analysis using:

```bash
plot y vs time a
```

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/37abeb15-6229-450a-a537-7b54a9509f84" alt="Transient Analysis Zoom" width="600">
</p>


Zoom in on the transient analysis at 1.65V to get timing values.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/1e11a409-2f08-4c89-bd2a-9538786427d1" alt="Transient Analysis Zoom" width="600">
</p>

Click on the desired point, and the terminal will reflect the exact x and y values.

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/fbe99f37-28c7-4c30-a3cd-81d0f922270f" alt="Terminal Values" width="600">
</p>


The results obtained from the graph are :

- Rise time: 0.0395ns
- Fall time: 0.0282ns
- Cell Rise delay: 0.03598ns
- Cell fall delay: 0.0483ns




# DAY 4: 



# LEF Extraction and Standard Cell Guidelines

During the place and route (PnR) process, an abstract view of the GDS files generated by Magic is used. This abstract view contains crucial information such as metal and pin details. This information is formally defined as LEF (Library Exchange Format) and is utilized by the PnR tool for interconnect routing, in conjunction with routing guides generated during the PnR flow.

There are two main types of LEF files that are essential for the PnR process:

1. **Technology LEF**: This file contains information about layers, vias, and restricted Design Rule Check (DRC) rules. It specifies the characteristics of the fabrication process.

2. **Cell LEF**: This file provides an abstract representation of standard cells used in the design. It includes pin information and other essential details.

### Guidelines for Creating Standard Cell Sets

To ensure proper functionality and compatibility with the PnR tool, it's crucial to follow specific guidelines when creating standard cell sets:

1. **Port Placement**: Input and output ports of standard cells must align with the intersection of vertical and horizontal tracks. This alignment ensures that signals can be routed efficiently.

2. **Cell Dimensions**: Standard cell width should be an odd multiple of the track pitch, and the height should be an odd multiple of the vertical track pitch. This adherence to odd multiples helps in grid alignment.

3. **Track Information**: Track information can be found in the `tracks.info` file, typically located at:

   ```
   ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info
   ```

   In this file, the first value indicates the offset, and the second value indicates the pitch along the provided direction. This information is used to set the grid for standard cells.

   

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/8e21ccfd-d70a-4c73-bfd5-8ab8344dd482" alt="Grid Information for Standard Cells" width="600">
</p>




By aligning with these guidelines, you can ensure that your standard cells are compatible with the PnR process. This compatibility allows for efficient routing and successful integration into the overall chip design.

**Before Setting Grid Info:**





<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/9370ddbf-bc26-419d-a13a-a556c1e0eb76" alt="Layout Before Grid Info" width="300">
</p>

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/98b53daf-7321-429a-b472-89481178b587" alt="Layout Before Grid Info" width="300">
</p>

**After Setting Grid Info:**


<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ebbf822d-53d9-49aa-981e-77944726e483" alt="Layout after Grid Info" width="400">
</p>




By reviewing the layout, you can confirm that pins A and Y are appropriately placed at the intersection of X and Y tracks, meeting the first condition. Additionally, the PR boundary adheres to a width of 3 grids and a height of 9 grids, satisfying the second condition.

These guidelines are crucial for a seamless and effective place and route process, ultimately contributing to the successful design of integrated circuits.


## LEF File Generation from Modified Layout

Once you have perfected your layout with the specified grid settings, you can proceed to generate the LEF (Library Exchange Format) file. Here are the steps to save your modified layout and extract the LEF file:

1. **Save the Modified Layout**:
   In the console, type the following command to save the modified layout, which includes the new grid settings:
   ```
   save sky130_vsdinv.mag
   ```
   This command saves the modified layout in the current working directory.

2. **Open the File and Extract LEF**:
   Next, you need to open the saved layout file and extract the LEF information. Use the following command to open the file with the specified technology file:
   ```
   magic -T sky130A.tech sky130_vsdinv.mag
   ```
   Once you have the layout open, access the console within Magic.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/eb6de418-9f1a-4a5b-b1e6-645d1da78690" alt="Layout Before Grid Info" width="600">
</p>




4. **Generate LEF**:
   Inside the console window, type the following command to generate the LEF file:
   ```
   lef write
   ```
   This command instructs Magic to write the layout information into an LEF file.

Following these steps will result in the creation of an LEF file that encapsulates the layout details of your design. This LEF file can then be used for various design and integration purposes in the overall chip design process.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/ea59bcbd-f45f-4c99-bec5-b9411a42aec9" alt="Layout Before Grid Info" width="600">
</p>





## Including Custom Cells in OpenLane

To integrate custom cells into OpenLANE effectively, follow these initial configuration steps:

1. **Characterize New Cell with GUNA:** Ensure your custom cell is fully characterized using GUNA for specified process corners.

2. **Include Cell-Level Liberty File:** Add the cell-level Liberty (`.lib`) file of the custom cell to the top-level Liberty file. This provides timing and functional data to OpenLANE.

3. **Reconfigure Synthesis Switches:** Modify the synthesis switches in `config.tcl` to make OpenLANE aware of the custom cell during synthesis and optimization.



<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/fd1ff26b-bf96-4922-a559-1744989ca9cf" alt="Layout Before Grid Info" width="600">
</p>

  

4. **Overwrite Previous Run:** When running OpenLANE for the project, overwrite any previous runs with the new configuration switches to include the custom cell.

   ```./flow.tcl -design picorv32a -tag run_8 -overwrite```




<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/984fb159-dbf4-445f-b876-b3681fcf8612" alt="Layout Before Grid Info" width="600">
</p>


5. **Check Synthesis Logs:** Review synthesis logs to confirm the successful integration of the custom cell. Address any errors or warnings related to the cell's usage.




<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/3afd50f7-ec48-4f5b-93ad-182af0d8adf3" alt="Layout Before Grid Info" width="600">
</p>


5. Run floorplan and placement to see the new custom design cell being used in the placement stage. Use the following command to run placement 
```
init_floorplan
run_placement
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

<p align="center">
  <img src="https://github.com/VardhanSuroshi/pes_pd/assets/132068498/45a52127-d14f-442f-9334-8d997997fb8d" alt="Layout Before Grid Info" width="600">
</p>




# Optimizing Timing Constraints in VLSI Design

Timing constraints are paramount in VLSI design, and minimizing slack violations is critical to ensure the reliable operation of circuits. Slack violations, typically detected during static timing analysis (STA), manifest as issues like worst negative slack (WNS) and total negative slack (TNS). Let's delve into strategies for effectively managing and reducing slack violations using tools like OpenLANE and OpenSTA:

## Understanding the Challenge

In VLSI design, timing constraints are pivotal to meet performance requirements. Slack violations, such as WNS and TNS, signify that certain paths in the circuit are not meeting their timing criteria. Addressing these issues is essential for ensuring correct circuit operation.

## Strategies for Slack Reduction

To tackle slack violations, consider the following strategies:

### 1. Synthesis Strategy Review

Begin by examining your synthesis strategy in OpenLANE. Optimize it to enhance timing performance. Options like enabling `CELL_SIZING` and configuring `SYNTH_STRATEGY` with parameters like "DELAY 1" can be beneficial in alleviating slack issues.

### 2. Fanout Load Adjustment

High delay paths due to excessive fanout can be optimized by revisiting the synthesis process. Modify parameters such as `SYNTH_MAX_FANOUT` to fine-tune the fanout load. This can lead to significant reductions in slack violations.

### 3. Cell Buffering

Enhance signal drive strength by enabling cell buffering within your design. This approach boosts the performance of critical paths and reduces signal delays.

### 4. Manual Cell Replacement

For in-depth slack reduction, consider manual cell replacement using the OpenSTA tool. Identify nets that are driving numerous outputs and replace the driver cells with larger versions of the same type. This manual optimization can yield substantial improvements in slack.

### 5. Fanout Optimization

Leverage OpenLANE's built-in tools to optimize fanout values across your design. Adjusting fanout settings can help balance signal loads, mitigating delays, and improving overall timing performance.




# Clock Tree Synthesis (CTS) and Post-CTS STA Analysis

In the realm of VLSI design, the intricacies of clock tree synthesis (CTS) and the subsequent static timing analysis (STA) play pivotal roles in ensuring precise circuit performance. Let's delve into how OpenLANE manages these critical processes.

## Clock Tree Synthesis (CTS)

### Addressing Key Concerns
After running the floorplan and standard cell placement in OpenLANE, the next crucial step is to introduce the clock tree for sequential elements within the design. Two primary concerns when generating the clock tree are:

1. **Clock Skew**: This refers to the difference in arrival times of the clock signal for sequential elements across the entire design.

2. **Delta Delay**: It represents the skew introduced through capacitive coupling of the clock tree nets.

### Executing CTS in OpenLANE
To perform clock tree synthesis in OpenLANE, follow these steps:

**Note:** CTS will introduce buffers throughout the clock tree, which will modify our netlist.

## Viewing Post-CTS Netlist
OpenLANE generates a new .def file containing information about your design after CTS is performed. To view this netlist, use the Magic tool:

## Post-CTS STA Analysis
OpenLANE integrates the OpenROAD application, which includes OpenSTA for timing analysis. You can perform STA analysis seamlessly from within OpenLANE by invoking OpenROAD. Here's how:

1. In OpenROAD, timing analysis involves creating a .db database file. This file is generated using the post-CTS LEF and DEF files. To generate the .db files within OpenROAD:

**Note:** Whenever the DEF file changes, recreate the .db file.

2. After .db generation, users can configure tools and then report propagated clock timing analysis.

## Enhancing the Process
After addressing slack violations in the initial synthesis phase, OpenLANE generates a mapped.v file in the synthesis results. However, to maintain consistency with the resolved violations from the pre_sta.conf file, you can write this netlist using `write_verilog` and replace the openlane-generated mapped file (e.g., picorv32a.synthesis.v).

Proceeding with the OpenLANE flow, continue with the following stages:
- run_floorplan
- run_placement
- run_cts

**Note:** The CTS step should have added buffers and modified the netlist.

## Fine-Tuning Post CTS-STA Analysis
OpenLANE seamlessly integrates the OpenROAD application, which, in turn, includes OpenSTA for timing analysis. To perform STA analysis within OpenLANE, invoke OpenROAD and follow these steps:

1. Create a .db database file within OpenROAD:
   - Read the LEF file from the tmp folder of runs.
   - Read the DEF file from the results of CTS.
   - Write the .db file.

2. Read the generated .db file.

3. Read the CTS-generated Verilog file.

4. Read the min and max liberty files.

5. Set the clocks.

6. Generate the necessary reports.

**Note:** The results may not meet the timing due to the usage of min and max liberty files, as OpenROAD does not support multi-corner optimization. Consider using only typical corner libraries.

















# Day 5: Power Distribution Network, Routing, and SPEF Extraction

In the world of VLSI design, establishing an efficient Power Delivery Network (PDN) and optimizing routing are pivotal steps. OpenLANE provides solutions for managing these processes effectively.

## Power Distribution Network (PDN) Generation

The PDN acts as a network of traces and components responsible for distributing power (VDD) effectively and reliably across the integrated circuit (IC). OpenLANE simplifies this process with the following components:

- **Power Ring Global**: This is a continuous metal ring encircling the entire IC core, ensuring uniform distribution of power to the core logic and functional blocks. It minimizes voltage drops, guaranteeing power supply to all core regions.

- **Power Halo Local**: The power halo forms a localized power distribution network around specific preplaced cells or macroblocks. Preplaced cells remain in fixed positions, and the power halo ensures they receive the necessary power connections.

- **Power Straps**: These are metal traces or structures that transport power from the chip's periphery to central regions, reducing the distance power must travel. Power straps maintain consistent power distribution across the entire chip.

- **Power Rails**: Metal lines run vertically or horizontally across the chip, supplying power to standard cells. Power rails ensure that each standard cell receives the required power for proper operation.

## Routing in Two Stages

Routing within OpenLANE is a two-stage process:

1. **Global Routing**: During global routing, routing guides are generated for interconnects on the netlist. These guides define the layers to use and specify where each net will be located on the chip.

2. **Detailed Routing**: In the detailed routing stage, metal traces are meticulously placed across the routing guides to physically implement the interconnects.

## Initiating Routing with OpenLANE

To kickstart the routing process within OpenLANE, simply use the command `run_routing`.

## SPEF Extraction for Parasitic Information

In the semiconductor industry, the Standard Parasitic Exchange Format (SPEF) is a vital file format used to represent parasitic information such as resistance and capacitance. Accurate modeling and extraction of these parasitics are critical for optimizing electronic devices in VLSI design.

To perform SPEF extraction:

1. Navigate to the SPEF Extractor directory using the following command:
   ```
   cd Desktop/work/tools/SPEF_Extractor
   ```

2. Execute the SPEF extraction command, providing paths to the LEF and DEF files:
   ```
   python3 /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/18-09_06-26/tmp/merged.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/18-09_06-26/results/routing/picorv32a.def
   ```

The resulting SPEF file can be found in the directory:
```
/home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/18-09_06-26/results/routing/
```

By following these steps, you ensure precise modeling and extraction of parasitic elements, a crucial aspect of optimizing electronic devices in VLSI design.







