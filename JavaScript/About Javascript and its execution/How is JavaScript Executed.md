# How is JavaScript Executed?

It need a Javascript Engine, like V8 in Chrome or SpiderMonkey in Firefox. 

They parse the code and compile to machine code which is faster to execute on the machine, and than executes the code. 

Modern engines have a lot of built-in optimization technics.  

## Interpreter
Parsing the code and convert it to bytecode. It pushes this bytecode format to the compiler. 
## Compiler
The compiler optimize the code and executes it in a lower machine level. For example if a previously executed code has not changed at all since the last execution the compiler will skip the compilation process and uses the older compiled version of this code segment. 

### Just in time compilation:
The compiler starts compiling + executing the compiled code while the code is being read. 

The interpreter and the compiler are also included in the browsers. 




[[Embed Javascript to HTML]]