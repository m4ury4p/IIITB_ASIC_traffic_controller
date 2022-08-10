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
The  4- bit PISO shift register circuit diagram is shown below. This circuit mainly includes 4, D flip flops which are connected as per the diagram shown. The CLK(clock) input signal is connected directly to all the flip flops however the input data is individually connected to every flip flop. Hence it is a synchronous sequential circuit. The previous flip flop’s output, as well as parallel input data, is simply connected to the input of the second flip flop. 

<p align='center'>
  <img src='https://user-images.githubusercontent.com/110677094/183280035-0182a932-d45a-402e-902a-a78977d61a86.png' > 
</p> 

<p align='center'> 
  <img src='https://user-images.githubusercontent.com/110677094/183281909-80ee7817-a4a4-4293-96cf-d459695a2f60.png'>
</p>


<p align='center'>
  <img src='https://user-images.githubusercontent.com/110677094/183254665-b745fa26-501c-4d35-a787-4001b81f4df0.png'>
</p>

## Required Tools and Installation Details

### iverilog

Icarus Verilog is a Verilog simulation and synthesis tool. It operates as a compiler, compiling source code written in Verilog (IEEE-1364) into some target format. For batch simulation, the compiler can generate an intermediate form called vvp assembly. This intermediate form is executed by the vvp command.

### GTKWave

GTKWave is a fully featured GTK+ based wave viewer for Unix and Win32 which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing. We will be using this tool to simulate the output of our main code using a testbench.

### Installation of iverilog and GTKwave

<ul>
  <li>
    <b> For Ubuntu/ Linux mint </b> 
    <br>
    Open the terminal and enter the following commands
    
    
    $   sudo apt-get update
    $   sudo apt-get install iverilog 
    $   sudo apt-get install gtkwave
   </li>
</ul>

### Functional Simulation

To install git, clone this repository and download the required files for simulation, enter the below commands in the terminal.

```
$   sudo apt install -y git
$   git clone https://github.com/mahati-basavaraju/iiitb_piso

$   cd iiitb_piso

$   iverilog -o iiitb_piso iiitb_piso_tb.v  iiitb_piso.v 
$   vvp iiitb_piso

$   gtkwave iiitb_piso.vcd
```

## Functional Characteristics

Find below simulation results when a 4-bit input '1011' is provided. Note that data_in is the input data, data_out is the output register, q is a temporary register to indicate shifting and, clk and load are clock and shift/load signals respectively.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110677094/183284643-1817f689-22ad-4cd7-be6b-963523d34a84.png">
</p>

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
