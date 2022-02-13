## const
The `const` keyword was introduced in [ES6 (2015)](https://www.w3schools.com/js/js_es6.asp).

As a general rule, always declare a variable with `const` unless you know that the value will change.
Definitely use `const` when you declare:
-   A new Array
-   A new Object
-   A new Function
-   A new RegExp

#### Reassigning
The value which is stored in this kind of variable can NOT change its value.
It does not define a constant value. It defines a constant reference to a value.
Because of this you can NOT:
-   Reassign a constant value
-   Reassign a constant [[Array]]
-   Reassign a constant [[Objects]]

But you CAN:
-   Change the elements of constant [[Array]]
```js
	// You can create a constant array:  
	const cars = ["Saab", "Volvo", "BMW"];  
	  
	// You can change an element:  
	cars[0] = "Toyota";  
	  
	// You can add an element:  
	cars.push("Audi");


	// But you can NOT reassign the array:
	const cars = ["Saab", "Volvo", "BMW"];  
  
	cars = ["Toyota", "Volvo", "Audi"]; // ERROR

```
-   Change the properties of constant [[Objects]]
```js
	// You can create a const object:  
	const car = {type:"Fiat", model:"500", color:"white"};  
	  
	// You can change a property:  
	car.color = "red";  
	  
	// You can add a property:  
	car.owner = "Johnson";


	// But you can NOT reassign the object:
	const car = {type:"Fiat", model:"500", color:"white"};  
	  
	car = {type:"Volvo", model:"EX60", color:"red"}; // ERROR

```

A `const` variable cannot be reassigned:
```js
	const PI = 3.141592653589793;  
	PI = 3.14; // This will give an error  
	PI = PI + 10; // This will also give an error
```

JavaScript `const` variables must be assigned a value when they are declared:
```js
	//correct
	const PI = 3.14159265359; 

	// incorrect
	const PI2;  
	PI2 = 3.14159265359;
	
```

The `const` can NOT initialized without starting value. 

#### Browser support
The `const` keyword is not fully supported in Internet Explorer 10 or earlier.

#### Redeclaration
Variables defined with `const` cannot be Redeclared in the same scope:
```js
	const x = "John Doe";  
	const x = 0;  
// SyntaxError: 'x' has already been declared
```

Redeclaring a variable using the `const` in different scopes, can solve the global scope problem of `var`.
Redeclaring a variable inside a block will not redeclare the variable outside the block 
(Redeclaring a variable with `const`, in another block, IS allowed):
```js
	const x = 10;  
	// Here x is 10  
	  
	{  
	const x = 2;  
	// Here x is 2  
	}  
	  
	// Here x is 10
```

#### Scope
Variables defined with `const` must be Declared before use.
Variables defined with `const` have Block Scope.

#### [[Hoisting WIP]]
Variables defined with `const` are also hoisted to the top of the block just like `var`, but not initialized. 
Meaning: Using a `const` variable before it is declared will result in a `ReferenceError`:
```js
	carName = "Saab";  // ReferenceError
	const carName = "Volvo";
```


## let
The `let` keyword was introduced in [ES6 (2015)](https://www.w3schools.com/js/js_es6.asp).

The value which is stored in this kind of variable can change. 
The `let` can initialized without any starting value. 

#### Browser support
The `let` keyword is not fully supported in Internet Explorer 11 or earlier.

#### Redeclaration
Variables defined with `let` cannot be Redeclared in the same scope:
```js
	let x = "John Doe";  
	let x = 0;  
// SyntaxError: 'x' has already been declared
```

Redeclaring a variable using the `let` in different scopes, can solve the global scope problem of `var`.
Redeclaring a variable inside a block will not redeclare the variable outside the block 
(Redeclaring a variable with `let`, in another block, IS allowed):
```js
let x = 10;  
// Here x is 10  
  
{  
let x = 2;  
// Here x is 2  
}  
  
// Here x is 10
```

#### Scope
Variables defined with `let` must be Declared before use.
Variables defined with `let` have Block Scope.

#### [[Hoisting WIP]]
Variables defined with `let` are also hoisted to the top of the block just like `var`, but not initialized. 
Meaning: Using a `let` variable before it is declared will result in a `ReferenceError`:
```js
	carName = "Saab";  // ReferenceError
	let carName = "Volvo";
```


## var
TL;DR: Do not use `var` in you applications! Use `let` and `const` instead. 

#### Redeclaration
Variables defined with `var` can BE Redeclared.
```js
	var x = "John Doe";  
  
	var x = 0;
```

Redeclaring a variable using the `var` keyword can impose problems.
Redeclaring a variable inside a block will also redeclare the variable outside the block:

```js
var x = 10;  
// Here x is 10  
  
{  
var x = 2;  
// Here x is 2  
}  
  
// Here x is 2
```

#### [[Hoisting WIP]]
Variables defined with `var` are **hoisted** to the top and can be initialized at any time.
Meaning: You can use the variable before it is declared:
```js
// valid js code
	carName = "Volvo";  
	var carName;
```