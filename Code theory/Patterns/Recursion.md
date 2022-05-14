# Recursion

## Normal recursion
The space complexity is O(n) because potenitially the function calls itself as much as much items we have. All these function calls are in the stack in mostly in the same time. 
Note: the factorial of zero is `1`.
```js
	const recFactorial = (n) => {
	    if (n =< 1) {
			return 1;
		} 
		return n * recFactorial(n-1);
	}
```


## Tail recursion
The normal revursion has at least O(n) space complexity. 
With tail recursion the space is O(1).
```js
	const tailRecursionFactorial = (n, totalSoFar = 1) => {
	    if (n === 0) {
			return totalSoFar;
		} 
		return tailRecursionFactorial(n-1, totalSoFar * n);
	}
```
In this case the tailRecursionFactorial function does not wait any new instace of the function. 
Here a new function call is returned. 
`Important, that javascript unfortunatelly will use O(n) because it does not support tail recursion :(`

