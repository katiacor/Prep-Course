# Big O Notation and Time Complexity

## Complexity Evaluation

Let's say we have a computational problem to solve and two different algorithms that can solve it. We need to find out which one is more efficient, meaning it has lower complexity.

Complexity consists of two factors:

- Time Complexity: the amount of time required for the algorithm to complete.
- Space Complexity: the amount of memory required for the algorithm to complete.

### Time Complexity

Since running time depends on the machine we are using, we use processor operations, or steps, to measure the algorithm running time instead of seconds.

- Any indivisible language operation is considered to be executed in **1 operation** (i = 0, i++, etc).
- Any loop is executed in the following number of steps:
    - **N * (number of operations inside the loop)**, where **N** is a number of iterations.


## Complexity Cases

- We always look for the worst-case time complexity.
- We do not write 'worst-case', but 'complexity'.
- If asked to evaluate complexity, evaluate the worst-case time complexity.

