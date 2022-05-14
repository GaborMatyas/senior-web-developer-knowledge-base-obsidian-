# Binary search


The Big O notation for Binary Search is **O(log N)**. In contrast to O(N) which takes an additional step for each data element, O(log N) means that the algorithm takes an additional step each time the data doubles.

The time complexity of the binary search algorithm is **O(log n)**. The best-case time complexity would be O(1) when the central index would directly match the desired value.
```js
const binarySearch = (sortedArray, key) => {
    let start = 0;
    let end = sortedArray.length - 1;

    while (start <= end ) {
        let middle = Math.floor((start + end) / 2);

        if (sortedArray[middle] === key) {
            // found the key
            return middle;
        } else if (sortedArray[middle] < key) {
            // continue searching to the right
            start = middle + 1;
        } else {
            // search searching to the left
            end = middle - 1;
        }
    }
	// key wasn't found
    return -1;
}
```

