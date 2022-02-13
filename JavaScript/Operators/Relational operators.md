# Relational operators

A relational operator compares its operands and returns a Boolean value based on whether 
the comparison is true.

## in
The [`in` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/in) returns `true` if the specified property is in the specified object. The syntax is:

```
propNameOrNumber in objectName
```

where `propNameOrNumber` is a string, numeric, or symbol expression representing a property name or array index, and `objectName` is the name of an object.

The following examples show some uses of the `in` operator.

```js
	// Arrays
	var trees = ['redwood', 'bay', 'cedar', 'oak', 'maple'];
	0 in trees;        // returns true
	3 in trees;        // returns true
	6 in trees;        // returns false
	'bay' in trees;    // returns false (you must specify the index number,
	                   // not the value at that index)
	'length' in trees; // returns true (length is an Array property)
	
	// built-in objects
	'PI' in Math;          // returns true
	var myString = new String('coral');
	'length' in myString;  // returns true
	
	// Custom objects
	var mycar = { make: 'Honda', model: 'Accord', year: 1998 };
	'make' in mycar;  // returns true
	'model' in mycar; // returns true
```