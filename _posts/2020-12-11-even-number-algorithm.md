---
layout: post
title: 짝수 찾기 알고리즘
category: Algorithm
tags: Algorithm
---

<br>
Given an integer, if that is an even number, return 'this is even number', otherwise return 'this is not even number'

## Example

```jsx
console.log(is_even(11)); // --> "this is not even number"
console.log(is_even(10)); // --> "this is even number"
```

## My Solution

```jsx
function is_even(num) {
  if (num % 2 === 0) {
    return "this is even number.";
  } else {
    return "this is not even number.";
  }
}

is_even(3);
```
