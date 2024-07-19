# Tree

Tree Data Structure is a `non-linear data structure` in which a collection of elements known as `nodes` are connected to each other via `edges` such that there exists exactly one `path` between any two nodes.

## Read
https://www.geeksforgeeks.org/tree-data-structure/

## What is Tree Data Structure?
A tree data structure is a `hierarchical structure` that is used to represent and organize data in a way that is `easy to navigate and search`. It is a `collection of nodes that are connected by edges` and has a hierarchical relationship between the nodes. 

The topmost node of the tree is called the `root`, and the nodes below it are called the `child nodes`. Each node can have multiple child nodes, and these child nodes can also have their own child nodes, forming a `recursive structure`.

## Terminologies In Tree Data Structure
- Parent Node: The node which is a `predecessor of a node` is called the parent node of that node. {B} is the parent node of {D, E}.
- Child Node: The node which is the `immediate successor of a node` is called the child node of that node. Examples: {D, E} are the child nodes of {B}.
- Root Node: The `topmost node` of a tree or the node which does `not have any parent node` is called the root node. {A} is the root node of the tree. A non-empty tree must contain exactly one root node and exactly one path from the root to all other nodes of the tree.
- Leaf Node or External Node: The nodes which do `not have any child nodes` are called leaf nodes. {K, L, M, N, O, P, G} are the leaf nodes of the tree.
- Ancestor of a Node: Any predecessor nodes on the path of the root to that node are called Ancestors of that node. {A,B} are the ancestor nodes of the node {E}
- Descendant: A node x is a descendant of another node y if and only if y is an ancestor of x.
- Sibling: Children of the `same parent node` are called siblings. {D,E} are called siblings.
- Level of a node: The `count of edges on the path` from the root node to that node. The root node has level 0.
- Internal node: A node with `at least one child` is called Internal Node.
- Neighbor of a Node: `Parent or child nodes` of that node are called neighbors of that node.
- Subtree: Any node of the tree along with its descendant.

## Types of Tree Data Structure
- **Binary tree**: In a binary tree, each node can have a `maximum of two children` linked to it. Some common types of binary trees include full binary trees, complete binary trees, balanced binary trees, and degenerate or pathological binary trees.
- **Ternary Tree**: A Ternary Tree is a tree data structure in which each node has `at most three child nodes`, usually distinguished as `left`, `mid` and `right`.
- **N-ary Tree or Generic Tree**: Generic trees are a collection of nodes where each node is a data structure that consists of records and a list of references to its children(duplicate references are not allowed). Unlike the linked list, each node stores the address of multiple nodes.

## Applications of Tree Data Structure
- **File System**:  This allows for efficient `navigation and organization` of files.
- **Data Compression**: `Huffman coding` is a popular technique for `data compression` that involves constructing a binary tree where the leaves represent characters and their frequency of occurrence. The resulting tree is used to encode the data in a way that minimizes the amount of storage required.
- **Compiler Design**: In compiler design, a `syntax tree` is used to represent the structure of a program. 
- **Database Indexing**: B-trees and other tree structures are used in `database indexing` to efficiently search for and retrieve data.

## Key Points about Trees:
### Definition: 
A tree is a hierarchical data structure consisting of nodes connected by edges. It is a nonlinear data structure compared to arrays, linked lists, stacks, and queues.
### Nodes and Edges:
- **Node**: Each element in a tree is called a node, which contains a value and may have zero or more child nodes.
- **Edge**: Connection or link between nodes.
### Root: 
The topmost node of the tree, from which all other nodes are descendants.
### Parent, Child, Sibling, and Descendant:
- Parent: A node directly connected to another node when moving towards the root.
- Child: A node directly connected to another node when moving away from the root.
- Sibling: Nodes that share the same parent.
- Descendant: A node reachable by repeated descent from a parent.
### Leaf: 
A node that has no children.
### Depth and Height:
- **Height of Tree**: The maximum depth of the tree, i.e., the length of the longest path from the root to a leaf node.
- **Depth of Node**: The depth of a node is the number of edges present in path from the root node of a tree to that node. The level of a node in the tree, with the root node being at depth 0. 
- **Height of Node**: The height of a node is the number of edges present in the longest path connecting that node to a leaf node.
### Binary Tree: 
A tree in which each node can have at most two children, typically referred to as the left child and the right child.
### Binary Search Tree (BST): 
A binary tree where for each node, the left subtree contains only nodes with values less than the node's value, and the right subtree only nodes with values greater than the node's value.


## Basic Operations on Tree Data Structure

## Height of Tree
```javascript
// JavaScript program to find the height of 
// an N-ary tree 
  
// Structure of a node of an n-ary tree 
class Node 
{ 
    constructor() 
    { 
        this.key = 0; 
        this.child = []; 
    } 
}; 
  
// Utility function to create a new tree node 
function newNode(key) 
{ 
    var temp = new Node(); 
    temp.key =  key; 
    temp.child = []; 
    return temp; 
} 
  
// Function that will return the depth 
// of the tree 
function depthOfTree(ptr) 
{ 
    // Base case 
    if (ptr == null) 
        return 0; 
  
    // Check for all children and find 
    // the maximum depth 
    var maxdepth = 0; 
    for(var it of ptr.child) 
        maxdepth = Math.max(maxdepth,  
                            depthOfTree(it)); 
  
    return maxdepth + 1 ; 
} 
  
// Driver Code 
  
/* Let us create below tree 
*             A 
*         / / \ \ 
*     B F D E 
*     / \ | /|\ 
*     K J G C H I 
*     /\         \ 
* N M         L 
*/
var root = newNode('A'); 
(root.child).push(newNode('B')); 
(root.child).push(newNode('F')); 
(root.child).push(newNode('D')); 
(root.child).push(newNode('E')); 
(root.child[0].child).push(newNode('K')); 
(root.child[0].child).push(newNode('J')); 
(root.child[2].child).push(newNode('G')); 
(root.child[3].child).push(newNode('C')); 
(root.child[3].child).push(newNode('H')); 
(root.child[3].child).push(newNode('I')); 
(root.child[0].child[0].child).push(newNode('N')); 
(root.child[0].child[0].child).push(newNode('M')); 
(root.child[3].child[2].child).push(newNode('L')); 
document.write(depthOfTree(root) + "<br>"); 
```  
```css
Output
4
```
- Time complexity: `O(n)`
- Auxiliary Space: `O(n)`

