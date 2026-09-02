# 08 - Singly Linked List

**Unit 3 · CEM2003C Data Structures** · [← Fundamentals](07-linked-list-fundamentals.md) · [Next: Doubly linked list →](09-doubly-linked-list.md)

## Structure

Each node has a data field and one pointer to its successor. The final pointer is `NULL`.

```mermaid
flowchart LR
    H["head"] --> N1["A"]
    N1 --> N2["B"]
    N2 --> N3["C"]
    N3 --> Z["NULL"]
```

## Traversal

```c
void traverse(struct node *head) {
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }

    for (struct node *temp = head; temp != NULL; temp = temp->next) {
        printf("Data = %d\n", temp->data);
    }
}
```

Stop when the current pointer becomes `NULL`.

## Insertion at the front

```text
1. Allocate a new node.
2. Put the item in newNode->data.
3. Set newNode->next = head.
4. Set head = newNode.
```

```c
struct node *insertFront(struct node *head, int data) {
    struct node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) return head;
    newNode->data = data;
    newNode->next = head;
    return newNode;
}
```

This operation is `O(1)`.

## Insertion at the end

Allocate a node with `next = NULL`, traverse to the last node, then set `last->next = newNode`. It is `O(n)` without a tail pointer and `O(1)` with a maintained tail pointer.

## Insertion at a position

To insert at position `p`, reach the node at position `p - 1`, preserve its old successor, then link in the new node:

```c
newNode->next = temp->next;
temp->next = newNode;
```

The order matters. Changing `temp->next` first would lose the remainder of the list.

## Deletion

### Front

Save `head` in a temporary pointer, move `head = head->next`, then `free` the saved node. Complexity: `O(1)`.

### End

Traverse while tracking the second-last node. Set its `next` to `NULL`, then free the former last node. Complexity: `O(n)` without a tail/previous pointer.

### Any position

Reach the target and its predecessor, bypass the target using `previous->next = target->next`, then free the target.

## Safety rules

- Check `head == NULL` before deletion.
- Check `malloc` before dereferencing a new node.
- Free every removed node exactly once.
- Never use a pointer after its node has been freed.

**Next:** [09 - Doubly Linked List](09-doubly-linked-list.md)
