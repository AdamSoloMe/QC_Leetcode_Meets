# Basic Arrays

Source: [Array cheatsheet for coding interviews | Tech Interview Handbook](https://www.techinterviewhandbook.org/algorithms/array/)

---

## Introduction To Arrays

Arrays and hash tables are some of the most fundamental data structures used in coding interview questions. 

**Arrays** are a contiguious piece of memory of fixed length that contain a specific pre-determined data type and space.

Example: `int array1[5] = [0,1,2,3,4]`  initializes an array of size 5 with the values `[0,1,2,3,4]` with respective indices of `[0,1,2,3,4]`.

In Python, **dynamic arrays** are used which grow and shrink according to the dataset.

**Advantages**

- Store multiple elements of the same type with one single variable name
- Accessing elements is fast as long as you have the index, as opposed to **linked lists** where you have to traverse from the head.

**Disadvantages**

- Addition and removal of elements into/from the middle of an array is slow because the remaining elements need to be shifted to accommodate the new/missing element. An exception to this is if the position to be inserted/removed is at the end of the array.
- For certain languages where the array size is fixed, it cannot alter its size after initialization. If an insertion causes the total number of elements to exceed the size, a new array has to be allocated and the existing elements have to be copied over. The act of creating a new array and transferring elements over takes O(n) time.

## Common terms

Common terms you see when doing problems involving arrays:

- Subarray - A range of contiguous values within an array.
  - Example: given an array `[2, 3, 6, 1, 5, 4]`, `[3, 6, 1]` is a subarray while `[3, 1, 5]` is not a subarray.
- Subsequence - A sequence that can be derived from the given sequence by deleting some or no elements without changing the order of the remaining elements.
  - Example: given an array `[2, 3, 6, 1, 5, 4]`, `[3, 1, 5]` is a subsequence but `[3, 5, 1]` is not a subsequence.

## Things to look out for during interviews

- Clarify if there are duplicate values in the array. Would the presence of duplicate values affect the answer? Does it make the question simpler or harder?
- When using an index to iterate through array elements, be careful not to go out of bounds.
- Be mindful about slicing or concatenating arrays in your code. Typically, slicing and concatenating arrays would take O(n) time. Use start and end indices to demarcate a subarray/range where possible.

## Time complexity

| Operation             | Big-O     | Note                                                         |
| --------------------- | --------- | ------------------------------------------------------------ |
| Access                | O(1)      |                                                              |
| Search                | O(n)      |                                                              |
| Search (sorted array) | O(log(n)) |                                                              |
| Insert                | O(n)      | Insertion would require shifting all the subsequent elements to the right by one and that takes O(n) |
| Insert (at the end)   | O(1)      | Special case of insertion where no other element needs to be shifted |
| Remove                | O(n)      | Removal would require shifting all the subsequent elements to the left by one and that takes O(n) |
| Remove (at the end)   | O(1)      | Special case of removal where no other element needs to be shifted |



## Techniques

Note that because both arrays and strings are sequences (a string is an array of characters), most of the techniques here will apply to string problems.

### Sliding window

Master the [sliding window technique](https://discuss.leetcode.com/topic/30941/here-is-a-10-line-template-that-can-solve-most-substring-problems) that applies to many subarray/substring problems. In a sliding window, the two pointers usually move in the same direction will never overtake each other. This ensures that each value is only visited at most twice and the time complexity is still O(n). Examples: [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/), [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/), [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

### Two pointers

Two pointers is a more general version of sliding window where the pointers can cross each other and can be on different arrays. Examples: [Sort Colors](https://leetcode.com/problems/sort-colors/), [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)

When you are given two arrays to process, it is common to have one index per array (pointer) to traverse/compare the both of them, incrementing one of the pointers when relevant. For example, we use this approach to merge two sorted arrays. Examples: [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

### Traversing from the right

Sometimes you can traverse the array starting from the right instead of the conventional approach of from the left. Examples: [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/), [Number of Visible People in a Queue](https://leetcode.com/problems/number-of-visible-people-in-a-queue/)

### Sorting the array

Is the array sorted or partially sorted? If it is, some form of binary search should be possible. This also usually means that the interviewer is looking for a solution that is faster than O(n).

Can you sort the array? Sometimes sorting the array first may significantly simplify the problem. Obviously this would not work if the order of array elements need to be preserved. Examples: [Merge Intervals](https://leetcode.com/problems/merge-intervals/), [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

### Precomputation

For questions where summation or multiplication of a subarray is involved, pre-computation using hashing or a prefix/suffix sum/product might be useful. Examples: [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/), [Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/), [LeetCode questions tagged "prefix-sum"](https://leetcode.com/tag/prefix-sum/)

### Index as a hash key

If you are given a sequence and the interviewer asks for O(1) space, it might be possible to use the array itself as a hash table. For example, if the array only has values from 1 to N, where N is the length of the array, negate the value at that index (minus one) to indicate presence of that number. Examples: [First Missing Positive](https://leetcode.com/problems/first-missing-positive/), [Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)

### Traversing the array more than once

This might be obvious, but traversing the array twice/thrice (as long as fewer than n times) is still O(n). Sometimes traversing the array more than once can help you solve the problem while keeping the time complexity to O(n).

## Essential questions

*These are essential questions to practice if you're studying for this topic.*

- [Two Sum](https://leetcode.com/problems/two-sum/)
- [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
- [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
- [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

## Recommended practice questions

*These are recommended questions to practice after you have studied for the topic and have practiced the essential questions.*

- [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
- [Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
- [3Sum](https://leetcode.com/problems/3sum/)
- [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
- [Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)



# Technique Practices and Solutions

[Valid Anagram - LeetCode](https://leetcode.com/problems/valid-anagram/)

```python
 class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
  			'''
        s = aaa
        t = aaaa
        { a: -1 }
        '''
        if len(s) != len(t):
            return False

        char_map = {}
        
        for char in s:
            char_map[char] = char_map.get(char, 0) + 1

        for char in t:
            if char not in char_map or char_map[char] <= 0:
                return False
            char_map[char] -= 1

        return True
```



## Two Pointers

 [Two Sum II - Input Array Is Sorted- LeetCode](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/)

```python
# Binary search: n log n 

class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        '''
        iterate thru list with index1
        binary search the rest of the list for index2
        '''
        
        n = len(numbers)    
        if n == 2:
            return [1,2]
        # for each number in list
        for i in range(n):
            first = numbers[i]
            left, right = i+1, n-1
            while left<= right:
                mid = (left + right)//2
                currSum = numbers[mid] + first
                if currSum == target:
                    return [i+1, mid+1]
                if currSum < target:
                    left = mid+1
                else:
                    right = mid-1
        return [0,0]
```

```python
# two pointers O(n)
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        # two pointers ->  left, right(last index), and sum
        # start with a very large window -> first, to last and shrink window as we go on
        left, right, sum = 0, len(numbers) - 1, 0
        # there is at least 1 solution but go until window is closed
        while left < right:
            sum = numbers[left] + numbers[right]
            print(sum)
            # If current sum is greater than target, move the right pointer to the left by 1, close the window
            if sum > target:
                right -= 1
            # If current sum is less than target, move the left pointer to the right by 1, make window bigger
            elif sum < target:
                left += 1
             # If current sum is equal to target return indices + 1 because 1-indexed
            else:
                return[left + 1, right + 1]	
```

[3Sum - LeetCode](https://leetcode.com/problems/3sum/description/)

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        
        # List to store the resulting triplets
        res = []
        
        # Sort the numbers list for the two-pointer technique and to skip duplicates
        nums.sort()

        # Iterate over each number in the list
        for i, a in enumerate(nums):
            
            # If the current number is positive, break, because no triplet can sum up to 0 with all positive numbers
            if a > 0:
                break

            # Skip duplicates to prevent duplicate triplets
            if i > 0 and a == nums[i - 1]:
                continue

            # Initialize two pointers: one just after the current number (l) and another at the end of the list (r)
            l, r = i + 1, len(nums) - 1
            
            # While the left pointer is to the left of the right pointer
            while l < r:
                # Calculate the sum of the current triplet
                threeSum = a + nums[l] + nums[r]

                # If the sum is greater than 0, move the right pointer leftwards to reduce the sum
                if threeSum > 0:
                    r -= 1
                # If the sum is less than 0, move the left pointer rightwards to increase the sum
                elif threeSum < 0:
                    l += 1
                # If a valid triplet is found
                else:
                    # Add the triplet to the results list
                    res.append([a, nums[l], nums[r]])
                    # Move both pointers to avoid duplicates
                    l += 1
                    r -= 1
                    # Skip the same numbers (duplicates) for the left pointer to avoid duplicate triplets
                    while nums[l] == nums[l - 1] and l < r:
                        l += 1
                        
        # Return the list of unique triplets
        return res

```



## Sliding Window









---

Sources

[Array cheatsheet for coding interviews | Tech Interview Handbook](https://www.techinterviewhandbook.org/algorithms/array/)

[NeetCode.io](https://neetcode.io/)
