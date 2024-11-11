# Traffic-Light-Controller-Using-Verilog-HDL
## AIM :
To design and simulate a traffic light controller using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 simulation environment. The objective is to control the traffic lights for a junction with a specific time-based sequence for Red, Yellow, and Green lights.

## APPARATUS REQUIRED :
Vivado 2023.1 or equivalent Verilog simulation tool.
Computer system with a suitable operating system.
FPGA board (optional for hardware verification).

## PROCEDURE :
Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Traffic Light Controller Verilog Code:

Write the Verilog code for the traffic light controller, using an FSM (Finite State Machine) to transition between Green, Yellow, and Red lights based on timing intervals.
Create the Testbench:

Write a testbench to simulate the traffic light controller. The testbench will check the sequence of light transitions based on time.
Add the Verilog Files:

Add the traffic light controller Verilog code and the testbench file to the project.
Run Simulation:

Run the behavioral simulation in Vivado to verify the correct sequence of the traffic lights.
Observe the Waveforms:

Examine the waveform output to verify that the traffic light transitions through the Green, Yellow, and Red lights in the correct sequence.
Save and Document Results:

Capture screenshots of the waveform and save the simulation logs to include in your report.

### Verilog Code for Traffic Light Controller:
~~~
module Traffic_light_controller_TB;
reg clk,rst;
wire[2:0]light_M1;
wire[2:0]light_S;
wire[2:0]light_MT;
wire[2:0]light_M2;

initial
begin
     clk=1'b0;
     forever # (1000000000/2) clk=~clk;
end
initial
begin
     rst=0;
     #1000000000;
     rst=1;
     #1000000000;
     rst=0;
     #(1000000000*200);
     $finish;
     end
     endmodule
~~~

## Output : 
![tl](https://github.com/user-attachments/assets/ae6b901c-6d4d-456a-a1ec-9ecc9a804447)

### Testbench for Traffic Light Controller:
~~~
module Traffic_light_controller_TB;
  reg clk, rst;
  wire [2:0] light_M1;  
  wire [2:0] light_S;   
  wire [2:0] light_MT; 
  wire [2:0] light_M2;  

 
  Traffic_light_controller DUT (
    .clk(clk),
    .rst(rst),
    .light_M1(light_M1),
    .light_S(light_S),
    .light_MT(light_MT),
    .light_M2(light_M2)
  );

  initial begin
    clk = 1'b0;
    forever #(1000000000 / 2) clk = ~clk;  
  end
  
  initial begin
    rst = 0;           
    #1000000000;         
    rst = 1;            
    #1000000000;        
    rst = 0;             
    #(1000000000 * 200); 
    $finish;            
  end
endmodule
~~~
## Output : 
![tl1](https://github.com/user-attachments/assets/a33ca09f-a55c-466b-8dee-b22eef476d64)
 
## Conclusion:
In this experiment, a traffic light controller was successfully designed and simulated using Verilog HDL. The design controlled the traffic lights to switch between Green, Yellow, and Red in a cyclic manner based on timing intervals. The testbench verified that the traffic lights followed the correct sequence and timing. The simulation results confirm the correct functionality of the traffic light controller, demonstrating the effectiveness of Verilog HDL in designing FSM-based controllers for real-world applications.
