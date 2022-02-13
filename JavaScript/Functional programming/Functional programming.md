# Functional programming

## Currying 
Ithappens when a function returns another function until the arguments are fully supplied.

For example:
```js
	function multiply(a) {
		return function executeMultiply(b) {
			return a * b;
		}
	}
	
	const double = multiply(2);
	
	double(3); // => 6
	double(5); // => 10
	
	const triple = multiply(3);
	triple(4); // => 12
```

`multiply` is a curried function that returns another function.

Currying, an important concept of functional programming, is also possible thanks to [[Scopes#The closure|closures]].

`executeMultiply(b)` is a closure that captures `a` from its lexical scope. When the closure is invoked, the captured variable `a` and the parameter `b` are used to calculate `a * b`.