Solution 1:

Pseudo Code:
- sort the list/ array so we can prevent the duplicate number
- define triplets set for unique results
- Iteration up to last 3 index
	- Validate when i > 0, nums[i] == nums[i-1] ==> continue prevent duplicate
	- Define first_num = index of I
	- j = i + 1
	- k = len(nums) - 1
	- Slide window when j < k:
		-  second_num = nums[j]
		- third_num = nums[k]
		- potential_result = first + second + third
		- if potential_result < 0 -> j +=1 
		- if potential_result > 0 -> k -= 1
		- else: triplets.add( (first,second,third) )
	 - return triplets


```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        triplets = set()
        for i in range(len(nums) - 2):
	        if i > 0 and nums[i] == nums[i - 1]:
			    continue
            firstNum = nums[i]
            j = i + 1
            k = len(nums) - 1 
            while j < k:
                secondNum = nums[j]
                thirdNum = nums[k]
                
                potentialSum = firstNum + secondNum + thirdNum
                if potentialSum < 0:
                    j += 1
                elif potentialSum > 0:
                    k -= 1
                else:
                    triplets.add((firstNum, secondNum, thirdNum))
                    j += 1
                    k -= 1
        return triplets




Solution 2:

Pseudo code:
- Define and classify: negatives, positives dictionary and zero count
- Iterate through nums List and  add it with occurrences in above dictionaries
- Cover these 2 edge case if there is 0 occurrences > 0:
	-  n + (-n) + 0
	- triple 0
- Triplets approach:
	- Iterate with main two sets of number: set_a, set_b
	- Iterating through pairs (set_a, set_b) 
		- Convert set_a_items = list of items from set_a, each item is tuple with number and its occurrences
	- Generate pairs of numbers  (x,x2) from set_a. These pairs can be:
			- Two different numbers.
			- The same number twice, but only if it appears more than once (i.e., `q > 1`).
	- **Check for the Complement**:
		- For each pair `(x, x2)` from `set_a`, calculate the value needed to complete the triplet so that the sum is zero:
	        - The required value is `- (x + x2)`.
		- Check if this required value exists in `set_b` (the opposite set). If it does, it means that `x`, `x2`, and `-(x + x2)` form a valid triplet that sums to zero.
	- **Store the Triplet**:
	    - If the triplet is valid, add it to the `result` list.



```python
from collections import defaultdict

class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nega = defaultdict(int)
        posi = defaultdict(int)
        zeros = 0
        
        # Classify the value
        for x in nums:
            if x < 0:
                nega[x] += 1
            elif x > 0:
                posi[x] += 1
            else:
                zeros += 1
                
        result = []
        
        # Cover edge cases
        if zeros:
            # edge case with 0, n, -n
            for n in nega:
                if -n in posi:
                    result.append((0, n, -n))
            
            # edge case with triple 0
            if zeros > 2:
                result.append((0, 0, 0))
                
        # Generate Triplets:
        for set_a, set_b in ((nega, posi), (posi, nega)):
            set_a_items = list(set_a.items())
            for i, (x, q) in enumerate(set_a_items):
                for x2, q2 in set_a_items[i:]:
                    if x != x2 or (x == x2 and q > 1):
                        if -x-x2 in set_b:
                            result.append((x, x2, -x-x2))

        return result
