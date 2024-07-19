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
Javascript

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


## Diameter of a Tree


## Find all Leaf nodes


## Find Siblings of a Node


## Find Children of a Node


## Tree Traversals (Inorder, Preorder and Postorder)

