```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BST {
    constructor() {
        this.root = null;
    }

    BFS() {
        let queue = [];
        let result = [];
        let currentNode = this.root;
        queue.push(currentNode);

        while (queue.length) {
            currentNode = queue.shift();
            result.push(currentNode.value);
            if (currentNode.left) queue.push(currentNode.left);
            if (currentNode.right) queue.push(currentNode.right);
        }
        return result;
    }

    DFSPreorder() {
        let result = [];
        function traverse(currentNode) {
            result.push(currentNode.value);
            if (currentNode.left) traverse(currentNode.left);
            if (currentNode.right) traverse(currentNode.right);            
        }
        traverse(this.root);
        return result;
    }

    DFSPostOrder() {
        let result = [];
        function traverse(currentNode) {
            if (currentNode.left) traverse(currentNode.left);
            if (currentNode.right) traverse(currentNode.right);
            result.push(currentNode.value);
        }
        traverse(this.root);
        return result;
    }

    DFSInOrder() {
        let result = [];
        function traverse(currentNode) {
            if (currentNode.left) traverse(currentNode.left);
            result.push(currentNode.value);
            if (currentNode.right) traverse(currentNode.right);
        } 
        traverse(this.root);
        return result;
    }
}

// Example Usage
let thisTree = new BST();
thisTree.insert(25);
thisTree.insert(13);
thisTree.insert(36);
thisTree.insert(5);
thisTree.insert(20);
thisTree.insert(31);
thisTree.insert(39);

// Traversal Outputs
thisTree.BFS(); //[25, 13, 36, 5, 20, 31, 39]

thisTree.DFSPreorder(); // [25, 13, 5, 20, 36, 31, 39]

thisTree.DFSPostOrder(); // [5, 20, 13, 31, 39, 36, 25]

thisTree.DFSInOrder(); // [5, 13, 20, 25, 31, 36, 39]
```

### Traversal Methods Explanation

#### BFS (Breadth-First Search)
BFS explores the tree level by level. It uses a queue to keep track of nodes to visit next, starting from the root. Each node is processed before moving to its children. This results in a sequence of nodes that represent each level of the tree.

**Example Code**:
```javascript
BFS() {
    let queue = [];
    let result = [];
    let currentNode = this.root;
    queue.push(currentNode);

    while (queue.length) {
        currentNode = queue.shift();
        result.push(currentNode.value);
        if (currentNode.left) queue.push(currentNode.left);
        if (currentNode.right) queue.push(currentNode.right);
    }
    return result;
}
```

#### DFS Preorder
- **Root**: The value of the current node is processed first.
- **Left**: The traversal moves to the left child and continues to explore down to the leftmost node.
- **Right**: After reaching the leftmost node and processing it, the traversal returns to the most recent parent and explores its right child.

**Example Code**:
```javascript
DFSPreorder() {
    let result = [];
    function traverse(currentNode) {
        result.push(currentNode.value);
        if (currentNode.left) traverse(currentNode.left);
        if (currentNode.right) traverse(currentNode.right);            
    }
    traverse(this.root);
    return result;
}
```

#### DFS PostOrder
### DFS PostOrder Explanation

- **Left**: The traversal first moves to the left child and continues to explore down to the leftmost node.
- **Right**: After reaching the leftmost node, it backtracks to process the right child of the most recent parent.
- **Root**: Finally, the value of the current node is processed after both subtrees have been traversed.

**Example Code**:
```javascript
DFSPostOrder() {
    let result = [];
    function traverse(currentNode) {
        if (currentNode.left) traverse(currentNode.left);
        if (currentNode.right) traverse(currentNode.right);
        result.push(currentNode.value);
    }
    traverse(this.root);
    return result;
}
```

#### DFS InOrder
### DFS InOrder Traversal Sequence
- **Left**: The traversal first moves to the left child and continues to explore down to the leftmost node.
- **Root**: The value of the current node is processed after all left descendants have been visited.
- **Right**: After processing the current node, the traversal then moves to the right child and explores its subtree.
**Example Code**:

```javascript
DFSInOrder() {
    let result = [];
    function traverse(currentNode) {
        if (currentNode.left) traverse(currentNode.left);
        result.push(currentNode.value);
        if (currentNode.right) traverse(currentNode.right);
    } 
    traverse(this.root);
    return result;
}
```

