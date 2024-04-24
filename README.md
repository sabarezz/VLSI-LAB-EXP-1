# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Vivado 2023.1


1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:

# Program
# Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Adder:
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 4 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```
# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```

OUTPUT:
# OR gate:
![OR gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/8cea22f7-a28b-4e95-b377-62974ea49ba8)

# NOT gate:
![NOT gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/4b362048-896f-4c1b-8cad-3fda2280a5ab)

# AND gate:
![AND gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/e95545f6-c00d-4c20-9b93-4dcc2e5b7326)

# NAND gate:
![NAND gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/cac5e937-2da2-46b8-b245-a639adae9525)

# NOR gate:
![NOR gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/7320a201-e18f-4645-86d9-7ee4ac03dd3a)

# XNOR gate:
![XNOR gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/6d381db7-edf1-484c-9d15-dc4d18f52945)

# XOR gate:
![XOR gate](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/95685eb3-3599-49b2-a98f-f8c023c58fbd)

# Half Adder:
![HALF ADDER ](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/855a83e0-5a5c-453f-a13c-801d271a8d15)

# Half Subtracter:
![halfsubtractor](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/cafed113-d463-4ed5-9a92-d2cd7dd436c3)

# Full Adder:
![full adder](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/dcc8df43-9b77-44e0-8ec2-1dddbdee5b0b)

# Full Subtracter:
![full subtractor](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/9bf78c96-9f4e-4bb5-91b2-090bd3384fb2)

# 4 Bit Ripple Carry Adder:
![4 BIT CARRY](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/60adadc5-3cfc-47f8-adea-2b3fe12e6da8)

# 8 Bit Ripple Carry Adder:
![8 BIT CARRY](https://github.com/sabarezz/VLSI-LAB-EXP-1/assets/165630121/be66bb17-81f9-4a63-96f9-e7a8552da47f)





RESULT:
simulation of Logic Gates ,Adders and Subtractors using Vivado 2023.2 completed successfully
