# CS366 - PA4: Theoretical Analysis

---

## Problem 1: Greedy Choice Property

**Prove that the greedy choice (always combining the two smallest sticks) leads to an optimal solution.**

### Greedy Choice Property Explanation

[Explain what the greedy choice property means for this problem

#The greedy choice property makes sure smaller sticks get combined earlier which minimlizes total cost. The total cost is decreased since smaller values contribute less to the total cost. 

]


### Informal Proof

[Provide an informal proof using exchange argument or similar technique. 

Proof: 
Suppose we have sticks s1 < s2 < s3 < ...
Assume there exists an optimal solution O that doesnt combine the first two smallest sticks (in this case s1 and s2) first. 

Non Greedy Choice O:
Lets select s3, and s2. By combining these two we still have to combine s1 later on.
Creating a total cost of (s2 + s3) + (s1 + (s2 + s3)) = 2s2 + 2s3 + s1 

Greedy choice G:
Select s1 and s2. By combining these two we create a total cost of (s1 + s2) + (s1 + s2 + s3)
=  2s1 + 2s2 + s3 

2s1 + 2s2 + s3 < 2s2 + 2s3 + s1 

2s2 + 2s3 + s1 - (s1 + 2s2) = 2s3
2s1 + 2s2 + s3 - (s1 + 2s2) = s1 + s3

s1 + s3 < 2s3
s1 + s3 - s3 = s1
2s3 - s3 = s3

s1 < s3

Conclusion:
Thus, any solution that does not combine the smallest two sticks first can be optimized by switching to a greedy choice, so the greedy strategy of always combining the two smallest sticks is optimal.

- What happens if we choose sticks other than the two smallest?
- How does the greedy choice affect the total cost?
- Why can't any other choice lead to a better solution?]

---

### Problem 2: Time Complexity Analysis - Greedy Naive Approach

**Analyze the time complexity of the greedy naive approach using an UNSORTED list.**

**Important Note:** This approach uses the same **greedy algorithm** as the optimized version (always combine the two smallest sticks). The difference is in the **implementation efficiency** - this version uses an **unsorted ArrayList** requiring O(n) linear scans to find minimums, rather than O(log n) heap operations.

### Algorithm Description

[Briefly describe the steps of the greedy naive algorithm - emphasize that it follows the greedy strategy but uses an **unsorted ArrayList** requiring linear scans for each minimum extraction. The list remains unsorted throughout - no sorting is performed.]

### Iteration Analysis

[Explain why each iteration takes O(n) time. Consider:

- Finding the first minimum in the **unsorted list**: O(n) - must scan all elements
- Finding the second minimum in the **unsorted list**: O(n-1) - must scan all elements again
- Removing elements: O(n)
- Adding element back to the **unsorted list**: O(n)]

### Total Complexity Calculation

[Show the calculation:

- Number of iterations: ?
- Cost per iteration: ?
- Total: O(n log n)?]

### Recurrence Relation

[Write and solve the recurrence relation for the greedy naive approach]

**Conclusion:** The greedy naive approach has time complexity of **\_\_\_\_**.

---

## Problem 3: Time Complexity Analysis - Greedy Optimized Approach

**Analyze the time complexity of the greedy optimized approach using a priority queue (heap).**

**Important Note:** This approach uses the **exact same greedy algorithm** as the naive version - it always combines the two smallest sticks. The only difference is using a heap data structure to efficiently find minimums, rather than linear scans.

### Heap Operations

[Explain the time complexity of each heap operation used:

- Building initial heap: O(?)
- Extract minimum (poll): O(?)
- Insert (offer): O(?)]

### Build-Heap Analysis

[Explain why building a heap from n elements is O(n), not O(n log n)]

### Iteration Analysis

[Analyze one iteration:

- Extract first minimum: O(?)
- Extract second minimum: O(?)
- Insert sum back: O(?)
- Total per iteration: O(?)]

### Total Complexity Calculation

[Show the calculation:

- Build heap: O(?)
- Number of iterations: ?
- Cost per iteration: O(?)
- Total: ?]

**Conclusion:** The greedy optimized (heap) approach has time complexity of **\_\_\_\_**.

---

## Problem 4: Performance Prediction

**Predict the speedup factor for different input sizes when comparing Greedy Naive vs Greedy Optimized implementations.**

**Important Note:** Both implementations use the same greedy strategy. This analysis demonstrates how data structure choice affects performance while keeping the algorithm constant.

### Theoretical Speedup Calculations

For input size n, compare O(n²) vs O(n log n):

**n = 100:**

- Naive: O(100²) = [calculate]
- Heap: O(100 × log₂ 100) ≈ [calculate]
- Speedup factor: [calculate]

**n = 1,000:**

- Naive: O(1000²) = [calculate]
- Heap: O(1000 × log₂ 1000) ≈ [calculate]
- Speedup factor: [calculate]

**n = 10,000:**

- Naive: O(10000²) = [calculate]
- Heap: O(10000 × log₂ 10000) ≈ [calculate]
- Speedup factor: [calculate]

### Empirical Results

[After implementing your solution, run compareApproaches() with different input sizes and record actual timing results]

| Input Size (n) | Naive Time (ms) | Heap Time (ms) | Actual Speedup |
| -------------- | --------------- | -------------- | -------------- |
| 100            |                 |                |                |
| 500            |                 |                |                |
| 1,000          |                 |                |                |
| 5,000          |                 |                |                |

### Analysis of Results

[Compare theoretical predictions with empirical results. Discuss:

- Do the empirical results match your theoretical predictions?
- At what input size does the heap approach become significantly faster?
- What factors might cause differences between theoretical and empirical speedup?]

---

_Course content developed by Declan Gray-Mullen for WNEU with Claude_
