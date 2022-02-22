You can use `await` in a `reduce` callback, but you have to remember to `await` the accumulator first!

```js
const reduceLoop = async _ => {
  console.log('Start')

  const sum = await fruitsToGet.reduce(async (promisedSum, fruit) => {
    const sum = await promisedSum
    const numFruit = await getNumFruit(fruit)
    return sum + numFruit
  }, 0)

  console.log(sum)
  console.log('End')
}
```

The simplest (and most efficient way) to use `await` in reduce is to:

1.  Use `map` to return an array promises
2.  `await` the array of promises
3.  `reduce` the resolved values

```js
const reduceLoop = async _ => {
  console.log('Start')

  const promises = fruitsToGet.map(getNumFruit)
  const numFruits = await Promise.all(promises)
  const sum = numFruits.reduce((sum, fruit) => sum + fruit)

  console.log(sum)
  console.log('End')
}
```