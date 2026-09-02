# 11 - Linked Implementations of Stack and Queue

**Unit 3 · CEM2003C Data Structures** · [← Circular linked list](10-circular-linked-list.md) · [Next: Applications →](12-linked-list-applications.md)

## Stack using a linked list

The list head acts as `top`. Push and pop happen at the head, so both are `O(1)`.

```mermaid
flowchart TD
    T["top"] --> A["30"]
    A --> B["20"]
    B --> C["10"]
    C --> N["NULL"]
```

### Push

```c
void push(struct node **top, int value) {
    struct node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) {
        printf("Stack Overflow\n");
        return;
    }
    newNode->data = value;
    newNode->next = *top;
    *top = newNode;
}
```

### Pop

```c
int pop(struct node **top, int *ok) {
    if (*top == NULL) {
        *ok = 0;
        return 0;
    }
    struct node *temp = *top;
    int value = temp->data;
    *top = temp->next;
    free(temp);
    *ok = 1;
    return value;
}
```

An allocation failure is treated as overflow; removing from an empty linked stack is underflow.

## Queue using a linked list

Maintain `front` and `rear` pointers. Enqueue at the rear and dequeue at the front.

```mermaid
flowchart LR
    F["front"] --> A["10"]
    A --> B["20"]
    B --> C["30"]
    C --> R["rear"]
```

### Enqueue

```c
void enqueue(struct node **front, struct node **rear, int value) {
    struct node *newNode = malloc(sizeof *newNode);
    if (newNode == NULL) {
        printf("Queue Overflow\n");
        return;
    }
    newNode->data = value;
    newNode->next = NULL;

    if (*rear == NULL) {
        *front = *rear = newNode;
    } else {
        (*rear)->next = newNode;
        *rear = newNode;
    }
}
```

### Linked-stack peek and display

```c
int peek(struct node *top, int *value) {
    if (top == NULL) {
        return 0;
    }
    *value = top->data;
    return 1;
}

void displayStack(struct node *top) {
    for (struct node *temp = top; temp != NULL; temp = temp->next) {
        printf("%d ", temp->data);
    }
    printf("\n");
}
```

### Dequeue

```text
1. If front == NULL, report Underflow.
2. Save front in temp.
3. Move front to front->next.
4. If front becomes NULL, also set rear = NULL.
5. Free temp.
```

### Complete linked-queue helpers

```c
int dequeue(struct node **front, struct node **rear, int *value) {
    if (*front == NULL) {
        printf("Queue Underflow\n");
        return 0;
    }

    struct node *temp = *front;
    *value = temp->data;
    *front = temp->next;
    if (*front == NULL) {
        *rear = NULL;
    }
    free(temp);
    return 1;
}

int peekQueue(struct node *front, int *value) {
    if (front == NULL) {
        return 0;
    }
    *value = front->data;
    return 1;
}

void displayQueue(struct node *front) {
    for (struct node *temp = front; temp != NULL; temp = temp->next) {
        printf("%d ", temp->data);
    }
    printf("\n");
}
```

When the last queue node is removed, both `front` and `rear` must become
`NULL`; otherwise a stale rear pointer remains.

## Complexity

| Structure | Insert | Delete | Extra memory |
|---|---:|---:|---:|
| Linked stack at head | `O(1)` | `O(1)` | One node per item |
| Linked queue with front/rear | `O(1)` | `O(1)` | One node per item |

**Next:** [12 - Linked-List Applications](12-linked-list-applications.md)
