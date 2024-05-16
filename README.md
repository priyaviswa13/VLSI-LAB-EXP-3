# SIMULATION AND IMPLEMENTATION OF MULTIPLIER

# AIM: 
To simulate and synthesis multiplier using  Vivado 2023.1

# APPARATUS REQUIRED:
 Vivado 2023.1
  
# PROCEDURE:
```
STEP:1  Open Vivado: Launch Xilinx Vivado software on your computer.
STEP:2  Create a New Project: Click on "Create Project" from the welcome page or navigate 
        through "File" > "Project" > "New".     
STEP:3  Project Settings: Follow the prompts to set up your project. Specify the project name, 
        location, and select RTL project type.                       
STEP:4  Add Design Files: Add your Verilog design files to the project. You can do this by 
        right-clicking on "Design Sources" in the Sources window, then selecting "Add 
        Sources". Choose your Verilog files from the file browser.
STEP:5  Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your 
        simulation language (Verilog in this case) and simulation tool (Vivado Simulator).
STEP:6  Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This 
        will launch the Vivado Simulator and compile your design for simulation.
STEP:7  Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's 
        not set automatically. This determines how long the simulation will run.
STEP:8  Run Simulation: Start the simulation by clicking on the "Run" button in the simulation 
        window.
STEP:9  View Results: After the simulation completes, you can view waveforms, debug signals, 
        and analyze the behavior of your design.
```
# Logic Diagram:

# 2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)
```
CODE:

ha adder2(w3,w4,p[2],cout);
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
module bitmul(a,b,p,cout);
input [1:0]a,b;
output [2:0]p;
output cout;
wire w1,w2,w3,w4;
and (p[0],a[0],b[0]);
and (w1,a[0],b[1]);
and (w2,a[1],b[0]);
and (w3,a[1],b[1]);
ha adder1(w1,w2,p[1],w4);
endmodule
```
# OUTPUT:
![324472642-d0d34571-1f27-44b6-bcf0-251caa88f880](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/166889783/2df28202-e9ca-46cf-980d-cf497b456d3b)

# 4 Bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)
```
CODE:

module ha(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule

module fa(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor(w1,a,b);
xor(sum,w1,c);
and(w2,w1,c);
and(w3,a,b);
or(carry,w2,w3);
endmodule
module mul4bit(a,b,p);
input [3:0]a,b;
output [7:0]p;
wire [15:0]w;
wire [3:0]hc;
wire [6:0]fc;
wire [4:0]fs;
wire hs;
and r11(p[0],a[0],b[0]);
and r12(w[1],a[1],b[0]);
and r13(w[2],a[2],b[0]);
and r14(w[3],a[3],b[0]);
and r21(w[4],a[0],b[1]);
and r22(w[5],a[1],b[1]);
and r23(w[6],a[2],b[1]);
and r24(w[7],a[3],b[1]);
ha r31(w[1],w[4],p[1],hc[0]);
fa r32(w[2],w[5],hc[0],fs[0],fc[0]);
fa r33(w[3],w[6],fc[0],fs[1],fc[1]);
ha r34(w[7],fc[1],hs,hc[1]);
and r41(w[8],a[0],b[2]);
and r42(w[9],a[1],b[2]);
and r43(w[10],a[2],b[2]);
and r44(w[11],a[3],b[2]);
ha r51(w[8],fs[0],p[2],hc[2]);
fa r52(w[9],fs[1],hc[2],fs[2],fc[2]);
fa r53(w[10],hs,fc[2],fs[3],fc[3]);
fa r54(w[11],hc[1],fc[3],fs[4],fc[4]);
and r61(w[12],a[0],b[3]);
and r62(w[13],a[1],b[3]);
and r63(w[14],a[2],b[3]);
and r64(w[15],a[3],b[3]);
ha r71(w[12],fs[2],p[3],hc[3]);
fa r72(w[13],fs[3],hc[3],p[4],fc[5]);
fa r73(w[14],fs[4],fc[5],p[5],fc[6]);
fa r74(w[15],fc[4],fc[6],p[6],p[7]);
endmodule
```

# OUTPUT:
![320424099-a383f18f-2e55-4bf4-a1e1-a1732a005735](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/166889783/66aeebf5-9536-4f48-b3af-a30be9fed648)

# Result:
simulation and synthesis multiplier using  Vivado 2023.1 completed successesfully.



