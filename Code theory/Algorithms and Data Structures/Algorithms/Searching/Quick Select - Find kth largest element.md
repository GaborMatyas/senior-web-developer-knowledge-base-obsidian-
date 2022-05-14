# Hoare's Quick Select - Find NTH largest element

 In our best case/average case scenario the time complexity is actually `O(N)`! The reason it is `O(N)` is because every iteration we are scanning through the array to find the partition point, once we find the partition we continue with the side of the partition that contains the index we're searching for and so on and so forth. This means that we search through the entire array on the first iteration, and in an ideal world the partition index we find is in the middle of the search space every single time, we are cutting our search space in half.

This means we get `O(N + N/2 + N/4 + N/8 + N/16)` .... which as we know is equal to `O(2N)` which is `O(N)`. The worst case is `O(N^2)` just like quicksort because if the partition element we choose each time ends up being the very last element index, then we actually only reduce our search space by 1 element, which means we get `O(N + N - 1 + N - 2 + N - 3 + N - 4....)` which is `O(N^2)`!


```js
const array = [5,3,1,6,4,2];
const kToFind = 4;

const swap = function (array, i, j) {
  const temp = array[i];
  array[i] = array[j];
  array[j] = temp;
};

const getPartition = function (nums, left, right) {
  let i = left;

  for (let j = left; j <= right; j++) {
    if (nums[j] <= nums[right]) {
      swap(nums, i, j);
      i++;
    }
  }
  return i - 1;
};

const quickSelect = function (nums, left, right, indexToFind) {
  const partitionIndex = getPartition(nums, left, right);

  if (partitionIndex === indexToFind) {
    return nums[partitionIndex];
  } else if (indexToFind < partitionIndex) {
    return quickSelect(nums, left, partitionIndex - 1, indexToFind);
  } else {
    return quickSelect(nums, partitionIndex + 1, right, indexToFind);
  }
};

var findKthLargest = function (nums, k) {
  const indexToFind = nums.length - k;

  return quickSelect(nums, 0, nums.length - 1, indexToFind);
};

console.log(findKthLargest(array, kToFind))
```