# Unit 6 - Hashing and File Structure Viva Questions

[← Important Questions](important-questions.md) | [Unit Index →](README.md)

Open each answer only after attempting it aloud.

---

## Hashing Fundamentals & Hash Tables

<details>
<summary><strong>1. What is hashing?</strong></summary>

A data storage and retrieval technique where a record's location is computed directly from its key value using an arithmetic hash function, achieving average $O(1)$ search time without requiring sorted data.
</details>

<details>
<summary><strong>2. What are the best-case and worst-case search complexities in hashing?</strong></summary>

Best-case and average-case complexity is $O(1)$; worst-case complexity is $O(n)$ when all keys collide into the same slot.
</details>

<details>
<summary><strong>3. What is Open Hashing (External Hashing)?</strong></summary>

A hashing architecture where records are stored in unlimited space (using linked lists attached to bucket table slots) with no restriction on table capacity.
</details>

<details>
<summary><strong>4. What is Close Hashing (Internal Hashing)?</strong></summary>

A hashing architecture where all records are stored directly inside fixed table slots, permitting only one element per slot and requiring re-hashing when collisions occur.
</details>

<details>
<summary><strong>5. What is a collision in a hash table?</strong></summary>

A condition where the hash function maps two distinct search keys to the exact same table slot.
</details>

---

## Hash Functions

<details>
<summary><strong>6. What are the three characteristics of a good hash function?</strong></summary>

1. Avoids collisions.
2. Spreads keys evenly across the table.
3. Is easy and fast to compute.
</details>

<details>
<summary><strong>7. How does the Division Method compute a hash address?</strong></summary>

By taking the remainder of key $K$ divided by table size $m$: $L = (K \bmod m) + 1$ (1-based) or $L = K \bmod m$ (0-based).
</details>

<details>
<summary><strong>8. How does the Midsquare Method work?</strong></summary>

It squares the key ($K^2$) and extracts the middle digits corresponding to the required address width.
</details>

<details>
<summary><strong>9. Differentiate Fold-shifting and Fold-boundary in the Folding Method.</strong></summary>

- **Fold-shifting:** Partitions the key into segments and adds their actual values directly.
- **Fold-boundary:** Reverses the outer boundary segments before addition, keeping middle segments unchanged.
</details>

<details>
<summary><strong>10. What is Digit Analysis?</strong></summary>

A distribution-dependent method where digit positions with uniform or frequent distribution are statistically identified, extracted, and reversed/shifted to form the address.
</details>

<details>
<summary><strong>11. How does the Length Dependent Method generate an address?</strong></summary>

It combines the length of the key with a selected portion of the key to generate a direct or intermediate hash address.
</details>

<details>
<summary><strong>12. What is Algebraic Coding in hashing?</strong></summary>

Representing an $n$-bit binary key as a polynomial $f(x)$ and computing the address polynomial as $f(x) \bmod d(x)$ using a divisor polynomial $d(x)$.
</details>

<details>
<summary><strong>13. State the formula for Multiplicative Hashing.</strong></summary>

$h(k) = \lfloor m \cdot (kc \bmod 1) \rfloor$, where $k$ is the non-negative key, $m$ is table size, and $c \in (0, 1)$ is a constant fraction.
</details>

---

## Collision Resolution Strategies

<details>
<summary><strong>14. What is Separate Chaining?</strong></summary>

A collision resolution method where each hash table slot acts as the head of a linked list storing all keys that hash to that slot.
</details>

<details>
<summary><strong>15. What is the primary disadvantage of Separate Chaining?</strong></summary>

It requires additional memory for pointer links in linked list nodes and performs poorly if chains become excessively long.
</details>

<details>
<summary><strong>16. What is Open Addressing?</strong></summary>

A closed-hashing strategy where colliding elements are stored in alternate available empty slots within the hash table itself.
</details>

<details>
<summary><strong>17. What is Linear Probing?</strong></summary>

An open addressing technique where, upon collision, subsequent adjacent slots $(h(k) + i) \bmod m$ are probed sequentially with wraparound.
</details>

<details>
<summary><strong>18. What is Primary Clustering?</strong></summary>

The tendency of colliding keys in linear probing to form long contiguous blocks of occupied slots, degrading average search and insertion times.
</details>

<details>
<summary><strong>19. How does Quadratic Probing reduce primary clustering?</strong></summary>

By probing slots using quadratic step intervals: $(h(k) + i^2) \bmod m \implies +1, +4, +9, \dots$ instead of consecutive linear increments.
</details>

<details>
<summary><strong>20. What is Double Hashing?</strong></summary>

An open addressing method that uses two hash functions: $h_1(k)$ computes the initial slot and $h_2(k)$ computes the variable step size for collision probes.
</details>

<details>
<summary><strong>21. State the probing formula for Double Hashing.</strong></summary>

$h(k, i) = (h_1(k) + i \cdot h_2(k)) \bmod m$, where $i = 0, 1, 2, \dots$ is the probe number.
</details>

---

## Blockchain and Hashing

<details>
<summary><strong>22. What is a blockchain?</strong></summary>

A distributed, tamper-evident ledger shared among multiple computers where transactions are grouped into chronologically connected blocks.
</details>

<details>
<summary><strong>23. What metadata fields are stored in a block header?</strong></summary>

