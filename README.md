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

