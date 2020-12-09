---
layout: post
title: 특정 두 수의 합에 대한 결과값의 인덱스를 반환하는 알고리즘
category: Algorithm
tags: Algorithm
---

\*
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order. \*

## Example

```
nums = [4, 9, 11, 14]
target = 13
output: [0, 1]
Output: Because nums[0] + nums[1] == 13, we return [0, 1].

```

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:
```

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

## My Solution

```jsx
const twoSum = (nums, target) => {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length; j++) {
      let sum = nums[i] + nums[j];
      if (sum === target) {
        let result = [i, j];
        return result;
      }
    }
  }
};

let nums = [4, 9, 11, 14];
twoSum(nums, 13);
```

## Another Solution

```jsx
function twoSum(nums, target) {
  for (let i = 0; i < nums.length - 1; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] + nums[j] === target) {
        return [i, j];
      }
    }
  }
}
```
