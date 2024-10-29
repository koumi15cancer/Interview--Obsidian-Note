There are a few characteristics of this algorithm that make it a greedy algorithm:

**Greedy Choice Property** By repeatedly making a _locally_ optimal choice, we can arrive at a _globally_ optimal solution.

In this case, after sorting the arrays, the locally optimal (or "greedy") choice is to give each child the smallest cookie that will satisfy them. After iterating over the array, we will have maximized the number of satisfied children (the global optimal solution).

In other words, we always make the best possible choice without worrying about the future consequences of that choice. When we do need to worry about future consequences, we often need to use dynamic programming instead.

**Optimal Substructure** The optimal solution to the problem can be constructed from the optimal solutions to its subproblems.

For this question, once we have assigned a cookie to a child, we can safely remove the child and the cookie from the arrays, and the problem reduces to assigning the remaining cookies to the remaining children. This allows us to solve the problem by making a series of locally optimal choices.

**No Backtracking** Greedy algorithms make a decision once and do not revisit it. In this case, once we have assigned a cookie to a child, we never revisit that decision by taking the cookie back and giving it to another child, or giving the child a different cookie.

### Greedy vs. Dynamic Programming

Greedy algorithms and [dynamic programming](https://www.hellointerview.com/learn/code/dynamic-programming/fundamentals) are both used to solve optimization problems, so it's useful to build an understanding of when to use each approach

If you're faced with an optimization problem, first try to identify whether the greedy choice property holds.

The most straightforward way to do so is to try to find a **counter example** in which following the greedy choice does not lead to the optimal solution. The above example of the longest increasing subsequence is a counter example that shows that a greedy approach does not work.

If you can find a counter example, it's often a sign that you need a dynamic programming approach instead, which allows you to consider all possible choices and make the best one.


```python
def greedy_algorithm(data):
    # Step 1: Sort or preprocess data if needed
    data.sort(key=lambda x: x[criteria])  # Optional, based on problem requirements

    # Step 2: Initialize necessary variables for tracking results
    result = initial_value
    current_state = initial_state  # To track the current position, count, or other criteria

    # Step 3: Iterate over data
    for item in data:
        if condition_based_on_current_state(item):
            # Step 4: Apply greedy choice by updating result and current state
            result += value_based_on_greedy_choice(item)
            current_state = update_current_state(item)

    # Step 5: Return the result
    return result


```