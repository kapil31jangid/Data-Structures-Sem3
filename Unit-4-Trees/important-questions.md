# Unit 4 - Important Questions

[← Unit Index](README.md) | [Viva Questions →](viva-questions.md)

---

## Short-Answer Questions (2–5 Marks)

1. **Define a Tree.** Why is a tree classified as a non-linear data structure?
2. **State the relationship between nodes and edges.** In a connected tree with $N$ nodes, how many edges are present?
3. **Define the following tree terms with examples:**
   - Root node
   - Parent and Child nodes
   - Siblings
   - Leaf (Terminal) node
   - Internal (Non-Terminal) node
4. **Differentiate between Degree of a Node and Degree of a Tree.**
5. **Define Level, Height, and Depth of a tree node.**
6. **Explain the Left-Child / Right-Sibling (LCRS) representation of general trees.**
7. **Define a Binary Tree.** What is the maximum degree of any node in a binary tree?
8. **Differentiate between Strictly Binary Tree and Complete Binary Tree.**
9. **What is an Extended Binary Tree?** If an original tree has $N$ nodes, how many dummy external nodes are added?
10. **State the 0-based and 1-based indexing formulas** for finding the parent, left child, and right child in an array-represented binary tree.
11. **State the traversal orders** for Inorder, Preorder, and Postorder traversals.
12. **What is the special property of In-Order traversal in a Binary Search Tree (BST)?**
13. **State the three rules to convert an arbitrary general tree to a binary tree.**
14. **Define an Expression Tree.** What do internal nodes and leaf nodes represent?
15. **What is a Threaded Binary Tree?** Differentiate single-threaded and double-threaded binary trees.
16. **Define an AVL Tree and state the formula for its Balance Factor.**
17. **What are the four types of AVL rotations?**
18. **Define an $m$-Way Search Tree.**
19. **State the fundamental structural properties of a B-Tree of order $m$.**
20. **What is a B+ Tree?** How does its leaf node structure differ from a B-Tree?

---

## Long-Answer / Theory Questions (7–10 Marks)

1. **Explain the memory representation of general trees.** Discuss both **List Representation** and **Left-Child / Right-Sibling Representation** with diagrams and pointer tables.
2. **Explain Binary Tree Traversals.** Write the complete recursive algorithms for:
   - `Procedure RINORDER(T)`
   - `Procedure RPREORDER(T)`
   - `Procedure RPOSTORDER(T)`
3. **Explain the procedure to construct a unique binary tree** when Inorder and Postorder traversal sequences are given. Why cannot a unique binary tree be constructed using only Preorder and Postorder?
4. **Define a Binary Search Tree (BST).** Write algorithms for insertion and searching in a BST. Discuss its time complexity in the average and worst cases.
5. **Explain AVL Tree rebalancing.** Define Critical Node and explain all four rotations (**LL, RR, LR, RL**) with before-and-after tree diagrams and balance factors.
6. **Discuss AVL deletion cases in detail.** Explain the $L$-series cases ($L_0, L_1, L_{-1}$) and $R$-series cases ($R_0, R_1, R_{-1}$) with illustrative examples.
7. **Explain B-Tree of order $m$.** Write the insertion algorithm (including node splitting and median promotion) and the deletion algorithm (including borrowing from siblings and node merging).
8. **Compare B-Tree and B+ Tree** in detail across data storage, leaf linking, fan-out/order, key duplication, and disk I/O efficiency.

---

## Numerical & Practical Problem Questions

### Problem 1: Binary Tree Traversals
Find the Inorder, Preorder, and Postorder traversals for the binary tree containing nodes `A` to `K` from the course reference slides:
- Root `A` with left child `B` and right child `C`
- `B` has left `D` (with children `I, J`) and right `F`
- `C` has left `G` (with child `K`) and right `H`

### Problem 2: Tree Construction from Traversals
Construct a binary tree from the given traversal sequences:
- **Inorder:** `D, B, E, A, F, C, G`
- **Postorder:** `D, E, B, F, G, C, A`  
*Verify your result by writing the Preorder sequence of the reconstructed tree.*

### Problem 3: BST Construction
Construct a Binary Search Tree (BST) step-by-step for the sequence of numbers:  
`10, 12, 5, 4, 20, 8, 7, 15, 13`

### Problem 4: BST Traversals
Create a BST for the following dataset and write its Preorder, Inorder, and Postorder sequences:  
`10, 3, 15, 22, 6, 45, 65, 23, 78, 34, 5`

### Problem 5: AVL Tree Insertion & Rotations
Construct an AVL Tree step-by-step by inserting the following sequence:  
`63, 9, 19, 27, 18, 108, 99, 81`  
*Show the Balance Factor of every node after each insertion and specify the type of rotation performed at each critical node.*

### Problem 6: AVL Deletion Cases
- **Case A ($R_0$):** Starting with root `20`, left child `10` (with children `5, 18`), right child `30`, delete key `30`.
- **Case B ($R_1$):** Starting with root `50`, left child `40` (with children `30, 45`, `30` has child `10`), right child `60` (with child `55`), delete key `55`.
- **Case C ($R_{-1}$):** Starting with root `45`, left child `36` (with children `27, 39`, `39` has children `37, 41`), right child `63` (with child `72`), delete key `72`.

### Problem 7: B-Tree Operations (Order $m = 5$)
Given an order-5 B-Tree with root `[10 | 50]` and leaves `[2, 3, 5, 7]`, `[22, 44, 45]`, `[55, 66, 68, 70]`:
1. Insert key `17`.
2. Insert key `6` (show median promotion and node split).
3. Insert key `21` (show median promotion and node split).
4. From the resulting tree, delete key `3` (show leaf underflow and node merging).

### Problem 8: Expression Tree Evaluation
Given the arithmetic expression `(a + b * c) * e + f`:
1. Construct the corresponding binary expression tree.
2. Write its prefix and postfix notation strings by tree traversals.

---

## Summary of Operation Complexities

| Data Structure | Search (Avg / Worst) | Insert (Avg / Worst) | Delete (Avg / Worst) | Auxiliary Space |
|---|:---:|:---:|:---:|:---:|
| **Binary Tree** | $O(n) / O(n)$ | $O(1) / O(1)$ | $O(n) / O(n)$ | $O(n)$ |
| **Binary Search Tree** | $O(\log n) / O(n)$ | $O(\log n) / O(n)$ | $O(\log n) / O(n)$ | $O(n)$ |
| **AVL Tree** | $O(\log n) / O(\log n)$ | $O(\log n) / O(\log n)$ | $O(\log n) / O(\log n)$ | $O(n)$ |
| **B-Tree (Order $m$)** | $O(\log_m n) / O(\log_m n)$ | $O(\log_m n) / O(\log_m n)$ | $O(\log_m n) / O(\log_m n)$ | $O(n)$ |
| **B+ Tree (Order $m$)** | $O(\log_m n) / O(\log_m n)$ | $O(\log_m n) / O(\log_m n)$ | $O(\log_m n) / O(\log_m n)$ | $O(n)$ |