## Height and Depth of Node
### Examples:
```css
Input: K = 25, 
          5
      /      \
   10       15
  /   \      /   \
20   25  30   35
         \
         45
Output:
Depth of node 25 = 2
Height of node 25 = 1
```
Explanation:
- The number of edges in the path from root node to the node 25 is 2. Therefore, depth of the node 25 is 2.
- The number of edges in the longest path connecting the node 25 to any leaf node is 1. Therefore, height of the node 25 is 1.
```css
Input: K = 10, 
          5
      /      \
   10       15
  /   \      /   \
20   25  30   35
         \
         45
Output: 
Depth of node 10 = 1
Height of node 10 = 2
```
<details><summary><h2><b>Approach 01</b></h2></summary>
<div>

The problem can be solved based on the following observations:
```css
Depth of a node K (of a Binary Tree) = Number of edges in the path connecting the root to the node K = Number of ancestors of K (excluding K itself). 
```
### Steps: 
- If the tree is empty, print -1.
- Otherwise, perform the following steps:
    - Initialize a variable, say dist as -1.
    - Check if the node K is equal to the given node.
    - Otherwise, check if it is present in either of the subtrees, by recursively checking for the left and right subtrees respectively.
    - If found to be true, print the value of dist + 1.
    - Otherwise, print dist.
```css
Height of a node K (of a Binary Tree) = Number of edges in the longest path connecting K to any leaf node. 
```
### Steps: 
- If the tree is empty, print -1.
- Otherwise, perform the following steps:
    - Calculate the height of the left subtree recursively.
    - Calculate the height of the right subtree recursively.
    - Update height of the current node by adding 1 to the maximum of the two heights obtained in the previous step. Store the height in a variable, say ans.
    - If the current node is equal to the given node K, print the value of ans as the required answer.

### Implementation
```javascript
// JavaScript program for the above approach

var height = -1;

// Structure of a Binary Tree Node
class Node 
{
    constructor()
    {
        this.data = 0;
        this.left = null;
        this.right = null;
    }
};

// Utility function to create
// a new Binary Tree Node
function newNode(item)
{
    var temp = new Node();
    temp.data = item;
    temp.left = temp.right = null;
    return temp;
}

// Function to find the depth of
// a given node in a Binary Tree
function findDepth(root, x)
{
    
    // Base case
    if (root == null)
        return -1;

    // Initialize distance as -1
    var dist = -1;

    // Check if x is current node=
    if ((root.data == x)|| 
    
        // Otherwise, check if x is
        // present in the left subtree
        (dist = findDepth(root.left, x)) >= 0 || 
        
        // Otherwise, check if x is
        // present in the right subtree
        (dist = findDepth(root.right, x)) >= 0)

        // Return depth of the node
        return dist + 1;
        
    return dist;
}

// Helper function to find the height
// of a given node in the binary tree
function findHeightUtil(root, x)
{
    
    // Base Case
    if (root == null)
    {
        return -1;
    }

    // Store the maximum height of
    // the left and right subtree
    var leftHeight = findHeightUtil(root.left, x);

    var rightHeight = findHeightUtil(root.right, x);

    // Update height of the current node
    var ans = Math.max(leftHeight, rightHeight) + 1;

    // If current node is the required node
    if (root.data == x)
        height = ans;

    return ans;
}

// Function to find the height of
// a given node in a Binary Tree
function findHeight(root, x)
{
    
    // Stores height of the Tree
    findHeightUtil(root, x);

    // Return the height
    return height;
}

// Driver Code
// Binary Tree Formation
var root = newNode(5);
root.left = newNode(10);
root.right = newNode(15);
root.left.left = newNode(20);
root.left.right = newNode(25);
root.left.right.right = newNode(45);
root.right.left = newNode(30);
root.right.right = newNode(35);
var k = 25;
// Function call to find the
// depth of a given node
console.log("Depth: " + findDepth(root, k));
// Function call to find the
// height of a given node
console.log("Height: " + findHeight(root, k));
```
```css
Output
Depth: 2
Height: 1
```
- Time Complexity: `O(N)`
- Auxiliary Space: `O(1)`
</div>
</details>
<details><summary><h2><b>Approach 02</b></h2></summary>
<div>

## (Using Level Order Traversal): Simple and Easy to understand
  
#### Steps:
1) Initialize height and depth variable with -1;
2) Initialize a queue and a level variable with 0 and push the root in the queue.
3) Perform level order traversal and if value of frontNode is equal to the target(K) node then value of depth will be equal to the level value and continue traversing.
4) After completion we can calculate the value of height using height = level – depth – 1;
5) Print the value of height and depth variable.

