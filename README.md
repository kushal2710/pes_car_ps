# pes_car_ps
 car parking system using a finite state machine (FSM). The system has inputs for sensors at the entrance and exit of the parking lot, as well as a password input consisting of two bits each. It controls two LEDs (a green one and a red one) to indicate the system's state, and it also displays characters on two 7-segment displays (HEX_1 and HEX_2) to show information. this Verilog code describes a car parking system with different states and transitions controlled by sensors and a password input. It also controls LEDs and 7-segment displays to provide visual feedback on the system's state. The behavior of the system is defined by the state machine logic and the conditions specified in the code.
 ### Simulation
```
iverilog pes_car_ps.v pes_car_ps_tb.v
./a.out
gtkwave pes_car_ps_tb.vcd
or gtkwave dump.vcd

```
![gtkwave-1](https://github.com/kushal2710/pes_car_ps/assets/115935208/2f5ee174-e9fb-49e0-b93a-e3c103bcaf35)

### Synthesis
```

read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog pes_car_ps.v
synth -top pescarps
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```

![synth-1](https://github.com/kushal2710/pes_car_ps/assets/115935208/8a04cf65-20af-44b1-a782-153d28430125)

![synth-2](https://github.com/kushal2710/pes_car_ps/assets/115935208/a55e53dd-4913-4c97-a1a7-c5a27e31ad39)

### Gate-Level Simulation
```
iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v pes_car_ps_netlist.v pes_car_ps_tb.v
./a.out
gtkwave pes_car_ps_tb.vcd
or gtkwave dump.vcd
```

![gtkwave-3](https://github.com/kushal2710/pes_car_ps/assets/115935208/a666b62b-1f97-4435-9891-c91b3ca733ce)

## Stage 2 (RTL2GDSII - OPENLANE) - Table of contents

<details>
<summary>Introduction to Openlane ASIC Design Flow</summary>
<br>

![Screenshot from 2023-11-02 17-26-22](https://github.com/kushal2710/pes_car_ps/assets/115935208/2129ab4d-3af1-44dc-a5a1-d98aeeb8bc2a)

#### Design Stages

1) **Synthesis**
   1. **yosys** - Yosys performs RTL synthesis, converting high-level RTL descriptions into gate-level netlists.
   2. **abc** - ABC is used for further optimization and technology mapping to enhance the gate-level design.
   3. **OpenSTA** - OpenSTA conducts static timing analysis to verify if the synthesized design meets timing constraints in the OpenLane flow.

2) **Floorplan & PND**
   1. **init_fp (Initial Floorplan)** - Floorplanning involves determining the initial placement and arrangement of various functional blocks or cells within the chip's       
   layout area.
   2. **ioplacer** - ioplacer is a tool used in the physical design process to place Input/Output (I/O) pads or pins on the chip's boundary.
   3. **pdn** - The PDN is responsible for distributing power (supply voltage) and ground (reference voltage) throughout the chip, ensuring that all components receive the       necessary power supply and maintain stable electrical operation.
   4. **tapcell** - A "tapcell" is a special type of cell used in digital integrated circuit design, particularly in standard cell libraries.It is typically used to create 
   tap connections for the bulk terminals in digital CMOS (Complementary Metal-Oxide-Semiconductor) designs.

3) **Placement**
   1. **Replace** - RePlace is a tool used in the OpenLane flow for cell placement optimization.It focuses on optimizing the placement of standard cells within the chip's   
   layout to achieve better area utilization, timing, and power efficiency.
   2. **Resizer** - Resizer is a tool employed during the physical design process to perform cell resizing and optimization.
   3. **OpenDP (Open Detailed Placement)** - OpenDP, or Open Detailed Placement, is a detailed placement tool used in OpenLane.It is responsible for the fine-grained 
   placement of cells, ensuring that they are precisely positioned within rows and tracks while adhering to design constraints and achieving optimal utilization of the chip's 
   layout area.
   4. **OpenPhysyn (Open Physical Synthesis)** - OpenPhysyn is a tool within OpenLane that performs physical synthesis tasks.It optimizes the logical and physical aspects of 
   the design simultaneously, improving the placement, power, area, and timing by considering both logic and physical information during the optimization process.

4) **CTS**
   1. **TritonCTS** - TritonCTS generates a clock distribution network.

5) **Routing**
   1. **FastRoute** - FastRoute is a global routing tool used in the physical design stage of ASIC chip design.
   2. **TritonRoute** - TritonRoute is a detailed or global routing tool used in the later stages of ASIC chip design, following placement and initial global routing.
   
6) **GDSII Generation**
   1. **Magic** - Magic is primarily a layout tool used for creating and editing IC layouts, and it is often used for digital CMOS design.
   2. **KLayout** - KLayout is primarily used for viewing, editing, and analyzing IC layouts but is not a layout creation tool like Magic.
   
8) **Checks**
   1. **CVC** - CVC is a tool primarily used for verification and debugging of digital designs.
   2. **Netgen** - Netgen is an open-source digital netlist comparison and LVS (Layout vs. Schematic) tool.

[Back to Stage-2](#Stage-2)

</details>

<details>
<summary>Creating folder and adding files</summary>
<br>

Create a new folder within OpenLane with the same name as your design file `pes_car_ps`.

Note `pes_car_ps` folder should have [config.json]  `pes_car_ps.v` and the `src` folder.

Make sure `src` folder should have these [Files]

The `pdks` folder must have this [File]




