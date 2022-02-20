# Insertion sort
It builds up the sort by gradually creating a larger left portion which is always sorted.
It places instantly each element to its 'final' place in the sorted portion of the array. 

## Performance
Being one of the fastest quadratic sorting algorithms, Insertion Sort usually outperforms [[Bubble Sort]], Gnome Sort and [[Selection Sort]]. In addition to that, when our input array size is very small (10-20 elements), Insertion Sort can even outperform Quicksort and Merge Sort.

This is why JavaScript, despite using Quicksort (`in Chrome`) or Merge Sort (`in Mozilla`) as the primary sorting algorithm, also uses Insertion Sort on small collections - and after Quicksort/Merge Sort has done the bulk of the work.

### Application: 
This really comes in handy when we want to add more elements in an already sorted array, because Insertion Sort will add the new elements in their proper places without resorting the entire collection.
This means that Insertion Sort works wonders when it comes to checking whether or not the array is sorted.

### Steps

```[5, 2, 4, 6, 1, 3]```

-   The first element in our unsorted array is 2.
-   2 < 5, so we move 5 one place to the right.

> Sorted array: _, 5

-   2 is placed in its right spot.

**Second Iteration:**

> Sorted array: 2, 5  
> Unsorted array: 4, 6, 1, 3

-   The first element in our unsorted array is 4.
-   4 < 5, so we move 5 one place to the right.

> Sorted array: 2, _, 5

-   4 !< 2, so we don't move 2.
-   4 is placed in its right spot.

**Third Iteration:**

> Sorted array: 2, 4, 5  
> Unsorted array: 6, 1, 3

-   The first element in our unsorted array is 6.
-   6 !< 5, so we don't move 5.

> Sorted array: 2, 4, 5

-   6 is placed in its right spot.

This is repeated until we're greeted with a sorted array: `1, 2, 3, 4, 5, 6`.

We can notice an invariant in each of these iterations. For the `k-th` iteration of our loop, the interval of `[0,k]` is guaranteed to be sorted.


### Implementation:
```js
function insertionSort(inputArr) {
	for (let i = 1; i < inputArr.length; i++) {
		// Choosing the first element in our unsorted subarray
		let current = inputArr[i];
		// The last element of our sorted subarray
		let j = i-1; 
		while ((j > -1) && (current < inputArr[j])) {
			inputArr[j+1] = inputArr[j];
			j--;
		}
		inputArr[j+1] = current;
	}
    return inputArr;
}
```
