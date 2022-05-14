# Radix Sort

Radix sort is a special sorting algorithm that works on lists of numbers.
**It uses baskets!**
`It never makes comparisons between elements!`

It exploits the fact that information about the size of a number is encoded in the number of digits.  
More digits means a bigger number!
It never makes comparisons between elements!


## Big O
- Time Complexity O(nk)
- Space Complexity O(n + k)
    n - length of array
    k - number of digits(average)



## Radix Sort Pseudocode
-   Define a function that accepts list of numbers
-   Figure out how many digits the largest number has
-   Loop from _k_ = 0 up to this largest number of digits
-   For each iteration of the loop:
	-   Create buckets for each digit (0 to 9)
	-   place each number in the corresponding bucket based on its _k_th digit
-   Replace our existing array with values in our buckets, starting with 0 and going up to 9
-   return list at the end!

```js
    // returns the digit in num at the given place value
    function getDigit(num, i) {
        return Math.floor(Math.abs(num) / Math.pow(10, i)) % 10;
    }

    // returns the number of digits in num
    function digitCount(num) {
        if (num === 0) return 1;
        return Math.floor(Math.log10(Math.abs(num))) + 1;
    }

    // Given an array of numbers, returns the number of digits in the largest numbers in the list
    function mostDigits(nums) {
        let maxDigits = 0;
        for (let i = 0; i < nums.length; i++) {
            maxDigits = Math.max(maxDigits, digitCount(nums[i]));
        }
        return maxDigits;
    }

    function radixSort(nums){
        let maxDigitCount = mostDigits(nums);
        for(let k = 0; k < maxDigitCount; k++){
            let digitBuckets = Array.from({length: 10}, () => []);
            for(let i = 0; i < nums.length; i++){
                let digit = getDigit(nums[i],k);
                digitBuckets[digit].push(nums[i]);
            }
            nums = [].concat(...digitBuckets);
        }
        return nums;
    }

    radixSort([23,345,5467,12,2345,9852]);
```