```javascript
class TreeNode {
    constructor(value) {
        this.data = value;
        this.left = null;
        this.right = null;
    }
}

function findDepthAndHeight(root, k) {
    if (root === null)
        return;

    let depth = -1;
    let height = -1;

    const queue = [];
    queue.push(root);
    let level = 0;

    while (queue.length > 0) {
        const n = queue.length;
        for (let i = 0; i < n; i++) {
            const frontNode = queue.shift();
            if (frontNode.data === k)
                depth = level;
            if (frontNode.left !== null)
                queue.push(frontNode.left);
            if (frontNode.right !== null)
                queue.push(frontNode.right);
        }
        level++;
    }

    height = level - depth - 1;
    console.log("Depth: " + depth);
    console.log("Height: " + height);
}

// Binary Tree Formation
const root = new TreeNode(5);
root.left = new TreeNode(10);
root.right = new TreeNode(15);
root.left.left = new TreeNode(20);
root.left.right = new TreeNode(25);
root.left.right.right = new TreeNode(45);
root.right.left = new TreeNode(30);
root.right.right = new TreeNode(35);

const k = 25;

findDepthAndHeight(root, k);
```
```css
Output
Depth : 2
Height : 1
```
- Time Complexity: `O(N)`, where `N` is the number of nodes in a given binary tree.
- Auxiliary Space: `O(N)` due to queue data structure.

</div>
</details>

## Level of a Given Node in Tree

### Approach 01
- The idea is to start from the root and level as 1. 
- If the key matches with root’s data, return level. 
- Else recursively call for left and right subtrees with level as level + 1. 

```javascript
    // Javascript program to Get Level of
    // a node in a Binary Tree
    /* A tree node structure */
     
    class Node
    {
        constructor(d) {
              this.data = d;
            this.left = null;
            this.right = null;
        }
    }
     
    let root;
  
    /* Helper function for getLevel().
       It returns level of
       the data if data is present in tree,
       otherwise returns
       0.*/
    function getLevelUtil(node, data, level)
    {
        if (node == null)
            return 0;
  
        if (node.data == data)
            return level;
  
        let downlevel
            = getLevelUtil(node.left, data, level + 1);
        if (downlevel != 0)
            return downlevel;
  
        downlevel
            = getLevelUtil(node.right, data, level + 1);
        return downlevel;
    }
  
    /* Returns level of given data value */
    function getLevel(node, data)
    {
        return getLevelUtil(node, data, 1);
    }
     
    /* Constructing tree given in the above figure */
    root = new Node(3);
    root.left = new Node(2);
    root.right = new Node(5);
    root.left.left = new Node(1);
    root.left.right = new Node(4);
    for (let x = 1; x <= 5; x++)
    {
      let level = getLevel(root, x);
      if (level != 0)
        document.write(
          "Level of " + x + " is "
          + getLevel(root, x) + "</br>");
      else
        document.write(
          x + " is not present in tree");
    }
```
```css
Output
Level of 1 is 3
Level of 2 is 2
Level of 3 is 1
Level of 4 is 3
Level of 5 is 2
```
- Time Complexity: `O(n)` where `n` is the number of nodes in the given Binary Tree.
- Auxiliary Space: `O(n)`

### Alternative Approach 02: 
The given problem can be solved with the help of `level order traversal` of given binary tree.
```javascript
// JavaScript program to print level in which X is present in
// binary tree
 
class Node
{
    constructor(d) {
        this.data = d;
        this.left = null;
        this.right = null;
    }
}
 
let root;
 
// Given a binary tree. Print its nodes in level order
// using array for implementing queue.
// Create a var represent current level of tree
let currLevel = 1;
 
function printLevelOrder(X){
    // Create an empty queue for level order traversal
    let queue = [root];
    while(queue[0]){
        let size = queue.length;
        for(let i=0;i<size;i++){
            let tempNode = queue.shift();
            if(tempNode.data==X){
                return currLevel;
            }
            /*Enqueue left child */
            if(tempNode.left){
                queue.push(tempNode.left);
            }
            /*Enqueue right child */
            if(tempNode.right){
                queue.push(tempNode.right);
            }
        }
        currLevel+=1;
    }
    return root.data;
}
 
 
/* creating a binary tree and entering
        the nodes */
root = new Node(1);
root.left = new Node(2);
root.right = new Node(3);
root.left.left = new Node(4);
root.left.right = new Node(5);
root.right.left = new Node(7);
root.right.right = new Node(6);
console.log(printLevelOrder(6));
```
```css
Output
3
```
- Time Complexity: `O(n)` where `n` is the number of nodes in the binary tree.
- Auxiliary Space: `O(n)` where `n` is the number of nodes in the binary tree.

## Search a Node in Tree
Given a Binary tree and a node. The task is to search and check if the given node exists in the binary tree or not. If it exists, print YES otherwise print NO.

### Approach:
The idea is to use any of the tree traversals to traverse the tree and while traversing check if the current node matches with the given node. Print YES if any node matches with the given node and stop traversing further and if the tree is completely traversed and none of the node matches with the given node then print NO.

