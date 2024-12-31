# Technique: Binary Search  
**Category**: Array, Search, Divide and Conquer  
**When to Use**:  
- When the input array or range is sorted (or can be transformed into a sorted order).  
- To find an element, the first/last occurrence, or the position where an element can be inserted while maintaining sorted order.  
- Problems involving monotonic functions or decisions.  

---

## 1. Core Concept  
- **Definition**:  
  Binary Search repeatedly divides the search space into halves to efficiently locate a target element or determine its position.  

- **Key Steps**:  
  1. Identify the sorted property or monotonic behavior in the input.  
  2. Define the search range (`low` and `high`).  
  3. Use the midpoint (`mid`) to decide whether to search the left or right half.  
  4. Adjust the range and repeat until the target is found or the range is exhausted.  

---

## 2. Example Problems  
- **Problem 1**: [Binary Search](https://leetcode.com/problems/binary-search)  
  - **Brief Description**: Find the index of a target value in a sorted array.  
  - **Why This Technique Applies**: The sorted order allows dividing the array into halves for efficient search.  

- **Problem 2**: [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array)  
  - **Brief Description**: Find the starting and ending positions of a target in a sorted array.  
  - **Why This Technique Applies**: Binary Search is used to locate the boundaries of the target range.  

---

## 3. General Algorithm (Pseudocode)
```python
def binary_search(array, target):
    low, high = 0, len(array) - 1
    
    while low <= high:
        mid = (low + high) // 2  # Compute the midpoint
        
        if array[mid] == target:
            return mid  # Target found
        elif array[mid] < target:
            low = mid + 1  # Search in the right half
        else:
            high = mid - 1  # Search in the left half
    
    return -1  # Target not found
```

## 4. Complexity Analysis  
- **Time Complexity**:  
  O(log n) — Each iteration halves the search range, resulting in logarithmic time complexity.  
- **Space Complexity**:  
  O(1) for iterative implementations (no additional space used).  
  O(log n) for recursive implementations (due to call stack usage).  

---

## 5. Edge Cases  
- Target is not present in the array.  
- Array has duplicate values (may require additional logic to find the first/last occurrence).  
- The input array is empty or contains only one element.  
- Target is smaller than the smallest element or larger than the largest element in the array.  
- Input array is sorted in descending order or has rotated segments.  

---

## 6. Common Mistakes  
- Miscomputing the midpoint, especially with integer overflow in languages without automatic handling (e.g., `(low + high) // 2` should be rewritten as `low + (high - low) // 2` in such cases).  
- Infinite loops due to improper adjustments of `low` or `high`.  
- Forgetting edge cases such as empty arrays or single-element arrays.  
- Mismanaging inclusive/exclusive boundaries when searching for first/last occurrence.  
- Applying Binary Search to unsorted inputs without preprocessing.  

---

## 7. Reflection Questions  
- How do you decide whether to search the left or right half?  
- What are the termination conditions for the loop or recursion?  
- How do you handle duplicate values or find the first/last occurrence of the target?  
- What adjustments are needed if the array is sorted in descending order or rotated?  
- Can the technique be extended to non-array problems (e.g., function minimization)?  

---

## 8. Patterns & Extensions  
- **Variations**:  
  - Lower Bound / Upper Bound: Finding the smallest/largest index where the target satisfies a condition.  
  - Rotated Sorted Arrays: Adapting Binary Search to handle rotations in the array.  
  - Binary Search on Monotonic Functions: Locating the minimum or maximum of a unimodal function.  
  - Search for Range: Finding the first and last position of the target in a sorted array.  

- **Related Techniques**:  
  - Two Pointers: Used for direct search without halving, especially in unsorted inputs.  
  - Sliding Window: Focused on contiguous subarray problems.  
  - Divide and Conquer: A broader category that includes Binary Search.  

---

## 9. Practice Problems  
- [Binary Search](https://leetcode.com/problems/binary-search)  
- [Search Insert Position](https://leetcode.com/problems/search-insert-position)  
- [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array)  
- [Find Peak Element](https://leetcode.com/problems/find-peak-element)  
- [H-Index II](https://leetcode.com/problems/h-index-ii)  

---

## 10. Notes for Revision  
- Verify if the input satisfies the sorted/monotonic property before applying Binary Search.  
- Ensure proper handling of edge cases like empty arrays or targets outside the range.  
- Always double-check the conditions for adjusting `low` and `high` pointers.  
- Understand when to use iterative vs. recursive approaches based on problem constraints.  
