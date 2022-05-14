# Quick Sort


It works in place, does not make any new arrays. 

Works by selecting one element (called the "pivot") and finding the index where the pivot should end up in the sorted array
Once the pivot is positioned appropriately, quick sort can be applied on either side of the pivot

-   In order to implement merge sort, it's useful to first implement a function responsible arranging elements in an array on either side of a pivot
-   Given an array, this helper function should designate an element as the pivot
-   It should then rearrange elements in the array so that all values less than the pivot are moved to the left of the pivot, and all values greater than the pivot are moved to the right of the pivot
-   The order of elements on either side of the pivot doesn't matter!
-   The helper should do this **in place**, that is, it should not create a new array
-   When complete, the helper should return the index of the pivot


## Big O
- Time Complexity O(n log n) 
		- - the worst is O(n^2) when the pivot is always the smallest or the biggest element, so please try to choose a random number or the middle index as a pivot point to avoid the situation when you have a sorted array already and iterate through it with this algorithm with O(n^2)
- Space Complexity O(log n)


## Pivot Pseudocode
-   It will help to accept three arguments: an array, a start index, and an end index (these can default to 0 and the array length minus 1, respectively)
-   Grab the pivot from the start of the array 
-   Store the current pivot index in a variable (this will keep track of where the pivot should end up)
-   Loop through the array from the start until the end
		-   If the pivot is greater than the current element, increment the pivot index variable and then swap the current element with the element at the pivot index
-   Swap the starting element (i.e. the pivot) with the pivot index
-   Return the pivot index


## Quicksort Pseudocode

-   Call the pivot helper on the array
-   When the helper returns to you the updated pivot index, recursively call the pivot helper on the subarray to the left of that index, and the subarray to the right of that index
-   Your base case occurs when you consider a subarray with less than 2 elements

```js

function pivot(arr, start = 0, end = arr.length - 1) {
	// helper function to swap values when it is smaller than the pivot value
  const swap = (arr, idx1, idx2) => {
    [arr[idx1], arr[idx2]] = [arr[idx2], arr[idx1]];
  };

  // We are assuming the pivot is always the first element
  let pivot = arr[start];
  let swapIdx = start;

  for (let i = start + 1; i <= end; i++) {
    if (pivot > arr[i]) {
      swapIdx++;
      swap(arr, swapIdx, i);
    }
  }

  // Swap the pivot from the start the swapPoint
  swap(arr, start, swapIdx);
  return swapIdx;
}


function quickSort(arr, left = 0, right = arr.length -1){
    if(left < right){
        let pivotIndex = pivot(arr, left, right) //3
        //left
        quickSort(arr,left,pivotIndex-1);
        //right
        quickSort(arr,pivotIndex+1,right);
      }
     return arr;
}

quickSort([100,-3,2,4,6,9,1,2,5,3,23])




// [4,6,9,1,2,5,3]
// [3,2,1,4,6,9,5]
//        4
//  3,2,1    6,9,5
//      3      6
//  2,1      5  9
//    2
//  1
```