```javascript
// javascript program to check if a node exists 
// in a binary tree     // Binary tree node
     class Node {
         
         constructor(data) {
            this.data = data;
            this.left = this.right = null;
        }
    }
 
    // Function to traverse the tree in preorder
    // and check if the given node exists in it
    function ifNodeExists(node , key) {
        if (node == null)
            return false;
 
        if (node.data == key)
            return true;
 
        // then recur on left subtree /
        var res1 = ifNodeExists(node.left, key);
 
        // node found, no need to look further
        if (res1)
            return true;
 
        // node is not found in left,
        // so recur on right subtree /
        var res2 = ifNodeExists(node.right, key);
 
        return res2;
    }
 
    // Driver Code
     
var root = new Node(0);
        root.left = new Node(1);
        root.left.left = new Node(3);
        root.left.left.left = new Node(7);
        root.left.right = new Node(4);
        root.left.right.left = new Node(8);
        root.left.right.right = new Node(9);
        root.right = new Node(2);
        root.right.left = new Node(5);
        root.right.right = new Node(6);
 
        var key = 4;
 
        if (ifNodeExists(root, key))
            document.write("YES");
        else
            document.write("NO");

``` 
```css
Output
YES
```
### Complexity Analysis:
- Time Complexity: `O(N)`, as we are using recursion to traverse `N` nodes of the tree.
- Auxiliary Space: `O(N)`, we are not using any explicit extra space but as we are using recursion there will be extra space allocated for recursive stack.

## Find the Parent of a Node

Given a tree and a node, the task is to find the parent of the given node in the tree. Print -1 if the given node is the root node.
### Examples
```css 
Input: Node = 3
     1
   /   \
  2     3
 / \
4   5
Output: 1

Input: Node = 1
     1
   /   \
  2     3
 /       \
4         5
         /
        6
Output: -1
```
### Approach: 
Write a recursive function that takes the current node and its parent as the arguments (root node is passed with -1 as its parent). If the current node is equal to the required node then print its parent and return else call the function recursively for its children and the current node as the parent.

```javascript
/* A binary tree node has data, pointer 
to left child and a pointer 
to right child */
class Node 
{
    constructor(data)
    {
        this.data = data;
        this.left = null;
        this.right = null;
    }
};
 
// Recursive function to find the
// parent of the given node
function findParent(node, val, parent)
{
    if (node == null)
        return;
 
    // If current node is the required node
    if (node.data == val) 
    {
 
        // Print its parent
        document.write(parent);
    }
    else
    {
 
        // Recursive calls for the children
        // of the current node
        // Current node is now the new parent
        findParent(node.left, val, node.data);
        findParent(node.right, val, node.data);
    }
}
 
// Driver code
var root = new Node(1);
root.left = new Node(2);
root.right = new Node(3);
root.left.left = new Node(4);
root.left.right = new Node(5);
var node = 3;
 
findParent(root, node, -1);
``` 
```css
Output: 
1
 ```
- Time Complexity: `O(N)`
- Auxiliary Space: `O(N)` 

## Diameter of a Tree

The diameter of an N-ary tree is the longest path present between any two nodes of the tree. These two nodes must be two leaf nodes. The following examples have the longest path[diameter] shaded.

```css
           O
        /  |  \
      O    4    O
    / | \      / \
  4   5   O   O   6                Diameter = 8
         / \   \
        O   2   O
       /
      O   
```

```css
           2
        /     \
      3         O
    / |       / | \
  4   5      O  3  O                Diameter = 10
              \      \
                O      O
               / \      \
              3   O      O
                   \      \
                    O      O
                   /
                  O

```

The path can either start from one of the nodes and go up to one of the LCAs (lowest common ancestors) of these nodes and again come down to the deepest node of some other subtree or can exist as a diameter of one of the child of the current node. 

The solution will exist in any one of these: 

- Diameter of one of the children of the current node 
- Sum of Height of the highest two subtree + 1 

<details><summary><h2><b>Approach 01</b></h2></summary>
<div>

```javascript
// Javascript program to find the
// height of an N-ary tree
    
    // Structure of a node of an n-ary tree
    class Node{
        
        // Utility function to create a new tree node
        constructor(key)
        {
            this.key=key;
            this.child=[];
        }
    }
    
    // Utility function that will
    // return the depth
    // of the tree
    function depthOfTree(ptr)
    {
        // Base case
    if (ptr == null)
        return 0;
 
    let maxdepth = 0;
 
    // Check for all children and find
    // the maximum depth
    for (let it=0;it< ptr.child.length;it++)
 
        maxdepth = Math.max(maxdepth,
                     depthOfTree(ptr.child[it]));
 
    return maxdepth + 1;
    }
     
    // Function to calculate the diameter
// of the tree
    function diameter(ptr)
    {
        // Base case
    if (ptr == null)
        return 0;
 
    // Find top two highest children
    let max1 = 0, max2 = 0;
    for (let it=0;it< ptr.child.length;it++)
    {
        let h = depthOfTree(ptr.child[it]);
        if (h > max1)
        {
            max2 = max1;
            max1 = h;
        }
        else if (h > max2)
        max2 = h;
    }
 
    // Iterate over each child for diameter
    let maxChildDia = 0;
    for (let it=0;it< ptr.child.length;it++)
        maxChildDia = Math.max(maxChildDia,
                          diameter(ptr.child[it]));
 
    return Math.max(maxChildDia, max1 + max2 + 1);
    }
    
    // Driver Code
    
    /* Let us create below tree
    *         A
    *         / / \ \
    *     B F D E
    *     / \     | /|\
    *     K J G C H I
    *     /\         \
    * N M         L
    */
    let root = new Node('A');
    (root.child).push(new Node('B'));
    (root.child).push(new Node('F'));
    (root.child).push(new Node('D'));
    (root.child).push(new Node('E'));
    (root.child[0].child).push(new Node('K'));
    (root.child[0].child).push(new Node('J'));
    (root.child[2].child).push(new Node('G'));
    (root.child[3].child).push(new Node('C'));
    (root.child[3].child).push(new Node('H'));
    (root.child[3].child).push(new Node('I'));
    (root.child[0].child[0].child).push(new Node('N'));
    (root.child[0].child[0].child).push(new Node('M'));
    (root.child[3].child[2].child).push(new Node('L'));
 
    document.write(diameter(root) + "\n");
```
```css
Output
7
```

