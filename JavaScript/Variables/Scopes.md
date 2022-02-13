# Scopes
## Block Scope

Before ES6 (2015), JavaScript had only **Global Scope** and **Function Scope**.

ES6 introduced two important new JavaScript keywords: [[Const, Let, Var#let|let]] and [[Const, Let, Var#const|const]].
These two keywords provide **Block Scope** in JavaScript.
Variables declared inside a { } block cannot be accessed from outside the block.

Note: [[Const, Let, Var#var|var]] is not block scoped so it is available from outside of its block.

```js
{  
	let x = 2;  
}  
// x can NOT be used here
```


## Global Scope

In a programming environment, the _global scope_ is the [scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope) that contains, and is visible in, all other scopes.

In client-side JavaScript, the global scope is generally the web page inside which all the code is being executed.

`window` and `document`, for example, are global variables supplied by the browser. In a Node environment, you can access `process` object as a global variable.


## Function Scope

A function in JavaScript defines a scope for variables declared using `var`, `let` and `const`.
Let's declare a `var` variable within a function body:
```js
	function run() {
		// "run" function scope
		var message = 'Run, Forrest, Run!';
		console.log(message); // 'Run, Forrest, Run!'
	}
	
	run();
	console.log(message); // throws ReferenceError
```

`run()` function body creates a scope. The variable `message` is accessible inside of the function scope, but inaccessible outside.

Same way, a function body creates a scope for `let`, `const` and even function declarations.
```js
	function run() {
		// "run" function scope
		const two = 2;
		let count = 0;
		function run2() {}
		console.log(two); // 2
		console.log(count); // 0
		console.log(run2); // function
	}
	
	run();
	console.log(two); // throws ReferenceError
	console.log(count); // throws ReferenceError
	console.log(run2); // throws ReferenceError
```


## Lexical scope

Let's define 2 functions, having the function `innerFunc()` is nested inside `outerFunc()`.
```js
	function outerFunc() {
		// the outer scope
		let outerVar = 'I am from outside!';
		
		function innerFunc() {
			// the inner scope
			console.log(outerVar); // 'I am from outside!'
		}
		return innerFunc;
	}
	
	const inner = outerFunc();
	inner();
```

Look at the last line of the snippet `inner()`: the `innerFunc()` invokation happens outside of `outerFunc()` scope. Still, how does JavaScript understand that `outerVar` inside `innerFunc()` corresponds to the variable `outerVar` of `outerFunc()`?

The answer is due to lexical scoping.

JavaScript implements a scoping mechanism named lexical scoping (or static scoping). Lexical scoping means that the accessibility of variables is determined statically by the position of the variables within the nested function scopes: _the `innerFunc` scope can access variables from the `outerFunc` scope_.

A formal definition of lexical scope:
In the example, the lexical scope of `innerFunc()` consists of the scope of `outerFunc()`.

Moreover, the `innerFunc()` is a _closure_ because it captures the variable `outerVar` from the lexical scope.


## The closure

The lexical scope allows to access the variables statically of the outer scopes. There's just one step until the closure!

Let's take a look again at the `outerFunc()` and `innerFunc()` example:
```js
	function outerFunc() {
		// the outer scope
		let outerVar = 'I am from outside!';
		
		function innerFunc() {
			// the inner scope
			console.log(outerVar); // 'I am from outside!'
		}
		return innerFunc;
	}
	
	const inner = outerFunc();
	inner();
```

Inside the `innerFunc()` scope, the variable `outerVar` is accessed from the lexical scope. That's known already.
Note that `innerFunc()` invocation happens inside its lexical scope (the scope of `outerFunc()`).
Let's make a change: `innerFunc()` to be invoked outside of its lexical scope: in a function `exec()`. Would `innerFunc()` still be able to access `outerVar`?

Let's make the adjustments to the code snippet:
```js
	function outerFunc() {
		let outerVar = 'I am outside!';
		function innerFunc() {
			console.log(outerVar); // => logs "I am outside!"
		}
	return innerFunc;
	}
	
	function exec() {
		const myInnerFunc = outerFunc();
		myInnerFunc();
	}
	
	exec();
```

Now `innerFunc()` is executed outside of its lexical scope, but exactly in the scope of `exec()` function. And what's important:

_`innerFunc()` still has access to `outerVar` from its lexical scope, even being executed outside of its lexical scope._

In other words, `innerFunc()` _closes over_ (a.k.a. captures, remembers) the variable `outerVar` from its lexical scope.

In other words, `innerFunc()` is a _closure_ because it closes over the variable `outerVar` from its lexical scope.
