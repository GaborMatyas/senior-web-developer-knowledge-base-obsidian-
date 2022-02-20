# Bubble sort
We have an unsorted array **arr = [ 1, 4, 2, 5, -2, 3 ]** the task is to sort the array using bubble sort. 

Bubble sort compares the element from index 0 and if the 0th index is less than 1st index then the values get swapped and if the 0th index is less than the 1st index then nothing happens.

then, the 1st index compares to the 2nd index then the 2nd index compares to the 3rd, and so on…

## Complexities

#### Worst Case and Average case time complexity 

If the array is in reverse order then this condition is the worst case and Its time complexity is **O(n2).**

#### Best case time complexity

If the array is already sorted then it is the best-case scenario and its time complexity is **O(n)**

**Auxiliary Space**: O(1)


```js
// Optimized implementation of bubble sort Algorithm

function bubbleSort(arr){

	var i, j;
	
	var len = arr.length;
	
	var isSwapped = false;
	
	for(i =0; i < len; i++){

		// if we hit the point when no elements were swapped, the next iteration will not 
		// swap neither, so we stop the loop when it is false
		isSwapped = false;
	
		for(j = 0; j < len; j++){
		
			if(arr[j] > arr[j + 1]){
			
				var temp = arr[j]
				
				arr[j] = arr[j+1];
				
				arr[j+1] = temp;
				
				isSwapped = true;

			 }
	
		 }

		 // IF no two elements were swapped by inner loop, then break
		
		 if(!isSwapped){
		
			 break;
		
		 }
		
	 }

	// Print the array

	console.log(arr)

}

var arr = [243, 45, 23, 356, 3, 5346, 35, 5];

// calling the bubbleSort Function

bubbleSort(arr)
```
