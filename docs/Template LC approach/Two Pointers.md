# Technique: Two Pointers  
**Category**: Array, String  
**When to Use**:  
- When the input array or string is sorted.  
- When looking for pairs, triplets, or subsets with specific properties.  
- To minimize or maximize a function involving two elements in a sorted array.  

---

## 1. Core Concept  
- **Definition**:  
  Use two indices (pointers) to traverse the array from both ends, or within a subarray, to efficiently find the desired result.  

- **Key Steps**:  
  1. Initialize two pointers: one at the beginning (`left`) and one at the end (`right`) of the array.  
  2. Adjust pointers based on the condition or constraint (e.g., sum, difference).  
  3. Stop when pointers overlap or meet a termination condition.  

---

## 2. Example Problems  
- **Problem 1**: [Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted)  
  - **Brief Description**: Find two numbers in a sorted array that sum up to a target value.  
  - **Why This Technique Applies**: The sorted nature of the array allows the two pointers to systematically narrow the search space.  

- **Problem 2**: [Container With Most Water](https://leetcode.com/problems/container-with-most-water)  
  - **Brief Description**: Find two indices such that the container they form holds the most water.  
  - **Why This Technique Applies**: Two pointers can shrink the search space while comparing potential solutions.  

---

## 3. General Algorithm (Pseudocode)
```python
def two_pointers(input, target):
    # Initialize pointers
    left, right = 0, len(input) - 1
    
    while left < right:
        # Compute current condition (e.g., sum of two elements)
        current_sum = input[left] + input[right]
        
        if current_sum == target:
            return (left, right)  # Return indices
        elif current_sum < target:
            left += 1  # Move left pointer to increase sum
        else:
            right -= 1  # Move right pointer to decrease sum
    
    return None  # No valid pair found
```

## 4. Complexity Analysis  
- **Time Complexity**:  
  (Explain how the time complexity is calculated. For example: O(n), where each element is processed at most once as the pointers move inward.)  
- **Space Complexity**:  
  (Describe any additional space used. For example: O(1) for constant space or O(n) if auxiliary data structures are used.)

---

## 5. Edge Cases  
- (List edge cases that need to be handled. For example:)  
  - Empty input or an array with fewer than two elements.  
  - No valid pairs exist.  
  - Inputs with duplicate or negative values.  
  - The array is unsorted but assumed to be sorted.  

---

## 6. Common Mistakes  
- (Describe common mistakes and how to avoid them. For example:)  
  - Forgetting to check if the input is sorted when required.  
  - Misplacing the logic for moving pointers (e.g., increasing `left` when it should be `right`).  
  - Not handling edge cases properly, such as empty or single-element arrays.  

---

## 7. Reflection Questions  
- How do you identify that the Two Pointers technique applies to a problem?  
- What conditions must the input satisfy (e.g., sorted, unique values)?  
- How do you determine when and how to adjust the pointers?  
- What variations exist for problems involving more than two pointers (e.g., 3Sum)?  

---

## 8. Patterns & Extensions  
- **Related Techniques**:  
  - (Mention techniques related to this one. For example:)  
    - Sliding Window (a dynamic variant of Two Pointers).  
    - Binary Search (one pointer moves dynamically based on conditions).  

- **Variations**:  
  - Multi-pointer problems (e.g., 3Sum or 4Sum).  
  - Merging two sorted arrays using Two Pointers.  
  - Fast and slow pointer problems (e.g., detecting cycles in a linked list).

---

## 9. Practice Problems  
- [Problem 1: Problem Title](Problem Link)  
- [Problem 2: Problem Title](Problem Link)  
- [Problem 3: Problem Title](Problem Link)  
- [Problem 4: Problem Title](Problem Link)

---

## 10. Notes for Revision  
- (Summarize key takeaways for revision. For example:)  
  - Two Pointers is ideal for sorted arrays or problems requiring pairwise comparisons.  
  - Always verify the input properties (e.g., sorted or unsorted).  
  - Focus on understanding when and how to move the pointers efficiently.
