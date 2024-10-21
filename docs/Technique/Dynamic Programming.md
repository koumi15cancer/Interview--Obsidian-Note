### Optimal Substructure

We can think of optimal substructure as a fancy way of saying we can use recursion to solve the problem.

More formally, the problem has optimal substructure if an optimal solution to the problem contains optimal solutions to subproblems.

For this problem, if we know:

- the number of ways to climb 3 steps
    
- the number of ways to climb 4 steps
    
![[Screenshot 2024-10-21 at 10.35.36 AM.png]]

Then, we can add those together to get the number of ways to climb 5 steps.

The number of ways to climb 3 and 4 steps represent the optimal solutions to the subproblems.

123


### Overlapping Subproblems

The call tree makes it easy to see that the brute-force solution has overlapping subproblems, which is a fancy way of saying there is repeat work being done.


For example, climbStairs(3) is called twice. Each of those calls then results in the same exact sequence of recursive calls to climbStairs(1) and climbStairs(2).

![[Screenshot 2024-10-21 at 10.36.14 AM.png]]

So, if a problem has optimal substructure (it can be solved using recursion), and there are overlapping subproblems (the same recursive call is made multiple times), then we can use dynamic programming to handle the overlapping subproblems more efficiently.

There are two strategies for doing so, but they both boil down to the same idea: _only solve each subproblem once_.


### Memoization

The first strategy is known as memoization.

Let's return to the call tree. It shows that climbStairs(3) is called once by climbStairs(4), and later on by climbStairs(5).

Since the result of climbStairs(3) won't change between these two calls, we can store the result of climbStairs(3) in a "cache". When climbStairs(5) needs to calculate climbStairs(3) again, we can simply look up the result in the cache instead of recalculating it, eliminating a series of redundant recursive calls. This is known as **memoization**.

Here's the same call tree with memoization applied. The nodes that have been memoized are highlighted in green. Notice how they return immediately without expanding to make any further recursive calls.

![[Screenshot 2024-10-21 at 10.36.59 AM.png]]

The savings from memoization become more visible as n grows larger. Take n = 6 for example. The calls that are memoized are highlighted in green, and the calls that get skipped are grayed out.

![[Screenshot 2024-10-21 at 10.37.29 AM.png]]

We can add memoization by taking our brute-force recursive solution and adding a dictionary memo. Memo maps n to the result of climbStairs(n), and serves as our cache. We need to remember to do two things when adding memoization:

1. Before making a recursive call, we check if the value for n is already in the cache. If it is, we return the value immediately without making any further recursive calls.
    
2. After obtaining the result for n, we store it in the cache before returning it to the caller.

```python
def climbStairs(n: int) -> int:

    memo = {}

    def climb_helper(i: int) -> int:

        if i <= 1:

            return 1

        # check if value is already in cache

        # before making recursive calls

        # corresponds to the green nodes in the diagram

        if i in memo:

            return memo[i]

        # store result in cache before returning

        memo[i] = climb_helper(i - 1) + climb_helper(i - 2)

        return memo[i]

    return climb_helper(n)

```


Adding memoization to our solution reduces the time complexity from O(2n) to O(n). As we can see in the memoized call tree, each subproblem is solved once and then stored in the cache, and future recursive calls to the same subproblem are looked up in O(1) time. The space complexity is also O(n) because we store the result of each value in the cache.


### Bottom-Up Approach

The recursive approach with memoization is known as the **top-down approach** to dynamic programming. The call tree starts with the original problem and works its way down to the base cases.

There's an alternative approach to dynamic programming known as the **bottom-up approach**, which is based on the following observation: we already know the base cases of our problem, namely that there is 1 way to climb 0 steps and 1 way to climb 1 step.

##### Implementing the Bottom-Up Approach

The bottom-up approach starts by creating an array dp of size n + 1 to store the number of ways to climb n steps. dp[0] contains the number of ways to climb 0 steps, dp[1] contains the number of ways to climb 1 step, and so on. This dp array is analogous to the cache we used in the memoized recursive approach.

We initialize the base cases dp[0] = 1 and dp[1] = 1, and then iterate from 2 to n, calculating dp[i] = dp[i - 1] + dp[i - 2]. The animation below shows the process of filling in the dp array for n = 5, and how it corresponds to going from the bottom of the memoized call tree to the top. When the iteration is complete, we return dp[n] as the final answer.

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <=1 :
            return 1

        dp = [0] * (n + 1)

        dp[0] = 1
        dp[1] = 1
        for i in range(2, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n]
        

```

### Summary

Both the top-down and bottom-up approaches are valid ways to solve problems by avoiding redundant calculations. The top-down approach uses recursion and memoization to store the results of subproblems, while the bottom-up approach iterates from the base cases to the original problem.

The top-down approach is often more intuitive to those who are first learning dynamic programming, but the bottom-up approach is generally more efficient because it avoids the overhead of recursive calls and function calls. In the next section, we'll build upon these concepts and follow a structured approach to solve dynamic programming problems.

## Solving a Question with Dynamic Programming

This page breaks down how to solve a question with dynamic programming into a series of steps which ultimately leads to the "bottom-up" solution to the problem.

1. Find the Recurrence Relation
    
2. Identify the Base Case(s)
    
3. Write the Recursive Solution
    
4. Add Memoization
    
5. Convert to "Bottom-Up" DP
    
6. Further Optimization