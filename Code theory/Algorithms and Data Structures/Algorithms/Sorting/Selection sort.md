# Selection Sort
Selection Sort, while relatively simple to comprehend and implement, unfortunately lags behind other sorting algorithms like Quick Sort, Heap Sort, and Merge Sort for larger data sets.

However, since Selection Sort functions in-place and requires no auxiliary memory, it does have a space advantage over some other more complicated algorithms.

Generally speaking, [Insertion Sort](https://dev.to/seanwelshbrown/implementing-an-insertion-sort-algorithm-in-javascript-19de) is likely to be a more performant alternative, although Selection Sort is still important to know and understand as a programmer and computer scientist.

Selection Sort has a _best case_, _worst case_, and _average case_ `runtime complexity of O(n^2), meaning it will always be quadratic in nature.`


### Steps:
We are setting the `minIndex` as a first index and loop through the array. 
If the current index's value is less than the previously setted `minIndex`'s value we are saving the index of this position. After the first iteration we have the smallest value's index. And we are swapping the two values. The smallest value comes to the initially saved index (in the beginning of the iteration) and the value of this initially saved index goes for the smallest values's place. 

```js
function selectionSort(array) {
  for (let i = 0; i < array.length - 1; i++) {

    let minIndex = i;
    for (let j = i + 1; j < array.length; j++) {
      if (array[j] < array[minIndex]) {
        minIndex = j;
      }     
    }
	// swapping the values with JS ES6
    [array[i], array[minIndex]] = [array[minIndex], array[i]];
  }
  return array;
}
```