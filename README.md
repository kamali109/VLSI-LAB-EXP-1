# VLSI-LAB-EXPERIMENTS
# AIM:  
    
    To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

# APPARATUS REQUIRED:  

     Vivado 2023.1

# PROCEDURE: 
```
STEP:1  Start the Xilinx navigator, Select and Name the New project. 
STEP:2  Select the device family, device, package and speed. 
STEP:3  Select new source in the New Project and select Verilog Module as the Source type. 
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it. 
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.
STEP:6  Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. 
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window. 
STEP:8  Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. 
STEP:10  Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. 
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.
STEP:12  Load the Bit file into the SPARTAN 6 FPGA.
```
# Logic Diagram :

# LOGIC GATES:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/285723d2-e83d-4d1a-b350-2849e83add0c)

# CODE:
~~~
      module gate(a,b,w1,w2,w3,w4,w5,w6,w7);
      input a,b;
      output w1,w2,w3,w4,w5,w6,w7;
      and g1 (w1,a,b);
      or g2 (w2,a,b);
      not g3 (w3,a);
      xor g4 (w4,a,b);
      xnor g5 (w5,a,b);
      nand g6 (w6,a,b);
      nor g7 (w7,a,b);
      endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/21178b59-ee9c-492c-aff9-56895d38b585)

# FULL ADDER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/3e3d842d-d0ce-4416-976e-8e17119515af)

# CODE:
~~~
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
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/7b2568c8-925a-4a56-9ef5-9fd329f0099d)

# HALF ADDER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/75ffc0b9-4f57-4b47-8e98-88b46d21c166)
# CODE:
~~~
        module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
~~~

# OUTPUT:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/6517181d-cdbb-450a-b7e2-dbc8be3f3aa6)

# HALF SUBTRACTOR:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/97414e0f-5049-415e-bb92-70869674155e)

# CODE:
~~~
       module hs(a,b,difference,borrow);
       input a,b;
       output difference,borrow;
       wire w;
       xor g1(difference,a,b);
       and g2(borrow,w,b);
       not g3(w,a);
       endmodule
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/74f7e9f5-64b1-40b2-bd9c-dffdb9d02661)


# FULL SUBTRACTOR:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/bc2291b0-16b8-4609-af47-1799b2027014)

# CODE:
~~~
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
~~~

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/ba6633a8-7b90-4aa0-91df-434b825bad5c)

# 8 RIPPLE CARRY ADDER:
![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/cb9e6496-e1e9-401d-8fad-a8d9624accf9)

# CODE:
```c
module FA(a, b, c, sum, carry);
input a, b, c;
output sum, carry;
assign sum=a ^ b ^ c;
assign carry=a & b|b & c|a & c;
endmodule

module RCA(a, b, c, sum, carry);
input [7:0] a, b;
input c;
output [7:0] sum;
output carry;
wire [6:0] w;
FA f1(a[0], b[0], c, sum[0], w[0]);
FA f2(a[1], b[1], w[0], sum[1], w[1]);
FA f3(a[2], b[2], w[1], sum[2], w[2]);
FA f4(a[3], b[3], w[2], sum[3], w[3]);
FA f5(a[4], b[4], w[3], sum[4], w[4]);
FA f6(a[5], b[5], w[4], sum[5], w[5]);
FA f7(a[6], b[6], w[5], sum[6], w[6]);
FA f8(a[7], b[7], w[6], sum[7], carry);
endmodule
```

# OUTPUT:

![image](https://github.com/kamali109/VLSI-LAB-EXP-1/assets/160600794/56258af5-8733-47d1-859b-9cde799ea2bb)


# RESULT:
```
   Hence, the stimulation and synthesis of a Logic Gates,Adders and Subtractor was run successfully by using Xilinx ISE.
```
