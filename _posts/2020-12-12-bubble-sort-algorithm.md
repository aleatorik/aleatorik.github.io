---
layout: post
title: 버블정렬(bubble sort)
category: Algorithm
tags: Algorithm
---

<br>
버블 정렬은 인접한 데이터를 교환해서 정렬하는 알고리즘.
알고리즘의 정렬되는 모습이 마치 거품처럼 보인다고 해서 붙여진 이름.

## Example

아래와 같은 정렬되지 않은 수가 있을 때, index 0 <-> 1 부터 교환하기 시작.
인접한 두 수를 비교하여 더 큰 것을 우측으로 이동시킴.<br>
_`6 5 3 2 8`_
-> _`5 6 3 2 8`_

그 다음은 index 1 <-> 2<br>
_`5 6 3 2 8`_
-> _`5 3 6 2 8`_

그 다음은 index 2 <-> 3<br>
_`5 3 6 2 8`_
-> _`5 3 2 6 8`_

그 다음은 index 3 <-> 4<br>
_`5 3 2 6 8`_
-> _`5 3 2 6 8`_<br>
이렇게 제일 마지막 두 수 까지 비교하면, 제일 큰 수가 제일 마지막 index에 위치하는 것을 알 수 있다.

다시 처음부터 시작.<br>
_`5 3 2 6 8`_
-> _`3 5 2 6 8`_

_`3 5 2 6 8`_
-> _`3 2 5 6 8`_

_`3 2 5 6 8`_
-> _`3 2 5 6 8`_<br>
이번 교환에는 index 2까지 비교하고 멈추면 됨
마지막 index는 이미 제일 큰 수가 정렬된 상태이기 때문.
이런식으로 계속 비교하고 교체.

## Problem

숫자로 이루어진 배열을 주면, 버블정렬 알고리즘으로 배열을 정렬하시오.

## My Solution

```jsx
const bubbleSort = (nums) => {
  let temp = "";

  for (i = 0; i < nums.length - 1; i++) {
    for (j = 0; j < nums.length - 1; j++) {
      if (nums[j] > nums[j + 1]) {
        // 두 수를 비교, 앞이 뒤 보다 크면 바꿔치기
        temp = nums[j];
        nums[j] = nums[j + 1];
        nums[j + 1] = temp;
      }
    }
  }
  return nums;
};

bubbleSort([3, 6, 1, 9, 5, 7, 2, 4]);
```

## Another Solution

```jsx
const bubbleSort = (nums) => {
  for (let i = 0; i < nums.length; i++) {
    for (let j = 0; j < nums.length - i - 1; j++) {
      if (nums[j] > nums[j + 1]) {
        let temp = nums[j + 1];
        nums[j + 1] = nums[j];
        nums[j] = temp;
      }
    }
  }

  return nums;
};

console.log(bubbleSort([2, 1]));
```
