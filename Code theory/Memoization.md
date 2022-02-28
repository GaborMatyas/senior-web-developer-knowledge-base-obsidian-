# Memoization

Storing the results of expensive function calls and returning the cached result when the same inputs occur again.

## A Finobacci calculator with memoization
The BigO of this function is O(n)
```js
	function fib(n, memo=[undefined, 1, 1]){

		if(memo[n] !== undefined) return memo[n]

		const res = fib(n-1, memo) + fib(n-2, memo);

		memo[n] = res;
		
		return res;
	}
```