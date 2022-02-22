# Depth First Search - DFS

## PreOrder
### **Steps for PreOrder - Recursively**
-   Create a queue (this can be an [[Array]]) or a [[Variables|variable]] to store the values of nodes visited
-   Write a helper function which accepts a node
    -   Push the value of the node to the variable that stores the values
    -   If there is a left property on the node call the helper function with the left property on the node
    -   If there is a right property on the node call the helper function with the right property on the node
-   Invoke the helper function with the 'root'
-   Return the array of values


## PostOrder
### **Steps for PostOrder - Recursively**
-   Create a queue (this can be an [[Array]]) or a [[Variables|variable]] to store the values of nodes visited
-   Write a helper function which accepts a node
    -   If there is a left property on the node call the helper function with the left property on the node
    -   If there is a right property on the node call the helper function with the right property on the node
    -   Push the value of the node to the variable that stores the values
-   Invoke the helper function with the 'root'
-   Return the array of values



## InOrder
This is useful when you have a tree, and you would like to get the values in ascending order as a flat array for example, because the order of traversal would fit for this need. 

### **Steps for InOrder - Recursively**

-   Create a queue (this can be an [[Array]]) or a [[Variables|variable]] to store the values of nodes visited
-   Write a helper function which accepts a node
    -   If there is a left property on the node call the helper function with the left property on the node
    -   Push the value of the node to the variable that stores the values
    -   If there is a right property on the node call the helper function with the right property on the node
-   Invoke the helper function with the 'root'
-   Return the array of values


### Implementation
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

    insert(value){
        let newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        let current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                }
                current = current.right;
            }
        }
    }

    find(value){
        if(this.root === null) return false;
        let current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }

    contains(value){
        if(this.root === null) return false;
        let current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }

    BFS(){
        let node = this.root,
            data = [],
            queue = [];
        queue.push(node);

        while(queue.length){
           node = queue.shift();
           data.push(node.value);
           if(node.left) queue.push(node.left);
           if(node.right) queue.push(node.right);
        }
        return data;
    }

    DFSPreOrder(){
        let data = [];
        function traverse(node){
            data.push(node.value);
            if(node.left) traverse(node.left);
            if(node.right) traverse(node.right);
        }
        traverse(this.root);
        return data;
    }

    DFSPostOrder(){
        let data = [];
        function traverse(node){
            if(node.left) traverse(node.left);
            if(node.right) traverse(node.right);
            data.push(node.value);
        }
        traverse(this.root);
        return data;
    }

    DFSInOrder(){
        let data = [];
        function traverse(node){
            if(node.left) traverse(node.left);
            data.push(node.value);
            if(node.right) traverse(node.right);
        }
        traverse(this.root);
        return data;
    }
}

let tree = new BinarySearchTree();
```
