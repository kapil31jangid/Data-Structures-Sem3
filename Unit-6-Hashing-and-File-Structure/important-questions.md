# Unit 6 - Important Questions

[← Unit Index](README.md) | [Viva Questions →](viva-questions.md)

---

## Short-Answer Questions (2–5 Marks)

1. **What is Hashing?** How does its search time complexity compare with linear search and binary search?
2. **State the best-case and worst-case time complexity of searching using hashing.**
3. **Differentiate between Open Hashing (External Hashing) and Close Hashing (Internal Hashing).**
4. **List three characteristics of a good hash function.**
5. **State the formula for the Division Method of hashing in 1-based and 0-based indexing.**
6. **Explain the Midsquare Method of hashing with a suitable example.**
7. **Differentiate between Fold-shifting and Fold-boundary in the Folding Method.**
8. **What is Digit Analysis? Why is it termed a distribution-dependent hashing method?**
9. **Explain the Length Dependent Method of hashing.**
10. **Explain how Algebraic Coding represents a key as a polynomial.**
11. **State the mathematical formula for Multiplicative Hashing.**
12. **What is a collision in hashing? Why does it occur?**
13. **What is Separate Chaining? State one advantage and one disadvantage.**
14. **What is Open Addressing? List the three open addressing collision resolution techniques.**
15. **What is Primary Clustering in linear probing? How does quadratic probing reduce it?**
16. **State the probing formulas for Double Hashing.**
17. **What is a Blockchain? What role does cryptographic hashing play in it?**
18. **List the metadata fields present in a standard block header.**
19. **Explain the Avalanche Effect in cryptographic hashing.**
20. **How is a blockchain conceptually related to a linked list?**
21. **Define a File, Record, Field, and Key Field.**
22. **List the six primitive operations performed on files.**
23. **What is a Sequential File? State the formula for the number of block accesses required to search it.**
24. **Explain Direct (Hashing) File Organization and the role of the Bucket Directory.**
25. **Define Indexing. What two fields are stored in an index file entry?**
26. **Differentiate between a Sparse Index and a Dense Index.**

---

## Long-Answer / Theory Questions (7–10 Marks)

1. **Explain Hashing and Hash Tables in detail.** Compare Open Hashing and Close Hashing with diagrams and bucket structures.
2. **Explain the different types of Hash Functions** (Division, Midsquare, Folding, Digit Analysis, Length Dependent, Algebraic Coding, Multiplicative) with mathematical formulations and examples.
3. **Discuss Collision Resolution Strategies in detail.** Explain Separate Chaining and Open Addressing with step-by-step algorithms and diagrams.
4. **Explain Linear Probing, Quadratic Probing, and Double Hashing.** Discuss how primary clustering arises in linear probing and how double hashing addresses it.
5. **Explain the architecture of a Blockchain.** Detail the block structure, hash chain linkage, and provide a worked example demonstrating how hash mismatch detects data tampering.
6. **Discuss Sequential File Organization.** Detail its structure, physical ordering, advantages, and disadvantages.
7. **Explain Direct / Hashing File Organization.** Explain how bucket directories and chained blocks operate, and state the formula for average block access time.
8. **Explain Indexing Techniques.** Detail Primary Indexes (Indexed Sequential Files), Clustering Indexes, and Secondary Indexes with diagrams and comparative analysis.

---

## Numerical & Worked Example Questions

### Problem 1: Hash Calculation Methods
- **Division Method:** For key $K = 23$ and table size $m = 10$, calculate the 1-based hash location using $L = (K \bmod m) + 1$.
- **Midsquare Method:** For key $K = 16$ and a desired 2-digit address, compute the square and extract the middle address.
- **Folding Method:** For key $K = 12345678$ and a desired 2-digit address, compute the location using:
  1. Fold-shifting
  2. Fold-boundary
- **Digit Analysis:** For key $K = 9861234$, if the 3rd and 5th position digits occur frequently, find the reversed hash address.

### Problem 2: Separate Chaining Construction
Construct a separate chaining hash table with **5 locations (indices 0 to 4)** for the dataset:  
$$\{1,\; 2,\; 3,\; 4,\; 5,\; 10,\; 21,\; 22,\; 33,\; 34,\; 15,\; 32,\; 31,\; 48,\; 49,\; 50\}$$  
*Show the final linked lists attached to each bucket.*

### Problem 3: Linear Probing Step-by-Step Trace
Insert the keys $\{5,\; 18,\; 55,\; 78,\; 35,\; 15\}$ into a hash table of size $m = 10$ (slots $0$ to $9$) using the hash function $f(\text{key}) = \text{key} \bmod 10$ and linear probing.  
*Show the table state after every single insertion.*

### Problem 4: Indexing vs Sequential File Access Cost
Given:
- Data file with $1024$ records of $128 \text{ bytes}$ each.
- Disk block size $= 2048 \text{ bytes}$.
- Index file key field size $V = 4 \text{ bytes}$ and block pointer size $P = 4 \text{ bytes}$.
1. Calculate the number of blocks and binary search block accesses for the sequential data file.
2. Calculate the number of blocks and binary search block accesses for the index file.

### Problem 5: Blockchain Tamper Detection Trace
Block 2 contains transaction data totaling $₹100$, producing hash $H_2$, which is stored in Block 3's `Previous Hash` field.  
Trace what occurs when an adversary alters Block 2's amount to $₹900$.

---

## Comparison Questions

### Comparison 1: Open Hashing vs Close Hashing

| Parameter | Open Hashing | Close Hashing |
|---|---|---|
| **Storage Area** | External / Unlimited space | Fixed / Internal array |
| **Node Storage** | Outside table in linked lists | Inside table slots directly |
| **Elements per Slot** | Multiple per bucket | Exactly one per slot |
| **Primary Method** | Separate Chaining | Open Addressing |

### Comparison 2: Linear Probing vs Quadratic Probing vs Double Hashing

| Feature | Linear Probing | Quadratic Probing | Double Hashing |
|---|---|---|---|
| **Probe Function** | $(h(k) + i) \bmod m$ | $(h(k) + i^2) \bmod m$ | $(h_1(k) + i \cdot h_2(k)) \bmod m$ |
| **Step Size** | Constant ($+1$) | Quadratic ($+1, +4, +9$) | Computed via $h_2(k)$ |
| **Clustering** | Suffers from Primary Clustering | Reduces Primary Clustering | Minimizes all clustering |
| **Table Coverage** | Guaranteed to find empty slot | May miss empty slots | Guaranteed if $h_2(k)$ and $m$ are coprime |

### Comparison 3: Primary Index vs Clustering Index vs Secondary Index

| Feature | Primary Index | Clustering Index | Secondary Index |
|---|---|---|---|
| **Data File Ordering** | Ordered on Primary Key | Ordered on Non-Key Field | Unordered / Non-Ordering Field |
| **Index Density** | Sparse (One entry per block) | Sparse (One entry per cluster) | Dense (One entry per record) |
| **Number of Indexes** | Exactly 1 per file | At most 1 per file | Multiple indexes allowed |
| **Storage Overhead** | Minimal | Moderate | Highest |
