---
layout: post
title: 문자열 인자에서 중복되지 않은 알파벳으로 이루어진 제일 긴 단어의 길이를 반환하기
category: Algorithm
tags: Algorithm
---

<br>
Given a string s, find the length of the longest substring without repeating characters.

## Example 1:

```jsx
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```

## Example 2:

```jsx
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

## Example 3:

```jsx
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

## My Solution

```jsx
const getLengthOfStr = (str) => {
  let sliceStr = [];
  let lastStr = 0;

  for (let i = 0; i < str.length; i++) {
    if (sliceStr.indexOf(str[i]) === -1) {
      sliceStr.push(str[i]);

      if (lastStr < sliceStr.length) {
        lastStr = sliceStr.length;
      }
    } else {
      sliceStr = sliceStr.slice(sliceStr.indexOf(str[i]) + 1);
      sliceStr.push(str[i]);
    }
  }
  return lastStr;
};

var str = "sttrg";
getLengthOfStr(str);
```

<br>
Source: [https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
