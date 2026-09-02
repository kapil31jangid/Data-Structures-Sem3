# 09 - Doubly Linked List

**Unit 3 · CEM2003C Data Structures** · [← Singly linked list](08-singly-linked-list.md) · [Next: Circular linked list →](10-circular-linked-list.md)

## Definition

A doubly linked list (DLL) stores links in both directions. Each node contains data, a pointer to the next node and a pointer to the previous node.

```mermaid
flowchart LR
    H["head"] <--> A["prev | A | next"]
    A <--> B["prev | B | next"]
    B <--> T["tail"]
```

The first node has `prev = NULL`; the last node has `next = NULL`. Maintaining both `head` and `tail` permits forward and backward traversal.

## Node definition

```c
struct node {
    int data;
    struct node *next;
    struct node *prev;
};
```

## Insertion at the beginning

```text
1. Allocate newNode and set its data.
2. Set newNode->prev = NULL and newNode->next = head.
3. If head exists, set head->prev = newNode.
4. Otherwise set tail = newNode.
5. Set head = newNode.
```

## Insertion at the end

With a tail pointer, connect `tail->next` to the new node, set `newNode->prev = tail`, set `newNode->next = NULL`, then move `tail` to the new node.

## Deletion

When deleting a node, reconnect both neighbouring links:

```text
previous->next = target->next
next->prev = target->prev
```

Handle separately when the target is the first or last node, then free it.

## Advantages and cost

| Advantage | Cost |
|---|---|
| Forward and backward traversal | Two link fields per node |
| Easier deletion when a node is known | More pointer updates |
| Efficient insertion before a known node | More memory than a singly list |

**Next:** [10 - Circular Linked List](10-circular-linked-list.md)
