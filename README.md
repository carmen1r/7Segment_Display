# 7Segment_Display

module adder ( input wire [2:0] in0_a,
					input wire [2:0] in1_a,
					output wire [3:0] out0_a
					);
			
assign out0_a = in0_a + in1_a;

endmodule

module transcoder ( input wire [3:0] in0_t,
						  output reg [6:0] out0_t
							);
							
always @(*)
begin
	case (in0_t)
			0: 
			begin 
				out0_t = 7'b0000001; 
			end
			
			1: 
			begin 
				out0_t = 7'b1001111; 
			end
			
			2: 
			begin 
				out0_t = 7'b0010010; 
			end
			
			3: 
			begin 
				out0_t = 7'b0000110; 
			end
			
			4: 
			begin 
				out0_t = 7'b1001100; 
			end
			
			5: 
			begin 
				out0_t = 7'b0100100; 
			end
			
			6: 
			begin 
				out0_t = 7'b0100000; 
			end
			
			7: 
			begin 
				out0_t = 7'b0001111; 
			end
			
			8: 
			begin 
				out0_t = 7'b0000000; 
			end
			
			9: 
			begin 
				out0_t = 7'b0000100; 
			end
			
			11: 
			begin 
				out0_t = 7'b0001000; 
			end
			
			12: 
			begin 
				out0_t = 7'b1100000; 
			end
			
			13: 
			begin 
				out0_t = 7'b0110001; 
			end
			
			14: 
			begin 
				out0_t = 7'b1000010; 
			end
			
			15: 
			begin 
				out0_t = 7'b0110000; 
			end
			
			16: 
			begin 
				out0_t = 7'b0111000; 
			end
	endcase
end

endmodule

module top ( input wire [2:0] in0_top,
				 input wire [2:0] in1_top,
				 output wire [6:0] out0_top
				);

wire connector_gate1_gate2;				
				
adder gate1 (.in0_a(in0_top),
				 .in1_a(in1_top),
				 .out0_a(connector_gate1_gate2)
				);
				
transcoder gate2 (.in0_t(connector_gate1_gate2),
				 .out0_t(out0_top)
				);
				
endmodule
