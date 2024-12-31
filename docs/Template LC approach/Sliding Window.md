# Technique: Sliding Window  
**Category**: Array, String  
**When to Use**:  
- When the problem involves finding a subarray or substring that satisfies a condition (e.g., maximum/minimum size, specific sum, unique characters).  
- When you need to efficiently process contiguous elements in an array or string.  

---

## 1. Core Concept  
- **Definition**:  
  A technique to efficiently manage a "window" of elements (subarray/substring) while iterating through the array or string. The window is dynamically resized or shifted to satisfy a given condition.  

- **Key Steps**:  
  1. Use two pointers (`start` and `end`) to represent the boundaries of the current window.  
  2. Expand the window by moving the `end` pointer.  
  3. Shrink the window by moving the `start` pointer when necessary to maintain or restore the condition.  
  4. Track the desired result (e.g., maximum sum, minimum size, longest substring).  

---

## 2. Example Problems  
- **Problem 1**: [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters)  
  - **Brief Description**: Find the length of the longest substring with all unique characters.  
  - **Why This Technique Applies**: A dynamic window helps ensure the substring's uniqueness by expanding and shrinking as needed.  

- **Problem 2**: [Maximum Sum Subarray of Size K](https://leetcode.com/problems/maximum-average-subarray-i/)  
  - **Brief Description**: Find the maximum sum of any subarray with a fixed size `k`.  
  - **Why This Technique Applies**: A fixed-size sliding window allows efficient computation by adding new elements and removing old ones.  

---

## 3. General Algorithm (Pseudocode)
```python
def sliding_window(input, condition):
    # Initialize variables
    start = 0
    result = some_initial_value
    current_state = some_initial_state

    for end in range(len(input)):
        # Expand the window by including the element at 'end'
        current_state = update_state(input[end])

        # Check and adjust the window to maintain the condition
        while not satisfies_condition(current_state):
            current_state = remove_state(input[start])
            start += 1

        # Update the result based on the current window
        result = update_result(current_state)

    return result
```

## 4. Complexity Analysis  
- **Time Complexity**:  
  (Explain how the time complexity is calculated. For example: O(n), where each element is processed at most twice, once when expanding the window and once when shrinking it.)  
- **Space Complexity**:  
  (Describe any additional space used, such as hash maps, sets, or arrays. For example: O(1) for constant space or O(n) for auxiliary data structures.)

---

## 5. Edge Cases  
- (List edge cases that need to be handled. For example:)  
  - Empty input or very small input size.  
  - All elements satisfy the condition.  
  - No elements satisfy the condition.  
  - Inputs with duplicate or negative values.  

---

## 6. Common Mistakes  
- (Describe common mistakes and how to avoid them. For example:)  
  - Forgetting to update the window state when shrinking it.  
  - Mismanaging edge cases like empty input or a single-element window.  
  - Expanding or shrinking the window incorrectly based on the condition.

---

## 7. Reflection Questions  
- How do you decide the window size or when to shrink/expand?  
- Does the problem require a fixed-size or variable-size window?  
- What data structures can help maintain the window's state efficiently (e.g., hash map, set, deque)?  
- How would you optimize the solution further if possible?

---

## 8. Patterns & Extensions  
- **Related Techniques**:  
  - (Mention techniques related to this one. For example:)  
    - Two Pointers (Sliding Window is a dynamic version of Two Pointers).  
    - Prefix Sum for problems involving cumulative sums without explicitly sliding the window.  

- **Variations**:  
  - Fixed-size window: Add one element and remove another in constant time.  
  - Variable-size window: Dynamically adjust `start` and `end` pointers based on the condition.  
  - Multi-window problems: Managing multiple sliding windows simultaneously.

---

## 9. Practice Problems  
- [Problem 1: Problem Title](Problem Link)  
- [Problem 2: Problem Title](Problem Link)  
- [Problem 3: Problem Title](Problem Link)  
- [Problem 4: Problem Title](Problem Link)

---

## 10. Notes for Revision  
- (Summarize key takeaways for revision. For example:)  
  - Sliding Window is ideal for problems involving contiguous subarrays or substrings.  
  - Ensure the window state is consistently updated during both expansion and contraction.  
  - Practice identifying when the Sliding Window technique applies to a problem.  
