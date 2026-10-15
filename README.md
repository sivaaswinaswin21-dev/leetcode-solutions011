# LeetCode 2913: Subarrays Distinct Element Sum of Squares I

## Problem

Given a 0-indexed integer array `nums`, the distinct count of a subarray `nums[i..j]` is the number of distinct values in it. Return the sum of the squares of the distinct counts of all subarrays of `nums`.

## Examples

| Input | Output | Explanation |
|-------|--------|-------------|
| `[1,2,1]` | `15` | Distinct counts are 1, 1, 1, 2, 2, 2, so 1+1+1+4+4+4 = 15 |
| `[1,1]` | `3` | Every subarray has 1 distinct value, so 1+1+1 = 3 |

## Constraints

- `1 <= nums.length <= 100`
- `1 <= nums[i] <= 100`

## Approach

Brute force. For each start index `i`, extend the end index `j` to the right while keeping a running set of the values seen. After each extension, add the square of the set size to the running total.

With n <= 100 there are at most 5,050 subarrays, so this is fast enough.

## Complexity

- **Time:** O(n^2)
- **Space:** O(n)

## Usage

```python
from solution import Solution

print(Solution().sumCounts([1, 2, 1]))  # 15
print(Solution().sumCounts([1, 1]))     # 3
```

## Solution

```python
from typing import List

class Solution:
    def sumCounts(self, nums: List[int]) -> int:
        n = len(nums)
        total = 0
        for i in range(n):
            seen = set()
            for j in range(i, n):
                seen.add(nums[j])
                total += len(seen) ** 2
        return total
```

## Follow-up

LeetCode 2916 is the harder version, with n up to 10^5. It needs a segment tree with lazy propagation and runs in O(n log n).
