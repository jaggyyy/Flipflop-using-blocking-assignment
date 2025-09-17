# EXPERIMENT 3: Simulation of All Flip-Flops using Blocking Statement

## AIM
To design and simulate basic flip-flops (SR, D, JK, and T) using **blocking statements** in Verilog HDL, and verify their functionality through simulation in Vivado 2023.1.

## APPARATUS REQUIRED
- Vivado 2023.1
- Computer with HDL Simulator

## DESCRIPTION
Flip-flops are the basic memory elements in sequential circuits.  
In this experiment, different types of flip-flops (SR, D, JK, T) are modeled using **behavioral modeling** with **blocking assignment (`=`)** inside the `always` block.  
Blocking assignments execute sequentially in the given order, which makes it easier to describe simple synchronous circuits.

## PROCEDURE
1. Open **Vivado 2023.1**.  
2. Create a **New RTL Project** (e.g., `FlipFlop_Simulation`).  
3. Add Verilog source files for each flip-flop (SR, D, JK, T).  
4. Add a testbench file to verify all flip-flops.  
5. Run **Behavioral Simulation**.  
6. Observe waveforms of inputs and outputs for each flip-flop.  
7. Verify that outputs match the truth table.  
8. Save results and capture simulation screenshots.

---

## VERILOG CODE

### SR Flip-Flop (Blocking)
```verilog
module sr_ff (
    input wire S, R, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### SR Flip-Flop Test bench 
```verilog
module sr_ff_tb;
reg clk, S, R;
wire Q;
sr_ff uut (.clk(clk),.S(S),.R(R),.Q(Q));
initial begin
clk = 0;
forever #10 clk = ~clk;
end
initial begin
S = 0; R = 0;
#100 S = 1; R = 0;
#100 S = 0; R = 0;
#100 S = 0; R = 1;
#100 S = 1; R = 1;
#100 S = 0; R = 0;
end
endmodule




```
#### SIMULATION OUTPUT
<img width="1891" height="1186" alt="image" src="https://github.com/user-attachments/assets/c9039906-37aa-4fd6-b9cb-97ff704b77af" />

---

### JK Flip-Flop (Blocking)
```verilog
module jk_ff (
    input wire J, K, clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### JK Flip-Flop Test bench 
```verilog
module tb_jk_ff;
reg clk;
reg J, K;
wire Q;
jk_ff uut (.clk(clk),.J(J),.K(K),.Q(Q));
initial begin
clk=0;
forever #20 clk=~clk;
end
initial begin
J = 0; K = 0;
#100 J=0; K=0;
#100 J=0; K=1;
#100 J=1; K=0;
#100 J=1; K=1;
#100 J=0; K=1;
#100 J=1; K=0;
#100 J=1; K=1;
end
endmodule




```
#### SIMULATION OUTPUT
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/ae5af63c-25e7-4a7c-a66f-e75d7f608f3d" />

---
### D Flip-Flop (Blocking)
```verilog
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### D Flip-Flop Test bench 
```verilog


module dff_tb;
reg clk_t, rst_t, d_t;
wire q_t;
dff dut (.clk(clk_t),.rst(rst_t),.d(d_t),.q(q_t) );
initial begin
clk_t = 1'b0;
rst_t = 1'b1;
d_t = 1'b0;
#100 rst_t = 1'b0;
#100 d_t = 1'b1;
#100 d_t = 1'b0;
#100 d_t = 1'b1;
end
always #10 clk_t = ~clk_t;
endmodule


```

#### SIMULATION OUTPUT
<img width="1919" height="1197" alt="image" src="https://github.com/user-attachments/assets/1bb0d2c9-d748-42d7-a42b-25f18ed75c22" />

---
### T Flip-Flop (Blocking)
```verilog
module d_ff (
    input wire d,clk,
    output reg Q
);
    always @(posedge clk) begin



endmodule
```
### T Flip-Flop Test bench 
```verilog

module t_ff_tb;
reg clk, rst, T;
wire Tout;
t_ff uut (.clk(clk),.rst(rst),.T(T),.Tout(Tout));
initial begin
clk = 0;
forever #10 clk = ~clk;
end
initial begin
rst = 1; T = 0;
#20 rst = 0;
#20 T = 1;
#20 T = 0;
#20 T = 1;
#20 T = 1;
#20 T = 0;
end
endmodule



```

#### SIMULATION OUTPUT
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/4a4173dc-74df-4c8d-bfb9-681e648546e0" />


---

### RESULT

All flip-flops (SR, D, JK, T) were successfully simulated using blocking statements in Verilog HDL.
The outputs matched the expected truth table values, demonstrating correct sequential behavior.
