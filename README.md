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
x q[2];

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
### (x ∧ y) ∨ z
ccx q[0], q[1], q[3]; // x AND y  
x q[3]; x q[2];  
ccx q[3], q[2], q[4]; // OR  
x q[4];  
measure q[4] -> c[0];  

### (x ∧ y) ∨ (y ∧ z)  
ccx q[0], q[1], q[3]; // x AND y  
ccx q[1], q[2], q[4]; // y AND z  
x q[3]; x q[4]; x q[5];  
ccx q[3], q[4], q[5]; // OR the results  
x q[5];  
measure q[5] -> c[0];  

### (x ∧ y) ⊕ z
ccx q[0], q[1], q[2]; // (x AND y) XOR z
measure q[2] -> c[0];

### (x ∧ y) ∨ (x ∧ z) ∨ (y ∧ z)
qreg q[7]; 
creg c[1];
ccx q[0], q[1], q[3]; // xy
ccx q[0], q[2], q[4]; // xz
ccx q[1], q[2], q[5]; // yz

x q[3]; x q[4]; x q[5];
mcx q[3], q[4], q[5], q[6];
x q[6];
measure q[6] -> c[0];
