# Red-Black Trees

### History

This note will talk about the traditional Red-Black Trees algorithms. This original data structure was invented in 1972 by [Rudolf Bayer](http://en.wikipedia.org/wiki/Rudolf_Bayer) and named "symmetric binary B-Tree", but acquired its modern name in a paper in 1978 by [Leonidas J. Guibas](http://en.wikipedia.org/wiki/Leonidas_J._Guibas) and [Robert Sedgewick](http://en.wikipedia.org/wiki/Robert_Sedgewick_(computer_scientist)) entitled "A Dichromatic Framework for Balanced Trees". ([From WikiPedia](http://en.wikipedia.org/wiki/Red%E2%80%93black_tree))

### Binary Search Tree

Before talking about the Red-Black Trees(RBT), we need better know the Binary Search Tree(BST), because in fact the RBT is a BST. 

##### 1. What's Binary Search Tree?

A binary search tree is an empty tree or a tree meets the properties as following:

	- The left subtree of a node contains only nodes with keys less than the node's key.
	- The right subtree of a node contains only nodes with keys greater than the node's key.
	- The left and right subtree each must also be a binary search tree.
	- Each node can have up to two successor nodes.
	- There must be no duplicate nodes.

An example of a Binary Search Tree is shown as following: from [WikiPedia](http://en.wikipedia.org/wiki/Binary_search_tree)

![Binary Search Tree Example](../images/Binary_search_tree_Example.png)

##### 2. The Running Time 

We know that each basic operation on a binary search tree runs in O(h), which h is the height of the tree. So we want to minimize the h. But how? We know the minimum of h should be lg(N), where N is the number of nodes in the tree. One way to meet O(lgN) time is the Randomly building the Binary Search Tree, which is described in the _Chapter 12.4 Randomly built binary tree_ in __[INTRODUCTION TO ALGORITHMS]__.

So when we initialize a binary tree randomly, maybe we can meet O(lgN) for a while. But with the operations(like insertion or deleting) doing, we cannot guarantee the BST's height be O(lgN). And the worst case running time may become O(N), which we don't want to see. Then let's see another definition of tree, called balanced search tree as following.

##### 3. Balanced Search Tree

Balanced Search Tree is a search tree data structure, maintaining dynamic set of N elements using tree of height O(lgN).

Here given some balanced search tree examples:

	- Red-Black Trees
	- AVL Tree
	- 2-3 Tree
	- 2-3-4 Tree
	- B-Tree
	- Skip List
	- Treaps

### Red-Black Trees

Red-Black Trees is a balanced search tree, which can maintain dynamic set of N nodes using tree of height O(lgN). Before we prove this, let's see what's the definition of Red-Black Trees. 

##### 1. What's Red-Balck Tree? 

It's a Binary Search Tree data structure with extra color field for each node and the following must be satisfied by the RBT:

	1. A node is either red or black.
	2. The root is black.
	3. All leaves(NIL) are black.
	4. Every red node must have two black child nodes. (Every red node has black parent.)
	5. Every path from a given node to any of its descendant leaves contains the same number of black nodes.

By the above 5 properties, we can get a critical property of red-black trees: that **_the path from the root to the furthest leaf is no more than twice as long as the path from the root to the nearest leaf._** The result is that the tree is roughly height-balanced. 

An example of Red-Black Trees is showing as following: from [WikiPedia](http://en.wikipedia.org/wiki/Red%E2%80%93black_tree)

![Red-Balck Trees Example](../images/Red-black_tree_example.png)

#### 2. Height of Red-Black Tree

By the definition of the RBT, does the height h meet the balanced search tree height of O(lgN) (h <= O(lgN))? 

The following steps are the proof of that Red-Black Trees with N keys has height h: 
<img src="http://www.forkosh.com/mathtex.cgi? h \leq 2 \lg (N+1) = O(\lg N) ">

* __Step 1__: Merge each red node to its black parent, after this, it will become a 2-3-4 trees. _(Shown in the following picture)_
![RBT_to_2_3_4](../images/RBT_to_2_3_4.png)
* __Step 2__: Easy to get the number of leaves in the 2-3-4 trees is N+1.
* __Step 3__: If we set  <img src="http://www.forkosh.com/mathtex.cgi? h^{'}"> be the height of a 2-3-4 trees, then easy to know the number of leaves(|leaves|)should be:
<img src="http://www.forkosh.com/mathtex.cgi? 2^{h^{'}} \leq  |leaves| \leq 4^{h^{'}}">
* __Step 4__: Then we get
<img src="http://www.forkosh.com/mathtex.cgi? 2^{h^{'}} \leq |leaves| = N+1   \Rightarrow   h^{'} \leq \lg (N+1)"> (Combined Step 2&3)
* __Step 5__: By the properties of RBT, we know that red node has black parent, so that there must be smaller than 1/2 nodes on any root-to-leaf path are red. When we did the Step 1, the disappeared red nodes must be smaller than 1/2 nodes. We can derivate that the height of RBT h must be 
<img src="http://www.forkosh.com/mathtex.cgi? h \leq 2h^{'} ">
* __Step 6__: Finally we get 
<img src="http://www.forkosh.com/mathtex.cgi? h \leq 2h^{'} = 2\lg{(N+1)} = O(\lg{N}) "> (Combined Step 4&5)

Now we can see that the Red-Black Tree is a good balanced tree, which can always maintain O(lgN) height. Once we get the data structure, we want to do some operations on this data structure.

#### 3. Operations

There are two different kinds of operations, one will maintain the RBT properties and another one may lead the violation of the properties.

###### 1. Queries

The queries include search, max, min, successor, predecessor etc. All of these operations just look up the node in the RBT, which won't break the tree structure. And all these queries can run in O(lgN) time in the Red-Black Tree.

###### 2. Updates

The updates contain insert and delete, which will lead the violation of the RBT properties. So after updating the nodes in the RBT, we may modify the tree to meet the RBT properties again. 

About modifying the tree, we need know:
	1. The basic Binary Search Tree operations, like root(), p(), left(), right() etc.
	2. Color changes, which is easy, change the node's color from one to another one. 
	3. Restructuring of links via Rotations

Here we won't give details about the BST operations and color changes. We just look at the algorithms on Rotations.

#### 4. Rotations

There are two ways to rotate the tree: Left-Rotate & Right-Rotate. _(Shown as following from [WikiPedia](http://en.wikipedia.org/wiki/Tree_rotation))_

![Tree_Rotation](../images/Tree_rotation.png)

##### Left-Rotate


##### Right-Rotate
