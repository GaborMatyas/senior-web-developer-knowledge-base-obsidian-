# Binary Search Trees (BST)

It is a special case of [[Binary Tree]]s.
Each node can have one or two children, or none if it is a leaf node. So maximum 2 children.
(Can not have 3 or more.)

Every node to the left of a parent node is always less/smaller than the parent.
Every node to the right of a parent node is always more/bigger than the parent.

The ordering makes this data structure really fast when some value should be found.

They are sorted in a particular way. (They can hold any sortable data like strings or numbers.)
![[Pasted image 20220220184655.png]]


## Big O
It is important that the tree is `sorted`.

Insertion = O(log n) at best, 
Searching = O(log n) at best, 

But in the worst case: 
![[Pasted image 20220220203355.png]]
**It is O(n).**


## Inserting a node
**Steps - Iteratively or Recursively**

-   Create a new node
-   Starting at the root
    -   Check if there is a root, if not - the root now becomes that new node!
    -   If there is a root, check if the value of the new node is greater than or less than the value of the root
    -   If it is greater 
        -   Check to see if there is a node to the right
            -   If there is, move to that node and repeat these steps
            -   If there is not, add that node as the right property
    -   If it is less
        -   Check to see if there is a node to the left
            -   If there is, move to that node and repeat these steps
            -   If there is not, add that node as the left property

## Finding a node
**Steps - Iteratively or Recursively**

-	Starting at the root
-   Check if there is a root, if not - we're done searching!
-   If there is a root, check if the value of the new node is the value we are looking for. If we found it, we're done!
-   If not, check to see if the value is greater than or less than the value of the root
-   If it is greater 
    -   Check to see if there is a node to the right
        -   If there is, move to that node and repeat these steps
        -   If there is not, we're done searching!
-   If it is less
    -   Check to see if there is a node to the left
        -   If there is, move to that node and repeat these steps
        -   If there is not, we're done searching
- 
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
            if(value === current.value) {
                return undefined;
            }

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
        if(this.root === null) {
			return false;
		}

        let current = this.root;
        let found = false;

        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }

        if(!found) {
            return undefined;
        }

        return current;
    }

    contains(value){
        if(this.root === null) {
            return false;
        }

        let current = this.root;
        let found = false;

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
}

let tree = new BinarySearchTree();
```
