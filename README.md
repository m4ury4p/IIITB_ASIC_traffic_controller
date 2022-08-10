# IIITB_ASIC_traffic_light_controller
This repository contains design of a traffic light controlling module made by verlilog and the simulation of the same.

## Introduction
Traffic lights are signaling devices used to manage traffic using different colours of light(Red, Green and Yellow). Usually we have two traffic light connected by same module working in sync. They are placed on cross-roads to avoid accidents and to maintain proper movement on roads. This model can be implemented using a microcontroller, programmable gate array or application specific IC. 

## Applications
Traffic lights are commonly used in
- places which are more crowded and have high risk of accidents
- places like schools and hospitals
- sometimes traffic lights are used to signal danger like places which are surrounded by fog

## Block Diagram
The block diagram of traffic light controller is shown below:


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
$   git clone https://github.com/mahati-basavaraju/iiitb_piso

$   cd iiitb_piso

$   iverilog -o iiitb_piso iiitb_piso_tb.v  iiitb_piso.v 
$   vvp iiitb_piso

$   gtkwave iiitb_piso.vcd
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
