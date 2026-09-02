# Unit 2 - Array and Stack Viva Questions

[← Important Questions](important-questions.md) | [Unit Index →](README.md)

Open each answer only after attempting it aloud.

## Array Viva

<details>
<summary><strong>1. What is an array?</strong></summary>

An array is a collection of same-type elements stored under one common name.

</details>

<details>
<summary><strong>2. What is the first index of a C array?</strong></summary>

Index `0`.

</details>

<details>
<summary><strong>3. Why is random access possible in an array?</strong></summary>

Elements are contiguous, so the address of `A[i]` is calculated from the base
address, index and element size.

</details>

<details>
<summary><strong>4. What are the valid indices of `int a[8]`?</strong></summary>

`0` through `7`.

</details>

<details>
<summary><strong>5. How is a 2D array organised?</strong></summary>

As an array of arrays, addressed using a row index and a column index.

</details>

<details>
<summary><strong>6. Why are nested loops used for a 2D array?</strong></summary>

One loop selects rows and the other selects columns, allowing every cell to be
visited.

</details>

<details>
<summary><strong>7. Name common array applications.</strong></summary>

Collections, traversal and aggregation, searching, sorting, tables/matrices,
and the storage layer for stacks and queues.

</details>

<details>
<summary><strong>8. What is a sparse matrix?</strong></summary>

A matrix in which most entries are zero. This is a supplementary Unit 2 topic.

</details>

<details>
<summary><strong>9. What does a triplet store?</strong></summary>

The row, column and value of each non-zero entry, plus a header containing the
matrix dimensions and non-zero count.

</details>

<details>
<summary><strong>10. When is sparse representation useful?</strong></summary>

When the number of non-zero values `k` is much smaller than `rows × columns`.

</details>

## Stack Viva

<details>
<summary><strong>1. What is a stack?</strong></summary>

A stack is a linear data structure in which insertion and deletion occur at one
end called the top.

</details>

<details>
<summary><strong>2. Which principle does a stack follow?</strong></summary>

Last In, First Out or LIFO.

</details>

<details>
<summary><strong>3. What does top = -1 mean?</strong></summary>

It means the array-based stack is empty.

</details>

<details>
<summary><strong>4. What is stack overflow?</strong></summary>

It is an attempt to push an element when `top == SIZE - 1`.

</details>

<details>
<summary><strong>5. What is stack underflow?</strong></summary>

It is an attempt to remove an element when `top == -1`.

</details>

<details>
<summary><strong>6. What does PUSH do?</strong></summary>

It increments `top` and inserts a new item at `stack[top]` after checking for
overflow.

</details>

<details>
<summary><strong>7. What does POP do?</strong></summary>

It returns the topmost item and decrements `top` after checking for underflow.

</details>

<details>
<summary><strong>8. Does PEEP remove an element?</strong></summary>

No. It retrieves an element from a specified valid position without modifying
the stack.

</details>

<details>
<summary><strong>9. What is the time complexity of PUSH and POP?</strong></summary>

Both have `O(1)` time complexity.

</details>

<details>
<summary><strong>10. What is the time complexity of DISPLAY?</strong></summary>

`O(n)`, because every stack element is visited.

</details>

<details>
<summary><strong>11. What is infix notation?</strong></summary>

The operator is placed between operands, as in `A + B`.

</details>

<details>
<summary><strong>12. What is prefix notation?</strong></summary>

The operator is placed before its operands, as in `+ A B`. It is also called
Polish notation.

</details>

<details>
<summary><strong>13. What is postfix notation?</strong></summary>

The operator is placed after its operands, as in `A B +`. It is also called
Reverse Polish notation.

</details>

<details>
<summary><strong>14. How is an operand handled during postfix evaluation?</strong></summary>

It is pushed onto the stack.

</details>

<details>
<summary><strong>15. How is an operator handled during postfix evaluation?</strong></summary>

Two operands are popped, the operation is performed in correct left-right
order, and the result is pushed back.

</details>

<details>
<summary><strong>16. What happens to an operand during infix-to-postfix conversion?</strong></summary>

It is immediately appended to the postfix output.

</details>

<details>
<summary><strong>17. What happens when ')' is encountered?</strong></summary>

Operators are popped into the output until `(` is found. The `(` is removed but
not added to the output.

</details>

<details>
<summary><strong>18. What are the main infix-to-prefix steps?</strong></summary>

Reverse the infix expression, swap parentheses, convert to postfix, and reverse
the postfix result.

</details>

<details>
<summary><strong>19. What is recursion?</strong></summary>

Recursion occurs when a function calls itself directly or indirectly.

</details>

<details>
<summary><strong>20. What is a base case?</strong></summary>

It is a terminating condition that stops further recursive calls.

</details>

<details>
<summary><strong>21. How are recursive calls stored?</strong></summary>

Each call receives its own stack frame on the call stack.

</details>

<details>
<summary><strong>22. Why does infinite recursion cause stack overflow?</strong></summary>

New stack frames continue to be allocated until the available call-stack memory
is exhausted.

</details>

<details>
<summary><strong>23. How many rods are used in Tower of Hanoi?</strong></summary>

Three: source, auxiliary and destination.

</details>

<details>
<summary><strong>24. What is the minimum number of moves for n disks?</strong></summary>

`2^n - 1`.

</details>

<details>
<summary><strong>25. What is Tower of Hanoi's time complexity?</strong></summary>

`O(2^n)`.

</details>

<details>
<summary><strong>26. What is its recursive stack-space complexity?</strong></summary>

`O(n)` because the maximum recursion depth is proportional to the number of
disks.

</details>

## Viva Readiness

- [ ] I can explain each operation using `top`.
- [ ] I can trace an expression-conversion stack.
- [ ] I can explain the call stack without memorised wording.
- [ ] I can derive the Tower of Hanoi recurrence.

[← Important Questions](important-questions.md) | [Unit Index →](README.md)
