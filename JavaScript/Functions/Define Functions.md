# Define Functions

```js
	function createFunction1(parameter1) {
	    let x = 20 + parameter1;
	    return x;
	}
```

## Shadowing
A globally available [[Const, Let, Var#const|const]] or [[Const, Let, Var#let|let]] variable can be redeclared in a block, and the new variable will be a whole new independent entity. 