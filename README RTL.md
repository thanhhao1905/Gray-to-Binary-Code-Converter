```verilog
module g2b_converter #(parameter N = 4)(input wire [N-1:0] gray,
                                        output wire [N-1:0] binary);
  
  genvar i;
  generate
    for(i=0;i<N-1;i=i+1) begin
      assign binary[i] = ^(gray>>1);
    end
  endgenerate
endmodule
