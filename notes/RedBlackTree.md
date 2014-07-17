# Red-Black Trees

### History

This note will talk about the traditional Red-Black Trees algorithms. This original data structure was invented in 1972 by [Rudolf Bayer](http://en.wikipedia.org/wiki/Rudolf_Bayer) and named "symmetric binary B-Tree", but acquired its modern name in a paper in 1978 by [Leonidas J. Guibas](http://en.wikipedia.org/wiki/Leonidas_J._Guibas) and [Robert Sedgewick](http://en.wikipedia.org/wiki/Robert_Sedgewick_(computer_scientist)) entitled "A Dichromatic Framework for Balanced Trees". ([refer from WikiPedia](http://en.wikipedia.org/wiki/Red%E2%80%93black_tree))

### [Binary Search Tree](http://en.wikipedia.org/wiki/Binary_search_tree)

Before talking about the Red-Black Trees(RBT), we need better know the Binary Search Tree(BST), because in fact the RBT is a BST. 

##### What's Binary Search Tree?

A binary search tree is an empty tree or a tree meets the properties as following:

	- The left subtree of a node contains only nodes with keys less than the node's key.
	- The right subtree of a node contains only nodes with keys greater than the node's key.
	- The left and right subtree each must also be a binary search tree.
	- Each node can have up to two successor nodes.
	- There must be no duplicate nodes.

##### The Running Time 

We know that each basic operations on a binary search tree runs in O(h), which h is the height of the tree. So we want to minimize the h. But how? We know the minimum of h should be lg(N), where N is the number of nodes in the tree. One way to meet O(lgN) time is the Randomly building the Binary Search Tree, which is described in [INTRODUCTION TO ALGORITHMS].

So when we initialize a binary tree in randomly, maybe we can meet O(lgN) for a while. But with the operations(like insertion or deleting) doing, we cannot guarantee the BST still be h as lgN. And the worst case running time may become O(N), which we don't want to see.

##### Balanced Search Tree

Balanced Search Tree is a search tree data structure, maintaining dynamic set of N elements using tree of height O(lgN).

Here given some balanced search tree examples:

	- AVL Tree
	- 2-3 Tree
	- 2-3-4 Tree
	- B-Tree
	- ** Red-Black Trees **
	- Skip List
	- Treaps

### Red-Black Trees

Red-Black Trees is a balanced search tree, which can maintain dynamic set of N nodes using tree of height O(lgN). Before we prove this, let's see what's the definition of Red-Black Trees. 

##### What's Red-Balck Tree? 

It's a Binary Search Tree data structure with extra color field for each node and the following must be satisfied by the RBT:

	- 1. A node is either red or black.
	- 2. The root is black.
	- 3. All leaves(NIL) are black.
	- 4. Every red node must have two black child nodes. (Every red node has black parent.)
	- 5. Every path from a given node to any of its descendant leaves contains the same number of black nodes.

By the above 5 properties, we can get a critical property of red-black trees: that **_the path from the root to the furthest leaf is no more than twice as long as the path from the root to the nearest leaf._** The result is that the tree is roughly height-balanced. 



