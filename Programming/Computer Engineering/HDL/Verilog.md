Defining a module ... 

```verilog 
module example(a , b, c , y) 
{
	input a ;
	input b ;
	input c ;
	output y ;
}

endmodule
```
1) Module declaration : similar to the function signature 
2) Arguments 
3) Port types , whether they are input or output 
**You can also define Busses** : 
```verilog
module example(a , b, c , y) 
{
	input [31 : 0] a ; // 32bit bus 
	output [15: 8] b ; // 8bit bus 
}

endmodule
```

This end-start syntax is preferred to the start-end syntax usually used within array definitions . Similar to python how we can string slice , we can apply the same methodology to busses . 
```verilog 
module example(a , b  , c, y)
{
	wire[31 : 0] longbus  ; 
	wire[7 : 0] shortbus ; 
	assign shortbus = longbus[12 : 5] // 7 bits long 
}
```
## Number representation in Verilog 
## N'bxx 
- Where N is the number of bits 
- b is the base 
- xx is the number 
Default is 32bits 

## Implementing Sequential Logic In Verilog 


[[Assembly]]