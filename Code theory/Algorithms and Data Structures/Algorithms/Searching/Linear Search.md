# Linear Search


The Big O notation for Linear Search is **O(N)**. The complexity is directly related to the size of the inputs — the algorithm takes an additional step for each additional data element.

Note for Javascript developers:
`indexOf, includes, find, findIndex` operations uses linear search under the hood in Javascript.

The Linear Search algorithm is a set of instructions to traverse the given list and check **every** element in the list until we find whatever element we are looking for. The technical term for the element we are looking for is - **key**.

The algorithm goes from the leftmost (or starting) element and continues searching until it either finds the desired element or goes through all the elements in the list.
```js
function linearSearch(arr, key){ 
	for(let i = 0; i < arr.length; i++){ 
		if(arr[i] === key){ 
			return i 
		} 
	} 
return -1 }
```


Let's look at the implementation of the global linear search where we wanna count every occurance of the key:
```js
function globalLinearSearch(arr, key){
    let results = []
    for(let i = 0; i < arr.length; i++){
        if(arr[i] === key){
            results.push(i)
        }
    }
    // If results array is empty, return -1
    if(!results){
        return -1
    }

    return results
}
```
