# verilog-code-for-64-bit-full-adder
64 bit full adder Verilog code using for loop 
// name - Prince Gupta
// email - pgph20142@student.nitw.ac.in

`timescale 1ns / 1ps


module sixty4_bit_FA(a,b,ci,s,co ); // for 64 bit full adder 
parameter size=64;                  // parameter upto 64 bit
input [size-1:0] a,b;               // vector innput 
input ci;                           //carry in
output co;                          // carry out
output [size-1:0] s;                // output bits
wire [size:0] carry;                // wire for inter connection
genvar i;
assign carry[0]=ci;
assign co=carry[size];
generate
for (i=0; i<size; i=i+1) 
begin: FA
fulladder(s[i],carry[i+1],a[i],b[i],carry[i]); //instantiatiating the full adder 
end
endgenerate

endmodule

//// creating the full adder which I have intantiated above

module fulladder(sum,carry,A,B,Cin);
output sum,carry;
input A,B,Cin;
wire w1,w2,w3;
xor g1(w1,A,B);
and g2(w2,A,B);
xor g3(sum,w1,Cin);
and g4(w3,w1,Cin);
xor g5(carry,w2,w3);

endmodule