Previous Block Hash, Timestamp, Nonce (consensus data), and Merkle Root.
</details>

<details>
<summary><strong>24. What is the Avalanche Effect in cryptographic hashing?</strong></summary>

A property where a microscopic change in input data causes the resulting cryptographic hash to change completely and unpredictably.
</details>

<details>
<summary><strong>25. How is a blockchain analogous to a linked list?</strong></summary>

Both connect records in sequence; while a linked list uses memory address pointers, a blockchain uses cryptographic hash references (hash pointers).
</details>

<details>
<summary><strong>26. How does a blockchain detect data tampering?</strong></summary>

Modifying data in a block alters its hash; the subsequent block's stored `Previous Hash` then mismatches, breaking the cryptographic chain and exposing the modification.
</details>

---

## File Structure & File Organizations

<details>
<summary><strong>27. Define a file, record, and field.</strong></summary>

- **Field:** A fixed-length data item describing an attribute.
- **Record:** A collection of related fields.
- **File:** A collection of related records having identical field structures.
</details>

<details>
<summary><strong>28. What is a key field in a file?</strong></summary>

A designated field whose value uniquely identifies an individual record (e.g., `Roll No.`).
</details>

<details>
<summary><strong>29. Name the six primitive operations performed on files.</strong></summary>

Creation, Reading, Insertion, Deletion, Updation, and Searching.
</details>

<details>
<summary><strong>30. What is a Sequential File?</strong></summary>

A file format where records are physically stored in contiguous order based on a designated ordering key field.
</details>

<details>
<summary><strong>31. What is the search time complexity in a sequential file with b blocks?</strong></summary>

$\log_2 b$ block accesses using Binary Search on the ordering key.
</details>

<details>
<summary><strong>32. State two major disadvantages of sequential files.</strong></summary>

1. High insertion/deletion overhead due to mandatory physical shifting of records.
2. Inefficient linear search when querying on non-ordering fields.
</details>

<details>
<summary><strong>33. What is Direct / Hashing File Organization?</strong></summary>

A secondary storage organization where records are partitioned into buckets using a hash function, allowing direct block address calculation without sequential scanning.
</details>

<details>
<summary><strong>34. What is a Bucket Directory in hashed files?</strong></summary>

A lookup directory that translates bucket numbers into the physical disk addresses of the first block of chained block linked lists.
</details>

<details>
<summary><strong>35. How many block accesses does a well-designed hashed file structure require?</strong></summary>

Typically 2 block accesses (1 to access the bucket directory + 1 to access the target data block).
</details>

---

## Indexing Techniques

<details>
<summary><strong>36. What is Indexing?</strong></summary>

An access acceleration technique that uses a small auxiliary sequential file (Index File) containing key-pointer pairs to quickly locate records in the main file.
</details>

<details>
<summary><strong>37. What fields are contained in an index file entry?</strong></summary>

A search key value and a physical disk block/record pointer ($V + P$).
</details>

<details>
<summary><strong>38. Why does searching an index file require fewer block accesses than searching the main data file?</strong></summary>

Because index entries are compact (e.g., 8 bytes vs 128 bytes), fitting many more entries per disk block and reducing the total number of blocks to search ($\log_2 \text{Index Blocks} \ll \log_2 \text{Data Blocks}$).
</details>

<details>
<summary><strong>39. What is a Primary Index (Indexed Sequential File)?</strong></summary>

A sparse index built on the primary key of a data file that is physically sorted on that same primary key (storing one entry per data block).
</details>

<details>
<summary><strong>40. What is a Clustering Index?</strong></summary>

A sparse index created on a non-key field of a data file that is physically ordered on that non-key field, pointing to the start of each duplicate cluster.
</details>

<details>
<summary><strong>41. What is a Secondary Index (Simple Index File)?</strong></summary>

A dense index created on a non-ordering field of a data file, containing an explicit entry for every record in the file.
</details>

<details>
<summary><strong>42. Differentiate Sparse Index and Dense Index.</strong></summary>

- **Sparse Index:** Contains an entry for each disk block or cluster (e.g., Primary & Clustering indexes).
- **Dense Index:** Contains an entry for every individual record in the data file (e.g., Secondary index).
</details>

<details>
<summary><strong>43. Can a file have multiple primary indexes? Multiple secondary indexes?</strong></summary>

A file can have only **one** primary index (since records can only be sorted in one physical order), but can have **multiple** secondary indexes for different search attributes.
</details>

---

## Viva Readiness Checklist

- [ ] I can explain why hashing provides $O(1)$ search time.
- [ ] I can state and calculate all 7 hashing methods (Division, Midsquare, Folding, Digit Analysis, Length Dependent, Algebraic, Multiplicative).
- [ ] I can resolve collisions using Separate Chaining, Linear Probing, Quadratic Probing, and Double Hashing.
- [ ] I can explain primary clustering and how double hashing eliminates it.
- [ ] I can draw the block structure and explain hash chaining in blockchain.
- [ ] I can explain the 6 primitive file operations and the $\log_2 b$ cost of sequential files.
- [ ] I can state the average block access formula for direct hashed files with bucket directories.
- [ ] I can differentiate Primary, Clustering, and Secondary indexes with density and ordering rules.
