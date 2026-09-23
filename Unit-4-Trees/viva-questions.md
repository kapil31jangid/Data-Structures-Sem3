# Unit 4 - Trees Viva Questions

[← Important Questions](important-questions.md) | [Unit Index →](README.md)

Open each answer only after attempting it aloud.

---

## Tree Fundamentals & Terminology

<details>
<summary><strong>1. What is a tree?</strong></summary>

A non-linear, hierarchical data structure consisting of a collection of nodes connected by edges in parent-child relationships.
</details>

<details>
<summary><strong>2. How many edges exist in a connected tree with N nodes?</strong></summary>

Exactly $N - 1$ edges.
</details>

<details>
<summary><strong>3. What is the root of a tree?</strong></summary>

The top-most node of a tree from which all hierarchical paths originate. It is the only node without a parent.
</details>

<details>
<summary><strong>4. Define parent and child nodes.</strong></summary>

A parent is a node that has one or more successor nodes (children); a child is the direct descendant of a parent node.
</details>

<details>
<summary><strong>5. What are siblings?</strong></summary>

Nodes that share the same parent node.
</details>

<details>
<summary><strong>6. What is a leaf or terminal node?</strong></summary>

A node that has no children (degree $= 0$).
</details>

<details>
<summary><strong>7. What is an internal node?</strong></summary>

A non-leaf node that has at least one child (degree $\ge 1$).
</details>

<details>
<summary><strong>8. Define degree of a node and degree of a tree.</strong></summary>

Degree of a node is the total number of children it has. Degree of a tree is the maximum degree among all nodes in the tree.
</details>

<details>
<summary><strong>9. Define level, height, and depth of a tree node.</strong></summary>

- **Level:** Distance in generational steps from root (Root is at Level 0).
- **Height of a node:** Number of edges on the longest path from the node down to a leaf.
- **Depth of a node:** Number of edges from the root down to that node.
</details>

<details>
<summary><strong>10. What is a path in a tree?</strong></summary>

A sequence of consecutive nodes and edges connecting two nodes.
</details>

---

## Tree Representations

<details>
<summary><strong>11. Why is an array of child pointers inefficient for general trees?</strong></summary>

Because nodes have variable numbers of children, sizing nodes to the maximum degree wastes substantial memory on `NULL` pointers.
</details>

<details>
<summary><strong>12. What two node types are used in List Representation of a tree?</strong></summary>

Data nodes (storing values and links to children lists) and Reference/Pointer nodes (storing pointers linking siblings and subtrees).
</details>

<details>
<summary><strong>13. What three fields are present in a Left-Child / Right-Sibling (LCRS) node?</strong></summary>

`DATA` (node value), `Left Child` (pointer to first child), and `Right Sibling` (pointer to immediate next sibling).
</details>

<details>
<summary><strong>14. What is the primary advantage of LCRS representation?</strong></summary>

It allows any arbitrary $N$-ary general tree to be represented as a binary tree with exactly two pointers per node.
</details>

---

## Binary Trees & Representations

<details>
<summary><strong>15. What is a binary tree?</strong></summary>

A tree in which every node has at most two children (0, 1, or 2 children).
</details>

<details>
<summary><strong>16. What is a Strictly (Full / Proper / 2-Tree) Binary Tree?</strong></summary>

A binary tree in which every node has either zero or two children (no node has exactly one child).
</details>

<details>
<summary><strong>17. What is a Complete Binary Tree?</strong></summary>

A binary tree where every internal node has exactly two children and all leaf nodes are at the same level.
</details>

<details>
<summary><strong>18. What is an Extended Binary Tree?</strong></summary>

A binary tree converted into a 2-tree by replacing every empty subtree (`NULL` pointer) with a dummy external node.
</details>

<details>
<summary><strong>19. If a binary tree has N internal nodes, how many external nodes are in its extended tree?</strong></summary>

Exactly $N + 1$ external (dummy) nodes.
</details>

