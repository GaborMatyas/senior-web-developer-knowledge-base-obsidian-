# Strategy Pattern


It solves the problem that can be occurred once the inheritance is overused in your codebase. 

### Problems: 
- Once you are starting to override the inherited methods of your superclass, you are loosing the whole benefints of inheritance. 
- If the overrided behaviour should be there in more subclasses, it leads code duplication in these classes. 
- It is hard to gain knowledge of all the subclasses plus the superclass because the methods are different in lots of places. 
- A simple change in the superclass could lead unexpected behaviours in the subclasses. 

*The inheritance does not work wll when behaviour changes across subclasses and it is not appropriate for all subclasses to have all behaviours.*

### Solution:
`Use composation over Inheritance`

If some aspect of your code is changing, that is a sign you should pull it out and separate it.
By srpatating out the parts of your code that change, you can extend or alter them without affecting the rest of your code. 

*Program to an Interface, not an Implementation*

Create a interfaces for the different methods, and write the concrete different implementations of these interfaces as methods outside of the classes then pass these implementations to the constructor of the subclasses (code reuseability) when they need to implement an interface.  

![[Strategy pattern.png]]