### Complexity Analysis
- The time complexity of the `diameter(ptr)` function in an N-ary tree is `O(n^2)`, where `n` is the number of nodes in the tree. This is because for each node, we potentially traverse all its children to calculate their depths, and then for each child, we calculate the diameter recursively, leading to a quadratic time complexity.

- The space complexity is `O(h)`, where `h` is the height of the tree. This is due to the recursive calls in the `depthOfTree(ptr)` function and the depth of the function call stack during the execution of `diameter(ptr)`.

### Overall:
- Time complexity: `O(n^2)`
- Space complexity: `O(h)`

</div>
</details>

Optimizations to above solution:  We can find diameter without calculating depth of the tree making small changes in the above solution, similar to finding diameter of binary tree.

<details><summary><h2><b>Approach 02</b></h2></summary>
<div>

```javascript
// Javascript program to find the height of an N-ary
// tree

// Structure of a node of an n-ary tree
// Structure of a node of an n-ary tree
    class Node{
        
        // Utility function to create a new tree node
        constructor(key)
        {
            this.key=key;
            this.child=[];
        }
    }
    let diameter_of_tree = 0;

function diameter(ptr)
{
    // Base case
    // Base case
    if (ptr == null)
        return 0;

    // Find top two highest children
    let max1 = 0, max2 = 0;
    for (let it=0;it< ptr.child.length;it++)
    {
        let h = diameter(ptr.child[it]);
        if (h > max1)
        max2 = max1, max1 = h;
        else if (h > max2)
        max2 = h;
    }

    // Find whether our node can be part of diameter
    diameter_of_tree = Math.max(max1 + max2 + 1,diameter_of_tree);

    return Math.max(max1,max2) + 1;
}


          /* Let us create below tree
         *            A
         *         / / \ \
         *        B F   D E
         *       / \   / /|\
         *      K   J G C H I
         *     /\         |
         *    N  M        L
         */
    let root = new Node('A');
    (root.child).push(new Node('B'));
    (root.child).push(new Node('F'));
    (root.child).push(new Node('D'));
    (root.child).push(new Node('E'));
    (root.child[0].child).push(new Node('K'));
    (root.child[0].child).push(new Node('J'));
    (root.child[2].child).push(new Node('G'));
    (root.child[3].child).push(new Node('C'));
    (root.child[3].child).push(new Node('H'));
    (root.child[3].child).push(new Node('I'));
    (root.child[0].child[0].child).push(new Node('N'));
    (root.child[0].child[0].child).push(new Node('M'));
    (root.child[3].child[2].child).push(new Node('L'));
    
    diameter(root,diameter_of_tree);
    
    console.log(diameter_of_tree);
```
```css
Output
7
```
### Complexity Analysis:
- **Time Complexity:** The time complexity of the diameter function is `O(n)`, where `n` is the number of nodes in the tree.

**Reasoning:** The function diameter traverses each node and its children exactly once. Within each call, it performs a loop to compute heights, which is linear with respect to the number of children (constant for each node in average case). Therefore, the overall time complexity is `O(n)`.
- **Space Complexity:** The space complexity is also `O(n)`.

**Reasoning:** This is due to the recursive nature of the diameter function, which utilizes the call stack. In the worst case, the call stack depth can be equal to the height of the tree, which is `O(n)` in the case of a skewed tree. Additionally, the space used for storing nodes and their children also contributes to the space complexity.
</div>
</details>

<details><summary><h2><b>Approach 03</b></h2></summary>
<div>
  
## Another Approach to get diameter using DFS in one traversal:

The diameter of a tree can be calculated as for every node

- The current node isn’t part of diameter (i.e Diameter lies on one of the children of the current node).
- The current node is part of diameter (i.e Diameter passes through the current node).

  **Note**: Adjacency List has been used to store the Tree.

<details><summary><h2><b>Explanation</b></h2></summary>
<div>
  
### Initialization:
  
- The code initializes two arrays: `height` to store the height of nodes and `tree` as an adjacency list to represent the tree structure.
- `diameter` is initialized to `0`, which will store the maximum diameter found during the traversal.

```javascript
let maxN = 10005;
let height = new Array(maxN);
let tree = new Array(maxN);

// Initialize height and tree arrays
for (let i = 0; i < maxN; i++) {
    height[i] = 0;
    tree[i] = [];
}

let diameter = 0;
```

### Adding Edges:
- The `addEdge` function is used to add edges between nodes u and v in both directions since the tree is undirected.
```javascript
function addEdge(u, v) {
    tree[u].push(v);
    tree[v].push(u);
}

// Adding edges to the tree
addEdge(1, 2);
addEdge(1, 3);
addEdge(1, 4);
addEdge(2, 5);
addEdge(4, 6);
addEdge(4, 7);
```
- This creates the following tree structure:
```markdown
     1
    /|\
   2 3 4
  /    /\
 5    6 7
```

