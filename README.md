# iiitb_tlc -> traffic_light_controller
This repository contains design of a traffic light controlling module made by verlilog and simulation of the same.

## Introduction
Traffic lights are signaling devices used to manage traffic using different colours of light(Red, Green and Yellow). Usually we have two traffic light connected by same module working in sync. They are placed on cross-roads to avoid accidents and to maintain proper movement on roads. This model can be implemented using a microcontroller, programmable gate array or application specific IC. 

## Applications
Traffic lights are commonly used in
- places which are more crowded and have high risk of accidents
- places like schools and hospitals
- sometimes traffic lights are used to signal danger like places which are surrounded by fog

## Block Diagram
The block diagram of traffic light controller is shown below:
<p align="left">
  <img src="https://2.bp.blogspot.com/-ydh2DFq1BXQ/WB1oLTULi2I/AAAAAAAAEq0/SIKy6J_1r4gBHid8o5Koa-SK6n68GRaKwCLcB/s400/tracfic1.jpg">
</p>

## Functional characteristics

The design has five main parameters to it.<br>
The C button here is a sensor response, which will activate once any disturbance occurs on the area it is directed.<br>
The clock will keep track of time which can be used to decide the time to change the traffic signal.<br>
The reset button is used for initialisation of the whole process. As the whole system is autonomous, reset button won't be needed after first step.<br>
And then there are light_farm and light_highway parameters which will output the respective signals on two traffic light connected by sensor.<br>

Below is the output of gkwave tool after using the verilog code and the testbench. The vvp file at the output is showing clock signal, traffic light near highway and the other traffic light (near farm).
<p align="center">
  <img width="900" height="250" src="/images/output.png">
</p>

## Required Tools and Installation Details

### iverilog

Icarus Verilog is a Verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) into some target format. For batch simulation, the compiler can generate an intermediate form called vvp assembly. This intermediate form is executed by the vvp command.

### GTKWave

GTKWave is a fully featured GTK+ based wave viewer for Unix and Win32 which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing. We will be using this tool to simulate the output of our main code using a testbench.

### Installation of iverilog and GTKwave

<ul>
  <li>
    <b> For Ubuntu/ Linux mint: </b> 
    <br>
    Open the terminal and enter the following commands
    
    
    $   sudo apt-get update
    $   sudo apt-get install iverilog 
    $   sudo apt-get install gtkwave
  </li>
  <li>
    <b> For arch based distros: </b>
    <br>
    Open the terminal and enter the following commands
  
  
    $   sudo pacman -Syu
    $   sudo pacman -S iverilog 
    $   sudo pacman -S gtkwave
  </li>
</ul>

### Functional Simulation

First, make sure to have git package installed in your device. Then proceed with following commands:

```
$   sudo apt install -y git
$   git clone https://github.com/m4ury4p/IIITB_ASIC_traffic_controller

$   cd IIITB_ASIC_traffic_controller/

$   iverilog iiitb_traffic_light_controller.v iiitb_traffic_light_controller_tb.v 
$   ./a.out

$   gtkwave output1.vcd
```
I would recommend setting the interval of 10 microseconds and "zoom to fit" to see waveforms properly. 

###  Synthesis using Yosys

In computer engineering, logic synthesis is a process by which an abstract specification of desired circuit behavior, typically at register transfer level (RTL), is turned into a design implementation in terms of logic gates, typically by a computer program called a synthesis tool. Common examples of this process include synthesis of designs specified in hardware description languages, including VHDL and Verilog.Some synthesis tools generate bitstreams for programmable logic devices such as PALs or FPGAs, while others target the creation of ASICs. Logic synthesis is one aspect of electronic design automation.<br>

This is a framework for RTL synthesis tools. It currently has extensive Verilog-2005 support and provides a basic set of synthesis algorithms for various application domains.<br>

Yosys can be adapted to perform any synthesis job by combining the existing passes (algorithms) using synthesis scripts and adding additional passes as needed by extending the yosys C++ code base.<br>

To install yosys use the following commands for arch-linux
```
sudo pacman -S yosys
```

Here, we will use following commands to run our script.

```
$ yosys
$ read_liberty -lib /lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog iiitb_tlc.v
$ synth -top iiitb_tlc 
$ abc -liberty /home/iiitb_tlc/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ write_verilog -noattr iiitb_tlc_synth.v
$ stat
$ show

```


## Contributors

- <b> Maurya Patel </b>
- <b> Kunal Ghosh </b>

## Acknowledgements

- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd.

## Contact Information

- Maurya Patel, Integrated MTech ECE Student, International Institute of Information Technology, Bangalore Maurya.Patel@iiitb.ac.in
- Kunal Ghosh, Director, VSD Corp. Pvt. Ltd. kunalghosh@gmail.com

## References
- https://www.fpga4student.com/2016/11/verilog-code-for-traffic-light-system.html
- https://www.academia.edu/21200096/DESIGN_AND_IMPLEMENTATION_OF_TRAFFIC_LIGHTS_CONTROLLER_USING_FPGA_A_Project_Based_Laboratory_Report_in_partial_fulfilment_for_the_award_of_III_IV_B_Tech_I_Semester_Submitted_by_Lab_Instructor
- https://iverilog.fandom.com/wiki/GTKWave
- https://en.wikipedia.org/wiki/Logic_synthesis
