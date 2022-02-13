Combining async with a for (or a for...of ) loop is possibly the most straightforward option when performing asynchronous operations over array elements. Using await inside a for loop will cause the code to stop and wait for the asynchronous operation to complete before continuing.

```js
	const forLoop = async _ => { 
		console.log('Start') 
		for (let index = 0; index < fruitsToGet.length; index++) { 
			const fruit = fruitsToGet[index] 
			const numFruit = await getNumFruit(fruit) 
			console.log(numFruit)
		} 
		console.log('End') 
	}
```