```verilog
module lfsr_rst_n ( input wire clk, rst,
                   output reg [3:0] op);
  
  always @ (posedge clk) begin
  if(rst == 0)
    op <= 4'b1111;
  else
    op <= {op[2:0] ,(op[3] ^ op[2])};
  end
endmodule
