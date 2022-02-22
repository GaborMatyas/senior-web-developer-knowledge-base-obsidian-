# Define Functions


### Function declaration / Function statement
Javascript hoists this function to the top. It acts like the function would be defined in the top of the file. So you can call the functions before you declared them. 
```js
	function createFunction1(parameter1) {
	    let x = 20 + parameter1;
	    return x;
	}
```


### Function expression 
This is also hoisted to the top but it is not initialized. Can not be used before defined. 
```js
const functionStart = function (){
	console.log('hello');
}
```


## Shadowing
A globally available [[Const, Let, Var#const|const]] or [[Const, Let, Var#let|let]] variable can be redeclared in a block, and the new variable will be a whole new independent entity. 