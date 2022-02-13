```js
	const mapLoop = async _ => { 
		console.log('Start') 
		const promises = fruitsToGet.map(async fruit => { 
			const numFruit = await getNumFruit(fruit) 
			return numFruit 
		}) 
		const numFruits = await Promise.all(promises) 
		console.log(numFruits) 
		console.log('End') 
	}
```


You can manipulate the value you return in your promises if you wish to. The resolved values will be the values you return.

```js
const mapLoop = async _ => {
  // ...
  const promises = fruitsToGet.map(async fruit => {
    const numFruit = await getNumFruit(fruit)
    // Adds onn fruits before returning
    return numFruit + 100
  })
  // ...
}
```

OR a more compact way:

```js
const asyncUppercase = item =>
  new Promise(resolve =>
    setTimeout(
      () => resolve(item.toUpperCase()),
      Math.floor(Math.random() * 1000)
    )
  );

const uppercaseItems = () => {
  const items = ['a', 'b', 'c'];
  return Promise.all(
    items.map(async item => {
      const uppercaseItem = await asyncUppercase(item);
      console.log(uppercaseItem);
    })
  ).then(() => {
    console.log('Items processed');
  });
};
// LOGS: 'A', 'C', 'B', 'Items processed'
```