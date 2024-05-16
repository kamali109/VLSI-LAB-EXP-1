# VLSI-LAB-EXPERIMENTS
## AIM: 
```
    To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.
```
## APPARATUS REQUIRED:
````
• Vivado 2023.1
```
## PROCEDURE:
```
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
```

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

Logic gates:
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

 OUTPUT:

AND GATE:
![316577225-058cddf7-0493-42f9-8576-0279fdf6446e](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/3d945dc1-33cc-4dab-9289-71703774a227)

 OR GATE:
![316577603-75a71393-5b20-452a-bc0d-9abcab9e3984](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/ed376b61-c0f2-46a1-a51d-e6f2ded86400)


NAND GATE:
![316577980-6c7ab43f-c1b0-4384-a9a5-ac243a380f89](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/bade7038-1fa0-408c-aab9-2b1ad8586ad7)


NOR GATE:
![316578307-1b095885-5b54-4807-a907-2d70a3467473](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/48b3a75c-5b3d-4987-8e66-5b404ebc345e)

XOR GATE:
![316578476-89a52acf-0fe7-463c-a1f4-2cc0381b38e2](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/397652ce-8ecb-4f1c-a5d3-8b43857d1697)

XNOR GATE:
![316578641-d35dabe8-2eb1-4e7d-bba8-6ceb0c93524a](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/833d043a-fcc6-4104-99a9-21765a56bcda)

 NOT GATE:
![316578799-87506908-7e40-4e93-b885-e0aa45866f88](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/fd7f67c0-8074-4ded-9eb8-309fb303f3e0)

HALF ADDER:
```
       module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
```
OUTPUT:

#### HALF ADDER:
![316579053-261b9ae9-03e0-42ab-b26a-73b79894bf36](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/d907f097-fe02-40df-9fcf-14cabda17000)

HALF SUBTRACTER:
```
       module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
```
OUTPUT:
![316579201-b8e72d88-54c2-4b78-9012-e9e24170aa06](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/c9a43fb3-5502-41c6-a4df-6b1aad7f7d95)

FULL ADDER:
```
       module fulladder(a,b,cin,sum,carry);
       input a,b,cin;
       output sum,carry;
       wire w1,w2,w3;
       xor g1(w1,a,b);
       xor g2(sum,w1,cin);
       and g3(w2,w1,cin);
       and  g4(w3,a,b);
       or g5(carry,w2,w3);
       endmodule
```
OUTPUT:

![FA](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/f4fcbf2a-55c6-4221-a73f-1597e9bdc5a7)

FULL SUBTRACTOR:
```
module fs(a,b,c,diff,borrow);
    input a,b,c;
    output diff,borrow;
    wire w1,w2,w3,w4,w5;
    xor g1(w3,a,b);
    xor g2(diff,c,w3);
    and g3(w2,b,w1);
    and g4(w5,w4,c);
    not g5(w1,a);
    not g6(w4,w3);
    nor g7(borrow,w5,w2);
    endmodule
```
OUTPUT: 

![FS](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/9e55541d-ca17-4c1f-bc9e-e1719d23d6f0)


RIPPLE ADDER:
```
  module fa(a,b,cin,sum,carry);
       input a,b,cin;
       output sum,carry;
       wire w1,w2,w3;
       xor g1(w1,a,b);
       and g2(w3,a,b);
       xor g3(sum,w1,cin);
       and g4(w2,w1,cin);
       or g5(carry,w2,w3);
 endmodule
 
 module rca(a,b,cin,sum,cout);
        input[3:0]a,b;
        input cin;
        output [3:0]sum;
        output cout;
        wire w1,w2,w3;
      fa g1(.a(a[0]),
            .b(b[0]),
            .cin(cin),
            .sum(sum[0]),
            .carry(c1)
            );
       fa g2(.a(a[1]),
             .b(b[1]),
             .cin(c1),
             .sum(sum[1]),
             .carry(c2)
             );
       fa g3(.a(a[2]),
             .b(b[2]),
             .cin(c2),
             .sum(sum[2]),
             .carry(c3)
             );
        fa g4(.a(a[3]),
              .b(b[2]),
              .cin(c3),
              .sum(sum[3]),
              .carry(cout)
              );
       endmodule
```
OUTPUT:

![RA](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/16cd9621-55ec-448a-b912-8a0b0aeefc22)




## RESULT:
```
     Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.
```
