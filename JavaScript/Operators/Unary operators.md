# [Unary operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#unary_operators "Permalink to Unary operators")

## delete
The [`delete`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete) operator deletes an object's property. The syntax is:
```js
	delete object.property;
	delete object[propertyKey];
	delete objectName[index];
```

If the `delete` operator succeeds, it removes the property from the object. Trying to access it afterwards will yield `undefined`. The `delete` operator returns `true` if the operation is possible; it returns `false` if the operation is not possible.

##### Deleting [[Array]] elements
Since [[Array]]s are just [[Objects]]s, it's technically possible to `delete` elements from them. This is however regarded as a bad practice, try to avoid it. When you delete an array property, the array length is not affected and other elements are not re-indexed. To achieve that behavior, it is much better to just overwrite the element with the value `undefined`. To actually manipulate the array, use the various array methods such as [splice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)


## typeof
The `typeof` operator returns a string indicating the type of the unevaluated operand. `operand` is the string, variable, keyword, or object for which the type is to be returned. The parentheses are optional.
```js
	var myFun = new Function('5 + 2');
	var shape = 'round';
	var size = 1;
	var foo = ['Apple', 'Mango', 'Orange'];
	var today = new Date();
	
	typeof myFun;       // returns "function"
	typeof shape;       // returns "string"
	typeof size;        // returns "number"
	typeof foo;         // returns "object"
	typeof today;       // returns "object"
	typeof doesntExist; // returns "undefined"
```