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


## Level of a Given Node in Tree


## Search a Node in Tree


## Find the Parent of a Node


## Diameter of a Tree


## Find all Leaf nodes


## Find Siblings of a Node


## Find Children of a Node


## Tree Traversals (Inorder, Preorder and Postorder)

