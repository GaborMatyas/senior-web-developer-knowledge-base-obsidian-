# How is JavaScript Executed?

It need a Javascript Engine, like V8 in Chrome or SpiderMonkey in Firefox. 

They parse the code and compile to machine code which is faster to execute on the machine, and than executes the code. 

Modern engines have a lot of built-in optimization technics.  

[[Embed Javascript to HTML]]

## Interpreter
Parsing the code and convert it to bytecode. It pushes this bytecode format to the compiler. 

## Compiler
The compiler optimize the code and executes it in a lower machine level. 

Optimization: For example if a previously executed code has not changed at all since the last execution the compiler will skip the compilation process and uses the older compiled version of this code segment. 

### Just in time compilation:
The compiler starts compiling + executing the compiled code while the code is being read. 

The interpreter and the compiler are also included in the browsers. 


## Inside the JavaScript Engine

### Heap
Stores data in your system memory and manages access to it (Long term data).
It stores the functions as well until their execution. When the function is called, the stack is getting active. 

### Stack
This is the execution context. Manages your program flow: the function calls and communication (Short term "memory"). The function executions are stored here in a specific order. (LIFO)

[[Reach the call stack in Google Chrome]]

### A function execution process with the heap and the stack
The executable function (from now on `greet()`) is pushed to the top of the stack. The component on the top of the stack is the current one. 
![[Pasted image 20220213124438.png]]

![[Pasted image 20220213124334.png]]

This function calls a new function, the `getName()` in the 6th line, so this function has to be pushed to the top of the stack. 
![[Pasted image 20220213124611.png]]

`getName` calls the built-in `prompt()` function in the 2nd line, so this will be on the top of our stack at the end of this chain.
![[Pasted image 20220213124732.png]]

When `prompt` is executing, it is removed from the stack. 
![[Pasted image 20220213124828.png]]

Important note: This does not mean that the function definition has been removed from the heap as well. The heap is a long term memory during the work. 

The `getName` function receives the returned value from the `prompt` so it is also removed from the stack. 
![[Pasted image 20220213125030.png]]

The `greet` function has no return value explicitly, but once the last code line is finished inside this function, it will return anyway so it is popped from the stack too. When Javascript sees a `return` keyword or the function is ended, it pops the function from call stack. 
![[Pasted image 20220213125146.png]]

The anonymous function was responsible for running our code, and since there are no other lines to work with, this is also removed from the heap an we are done. 
![[Pasted image 20220213125300.png]]

### Garbage Collector
This is the part of the Javascript engine. Periodically checks the [[How is JavaScript Executed#Heap|heap]] for unused objects and removes them. (These are the objects without references).

### Memory Leaks
When you have an unused objects but still have a reference for it.

