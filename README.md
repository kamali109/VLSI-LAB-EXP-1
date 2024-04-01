# VLSI-LAB-EXPERIMENTS
## AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.
## APPARATUS REQUIRED: 
• Xilinx 14.7 Spartan6 FPGA

## PROCEDURE: 
STEP:1 Start the Xilinx navigator, Select and Name the New project.<br>
STEP:2 Select the device family, device, package and speed.<br>
STEP:3 Select new source in the New Project and select Verilog Module as the Source type.<br>
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.<br>
STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.<br>
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.<br>
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.<br>
STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.<br>
STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.<br>
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.<br>
STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.<br>
STEP:12 Load the Bit file into the SPARTAN 6 FPGA.<br>

## Logic Diagram :

### Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


### Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


### Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


### Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



### Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



### 8 Bit Ripple Carry Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



## VERILOG CODE:

### Logic gates:
```h
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

### Half Adder:
```h
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

### Half Subtractor:
```h
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```

### Full Adder:
```h
module FA(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=a&b|b&c|a&c;
endmodule

module RCA(a,b,c,sum,carry);
input[7:0]a,b;
input c;
output[7:0]sum;
output carry;
wire [6:0]w;
FA f1(a[0],b[0],c,sum[0],w[0]);
FA f2(a[1],b[1],w[0],sum[1],w[1]);
FA f3(a[2],b[2],w[1],sum[2],w[2]);
FA f4(a[3],b[3],w[2],sum[3],w[3]);
FA f5(a[4],b[4],w[3],sum[4],w[4]);
FA f6(a[5],b[5],w[4],sum[5],w[5]);
FA f7(a[6],b[6],w[5],sum[6],w[6]);
FA f8(a[7],b[7],w[6],sum[7],carry);
endmodule
```

### Full Subtractor:
```h
module FS(a,b,c,difference,borrow);
input a,b,c;
output difference,borrow;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(difference,w1,c);
or g4(borrow,w2,w3);
and (w3,w1,c);
endmodule
```

### Ripple Adder:
```h
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

## OUTPUT:

#### AND GATE:
![316577225-058cddf7-0493-42f9-8576-0279fdf6446e](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/3d945dc1-33cc-4dab-9289-71703774a227)

#### OR GATE:
![316577603-75a71393-5b20-452a-bc0d-9abcab9e3984](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/ed376b61-c0f2-46a1-a51d-e6f2ded86400)


#### NAND GATE:
![316577980-6c7ab43f-c1b0-4384-a9a5-ac243a380f89](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/bade7038-1fa0-408c-aab9-2b1ad8586ad7)


#### NOR GATE:
![316578307-1b095885-5b54-4807-a907-2d70a3467473](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/48b3a75c-5b3d-4987-8e66-5b404ebc345e)


#### XOR GATE:
![316578476-89a52acf-0fe7-463c-a1f4-2cc0381b38e2](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/397652ce-8ecb-4f1c-a5d3-8b43857d1697)


#### XNOR GATE:
![316578641-d35dabe8-2eb1-4e7d-bba8-6ceb0c93524a](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/833d043a-fcc6-4104-99a9-21765a56bcda)


#### NOT GATE:
![316578799-87506908-7e40-4e93-b885-e0aa45866f88](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/fd7f67c0-8074-4ded-9eb8-309fb303f3e0)


#### HALF ADDER:
![316579053-261b9ae9-03e0-42ab-b26a-73b79894bf36](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/d907f097-fe02-40df-9fcf-14cabda17000)


#### HALF SUBTRACTOR:
![316579201-b8e72d88-54c2-4b78-9012-e9e24170aa06](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/c9a43fb3-5502-41c6-a4df-6b1aad7f7d95)


#### FULL ADDER:
![FA](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/f4fcbf2a-55c6-4221-a73f-1597e9bdc5a7)



#### FULL SUBTRACTOR:
![FS](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/9e55541d-ca17-4c1f-bc9e-e1719d23d6f0)


#### RIPPLE ADDER:
![RA](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/16cd9621-55ec-448a-b912-8a0b0aeefc22)




## RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.
