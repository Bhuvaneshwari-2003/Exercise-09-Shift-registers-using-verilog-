
# Experiment--09-Implementation-of Shift-registers-using-verilog-
### AIM: To implement PISO , PIPO,PISO  using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
Shift registers are basically of 4 types. These are:

Serial In Serial Out shift register
Serial In parallel Out shift register
Parallel In Serial Out shift register
Parallel In parallel Out shift register
Serial-In Serial-Out Shift Register (SISO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a serial output is known as Serial-In Serial-Out shift register. Since there is only one output, the data leaves the shift register one bit at a time in a serial pattern, thus the name Serial-In Serial-Out Shift Register.

The logic circuit given below shows a serial-in serial-out shift register. The circuit consists of four D flip-flops which are connected in a serial manner. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337366-540cc45e-11fe-4cce-9503-560dc704bc7d.png)
FIGURE -01 
erial-In Parallel-Out shift Register (SIPO) –
The shift register, which allows serial input (one bit after the other through a single data line) and produces a parallel output is known as Serial-In Parallel-Out shift register.

The logic circuit given below shows a serial-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal is connected in addition to the clock signal to all the 4 flip flops in order to RESET them. The output of the first flip flop is connected to the input of the next flip flop and so on. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.

![image](https://user-images.githubusercontent.com/36288975/172337438-03416c7e-7c9d-4939-ba34-c355b9fc79c5.png)
FIGURE-02
The above circuit is an example of shift right register, taking the serial data input from the left side of the flip flop and producing a parallel output. They are used in communication lines where demultiplexing of a data line into several parallel lines is required because the main use of the SIPO register is to convert serial data into parallel data.
Parallel-In Serial-Out Shift Register (PISO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and produces a serial output is known as Parallel-In Serial-Out shift register.

The logic circuit given below shows a parallel-in-serial-out shift register. The circuit consists of four D flip-flops which are connected. The clock input is directly connected to all the flip flops but the input data is connected individually to each flip flop through a multiplexer at the input of every flip flop. The output of the previous flip flop and parallel data input are connected to the input of the MUX and the output of MUX is connected to the next flip flop. All these flip-flops are synchronous with each other since the same clock signal is applied to each flip flop.
![image](https://user-images.githubusercontent.com/36288975/172337544-1632407f-1743-4b17-b480-00663d01e59f.png)
FIGURE-03
A Parallel in Serial out (PISO) shift register us used to convert parallel data to serial data.

Parallel-In Parallel-Out Shift Register (PIPO) –
The shift register, which allows parallel input (data is given separately to each flip flop and in a simultaneous manner) and also produces a parallel output is known as Parallel-In parallel-Out shift register.

The logic circuit given below shows a parallel-in-parallel-out shift register. The circuit consists of four D flip-flops which are connected. The clear (CLR) signal and clock signals are connected to all the 4 flip flops. In this type of register, there are no interconnections between the individual flip-flops since no serial shifting of the data is required. Data is given as input separately for each flip flop and in the same way, output also collected individually from each flip flop![image](https://user-images.githubusercontent.com/36288975/172337661-babb1f90-6286-4d14-8cbd-26a380ee085e.png)
FIGURE-04
A Parallel in Parallel out (PIPO) shift register is used as a temporary storage device and like SISO Shift register it acts as a delay element.

Procedure:
Step1: Create a new Quartus II project.

Step2: Create a new file in the Quartus II where name of the module is name of the project.

Step3: Declare a function for each logical circuit.

Step4: For each definition give end module.

Step5: Run RTL simulation and timing diagram.



PROGRAM :
/*
Program for  Implementation-of Shift-registers-using-verilog-
Developed by: bhuvaneshwari.s
RegisterNumber:212221240010
*/

## SIPO:
module sipo(si,clk,po);
input si,clk;
output [0:7]po;
reg [0:7]temp;
always@(posedge clk)
begin
temp = {temp[0:6],si};
end
assign po=temp;
endmodule

## PISO:
module ex9(clk,pin,load,so);
input load,clk;
input [3:0]pin;
output reg so;
reg [3:0]temp;
always@(posedge clk)
begin
if(load)
temp<=pin;
end
begin
so<=temp[3]
temp<={temp[2:0],1'b0};
end
endmodule

## PIPO:
module ex9(po,pi,clk);
input clk;
input [3:0] pi;
output reg[3:0]po;
always@(posedge clk)
begin
po=pi;
end
endmodule






RTL LOGIC  REGISTERS:
SIPO:
![201098786-5be104e9-8207-49b0-9404-1482042ddb87](https://user-images.githubusercontent.com/94828604/201915031-d47ed4ce-95e8-4690-b8f3-11a402f29a99.png)

PISO:
![201098825-781af87e-9f55-4649-b8aa-df5ecc88bcf4](https://user-images.githubusercontent.com/94828604/201915156-63299b65-24f3-4469-bf63-8c7fc9586468.png)

PIPO:
![201098868-304f48c9-9140-4421-af94-b924c82717c5](https://user-images.githubusercontent.com/94828604/201915310-01363382-b230-48e7-abd1-1cbf06403a96.png)










TIMING DIGRAMS FOR SHIFT REGISTERS:
SIPO:
![201099533-4fec1410-f897-405c-a311-4d25e769e162](https://user-images.githubusercontent.com/94828604/201915464-9f0160d0-0cd3-4db7-9062-137ec7f47e0f.png)
PISO:
![201103017-02a474ad-cc58-4293-907b-7c923b12da61](https://user-images.githubusercontent.com/94828604/201915582-7d21abe4-7cbf-41cd-b858-14cf83873527.jpg)
PIPO:
![201103045-f016f980-09ea-4c24-8889-75db3bf5b701](https://user-images.githubusercontent.com/94828604/201916184-385bf78a-4f31-413e-8f76-7c0c874d49c7.jpg)



RESULTS:
Therefore PISO,PIPO,PISO are implemented succesfully using verilog and validated their functionality using their functional tables.

