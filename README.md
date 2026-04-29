## CP:  
cp(pi) q[0], q[1];  


## CCZ gate:  
h q[2];  
ccx q[0], q[1], q[2];  
h q[2];  

## 4 qubit GHZ:  
h q[0];  
cx q[0], q[1];  
cx q[1], q[2];  
cx q[2], q[3];  

## Toffoli
### AND = Toffoli(A,B,0)
ccx q[0], q[1], q[2];  
measure q[2] -> c[0];  

### OR = NOT(NOT A AND NOT B)
x q[0];  
x q[1];  

ccx q[0], q[1] q[2];  

x q[2];  
measure q[2]->c[0];  

### NOT = Toffoli(1,1,A)
x q[0];  
x q[1];  
ccx q[0], q[1], q[2];  

## Fredkin
### AND = if control=A, swap(B,0)
cswap q[0], q[1], q[2];  
measure q[2] -> c[0];  


### OR = if control=A, swap(1,B)
x q[1];  
cswap q[0], q[1], q[2];  
measure q[2] -> c[0];  

### NOT = if control=1, swap(A, B)
x q[0];  
cswap q[0], q[1], q[2];  
measure q[2] -> c[0];  

## half adder
ccx q[0], q[1], q[2];   // carry  
cx q[0], q[1];  
measure q[1] -> c[0]; // Sum  
measure q[2] -> c[1]; // Carry  

## full adder
ccx q[0], q[1], q[3];  
cx q[0], q[1];  
ccx q[1], q[2], q[3];  
cx q[1], q[2];  
measure q[2] -> c[0]; // Sum  
measure q[3] -> c[1]; // Carry  

## boolean func
