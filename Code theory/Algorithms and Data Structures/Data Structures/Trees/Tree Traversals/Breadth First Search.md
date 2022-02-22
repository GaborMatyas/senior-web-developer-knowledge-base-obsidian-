# Breadth First Search - BFS (width)

**Steps - Iteratively**

-   Create a queue (this can be an [[Array]]) or a [[Variables|variable]] to store the values of nodes visited
-   Place the root node in the [[Queues|queue]]
-   Loop as long as there is anything in the queue
    -   Dequeue a node from the queue and push the value of the node into the variable that stores the nodes
    -   If there is a left property on the node dequeued - add it to the queue
    -   If there is a right property on the node dequeued - add it to the queue
-   Return the variable that stores the values

```js
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }

    BFS(){
        let node = this.root,
            data = [],
            queue = [];
        queue.push(node);

        while(queue.length){
            node = queue.shift();
            data.push(node.value);
            if(node.left) {
               queue.push(node.left);
            }
            if(node.right) {
                queue.push(node.right);
            }
        }
        return data;
    }
}

let tree = new BinarySearchTree();
```
