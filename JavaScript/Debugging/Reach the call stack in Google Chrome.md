# Reach the call stack in Google Chrome

In Google Chrome browser just visit the developer tools / sources tab. 
If you use breakpoints in your file and stop the execution, the `call stack` is available in the user interface. 
This is not the full stack, because it manages also short living variables, but here we can find only the function calls (hence `call` stack).

![[Pasted image 20220213125825.png]]