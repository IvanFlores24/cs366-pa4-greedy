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
Assume there exists an optimal solution O that doesn't combine the first two smallest sticks (in this case s1 and s2) first. 

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

[Briefly describe the steps of the greedy naive algorithm - emphasize that it follows the greedy strategy but uses an **unsorted ArrayList** requiring linear scans for each minimum extraction. The list remains unsorted throughout - no sorting is performed.

#The greedy naive choice algorithm tries to ensure smaller sticks get combined  using an unsorted ArrayList. Each ArrayList element stays in their orginal order. Each time, the alogirthm must preform a linear scan on the entire ArrayList to find the smallest stick, its then removed and added to the total.This is repeated untill the list is completely empty. 

]

### Iteration Analysis

[Explain why each iteration takes O(n) time. Consider:
Each iteration you have to find the first minimum, remove the element and added which
can be represented as 
O(n) + O(n) + O(1) = O(n)

- Finding the first minimum in the **unsorted list**: O(n) - must scan all elements
- Finding the second minimum in the **unsorted list**: O(n-1) - must scan all elements again
- Removing elements: O(n)
- Adding element back to the **unsorted list**: O(1)]

### Total Complexity Calculation

[Show the calculation:

- Number of iterations: n
- Cost per iteration: O(n)
- Total: O(n^2)]

### Recurrence Relation

[Write and solve the recurrence relation for the greedy naive approach

T(n) = T(n-1) + f(n)

T(n) = T(n-1) + n

= n(n+1) / 2

T(n) = 0(n^2)

]

**Conclusion:** The greedy naive approach has time complexity of **O(n^2)**.

---

## Problem 3: Time Complexity Analysis - Greedy Optimized Approach

**Analyze the time complexity of the greedy optimized approach using a priority queue (heap).**

**Important Note:** This approach uses the **exact same greedy algorithm** as the naive version - it always combines the two smallest sticks. The only difference is using a heap data structure to efficiently find minimums, rather than linear scans.

### Heap Operations

[Explain the time complexity of each heap operation used:

- Building initial heap: O(n)
- Extract minimum (poll): O(log n)
- Insert (offer): O(log n)]

### Build-Heap Analysis

[Explain why building a heap from n elements is O(n), not O(n log n)
Building a heap from n elements is O(n) and not O(n log n) because of what actually happens during the build heap process. During the build heap process heapify processees are repeated. Since building a heap uses the bottom-up aproach most of the work is done at the lower level of the binary tree. A complete binary tree has more nodes at the lower level than it does the higher level. This way of distributing work means the total work = a linear amount O(n) not O(n log n)
]

### Iteration Analysis

[Analyze one iteration:

- Extract first minimum: O(log n)
- Extract second minimum: O(log n)
- Insert sum back: O(log n)
- Total per iteration: O(log n)]

### Total Complexity Calculation

[Show the calculation:

- Build heap: O(n)
- Number of iterations: n - 1
- Cost per iteration: O(log n)
- Total: O(n log n)

**Conclusion:** The greedy optimized (heap) approach has time complexity of **O(n log n)**.

---

## Problem 4: Performance Prediction

**Predict the speedup factor for different input sizes when comparing Greedy Naive vs Greedy Optimized implementations.**

**Important Note:** Both implementations use the same greedy strategy. This analysis demonstrates how data structure choice affects performance while keeping the algorithm constant.

### Theoretical Speedup Calculations

For input size n, compare O(n²) vs O(n log n):

**n = 100:**

- Naive: O(100²) = [10,000]
- Heap: O(100 × log₂ 100) ≈ [664]
- Speedup factor: [15.1]

**n = 1,000:**

- Naive: O(1000²) = [1,000,000]
- Heap: O(1000 × log₂ 1000) ≈ [9970]
- Speedup factor: [100.3]

**n = 10,000:**

- Naive: O(10000²) = [100000000]
- Heap: O(10000 × log₂ 10000) ≈ [132900]
- Speedup factor: [752.44]

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
