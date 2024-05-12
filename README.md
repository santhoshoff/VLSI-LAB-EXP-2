 # simulation of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR 

# AIM:
 
     To simulate ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.1.

# APPARATUS REQUIRED:

                  VIVADO 2023.1

# PROCEDURE:

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.
**LOGIC DIAGRAM**

# ENCODER

![327060950-2800c862-2254-49c4-b730-6ca3c8df6584](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/1e987a2a-fe46-4724-b681-17d4782f7a67)

# VERILOG CODE
```
module encoder_8_to_3(a0,a1,a2,d7,d6,d5,d4,d3,d2,d1,d0);
input d7,d6,d5,d4,d3,d2,d1,d0;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
# OUTPUT WAVEFORM
![327060987-093d7b33-591b-437a-ac30-233c13229c13](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/37b95222-cbf9-4318-a415-32076273b016)


# RTL DESIGN

<img width="764" alt="327061060-a9451518-1a93-4213-8629-5463eb6fc874" src="https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/828ba4e3-4fe4-40bc-9542-1cc211405b1b">


# DECODER

![327061086-fa3da222-2ecf-46a0-9a50-99e5c8a75bf2](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/9b090fae-1450-4c76-9cf4-4e63b48fc0bb)

# VERILOG CODE
```
module decoder(input [2:0] a,output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
```
# OUTPUT WAVEFORM
![327061114-2e93b773-1d07-42c6-b913-967dc0e8e424](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/165bc6de-0f9a-4dac-a17e-0cd38626ade7)

# RTL DESIGN

<img width="766" alt="327061138-535c512f-cdce-49dd-89ed-8d78b04ac04c" src="https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/e42c7395-74a8-4c97-84f9-13b3aa598585">



# MULTIPLEXER

![327061159-74429fb9-d2c7-46a3-bf13-0043073176e8](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/8baadba6-ed83-43e0-9778-8794bd7685d8)


# VERILOG CODE 
```
module mux(a,s,y);
input [7:0]a;
input [2:0]s;
output y;
reg y;
always@({s ,a})
   begin
      case(s)
         3'b000: y=a[0];
         3'b001: y=a[1];
         3'b010: y=a[2];
         3'b011: y=a[3];
         3'b100: y=a[4];
         3'b101: y=a[5];
         3'b110: y=a[6];
         3'b111: y=a[7];
      endcase
   end
endmodule
```
# WAVEFORM OUTPUT
![327061279-27eada58-a6d5-4c26-ba1f-9fc52152f674](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/319fa457-cc93-4de5-a8bf-1cc64c77a5c7)


# RTL DESIGN
<img width="761" alt="327061302-f1d139ab-d189-4969-9740-82a2c8241453" src="https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/1c7146e1-4041-43c2-b2cc-23cd33a4821f">


# DEMULTIPLEXER

![327061443-c7b7c879-da86-4f65-b99b-63b84aaee593](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/02940228-385f-4b52-b1a7-ccf6d5b345d9)


# VERILOG CODE 
```
module demux(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s [2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
```

# WAVEFORM OUTPUT
![327061484-8c1ade22-30fc-4597-8b9c-fac61a6a77c4](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/389ca224-724f-4b59-b07b-5aa381cbc072)


# RTL DESIGN
<img width="767" alt="327061513-d528750e-746e-4db1-8090-906e14ea4757" src="https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/aef374af-a53a-4efb-9212-692fcab2330c">


# MAGNITUDE COMPARATOR

![327061542-401c5867-2c0f-4451-9bcb-1adf9cfb9763](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/14f13405-e6ee-49dd-80c8-e97d9d38ab7f)


# VERILOG CODE
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
if (a==b)
begin
eq = 1'b1;
lt = 1'b0;
gt = 1'b0;
end
else if (a>b)
begin
eq = 1'b0;
lt = 1'b0;
gt = 1'b1;
end
else
begin
eq = 1'b0;
lt = 1'b1;
gt = 1'b0;
end
end
endmodule
```
# WAVEFORM OUTPUT
![327061585-d2adb194-5e9b-446c-9eea-7d63687e90ee](https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/0a633c99-4733-46b2-8d3e-4071ed01822d)


# RTL DESIGN


<img width="761" alt="327061617-e79737ec-7619-414a-8427-9f9570283885" src="https://github.com/santhoshoff/VLSI-LAB-EXP-2/assets/143347356/dc89beeb-c488-4bb4-93b5-15375475cf28">

# RESULT
simulation and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE is verified.


