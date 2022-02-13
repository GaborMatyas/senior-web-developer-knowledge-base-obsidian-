# Assignment Operators

[Operators and Expressions in MDN documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators)


- [Assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Assignment)`x = f()`
- [Addition assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Addition_assignment)`x += f()` or `x = x + f()`
- [Subtraction assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Subtraction_assignment)`x -= f()` or `x = x - f()`
- [Multiplication assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Multiplication_assignment)`x *= f()` or `x = x * f()`
- [Division assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Division_assignment)`x /= f()` or `x = x / f()`
- [Remainder assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Remainder_assignment)`x %= f()` or `x = x % f()`
- [Exponentiation assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Exponentiation_assignment)`x **= f()` or `x = x ** f()`
- [Left shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Left_shift_assignment)`x <<= f()` or `x = x << f()`
- [Right shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Right_shift_assignment) `x >>= f()` or `x = x >> f()`
- [Unsigned right shift assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift_assignment)`x >>>= f()` or `x = x >>> f()`
- [Bitwise AND assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_AND_assignment)`x &= f()` or `x = x & f()`
- [Bitwise XOR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_XOR_assignment)`x ^= f()` or `x = x ^ f()`
- [Bitwise OR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_OR_assignment)`x |= f()` or `x = x | f()`

## From ECMAScript 2021
[Logical AND assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_AND_assignment)`x &&= f()` or `x && (x = f())`
The logical AND assignment (`x &&= y`) operator only assigns if `x` is [truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy).
```js
	let a = 1;
	let b = 0;
	
	a &&= 2;
	console.log(a);
	// expected output: 2
	
	b &&= 2;
	console.log(b);
	// expected output: 0
	
```

[Logical OR assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR_assignment)`x ||= f()` or `x || (x = f())`
The logical OR assignment (`x ||= y`) operator only assigns if `x` is [falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy).
```js
	const a = { duration: 50, title: '' };
	
	a.duration ||= 10;
	console.log(a.duration);
	// expected output: 50
	
	a.title ||= 'title is empty.';
	console.log(a.title);
	// expected output: "title is empty"
```

[Logical nullish assignment](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_nullish_assignment)
The logical nullish assignment (`x ??= y`) operator only assigns if `x` is [nullish](https://developer.mozilla.org/en-US/docs/Glossary/Nullish) (`null` or `undefined`).
```js
	const a = { duration: 50 };
	
	a.duration ??= 10;
	console.log(a.duration);
	// expected output: 50
	
	a.speed ??= 25;
	console.log(a.speed);
	// expected output: 25
```