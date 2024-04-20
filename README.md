# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Vivado Software

APPARATUS REQUIRED: Vivado™ ML 2023.2 


**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
PROCEDURE:

Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

VERILOG CODE
~~~
DECODER 3 to 8

module decoder_struct(  
  input [2:0] a,    
  output [7:0] d    
   );
wire x,y,z;
not g1(z,a[0]);
not g2(y,a[1]);
not g3(x,a[2]);
and g4(d[0],x,y,z);
and g5(d[1],x,y,a[0]);
and g6(d[2],x,a[1],z);
and g7(d[3],x,a[1],a[0]);
and g8(d[4],a[2],y,z);
and g9(d[5],a[2],y,a[0]);
and g10(d[6],a[2],a[1],z);
and g11(d[7],a[2],a[1],a[0]);
endmodule
~~~
~~~
DEMULTIPLEXER 1 to 8
module demux_1_8(y,s,a);
output reg [7:0]y;
input [2:0]s;
input a;

always @(*)
begin 
y=0;
case(s)
3'd0: y[0]=a;
3'd1: y[1]=a;
3'd2: y[2]=a;
3'd3: y[3]=a;
3'd4: y[4]=a;
3'd5: y[5]=a;
3'd6: y[6]=a;
3'd7: y[7]=a;
endcase
end
endmodule
~~~
~~~
ENCODER 8 to 3
module encoder_8_to_3(a0,a1,a2,d0,d1,d2,d3,d4,d5,d6,d7);
input d0,d1,d2,d3,d4,d5,d6,d7;
output a0,a1,a2;
assign a0 = ( d1 | d3 | d5 | d7 );
assign a1 = ( d2 | d3 | d6 | d7 );
assign a2 = ( d4 | d6 | d5 | d7 );
endmodule
~~~
~~~
MAGNITUDE COMPARATOR
Module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 
 
 
end 
endmodule
~~~
~~~
MULTIPLEXER 8 to 1
module mux_8tol (in, sel, out);
    input [7:0] in;
    input [2:0] sel;
    output reg out;
    always @(*)
       begin
          case (sel)
              3'b000: out = in [0];
              3'b001: out = in [1];
              3'b010: out = in [2];
              3'b011: out = in [3];
              3'b100: out = in [4];
              3'b101: out = in [5];
              3'b110: out = in [6];
              3'b111: out = in [7];
              default: out = 1'bx;
          endcase
       end
endmodule
~~~





OUTPUT WAVEFORM

DECODER 3 to 8:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/d39db28d-24ac-4ac5-bfd1-c23d718a5a81)
Elabrated Diagram:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/9e4329c4-bda4-4b7f-ae32-ff2e98b3a2c8)

Demultiplexer 1 to 8:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/b867c07b-eaad-4bcc-91b6-88bb58dd7eec)
Elabrated Diagram:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/fddc10cc-d783-4183-a5e3-d0d220ddd44a)

Encoder 8 to 3:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/4674c439-403d-4abf-95d1-ebb7312e76d0)
Elabrated Diagram:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/3f9600e6-db5a-407f-aa29-58122affa1e1)

Magnitude Comparator:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/c4f56349-1ee4-4343-adad-9c15732e367f)
Elabrated Diagram:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/8557f9c3-501d-42ff-983c-0b3d69910876)

Multiplexer 8 to 1:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/1209f3a9-0487-46ef-a102-feb124739633)
Elabrated Diagram:![image](https://github.com/Madhan0302/VLSI-LAB-EXP-2/assets/160517887/ccb6dfc9-5f5d-4693-ab9f-c8db00811d64)



RESULT:
        The simulation and synthesis Logic Gates,Adders and Subtractor successfully verified using Vivadoo Software.


