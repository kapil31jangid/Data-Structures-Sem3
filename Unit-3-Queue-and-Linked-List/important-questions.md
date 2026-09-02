# Unit 3 - Important Questions

[← Unit Index](README.md) | [Viva Questions →](viva-questions.md)

## Queue: short-answer questions

1. Define a queue and explain FIFO.
2. What are `front`, `rear` and `size`?
3. State the underflow and overflow conditions of a linear queue.
4. List the basic queue operations.
5. Why does a linear queue waste array space?
6. Define a circular queue.
7. State the modulo formulas for the next front and rear positions.
8. State the overflow and underflow conditions of a circular queue.
9. Define a deque.
10. Differentiate input-restricted and output-restricted deques.
11. Define a priority queue.
12. Differentiate ascending and descending priority queues.
13. List applications of queues.

## Linked list: short-answer questions

1. Define a linked list and a node.
2. What is a self-referential structure?
3. What is the role of the head pointer?
4. Why is random access unavailable in a linked list?
5. State the features of a singly linked list.
6. Differentiate singly, doubly and circular linked lists.
7. What fields are present in a doubly linked node?
8. Why does a circular list not end with `NULL`?
9. What is the purpose of `free()` after deletion?
10. How are stack and queue implemented using linked nodes?

## Descriptive and algorithm questions

1. Explain array representation of a linear queue with enqueue and dequeue algorithms.
2. Explain circular-queue insertion, deletion and traversal with wrap-around diagrams.
3. Explain deques, their types and the insert-front algorithm.
4. Explain priority queues, their characteristics, types and implementations.
5. Explain queue applications in round-robin scheduling, customer service and shared printing.
6. Define a singly linked list and write traversal, insertion and deletion algorithms.
7. Explain insertion and deletion at the beginning, end and a specified position.
8. Explain doubly linked-list structure and bidirectional traversal.
9. Explain circular linked-list traversal and safe stopping conditions.
10. Implement a stack using linked nodes and analyse its operations.
11. Implement a queue using `front` and `rear` linked pointers.
12. Compare array and linked implementations of stacks and queues.

## Complexity prompts

| Operation | Typical complexity |
|---|---:|
| Array enqueue / dequeue | `O(1)` |
| Circular enqueue / dequeue | `O(1)` |
| Queue display | `O(n)` |
| Singly-list insertion at head | `O(1)` |
| Singly-list insertion at end without tail | `O(n)` |
| Linked stack push / pop | `O(1)` |
| Linked queue enqueue / dequeue with both pointers | `O(1)` |