### DFS Function:
- The `dfs` function performs a Depth-First Search starting from node `cur` and ignoring its parent `par`.
- It calculates heights of nodes and determines the diameter of the tree using the logic provided.
```javascript
function dfs(cur, par) {
    let max1 = 0;
    let max2 = 0;

    // Traverse through each child of the current node `cur`
    for (let u = 0; u < tree[cur].length; u++) {
        if (tree[cur][u] === par) // If the child is the parent, skip it
            continue;

        // Recursively call DFS for the child node
        dfs(tree[cur][u], cur);

        // Update `height` of the current node `cur`
        height[cur] = Math.max(height[cur], height[tree[cur][u]]);

        // Update `max1` and `max2` based on heights of children
        if (height[tree[cur][u]] >= max1) {
            max2 = max1;
            max1 = height[tree[cur][u]];
        } else if (height[tree[cur][u]] > max2) {
            max2 = height[tree[cur][u]];
        }
    }

    // Increment the height of the current node
    height[cur] += 1;

    // Calculate the diameter passing through the current node `cur`
    diameter = Math.max(diameter, height[cur]);
    diameter = Math.max(diameter, max1 + max2 + 1);
}
```
### Execution:
- The DFS is called from the root node `1` with `par = 0` (no parent).
- It recursively calculates heights and updates `max1`, `max2`, and `diameter` accordingly.

### Output:
- After the DFS completes, the variable `diameter` holds the calculated diameter of the tree.
- The result is displayed by subtracting `1` from `diameter` (since the diameter calculated includes the nodes).

### Dry Run Explanation:
During the execution of DFS from node `1`:

- DFS(1, 0):
  - Iterates over children 2, 3, 4.
  - Calculates heights and updates max1, max2.
  - Computes the diameter based on the heights of nodes.
- DFS(2, 1), DFS(3, 1), DFS(4, 1):
  - Each explores their respective children, updating heights and calculating max1, max2, and the diameter.
- Final Diameter Calculation:
  - After completing DFS, diameter holds the maximum diameter found in the tree.

```css
Output
Diameter of tree is : 4
```

<details><summary><h2><b>Code with Console logs</b></h2></summary>
<div>
  
  ```javascript
// Javascript implementation to find
// diameter of a tree using
// DFS in ONE TRAVERSAL

let maxN = 10005;

// The array to store the
// height of the nodes
let height=new Array(maxN);

// Adjacency List to store
// the tree
let tree=new Array(maxN);
for(let i=0;i<maxN;i++)
{
    height[i]=0;
    tree[i]=[];
}

// variable to store diameter
// of the tree
let diameter = 0;

// Function to add edge between
// node u to node v
function addEdge(u,v)
{
    // add edge from u to v
    tree[u].push(v);
 
    // add edge from v to u
    tree[v].push(u);
}

function dfs(cur,par)
{
    console.log('*******  DFS(cur,par) = DFS(',cur,',',par, ')  ', 'tree[cur].length: ',tree[cur].length, 'tree[cur]: ',tree[cur])
    // Variables to store the height of children
    // of cur node with maximum heights
    let max1 = 0;
    let max2 = 0;
 
    // going in the adjacency list 
    // of the current node
    for (let u=0;u<tree[cur].length;u++) {
        //  console.log('loop: u: ',u, ', tree[cur][u] : ',tree[cur][u])
        // if that node equals parent discard it
        if (tree[cur][u] == par)
            continue;
 
        // calling dfs for child node
        dfs(tree[cur][u], cur);
 
         console.log('DFS(',cur,',',par, ')  ,   tree[cur][u] = ', 'tree[',cur,'][',u,']',' = ',tree[cur][u],'   height[cur] = ',height[cur])
        // calculating height of nodes
        height[cur] = Math.max(height[cur], 
        height[tree[cur][u]]);

        // getting the height of children
        // of cur node with maximum height
        if (height[tree[cur][u]] >= max1) {
            max2 = max1;
            max1 = height[tree[cur][u]];
            console.log('max1 = ',max1, '  , max2 = ',max2)
        }
        else if (height[tree[cur][u]] > max2) {
            max2 = height[tree[cur][u]];
            console.log('max2 = ',max2)
        }
        console.log('___________________________________________________________end loop iteration');
    }
    console.log('DFS(',cur,',',par, ')  ,   diameter = ',diameter,'   height[cur] = ',height[cur], '  max2 = ',max2, '  max1 = ',max1)
    height[cur] += 1;
 
    // Diameter of a tree can be calculated as
    // diameter passing through the node
    // diameter doesn't includes the cur node
    diameter = Math.max(diameter, height[cur]);
    diameter = Math.max(diameter, max1 + max2 + 1);
    console.log('------------------------------------------------------------------------- DFS end');
}

// Driver Code

// n is the number of nodes in tree
let n = 7;

// Adding edges to the tree
addEdge(1, 2);
addEdge(1, 3);
addEdge(1, 4);
addEdge(2, 5);
addEdge(4, 6);
addEdge(4, 7);

// Calling the dfs function to
// calculate the diameter of tree
console.log('tree: ',tree)
console.log('height: ',height)
dfs(1, 0);
console.log('height: ',height)
document.write("Diameter of tree is : " +(diameter - 1))
  ```
</div>
</details>

- Time Complexity: `O(N)`, Where `N` is the number of nodes in given binary tree.
- Auxiliary Space: `O(N)`
  
</div>
</details>

</div>
</details>


## Find all Leaf nodes
Print all leaf nodes of the given binary tree from left to right. That is, the nodes should be printed in the order they appear from left to right in the given tree.

The idea to do this is similar to `DFS algorithm`. Below is a step by step algorithm to do this: 

