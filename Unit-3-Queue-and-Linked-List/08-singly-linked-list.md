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

## Complete menu-driven C implementation

Positions in this program are **1-based**, which matches the step-by-step
insertion and deletion descriptions in the faculty notes.

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node *next;
} Node;

Node *head = NULL;

void display(void) {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }

    for (Node *temp = head; temp != NULL; temp = temp->next) {
        printf("%d ", temp->data);
    }
    printf("\n");
}

void insertFront(int data) {
    Node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = head;
    head = newNode;
}

void insertEnd(int data) {
    Node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = NULL;

    if (head == NULL) {
        head = newNode;
        return;
    }

    Node *temp = head;
    while (temp->next != NULL) {
        temp = temp->next;
    }
    temp->next = newNode;
}

void insertAtPosition(int data, int position) {
    if (position <= 1) {
        insertFront(data);
        return;
    }

    Node *temp = head;
    for (int i = 1; temp != NULL && i < position - 1; i++) {
        temp = temp->next;
    }
    if (temp == NULL) {
        printf("Invalid position.\n");
        return;
    }

    Node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) {
        printf("Memory allocation failed.\n");
        return;
    }
    newNode->data = data;
    newNode->next = temp->next;
    temp->next = newNode;
}

void deleteFront(void) {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }
    Node *toDelete = head;
    head = head->next;
    free(toDelete);
}

void deleteEnd(void) {
    if (head == NULL) {
        printf("List is empty.\n");
        return;
    }

    if (head->next == NULL) {
        free(head);
        head = NULL;
        return;
    }

    Node *previous = NULL;
    Node *toDelete = head;
    while (toDelete->next != NULL) {
        previous = toDelete;
        toDelete = toDelete->next;
    }
    previous->next = NULL;
    free(toDelete);
}

void deleteAtPosition(int position) {
    if (head == NULL || position < 1) {
        printf("Invalid position.\n");
        return;
    }
    if (position == 1) {
        deleteFront();
        return;
    }

    Node *previous = head;
    for (int i = 1; previous != NULL && i < position - 1; i++) {
        previous = previous->next;
    }
    if (previous == NULL || previous->next == NULL) {
        printf("Invalid position.\n");
        return;
    }

    Node *toDelete = previous->next;
    previous->next = toDelete->next;
    free(toDelete);
}

void freeList(void) {
    while (head != NULL) {
        deleteFront();
    }
}

int main(void) {
    int choice, data, position;

    do {
        printf("\n1.Insert front  2.Insert end  3.Insert position\n");
        printf("4.Delete front  5.Delete end  6.Delete position\n");
        printf("7.Display        0.Exit\nChoice: ");
        if (scanf("%d", &choice) != 1) {
            break;
        }

        switch (choice) {
            case 1:
                printf("Data: "); scanf("%d", &data); insertFront(data); break;
            case 2:
                printf("Data: "); scanf("%d", &data); insertEnd(data); break;
            case 3:
                printf("Data and 1-based position: ");
                scanf("%d%d", &data, &position);
                insertAtPosition(data, position); break;
            case 4: deleteFront(); break;
            case 5: deleteEnd(); break;
            case 6:
                printf("1-based position: "); scanf("%d", &position);
                deleteAtPosition(position); break;
            case 7: display(); break;
            case 0: break;
            default: printf("Invalid choice.\n");
        }
    } while (choice != 0);

    freeList();
    return 0;
}
```

The pointer changes in the middle operations are the key exam steps:

```text
newNode->next = temp->next;   // preserve the remaining list
temp->next = newNode;         // insert the new link

previous->next = toDelete->next; // bypass the deleted node
free(toDelete);                  // release its memory
```

**Next:** [09 - Doubly Linked List](09-doubly-linked-list.md)
