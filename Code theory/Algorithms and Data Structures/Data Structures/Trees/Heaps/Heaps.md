# Heaps


## WHAT IS A BINARY HEAP?

**Very** similar to a binary search tree, but with some different rules!

In a **MaxBinaryHeap**, parent nodes are always larger than child nodes. In a **MinBinaryHeap**, parent nodes are always smaller than child nodes.
In the following picture, the root is the largest number in the heap. There is no order on the second level, the nodes are smaller than their parent, that is all.

Binary Heaps are used to implement Priority Queues, which are **very** commonly used data structures.

They are also used quite a bit, with **graph traversal** algorithms.


## MAX BINARY HEAP
![[Pasted image 20220222225151.png]]
-   Each parent has at most two child nodes
-   The value of each parent node is **always** greater than its child nodes
-   In a max Binary Heap the parent is greater than the children, but there are no guarantees between sibling nodes.
-   A binary heap is as compact as possible. All the children of each node are as full as they can be and left children are filled out first


## MIN BINARY HEAP
![[Pasted image 20220222225559.png]]
-   Each parent has at most two child nodes
-   The value of each parent node is **always** smaller than its child nodes
-   In a min Binary Heap the parent is smaller than the children, but there are no guarantees between sibling nodes.
-   A binary heap is as compact as possible. All the children of each node are as full as they can be and left children are filled out first.


### THERE'S AN EASY WAY OF STORING A BINARY HEAP...A LIST/ARRAY
For any `n` index of an array,
the left child is stored at `2n + 1`
the right child is at `2n + 2`.


### WHAT IF WE HAVE A CHILD NODE AND WANT TO FIND ITS PARENT?
For any child node at index `n`
its parent is at index `(n-1)/2` floored.


### Steps of inserting a new value to the heap
-   Push the value into the values property on the heap
-   Bubble the value up to its correct spot!

#### Insert Pseudocode
-   Push the value into the values property on the heap
-   Bubble Up:
    -   Create a variable called index which is the length of the values property - 1
    -   Create a variable called parentIndex which is the floor of (index-1)/2
    -   Keep looping as long as the values element at the parentIndex is less than the values element at the child index
        -   Swap the value of the values element at the parentIndex with the value of the element property at the child index
        -   Set the index to be the parentIndex, and start over!

```js
class MaxBinaryHeap {
    constructor(){
        this.values = [];
    }

    insert(element){
        this.values.push(element);
        this.bubbleUp();
    }

    bubbleUp(){
        let idx = this.values.length - 1;
        const element = this.values[idx];
        while(idx > 0){
            let parentIdx = Math.floor((idx - 1)/2);
            let parent = this.values[parentIdx];
            if(element <= parent) break;
            this.values[parentIdx] = element;
            this.values[idx] = parent;
            idx = parentIdx;
        }
    }

    dequeue(){
        const min = this.values[0];
        const end = this.values.pop();
        if(this.values.length > 0){
            this.values[0] = end;
            this.sinkDown();
        }
        return min;
    }

    sinkDown(){
        let idx = 0;
        const length = this.values.length;
        const element = this.values[0];
        while(true){
            let leftChildIdx = 2 * idx + 1;
            let rightChildIdx = 2 * idx + 2;
            let leftChild,rightChild;
            let swap = null;

            if(leftChildIdx < length){
                leftChild = this.values[leftChildIdx];
                if(leftChild.priority < element.priority) {
                    swap = leftChildIdx;
                }
            }
            if(rightChildIdx < length){
                rightChild = this.values[rightChildIdx];
                if(
                    (swap === null && rightChild.priority < element.priority) ||
                    (swap !== null && rightChild.priority < leftChild.priority)
                ) {
                   swap = rightChildIdx;
                }
            }
            if(swap === null) break;
            this.values[idx] = this.values[swap];
            this.values[swap] = element;
            idx = swap;
        }
    }
}

let heap = new MaxBinaryHeap();
heap.insert(41);
heap.insert(39);
heap.insert(33);
heap.insert(18);
heap.insert(27);
heap.insert(12);
heap.insert(55);
```


### Steps of inserting a new value to the heap
-   Remove the root
-   Replace with the most recently added
-   Adjust (sink down). This is the procedure for deleting the root from the heap (effectively extracting the maximum element in a max-heap or the minimum element in a min-heap) and restoring the properties is called _down-heap_ (also known as _bubble-down_, _percolate-down_, _sift-down_, _trickle down_, _heapify-down_, _cascade-down_, and _extract-min/max_).

#### Insert Pseudocode
-   Swap the first value in the values property with the last one
-   Pop from the values property, so you can return the value at the end.
-   Have the new root "sink down" to the correct spot...
    -   Your parent index starts at 0 (the root)
    -   Find the index of the left child: 2 * index + 1 (make sure its not out of bounds)
    -   Find the index of the right child: 2*index + 2 (make sure its not out of bounds)
    -   If the left or right child is greater than the element...swap. If both left and right children are larger, swap with the largest child.
    -   The child index you swapped to now becomes the new parent index.  
    -   Keep looping and swapping until neither child is larger than the element.
    -   Return the old root!!
Visit the code of the `dequeue` and `sinkDown` functions.
