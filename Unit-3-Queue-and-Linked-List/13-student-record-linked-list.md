# 13 - Student Records with a Singly Linked List

**Unit 3 · CEM2003C Data Structures** · [← Linked-list applications](12-linked-list-applications.md) · [Unit index](README.md)

> **Source-aligned example:** The faculty notes create a singly linked list for
> three students, storing roll number, name and age in each node. This version
> keeps the same idea while adding safe input widths and a clear traversal.

## Record node

```c
struct Student {
    int roll;
    char name[30];
    int age;
    struct Student *next;
};
```

```mermaid
flowchart LR
    H["head"] --> S1["roll | name | age"]
    S1 --> S2["roll | name | age"]
    S2 --> S3["roll | name | age"]
    S3 --> N["NULL"]
```

## Complete C example

```c
#include <stdio.h>
#include <stdlib.h>

struct Student {
    int roll;
    char name[30];
    int age;
    struct Student *next;
};

int main(void) {
    struct Student *head = NULL;
    struct Student *tail = NULL;
    int count;

    printf("Number of students: ");
    if (scanf("%d", &count) != 1 || count < 1) {
        printf("Invalid count.\n");
        return 1;
    }

    for (int i = 0; i < count; i++) {
        struct Student *node = malloc(sizeof *node);
        if (node == NULL) {
            printf("Memory allocation failed.\n");
            return 1;
        }

        printf("Enter roll, name and age for student %d: ", i + 1);
        if (scanf("%d %29s %d", &node->roll, node->name, &node->age) != 3) {
            free(node);
            printf("Invalid record.\n");
            return 1;
        }
        node->next = NULL;

        if (head == NULL) {
            head = tail = node;
        } else {
            tail->next = node;
            tail = node;
        }
    }

    printf("\nStudent records:\n");
    for (struct Student *current = head; current != NULL;
         current = current->next) {
        printf("Roll: %d, Name: %s, Age: %d\n",
               current->roll, current->name, current->age);
    }

    while (head != NULL) {
        struct Student *oldHead = head;
        head = head->next;
        free(oldHead);
    }
    return 0;
}
```

## Pointer sequence to remember

1. Allocate a node.
2. Read its record fields.
3. Set `next = NULL`.
4. Connect the previous tail to the new node.
5. Move `tail` to the new node.
6. Traverse from `head` until `NULL`.

This example demonstrates the source material's central idea: a linked list can
store complete records, not only one integer value per node.
