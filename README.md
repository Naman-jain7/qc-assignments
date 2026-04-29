CP:  
cp(pi) q[0], q[1];  


CCZ gate:  
h q[2];  
ccx q[0], q[1], q[2];  
h q[2];  

4 qubit GHZ:  
h q[0];  
cx q[0], q[1];  
cx q[1], q[2];  
cx q[2], q[3];  

