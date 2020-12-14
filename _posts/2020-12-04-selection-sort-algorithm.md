---
layout: post
title: 선택정렬(selection sort)
category: Algorithm
tags: Algorithm
---

<br>
정렬 알고리즘은 순서가 없던 데이터를 순서대로 바꾸어 나열하는 알고리즘
> 선택정렬,
> [버블정렬](https://aleatorik.github.io/algorithm/2020/12/12/bubble-sort-algorithm/),
> 삽입정렬,
> [퀵정렬](https://aleatorik.github.io/algorithm/2020/12/05/quick-sort-algorithm/)

<br>
**선택정렬**은 정렬되지 않은 데이터 중 가장 작은 데이터를 선택해서
맨 앞에서부터 순서대로 정렬해 나가는 알고리즘이다.

_"It has O(n2) time complexity, making it inefficient on large lists, and generally performs worse than the similar insertion sort.
Selection sort is noted for its simplicity, and it has performance advantages over more complicated algorithms in certain situations, particularly where auxiliary memory is limited."_

("O(n2) 시간복잡도를 가지고, 큰 리스트에서 비효율적이고 일반적으로 비슷한 삽입정렬에 비해 좋지 않은 성능을 갖는다.
몇몇의 특정 상황에서 다른 복잡한 알고리즘보다 더 좋은 성능상의 이점을 갖는데 특히, 보조 메모리가 제한적인 경우에 그렇다.")

## 알고리즘 분석

- 정렬을 해야하는 배열은 [7,5,4,2] 이다.<br>
- 첫 번째 loop에서는 index 0부터 3까지 확인하며 가장 작은 수를 찾는다.<br>
- 2 이므로 index 0의 7과 교체. -> [2,5,4,7]<br>
- 두 번째는 index 1부터 3까지 확인하며 가장 작은 수를 찾는다.<br>
- 4이므로 index 1의 5와 교체. -> [2,4,5,7]<br>
- 세 번째는 index 2부터 3까지.. 이런식으로 가장 작은 수를 선택해서 순서대로 교체하는 것을 선택정렬이라고 한다.

## Example

| nums라는 정렬되지 않은 숫자 배열이 주어지면, 오름차순(1,2,3..10) 으로 정렬된 배열을 return하라.

## My Solution

```jsx
const selectionSort = (nums) => {
  for (let i = 0; i < nums.length; i++) {
    let minIdx = i;

    for (let j = i + 1; j < nums.length; j++) {
      if (nums[minIdx] > nums[j]) {
        minIdx = j;
      }
    }

    let temp = nums[i];
    nums[i] = nums[minIdx];
    nums[minIdx] = temp;
  }

  return nums;
};
```

## Another Solution

```jsx
function selectionSort(nums) {
  for (let i = 0; i < nums.length; i++) {
    let minIndex = i;
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[minIndex] > nums[j]) {
        minIndex = j;
      }
    }
    if (minIndex !== i) {
      let swap = nums[minIndex];
      nums[minIndex] = nums[i];
      nums[i] = swap;
    }
    console.log(`${i}회전: ${nums}`);
  }
  return nums;
}
console.log(selectionSort([5, 4, 3, 2, 1]));
```