<details>
<summary><strong>20. In an array-represented binary tree (0-based), what are the indices of the children and parent of node i?</strong></summary>

Left child: $2i + 1$, Right child: $2i + 2$, Parent: $\lfloor (i - 1) / 2 \rfloor$.
</details>

<details>
<summary><strong>21. What fields does a linked binary tree node contain?</strong></summary>

`LPTR` (left pointer), `DATA` (value), and `RPTR` (right pointer).
</details>

---

## Binary Tree Traversals & Tree Construction

<details>
<summary><strong>22. What is binary tree traversal?</strong></summary>

The process of visiting every node in a binary tree exactly once in a systematic order.
</details>

<details>
<summary><strong>23. State the processing order for Inorder, Preorder, and Postorder traversals.</strong></summary>

- **Inorder:** Left $\to$ Root $\to$ Right (`L - Root - R`)
- **Preorder:** Root $\to$ Left $\to$ Right (`Root - L - R`)
- **Postorder:** Left $\to$ Right $\to$ Root (`L - R - Root`)
</details>

<details>
<summary><strong>24. What is the time and space complexity of recursive tree traversal?</strong></summary>

Time complexity is $O(n)$ where $n$ is the number of nodes. Space complexity is $O(h)$ auxiliary stack memory, where $h$ is tree height.
</details>

<details>
<summary><strong>25. Why is Inorder traversal essential to construct a unique binary tree?</strong></summary>

Because Inorder is the only traversal that divides nodes into left and right subtrees around the root.
</details>

<details>
<summary><strong>26. Can a unique binary tree be constructed from Preorder and Postorder alone?</strong></summary>

No, because neither traversal distinguishes left subtrees from right subtrees for nodes with a single child.
</details>

---

## Binary Search Tree (BST)

<details>
<summary><strong>27. What is the BST property?</strong></summary>

For every node with key $K$, all keys in its left subtree are $\le K$, and all keys in its right subtree are $> K$.
</details>

<details>
<summary><strong>28. What does Inorder traversal of a BST produce?</strong></summary>

A sequence of keys in strictly sorted (ascending) order.
</details>

<details>
<summary><strong>29. What is the search time complexity in a BST?</strong></summary>

$O(\log n)$ on average in a balanced BST, and $O(n)$ in the worst case (skewed tree).
</details>

---

## Tree Conversion & Applications

<details>
<summary><strong>30. State the rules for converting a general tree to a binary tree.</strong></summary>

1. Root of general tree becomes Root of binary tree.
2. First (leftmost) child of a node becomes its Left Child.
3. Next right sibling of a node becomes its Right Child.
</details>

<details>
<summary><strong>31. Name five major applications of trees from the course syllabus.</strong></summary>

1. Manipulating hierarchical data (file systems)
2. Fast searching and retrieval (BST)
3. Manipulating sorted lists
4. Router algorithms and routing tables
5. Expression trees for compiler expression evaluation
</details>

---

## Expression Trees & Threaded Binary Trees

<details>
<summary><strong>32. What is an Expression Tree?</strong></summary>

A binary tree where internal nodes store operators (`+`, `-`, `*`, `/`) and leaf nodes store operands.
</details>

<details>
<summary><strong>33. Which traversals of an expression tree yield prefix and postfix expressions?</strong></summary>

Preorder yields Prefix (Polish) notation, and Postorder yields Postfix (Reverse Polish) notation.
</details>

<details>
<summary><strong>34. What is a Threaded Binary Tree?</strong></summary>

A binary tree where `NULL` left pointers point to the node's Inorder Predecessor, and `NULL` right pointers point to its Inorder Successor.
</details>

<details>
<summary><strong>35. What is the advantage of a Threaded Binary Tree?</strong></summary>

It enables fast, iterative Inorder traversal without recursion or an auxiliary stack, utilizing otherwise wasted `NULL` pointers.
</details>

---

## AVL Trees & Rotations

