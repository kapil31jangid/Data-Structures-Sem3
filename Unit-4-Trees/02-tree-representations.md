# 02 - Tree Representations

**Unit 4 · CEM2003C Data Structures** · [← Tree Definitions](01-tree-definitions-and-concepts.md) · [Next: Binary Tree →](03-binary-tree.md)

> **Source note:** Based on Chapter 4, slides 12–14. In general trees, nodes can have varying numbers of children. Two standard representation methods are used to store general trees in memory: **List Representation** and **Left Child - Right Sibling Representation**.

## Why Specialized Representations?

In a general tree, each node can have an arbitrary number of children (e.g., node $B$ has 3 children, $C$ has 2, $G$ has 1, and $D$ has 0). If we allocate an array of child pointers in every node matching the maximum degree of the tree, significant memory is wasted on `NULL` pointers.

To solve this, general trees are represented using two flexible memory models:
1. **List Representation**
2. **Left Child - Right Sibling Representation**

---

## 1. List Representation

In the **List Representation**, each node and its children are modeled as linked lists. Two distinct node structures are used:
1. **Data Nodes:** Store the actual element (e.g., `A`, `B`, `C`) and a link to the children list.
2. **Reference / Pointer Nodes:** Store only references (pointers) linking sibling elements and subtrees together.

### How it works:
- We start with a node containing the data of the **root node** (`A`).
- The root node points to a linked list of reference nodes representing its children (`B` and `C`).
- An internal node (like `B`) has its own reference node list representing its children (`D`, `E`, `F`).
- Leaf nodes directly terminate with a `NULL` pointer (`0`).

```text
[A | •] ──> [ • | • ] ───────────────────────────> [ • | 0 ]
              │                                      │
              ▼                                      ▼
            [B | •] ──> [D | •] ──> [ • | • ] ──> [F | 0]    [C | •] ──> [ • | • ] ──> [H | 0]
                                      │                                    │
                                      ▼                                    ▼
                                    [E | •] ──> [I | •] ──> [J | 0]      [G | •] ──> [K | 0]
```

### Key Characteristics:
- Nested lists naturally reflect parent-child hierarchy: `(A (B (D, E (I, J), F), C (G (K), H)))`.
- Efficient memory usage since lists grow dynamically according to the number of children.

---

## 2. Left Child - Right Sibling Representation

The **Left Child - Right Sibling (LCRS)** representation is the standard linked representation for arbitrary general trees.

### Node Structure
Every node contains exactly **three fields**:
1. **`DATA`**: The value stored in the node.
2. **`Left Child (LC)`**: Pointer to the **first (leftmost) child** of this node.
3. **`Right Sibling (RS)`**: Pointer to the **immediate next sibling** (node sharing the same parent to its right).

```text
+-------------------+
|       DATA        |
+---------+---------+
|  Left   |  Right  |
|  Child  | Sibling |
+---------+---------+
```

```c
struct LCRSNode {
    char data;
    struct LCRSNode *leftChild;
    struct LCRSNode *rightSibling;
};
```

---

## Reference Example: 11-Node Tree Representation

Consider the general tree from slide 12:

```text
               A
             /   \
            B     C
          / | \   | \
         D  E  F  G  H
           / \    |
          I   J   K
```

### LCRS Representation Mapping (Slide 14):

```text
             [ A ]
            /     \
         (LC)     (RS)
          /         \
        [ B ] ────(RS)────> [ C ]
       /     \             /     \
    (LC)     (RS)       (LC)     (RS)
     /         \         /         \
   [ D ]─(RS)─>[ E ]─(RS)─>[ F ]  [ G ]─(RS)─>[ H ]
                /                  /
             (LC)               (LC)
              /                  /
            [ I ]─(RS)─>[ J ]  [ K ]
```

### Node-by-Node Pointer Table:

| Node | `Left Child` (First Child) | `Right Sibling` (Next Sibling) |
|:---:|:---:|:---:|
| **`A`** (Root) | `B` | `NULL` |
| **`B`** | `D` | `C` |
| **`C`** | `G` | `NULL` |
| **`D`** | `NULL` | `E` |
| **`E`** | `I` | `F` |
| **`F`** | `NULL` | `NULL` |
| **`G`** | `K` | `H` |
| **`H`** | `NULL` | `NULL` |
| **`I`** | `NULL` | `J` |
| **`J`** | `NULL` | `NULL` |
| **`K`** | `NULL` | `NULL` |

---

## Comparison of Representations

| Feature | List Representation | Left Child - Right Sibling |
|---|---|---|
| **Pointer Overhead** | Requires extra header/reference nodes | Exactly 2 pointers per node |
| **Data Uniformity** | Uses two node types (data vs reference) | Uniform node structure for all nodes |
| **Binary Tree Mapping** | Indirect | Direct 1-to-1 isomorphic mapping to a binary tree |
| **Traversal Simplicity** | Complex pointer jumping | Standard binary tree traversal algorithms apply |

> **Exam Tip:** Left Child - Right Sibling representation is fundamental because it proves that **any arbitrary $N$-ary general tree can be transformed into a Binary Tree** using only two pointer fields per node.

**Next:** [03 - Binary Tree](03-binary-tree.md)