- Check if the given node is null. If null, then return from the function.
- Check if it is a leaf node. If the node is a leaf node, then print its data.
- If in the above step, the node is not a leaf node then check if the left and right children of node exist. If yes then call the function for left and right child of the node recursively.
### Recursive Method
```javascript
// Javascript program to print leaf nodes
// from left to right 
 
// A Binary Tree Node 
class Node 
{ 
    constructor()
    {
        this.data = 0;
        this.left = null;
        this.right = null;
    }
}; 
 
// Function to print leaf 
// nodes from left to right 
function printLeafNodes(root) 
{ 
     
    // If node is null, return 
    if (root == null) 
        return; 
     
    // If node is leaf node, print its data     
    if (root.left == null && 
        root.right == null) 
    { 
        document.write(root.data + " ");
        return; 
    } 
     
    // If left child exists, check for leaf 
    // recursively 
    if (root.left != null) 
        printLeafNodes(root.left); 
         
    // If right child exists, check for leaf 
    // recursively 
    if (root.right != null) 
        printLeafNodes(root.right); 
} 
 
// Utility function to create a new tree node 
function newNode(data) 
{ 
    var temp = new Node(); 
    temp.data = data; 
    temp.left = null;
    temp.right = null; 
    return temp; 
} 
 
// Driver code
 
// Let us create binary tree shown in 
// above diagram 
var root = newNode(1); 
root.left = newNode(2); 
root.right = newNode(3); 
root.left.left = newNode(4); 
root.right.left = newNode(5); 
root.right.right = newNode(8); 
root.right.left.left = newNode(6); 
root.right.left.right = newNode(7); 
root.right.right.left = newNode(9); 
root.right.right.right = newNode(10); 
 
// Print leaf nodes of the given tree 
printLeafNodes(root);
```
```css
Output
4 6 7 9 10 
```
- Time Complexity: `O(n)`, where `n` is the number of nodes in the binary tree. 
- Auxiliary Space: `O(n)`

### Stack-based iterative method

- Create an empty stack ‘st’ and push the root node to stack.
- Do the following while stack is not empty.
  - Pop an item from the stack
  - If the node is a leaf node then print it.
  - Else:
    - If the right node is not NULL
      - push the right node into the stack
    - If the left node is not NULL
      - push the left node into the stack

```javascript
// Javascript program to print leaf nodes from left to right
 
// A Binary Tree Node
class Node {
    constructor(data){
        this.data=data;
        this.left=null;
        this.right=null;
    }
}
 
// fun to print leaf nodes from left to right
function printleafNodes(root)
{
    // base case
    if (!root)
        return;
 
    // implement iterative preorder traversal and start
    // storing leaf nodes.
    let st=[];
    st.push(root);
 
    while (st.length>0) {
        root = st[st.length-1];
        st.pop();
 
        // if node is leafnode, print its data
        if (!root.left && !root.right)
            document.write(root.data + " ");
 
        if (root.right)
            st.push(root.right);
        if (root.left)
            st.push(root.left);
    }
}
 
// Driver program to test above functions
// create a binary tree
let root = new Node(1);
root.left = new Node(2);
root.right = new Node(3);
root.left.left = new Node(4);
root.right.left = new Node(5);
root.right.right = new Node(8);
root.right.left.left = new Node(6);
root.right.left.right = new Node(7);
root.right.right.left = new Node(9);
root.right.right.right = new Node(10);
 
// prints leaf nodes of the given tree
printleafNodes(root);
```
```css
Output
4 6 7 9 10 
```
- Time Complexity: `O(n)`, where `n` is the number of nodes in the binary tree. 
- Auxiliary Space: `O(n)`

## Find Siblings of a Node

Print siblings of a given Node in N-ary Tree

To improve the time complexity to `O(N)`, which is optimal for traversing and processing each node in an N-ary tree:

- **Use Single Pass Traversal:** Instead of processing nodes multiple times, ensure each node and its children are processed only once.
- **Avoid Nested Iterations:** Minimize or eliminate nested iterations where possible. For example, directly traverse through the tree with a single BFS or DFS pass, and use auxiliary data structures like arrays or queues to maintain necessary state and ensure nodes are processed efficiently.

```javascript
// Structure of a node of N-ary tree
class Node {
    constructor(key) {
        this.child = [];
        this.key = key;
    }
}

// Function to find the siblings of the node value
function findSiblings(root, value) {
    if (!root) return;

    let siblings = [];

    // Helper function to perform BFS
    function bfs(node) {
        let queue = [node];
        let found = false;

        while (queue.length > 0 && !found) {
            let current = queue.shift();

            // Check if current node's children contain the target value
            for (let child of current.child) {
                if (child.key === value) {
                    found = true;
                } else {
                    siblings.push(child.key);
                }
                queue.push(child);
            }
        }
    }

    // Perform BFS starting from the root
    bfs(root);

    // If siblings found, print them; otherwise, print "No siblings!!"
    if (siblings.length > 0) {
        console.log(`Siblings of ${value}: ${siblings.join(', ')}`);
    } else {
        console.log("No siblings!!");
    }
}

// Constructing the tree
function constructTree() {
    let root = new Node(10);

    root.child.push(new Node(20));
    root.child.push(new Node(30));
    root.child.push(new Node(40));

    root.child[0].child.push(new Node(50));
    root.child[0].child.push(new Node(60));

    root.child[1].child.push(new Node(70));
    root.child[1].child.push(new Node(80));

    root.child[2].child.push(new Node(90));
    root.child[2].child.push(new Node(100));
    root.child[2].child.push(new Node(110));

    return root;
}

// Driver code
let root = constructTree();
let X = 30;
findSiblings(root, X); // Output: Siblings of 30: 20, 40

// Example usage:
// findSiblings(root, 80); // Output: Siblings of 80: 70
```

