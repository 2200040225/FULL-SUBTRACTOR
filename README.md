# FULL-SUBTRACTOR

Design code:


//gate level modeling


module fs(
input a,b,bin,
output d,bout
);
wire w1,w2,w3,w4;
xor(d,a,b,bin);
not(w1,a);
and(w2,w1,bin);
and(w3,w1,b);
and(w4,b,bin);
or(b,w2,w3,w4);
endmodule

//data flow deassign

module fs(
input a,b,bin,
output d,bout
);
assign d=a^b^bin;
assign bout = (~a&b)|(~a&bin)|(b&bin);
endmodule


Test Bench :


module fs_tb();
reg a,b,bin;
wire d,bout;
fs uut(a,b,bin,d,bout);
initial 
begin
a=0;b=1;bin=1;
#10
a=1;b=1;bin=1;
#10
a=0;b=0;bin=1;
#10
a=0;b=1;bin=0;
#10
end
$finish();
endmodule




