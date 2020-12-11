---
layout: post
title: 퀵정렬(quick sort)
category: Algorithm
tags: Algorithm
---

<br>
퀵 정렬은 분할 정복(divide and conquer) 방법을 통해 리스트를 정렬한다.

## 분할정복이란?

분할정복 알고리즘은 문제를 나눌 수 없을 때까지 나누어서 각각을 풀면서 다시 합쳐서 문제의 답을 얻는 알고리즘이다.

## 알고리즘 설계 순서

1. Divide : 문제가 분할이 가능한 경우, 2개 이상의 문제로 나눈다.
2. Conquer: 나누어진 문제가 여전히 분할이 가능하면, 또 다시 Divide를 수행한다. 그렇지 않으면 문제를 푼다.
3. Combine: Conquer한 문제들을 통합하여 원래 문제의 답을 얻는다.

> - 문제를 제대로 나누면 Conquer하는 것은 쉽기 때문에 Divide를 제대로 하는 것이 중요
> - 분할정복 알고리즘에서 재귀 알고리즘이 많이 사용되는데, 이 부분에서 성능 효율성이 떨어질 수 있음

![분할정복예시](http://www.robasworld.com/wp-content/uploads/2017/02/QuickSort-261x300.png)
`Quick Sort Demonstration`

1. 리스트 가운데서 하나의 원소를 고른다. 이렇게 고른 원소를 **피벗**이라고 한다. (위 그림 상의 초록색 사람)
2. 피벗 앞에는 피벗보다 값이 작은 모든 원소들이 오고, 피벗 뒤에는 피벗보다 값이 큰 모든 원소들이 오도록 피벗을 기준으로 리스트를 둘로 나눈다. 이렇게 리스트를 둘로 나누는 것을 **분할**이라고 한다. 분할을 마친 뒤에 피벗은 더 이상 움직이지 않는다.
3. 분할된 두 개의 작은 리스트에 대해 재귀(Recursion)적으로 이 과정을 반복한다. 재귀는 리스트의 크기가 0이나 1이 될 때까지 반복된다.

```jsx
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  return merge(mergeSort(left), mergeSort(right));
}

function merge(left, right) {
  let result = [];

  while (left.length && right.length) {
    if (left[0] < right[0]) {
      result.push(left.shift());
    } else {
      result.push(right.shift());
    }
  }
  while (left.length) {
    result.push(left.shift());
  }
  while (right.length) {
    result.push(right.shift());
  }

  return result;
}

const arr = [
  "froh",
  "goose",
  "horse",
  "polar bear",
  "zebra",
  "gorilla",
  "giraffe",
  "chicken",
  "elephant",
];
console.log(mergeSort(arr));
//['froh', 'goose', 'gorilla', 'giraffe', 'chicken', 'horse', 'polar bear', 'zebra', 'elephant']
```

<br>
출처: [위키피디아](https://ko.wikipedia.org/wiki/%EC%8B%9C%EB%A7%A8%ED%8B%B1_%EC%9B%B9),
[사진자료](https://www.robasworld.com/sorting-algorithms/),
[블로그](https://janghw.tistory.com/entry/%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-Divide-and-Conquer-%EB%B6%84%ED%95%A0%EC%A0%95%EB%B3%B5)