### Complexity Analysis
- Time Complexity: `O(N)`, where `N` is the number of nodes in the tree. Each node and its children are processed exactly once using BFS, ensuring optimal traversal.
- Space Complexity: `O(N)`, primarily due to the queue used for BFS and the siblings array to store sibling keys.


## Find Children of a Node

### Approach
- Initialize the number of children as 0.
- For every node in the n-ary tree, check if its value is equal to x or not. If yes, then return the number of children.
- If the value of x is not equal to the current node then, push all the children of current node in the queue.
- Keep Repeating the above step until the queue becomes empty.

```javascript
// javascript program to find number
// of children of given node
 
// Represents a node of an n-ary tree
class Node
{
    constructor(data)
    {
        this.key = data;
        this.child = []
    }
};
 
// Function to calculate number
// of children of given node
function numberOfChildren(root, x)
{
    // initialize the numChildren as 0
    var numChildren = 0;
 
    if (root == null)
        return 0;
 
    // Creating a queue and pushing the root
    var q = [];
    q.push(root);
 
    while (q.length != 0)
    {
        var n = q.length;
 
        // If this node has children
        while (n > 0) 
        {
 
            // Dequeue an item from queue and
            // check if it is equal to x
            // If YES, then return number of children
            var p = q[0];
            q.shift();
            if (p.key == x) 
            {
                numChildren = numChildren +
                              p.child.length;
                return numChildren;
            }
 
            // push all children of the dequeued item
            for (var i = 0; i < p.child.length; i++)
                q.push(p.child[i]);
            n--;
        }
    }
    return numChildren;
}
 
// Driver Code
// Creating a generic tree
var root = new Node(20);
(root.child).push(new Node(2));
(root.child).push(new Node(34));
(root.child).push(new Node(50));
(root.child).push(new Node(60));
(root.child).push(new Node(70));
(root.child[0].child).push(new Node(15));
(root.child[0].child).push(new Node(20));
(root.child[1].child).push(new Node(30));
(root.child[2].child).push(new Node(40));
(root.child[2].child).push(new Node(100));
(root.child[2].child).push(new Node(20));
(root.child[0].child[1].child).push(new Node(25));
(root.child[0].child[1].child).push(new Node(50));
 
// Node whose number of
// children is to be calculated
var x = 50;
 
// Function calling
document.write(numberOfChildren(root, x));
```
```css
Output: 
3
```
### Complexity Analysis:
- Time Complexity : `O(N)`, where `N` is the number of nodes in tree. 
- Auxiliary Space : `O(N)`, where `N` is the number of nodes in tree. 

## Tree Traversals (Inorder, Preorder and Postorder)

Tree Traversal refers to the process of visiting or accessing each node of the tree exactly once in a certain order. Tree traversal algorithms help us to visit and process all the nodes of the tree. Since tree is not a linear data structure, there are multiple nodes which we can visit after visiting a certain node. There are multiple tree traversal techniques which decide the order in which the nodes of the tree are to be visited.

A Tree Data Structure can be traversed in following ways:

- Depth First Search or `DFS`
  - Inorder Traversal
  - Preorder Traversal
  - Postorder Traversal
- Level Order Traversal or Breadth First Search or `BFS`

```markdown
       1
     /   \
   2       3
  / \     / \
 4   5   6   7

InOrder Traversal          Left -> Root -> Right       4 , 2 , 5 , 1 , 6 , 3 , 7
PreOrder Traversal         Root -> Left -> Right       1 , 2 , 4 , 5 , 3 , 6 , 7
PostOrder Traversal        Left -> Right -> Root       4 , 5 , 2 , 6 , 7 , 3 , 1
Level Order Traversal                                  1 , 2 , 3 , 4 , 5 , 6 , 7
```

InOrder Traversal
```javascript
// Given a binary tree, print its nodes in inorder
function printInorder(node) {
    if (node == null)
        return;

    // First recur on left child */
    printInorder(node.left);

    // Then print the data of node
    console.log(node.key + " ");

    // Now recur on right child
    printInorder(node.right);
}
```
PreOrder Traversal
```javascript
// Given a binary tree, print its nodes in preorder
function printPreorder(node) {
    if (node == null)
        return;

    // First print data of node
    document.write(node.key + " ");

    // Then recur on left subtree
    printPreorder(node.left);

    // Now recur on right subtree
    printPreorder(node.right);
}
```
PostOrder Traversal
```javascript
// Given a binary tree, print its nodes according 
// to the "bottom-up" postorder traversal
function printPostorder(node) {
    if (node == null)
        return;

    // First recur on left subtree
    printPostorder(node.left);

    // Then recur on right subtree
    printPostorder(node.right);

    // Now deal with the node
    console.log(node.key + " ");
}
```
Level Order Traversal
```javascript
// Function to perform level order traversal of a binary tree
function printLevelOrder(root) {
    // Create a deque to store nodes for traversal
    const queue = new Deque();
    // Add the root node to the queue
    queue.enqueue(root);
    // Continue traversal until the queue is empty
    while (!queue.isEmpty()) {
        // Remove and get the first node from the queue
        const tempNode = queue.dequeue();
        // Print the data of the current node
        console.log(tempNode.data + " ");

        // Enqueue the left child if it exists
        if (tempNode.left !== null) {
            queue.enqueue(tempNode.left);
        }
        // Enqueue the right child if it exists
        if (tempNode.right !== null) {
            queue.enqueue(tempNode.right);
        }
    }
}
```
