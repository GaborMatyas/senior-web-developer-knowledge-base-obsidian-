# Optional Chaining

The **optional chaining** operator (**`?.`**) enables you to read the value of a property located deep within a chain of connected objects without having to check that each reference in the chain is valid.

The `?.` operator is like the `.` chaining operator, except that instead of causing an error if a reference is [nullish](https://developer.mozilla.org/en-US/docs/Glossary/Nullish) ([`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null) or [`undefined`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/undefined)), the expression short-circuits with a return value of `undefined`. When used with function calls, it returns `undefined` if the given function does not exist.

***IMPORTANT: Optional chaining cannot be used on a non-declared root object, but can be used with an undefined root object.***

```js
	const adventurer = {
	  name: 'Alice',
	  cat: {
	    name: 'Dinah'
	  }
	};
	
	const dogName = adventurer.dog?.name;
	console.log(dogName);
	// expected output: undefined
	
	console.log(adventurer.someNonExistentMethod?.());
	// expected output: undefined
	
	
	obj.val?.prop
	obj.val?.[expr]
	obj.arr?.[index]
	obj.func?.(args)
```

### [Optional chaining with function calls](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining#optional_chaining_with_function_calls "Permalink to Optional chaining with function calls")

You can use optional chaining when attempting to call a method which may not exist. This can be helpful, for example, when using an API in which a method might be unavailable, either due to the age of the implementation or because of a feature which isn't available on the user's device.

Using optional chaining with function calls causes the expression to automatically return `undefined` instead of throwing an exception if the method isn't found:

```js
let result = someInterface.customMethod?.();
```
**Note:** If there is a property with such a name and which is not a function, using `?.` will still raise a [`TypeError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) exception (`someInterface.customMethod is not a function`).

**Note:** If `someInterface` itself is `null` or `undefined`, a [`TypeError`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypeError) exception will still be raised (`someInterface is null`). If you expect that `someInterface` itself may be `null` or `undefined`, you have to use `?.` at this position as well: `someInterface?.customMethod?.()`

```js
	// Using optional chaining with function calls
	function doSomething(onContent, onError) {
	  try {
	   // ... do something with the data
	  }
	  catch (err) {
	    onError?.(err.message); // no exception if onError is undefined
	  }
	}
```

### [Combining with the nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining#combining_with_the_nullish_coalescing_operator "Permalink to Combining with the nullish coalescing operator")

The [nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator) may be used after optional chaining in order to build a default value when none was found:

```js
	let customer = {
	  name: "Carl",
	  details: { age: 82 }
	};
	const customerCity = customer?.city ?? "Unknown city";
	console.log(customerCity); // Unknown city
```