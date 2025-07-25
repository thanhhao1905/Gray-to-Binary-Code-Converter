```verilog
`timescale 1ps/1ps
module tbg2bconverter;
  parameter N=4;
  
  wire [N-1:0] binary;
  reg [N-1:0] exp_binary;
  reg [N-1:0] gray;
  integer err=0;
  integer i,j;
  
  g2b_converter #(N) DUT (gray, binary);
  
  initial begin
    $monitor("time=%0t, gray=%b, binary=%b | exp_binary=%b",$time, gray, binary, exp_binary);
    
    for(i=0;i<2*N;i=i+1)begin
      gray = i;
     
     exp_binary[N-1] = gray[N-1];
     for(j=N-2; j>=0; j=j-1)begin
        exp_binary[j] = exp_binary[j+1] ^ gray[j];
       #5
       check(binary, exp_binary);
     end
    end
    
    if(err==0) begin
      $display("-----------");
      $display("Test Pass");
      $display("-----------");
    end else begin
      $display("-----------");
      $display("Test false with %d error",err);
      $display("-----------");
    end
    
     $finish;
  end
        
      task check(input [N-1:0]binary, input [N-1:0]binary)
        begin
          if(binary !== exp_binary) begin
            $display("[CHECK] : ERROR");
            err= err+1;
          end else begin
            $display("[CHECK] : MATCHING");
          end
        end
      endtask
      
      initial begin
        $dumpfile(dump.vcd);
        $dumpvars;
      end
    endmodule
          
          
