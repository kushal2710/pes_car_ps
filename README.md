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

### RISC-V

<details>
<summary>DAY-3 : Digital Logic with TL-Verilog in Makerchip IDE</summary>
<br>

## Task-1 : Logic Gates
![image](https://github.com/kushal2710/pes_car_ps/assets/115935208/c7c5d152-e613-4aa0-a0ec-088139c8d146)

## Task-2 : Lab - Makerchip platfrom
To use Makerchip IDE, you need to visit makerchip website at http://makerchip.com/ and launch Makerchip IDE To access a specific example.
![ss-26](https://github.com/kushal2710/pes_car_ps/assets/115935208/955645bc-d3be-4948-91ba-e057f00831d2)

###  Load FGPA Multiplier Example
![ss-27](https://github.com/kushal2710/pes_car_ps/assets/115935208/49ade51a-5101-4bce-b93b-43841bf2115e)

## Task-3 : Lab - Combitional logic
#### A) Inverter
![ss-1](https://github.com/kushal2710/pes_car_ps/assets/115935208/a959f1bf-0c7a-4fc8-ba7d-f03a1e71ebb4)
![ss-2](https://github.com/kushal2710/pes_car_ps/assets/115935208/358bdcd0-9157-4aef-ad7a-e9e481a9e0ad)

#### B) XOR Gate
```
$out = ! $in;
$out1 = ($in1 ^ $in2);
```

![ss-3](https://github.com/kushal2710/pes_car_ps/assets/115935208/b3640c01-490c-4db4-911d-64554e9562df)
![ss-4](https://github.com/kushal2710/pes_car_ps/assets/115935208/4c0d9a28-0344-4883-a2c2-d6b79a0d521c)

#### C) Vectors
```
$out[4:0] = $in1[3:0] + $in2[3:0];
```

![ss-5](https://github.com/kushal2710/pes_car_ps/assets/115935208/45067711-3d87-4020-ac4f-a0edd8edcc0d)
![ss-6](https://github.com/kushal2710/pes_car_ps/assets/115935208/f7723b1c-6546-41c7-a839-67e9fdfa0070)

#### D) Mux without vector & with vectors

```
$out = $sel ? $in1 : $in2;
```


![ss-7](https://github.com/kushal2710/pes_car_ps/assets/115935208/6188dc1f-8ea2-41ba-9401-64ee905cb4d3)
![ss-8](https://github.com/kushal2710/pes_car_ps/assets/115935208/cadddaa7-5419-41a8-b36e-eefc66838dcf)

```
$out[7:0] = $sel ? $in1[7:0] : $in2[7:0];
```


![ss-9](https://github.com/kushal2710/pes_car_ps/assets/115935208/9ef34c67-7331-43a9-853c-a01845b884a1)
![ss-10](https://github.com/kushal2710/pes_car_ps/assets/115935208/be037a01-2c6f-4495-ab69-aa4d187a5ee2)

#### E) Simple Claculator
```
$val1[31:0] = $rand1[3:0]; 
$val2[31:0] = $rand2[3:0];
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum);
```

![ss-11](https://github.com/kushal2710/pes_car_ps/assets/115935208/d932c6af-27bb-447e-8094-63d0727c9d8f)
![ss-12](https://github.com/kushal2710/pes_car_ps/assets/115935208/82cf7eef-df2d-4cb4-9ed1-1e3659c84a7d)

## Task-4 : Sequential logic
![ss-28](https://github.com/kushal2710/pes_car_ps/assets/115935208/98ab96b1-6e31-487d-995b-840e5cc44a5c)

#### A) Fibonacci series
```
$fib[31:0] = $reset ? 1 : (>>1$fib + >>2$fib);
```
![ss-13](https://github.com/kushal2710/pes_car_ps/assets/115935208/88a5214d-200b-466a-83bb-8479b0ed55d9)
![ss-14](https://github.com/kushal2710/pes_car_ps/assets/115935208/77460a2a-8101-4d9b-bcff-dba77a9e9675)



#### B) Up-Counter
```
$num[2:0] = $reset ? 0 : (>>1$num + 1); 
```

![ss-15](https://github.com/kushal2710/pes_car_ps/assets/115935208/b7f7e7d0-d35a-4e27-baa3-61f460a55802)
![ss-16](https://github.com/kushal2710/pes_car_ps/assets/115935208/6d1a4f85-bcc4-49d1-891a-55fa6755fa7d)


#### C) Sequential Calculator
```
$val1[31:0] = (>>1$out); 
$val2[31:0] = $rand2[3:0]; 
$sum[31:0] = $val1 + $val2;
$diff[31:0] = $val1 - $val2;
$prod[31:0] = $val1 * $val2;
$qut[31:0] = $val1 / $val2;
$out[31:0] = $op[1] ? ($op[0] ? $qut: $prod): ($op [0] ? $diff: $sum);
```
![ss-17](https://github.com/kushal2710/pes_car_ps/assets/115935208/04e03888-142f-4d6b-b289-54aac42d5729)
![ss-18](https://github.com/kushal2710/pes_car_ps/assets/115935208/1e306999-4701-4122-881d-d4a125b0e0e2)

## Task-5 : Pipelined logic
### A) A simple pipeline through Pythagorean example
```
`include "sqrt32.v"
|calc
      @1
         $aa_sq[31:0] = $aa[3:0] * $aa;
         $bb_sq[31:0] = $bb[3:0] * $bb;
      @2
         $cc_sq[31:0] = $aa_sq + $bb_sq;
      @3
         $cc[31:0] = sqrt($cc_sq);
```
![ss-19](https://github.com/kushal2710/pes_car_ps/assets/115935208/b09d3943-b6da-4e37-8d93-22200c0ebd8d)
![ss-20](https://github.com/kushal2710/pes_car_ps/assets/115935208/f7c22ee1-45d9-4731-9aa6-0f68c2efc6a0)


#### B) Pipeline Implementation
```
|comp
      @1
         $err1 = $bad_input || $illegal_op;
      @2
         $err2 = $err1 || $over_flow;
      @3
         $err3 = $div_by_zero || $err2;
```
![ss-21](https://github.com/kushal2710/pes_car_ps/assets/115935208/a8a101ec-3f1e-464b-beb5-1fd2da857a2f)
![ss-22](https://github.com/kushal2710/pes_car_ps/assets/115935208/442b790d-665e-4dd8-b442-8558aaf9bfa6)

## Task-6 : Validity
#### A) 2 cycle calculator with validity
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $out [31:0] = $reset ? 32'b0 :
                      ($op[1:0] == 2'b00) ? $sum :
                      ($op[1:0] == 2'b01) ? $diff :
                      ($op[1:0] == 2'b10) ? $prod :
                                              $qut ;
```
![ss-23](https://github.com/kushal2710/pes_car_ps/assets/115935208/9488fdcc-b9be-4a2f-a62a-22349c8fdcb1)
![ss-24](https://github.com/kushal2710/pes_car_ps/assets/115935208/6b7cb6fa-33ee-4b24-b664-5b416d41fd77)

#### B) Distance Calculator
```
|calc
      @1
         $reset = *reset;
         
      ?$valid
         @1
            $aa_sq[31:0] = $aa[3:0] * $aa;
            $bb_sq[31:0] = $bb[3:0] * $bb;;
         @2
            $cc_sq[31:0] = $aa_sq + $bb_sq;;
         @3
            $cc[31:0] = sqrt($cc_sq);
      @4
         $total_distance[63:0] =
            $reset ? 0 :
            $valid ? >>1$total_distance + $cc :
                     >>1$total_distance;
```

![ss-29](https://github.com/kushal2710/pes_car_ps/assets/115935208/8e967a52-5c6e-42ec-8b62-e1b2430fcb53)
#### A) Calulator Memory
```
|calc
      @0
         $reset = *reset;
         
      @1
         $val1 [31:0] = >>2$out [31:0];
         $val2 [31:0] = $rand2[3:0];
         
         $valid = $reset ? 1'b0 : >>1$valid + 1'b1;
         $valid_or_reset = $valid || $reset;
         
      ?$valid_or_reset
      @1
         $sum [31:0] = $val1 + $val2;
         $diff[31:0] = $val1 - $val2;
         $prod[31:0] = $val1 * $val2;
         $qut [31:0] = $val1 / $val2;
         
      @2
         $mem[31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b101) ? $val1 : >>2$mem ;
         
         $out [31:0] = $reset ? 32'b0 :
                      ($op[2:0] == 3'b000) ? $sum :
                      ($op[2:0] == 3'b001) ? $diff :
                      ($op[2:0] == 3'b010) ? $prod :
                      ($op[2:0] == 3'b011) ? $qut  :
                      ($op[2:0] == 3'b100) ? >>2$mem : >>2$out ;
```
![ss-30](https://github.com/kushal2710/pes_car_ps/assets/115935208/1eb84018-4d5d-4d6b-9111-a08be758df98)








