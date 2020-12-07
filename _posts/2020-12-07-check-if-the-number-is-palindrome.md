---
layout: post
title: 팰린드롬 알고리즘
category: Algorithm
tags: Algorithm
---

<br>
_팰린드롬: 앞에서 읽으나 뒤에서 읽으나 항상 똑같이 읽어지는 문자열을 의미_

## Examples

```
num = 123
return false
=> 뒤집은 모양이 321 이기 때문
```

```
num = 1221
return true
=> 뒤집은 모양이 1221 이기 때문
```

```
num = -121
return false
=> 뒤집은 모양이 121- 이기 때문
```

```
num = 10
return false
=> 뒤집은 모양이 01 이기 때문
```

## My Solution

```jsx
const sameReverse = (num) => {
  let str = num.toString();
  // value값을 비교하기 위해 배열로 각 자릿값을 쪼개야하므로 number -> string
  let arr = str.split("");

  console.log(arr);
  // 변환된 string을 배열로 쪼개기
  let firstDigit = arr.indexOf();
  let lastDigit = arr.lastIndexOf();

  console.log(arr[0]);

  if (arr[0] == "-") {
    return false;
  } else if (firstDigit.valueOf() == lastDigit.valueOf()) {
    return true;
  } else {
    return false;
  }
};

let num = -101;
sameReverse(num);
```

> 방법1) '-'가 있으면 제거하고 비교<br>
> 방법2) '-'가 있으면 무조건 false<br>
> indexOf, lastIndexOf
> => 첫번째인자와 마지막인자의 value가 같으면 true, else-> false<br>
> lastIndexOf) 첫 번째 문자의 인덱스는 0이며, 마지막 문자의 인덱스는 str.length -1

## Another Solution

```jsx
const sameReverse = (num) => {
  let arr = "" + num;
  let rev = arr.split("").reverse();
  let str = rev.toString().replace(/,/gi, "");
  if (arr === str) {
    return true;
  } else {
    return false;
  }
};
```
