---
layout: post
title: 가장 자주 등장한 숫자를 특정 개수만큼 반환하기
category: Algorithm
tags: Algorithm
---

<br>
Given a non-empty array of integers, return the k most frequent elements.

## Example 1:

```jsx
Input: (nums = [1, 1, 1, 2, 2, 3]), (k = 2);
Output: [1, 2];
```

## Example 2:

```jsx
Input: (nums = [1]), (k = 1);
Output: [1];
```

## My Solution

```jsx
function topK(nums, k) {
  let obj = {};
  let arr = [];
  nums.forEach((el) => {
    if (obj[el]) {
      obj[el]++;
    } else {
      obj[el] = 1;
    }
  });
  for (let properyName in obj) {
    arr.push([properyName, obj[properyName]]);
  }
  return arr
    .sort((a, b) => b[1] - a[1])
    .slice(0, k)
    .map((el) => Number(el[0]));
}
topK([1, 2, 2, 2, 3, 4, 4, 7, 4], 2);
```

## Another Solution

```jsx
function getLengthOfStr(s) {
  let strArr = [];
  let prevStrArr = [];
  console.log(s);
  for (let i = 0; i < s.length; i++) {
    console.log("=======================", i);

    let ss = s.slice(i, i + 1);
    console.log(" 검사 ss ==> ", ss);
    for (let j = 0; j < strArr.length; j++) {
      if (ss === strArr[j]) {
        if (prevStrArr.length < strArr.length) {
          prevStrArr = strArr.slice();
          console.log("prevStrArr에 저장", prevStrArr);
        }

        strArr = strArr.splice(j + 1, strArr.length);
        console.log("자르고 다시 시작 strArr", strArr, j);
        //splice arr 자르는 함수
        break;
      }
    }

    strArr.push(ss);
    console.log("추가한 후 strArr", strArr);
  }

  return Math.max(strArr.length, prevStrArr.length);
}
console.log(getLengthOfStr("taaaytts"));
```

<br>
Source: [https://leetcode.com/problems/top-k-frequent-elements/](https://leetcode.com/problems/top-k-frequent-elements/)
