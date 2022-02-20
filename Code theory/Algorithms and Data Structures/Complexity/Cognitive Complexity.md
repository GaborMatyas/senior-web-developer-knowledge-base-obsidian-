This measures the amount of cognitive effort required to understand the code’s flow. You compute cognitive complexity similarly to cyclomatic complexity. 

However, it doesn’t increment with **if** statements that have logical operators in them. 

Cognitive complexity only increments once with switch cases, but it does increment complexity with nested flow breaks.

1.  Try to use Anonymous Object instead of the creation of variables.
3.  Refactor your code.
4.  Reduce No. of parameters of the method.