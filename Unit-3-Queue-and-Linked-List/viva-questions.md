# Unit 3 - Queue and Linked List Viva Questions

[← Important Questions](important-questions.md) | [Unit Index →](README.md)

Open each answer only after attempting it aloud.

## Queue viva

<details>
<summary><strong>1. What is a queue?</strong></summary>

A linear data structure where insertion occurs at the rear and deletion occurs
at the front.
</details>

<details>
<summary><strong>2. Which principle does a queue follow?</strong></summary>

FIFO: First In, First Out.
</details>

<details>
<summary><strong>3. What do front and rear represent?</strong></summary>

`front` identifies the next element to delete; `rear` identifies the last
inserted element.
</details>

<details>
<summary><strong>4. What is queue underflow?</strong></summary>

Trying to delete from an empty queue, represented by `front == -1` in the array
implementation.
</details>

<details>
<summary><strong>5. What is queue overflow?</strong></summary>

Trying to insert when the queue has no available capacity. In a linear queue,
the condition is `rear == size - 1`.
</details>

<details>
<summary><strong>6. Why is a circular queue better than a linear queue?</strong></summary>

It reuses empty cells released at the front by wrapping indices with modulo
arithmetic.
</details>

<details>
<summary><strong>7. State circular-queue overflow.</strong></summary>

`front == (rear + 1) % size`.
</details>

<details>
<summary><strong>8. What is a deque?</strong></summary>

A queue that permits insertion and deletion at both ends.
</details>

<details>
<summary><strong>9. What is a priority queue?</strong></summary>

A queue that serves elements according to priority; tied priorities retain FIFO
order.
</details>

<details>
<summary><strong>10. Name queue applications from the notes.</strong></summary>

Round-robin processor scheduling, customer service systems and shared-network
printer jobs.
</details>

## Linked-list viva

<details>
<summary><strong>11. What is a node?</strong></summary>

A record containing data and one or more links to other nodes.
</details>

<details>
<summary><strong>12. What is a self-referential structure?</strong></summary>

A structure containing a pointer to the same structure type, such as
`struct node *next`.
</details>

<details>
<summary><strong>13. What does head store?</strong></summary>

The address of the first node in a linked list.
</details>

<details>
<summary><strong>14. Why is random access unavailable?</strong></summary>

Nodes are reached by following links sequentially; there is no direct index
calculation as in an array.
</details>

<details>
<summary><strong>15. What terminates a singly linked list?</strong></summary>

The last node's `next` pointer is `NULL`.
</details>

<details>
<summary><strong>16. What extra field does a doubly linked node contain?</strong></summary>

A `prev` pointer to the previous node.
</details>

<details>
<summary><strong>17. How is a circular list different?</strong></summary>

Its last node points back to the first node, so it has no terminating `NULL`.
</details>

<details>
<summary><strong>18. Why must a deleted node be freed?</strong></summary>

To return its dynamically allocated memory and prevent a memory leak.
</details>

<details>
<summary><strong>19. Where is a linked stack inserted and deleted?</strong></summary>

At the head, which acts as `top`; both operations are `O(1)`.
</details>

<details>
<summary><strong>20. Which pointers are needed for a linked queue?</strong></summary>

`front` for deletion and `rear` for insertion. When the last node is removed,
both must become `NULL`.
</details>

## Viva readiness

- [ ] I can trace front and rear after every queue operation.
- [ ] I can explain modulo wrap-around without drawing confusion.
- [ ] I can update both links in a doubly linked list.
- [ ] I can stop circular traversal after one complete cycle.
- [ ] I can justify every `malloc` and `free`.
