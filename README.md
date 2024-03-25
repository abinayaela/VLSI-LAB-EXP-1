# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

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



VERILOG CODE
# logic gates
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
# half adder
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
endmodule
module multi_2(a,b,p,carry);
input [1:0]a,b;
output [2:0]p;
output carry;
endmodule
```
# half subtractor
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# full adder 
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
# full subtractor 
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
# ripple adder 
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```



OUTPUT
AND GATE
![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/058cddf7-0493-42f9-8576-0279fdf6446e)
OR GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/75a71393-5b20-452a-bc0d-9abcab9e3984)
NAND GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/6c7ab43f-c1b0-4384-a9a5-ac243a380f89)
NOR GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/1b095885-5b54-4807-a907-2d70a3467473)
XOR GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/89a52acf-0fe7-463c-a1f4-2cc0381b38e2)
XNOR GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/d35dabe8-2eb1-4e7d-bba8-6ceb0c93524a)
NOT GATE

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/87506908-7e40-4e93-b885-e0aa45866f88)
HALF ADDER

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/261b9ae9-03e0-42ab-b26a-73b79894bf36)
HALF SUBTRACTOR

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/b8e72d88-54c2-4b78-9012-e9e24170aa06)
FULL ADDER 

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/db531338-b7e0-40ad-bd21-9de6246cc460)
FULL SUBTRACTOR 

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/fe1e3b31-b3ed-41e1-91f3-34a090a312e8)
RIPPLE ADDER 

![image](https://github.com/abinayaela/VLSI-LAB-EXP-1/assets/164911294/57540d99-2b22-42fe-a5d6-d8b96f1b4ed9)

RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.

