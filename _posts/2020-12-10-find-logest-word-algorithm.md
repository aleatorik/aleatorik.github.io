---
layout: post
title: 주어진 리스트 안에 가장 긴 단어를 찾는 알고리즘
category: Algorithm
tags: Algorithm
---

## Example

```jsx
Input: words = ["java","golang","python","javascript"]
Output: javascript
Explanation: the longest word from the given array is "javascript"
```

## My Solution

```jsx
function find_longest_word(list) {
  let longestStr = list[0];
  for (let i in list) {
    if (longestStr.length < list[i].length) {
      longestStr = list[i];
    }
  }
  return longestStr;
}

find_longest_word(["java", "golang", "python", "javascript"]);
```
