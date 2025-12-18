---
layout: default
title: "Chapter 1: Two Sum"
---

---
layout: default
title: "01. Two Sum Solution"
---

# Two Sum Problem

Given an array of integers $A = \{a\_1, a\_2, \ldots, a\_n\}$ and an integer $T$, find indices $i$ and $j$ such that $a\_i + a\_j = T$, where $i \neq j$.

## 1. Brute Force Approach

The simplest method is to check every pair. We iterate through each element $x$ and check if there is another element $y$ such that $x+y=T$.

$$\sum_{i=0}^{n} \sum_{j=i+1}^{n} (a\_i + a\_j)$$

* **Time Complexity:** $O(n^2)$
* **Space Complexity:** $O(1)$

## 2. Optimized Approach (Hash Map)

We can optimize this by maintaining a history of elements we have seen so far using a Hash Map $M$.

### The Algorithm
For every element $val$ at index $i$:
1. Calculate the difference: $diff = T - val$.
2. Check if $diff$ exists in map $M$.
3. If it exists, we found the pair: return $(M[diff], i)$.
4. If not, store the current element: $M[val] = i$.

### Mathematical Proof
We are looking for $f(i)$ such that:
$$\exists j < i \text{ where } M[T - a\_i] = j$$

### Implementation

```python
def twoSum(nums: List[int], target: int) -> List[int]:
    prevMap = {}  # val : index

    for i, n in enumerate(nums):
        diff = target - n
        if diff in prevMap:
            return [prevMap[diff], i]
        prevMap[n] = i
    return []