```verilog
module tb_lfsr_rst_n;
  reg clk ,rst;
  wire [3:0] op;
  
  lfsr_rst_n DUT (clk,rst,op);
  
  always #2 clk= ~clk;
  
  initial begin
    $monitor ("time=%0t,clk=%b,rst=%b | op",$time,clk,rst,op);
    clk=0;
    rst=0;
    
    #5 rst= 1;
    #10 ;
    $finish;
  end
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
  end
endmodule