<details>
<summary><strong>36. What is an AVL Tree?</strong></summary>

A strictly height-balanced Binary Search Tree where the Balance Factor of every node is $-1$, $0$, or $+1$.
</details>

<details>
<summary><strong>37. How is the Balance Factor calculated?</strong></summary>

$\text{Balance Factor} = \text{Height of Left Subtree} - \text{Height of Right Subtree}$.
</details>

<details>
<summary><strong>38. What is a Critical Node in an AVL Tree?</strong></summary>

The lowest ancestor node whose Balance Factor becomes $\pm 2$ following an insertion or deletion.
</details>

<details>
<summary><strong>39. Name the four AVL rotations. Which are single and which are double?</strong></summary>

- **Single Rotations:** LL (Right Rotation), RR (Left Rotation)
- **Double Rotations:** LR (Left then Right Rotation), RL (Right then Left Rotation)
</details>

<details>
<summary><strong>40. What is the guaranteed worst-case search time in an AVL tree?</strong></summary>

$O(\log n)$, because the tree height is bounded to $\approx 1.44 \log_2 n$.
</details>

<details>
<summary><strong>41. In AVL deletion, what are L-cases and R-cases?</strong></summary>

- **$L$-cases ($L_0, L_1, L_{-1}$):** Node was deleted from the Left subtree of critical node $A$.
- **$R$-cases ($R_0, R_1, R_{-1}$):** Node was deleted from the Right subtree of critical node $A$.
</details>

---

## Multi-Way Search Trees, B-Trees & B+ Trees

<details>
<summary><strong>42. What is an m-way search tree?</strong></summary>

A tree where each node can have up to $m$ children and up to $m - 1$ sorted keys.
</details>

<details>
<summary><strong>43. What is the primary purpose of m-way and B-Trees?</strong></summary>

To increase fan-out and minimize tree height, reducing costly disk I/O operations when indexing large datasets on secondary storage.
</details>

<details>
<summary><strong>44. State the minimum and maximum children for internal nodes in a B-Tree of order m.</strong></summary>

Minimum children: $\lceil m/2 \rceil$. Maximum children: $m$.
</details>

<details>
<summary><strong>45. What happens when a B-Tree leaf node overflows during insertion?</strong></summary>

The node splits at its median into two half-full nodes, and the median key is promoted to the parent node.
</details>

<details>
<summary><strong>46. What happens when a B-Tree node underflows during deletion?</strong></summary>

It borrows a key from an immediate sibling if available; otherwise, it merges with a sibling and pulls down the parent separator key.
</details>

<details>
<summary><strong>47. What is the key structural difference between a B-Tree and a B+ Tree?</strong></summary>

In a B-Tree, keys and data records are stored in both internal and leaf nodes. In a B+ Tree, all data records are stored exclusively in leaf nodes, and internal nodes store only index keys.
</details>

<details>
<summary><strong>48. Why do B+ Tree leaf nodes form a linked list?</strong></summary>

To support fast, sequential range queries and bulk scans without repeatedly traversing up and down tree levels.
</details>

<details>
<summary><strong>49. Why does a B+ Tree have a higher fan-out (order) than a B-Tree of the same block size?</strong></summary>

Because B+ Tree internal nodes store only router keys and child pointers (no data pointers), allowing many more index keys to fit in a single disk block.
</details>

---

## Viva Readiness Checklist

- [ ] I can state definitions and properties of tree terms without hesitation.
- [ ] I can trace Inorder, Preorder, and Postorder traversals on any binary tree.
- [ ] I can construct a binary tree from Inorder and Postorder sequences step-by-step.
- [ ] I can trace BST insertions and calculate node Balance Factors in an AVL Tree.
- [ ] I can identify and execute LL, RR, LR, and RL rotations.
- [ ] I can explain B-Tree splitting (median promotion) and merging.
- [ ] I can recite all 8 key differences between B-Trees and B+ Trees.
