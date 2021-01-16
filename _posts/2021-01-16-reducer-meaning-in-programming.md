---
layout: post
title: 프로그래밍에서의 리듀서 의미
category: Javascript
tags: Javascript
---

## 자바스크립트 mdn 문서에서의 reduce() 함수의 정의:

The `reduce()` method executes a reducer function (that you provide) on each element of the array, resulting in single output value. <br>
->리듀스는 주어진 배열의 엘리먼트마다 리듀서 함수를 실행하여 하나의 결과값을 반환하는 메소드.

```jsx
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15
```

## 리덕스 공식문서에서의 리듀서 정의 :

Reducers are functions that take the current state and an action as arguments, and return a new state result. In other words, `(state, action) => newState.` <br>

->리듀서는 현재 상태와 액션을 아규먼트 해서 새로운 상태를 리턴하는 함수.

---

리듀스, 리듀서 같은 듯.. 조금씩 다른 듯한 이 것들이 어떤 파라미터를 가지고 어떤 기능을 하는지는 알겠지만,
어휘적 형태 그 자체로는 위에 설명된 느낌들이 잘 와닿지 않는다.

하지만 아래의 설명이 reduce 또는 reducer의 어휘적 의미를 잘 건드렸다고 생각되서 공유해본다.

> **영단어 Reduce 본래 의미를 보자면,** > **단순하게 줄이다라는 의미보다 변경이라는 의미에 가깝습니다.** > **"to change something into a simpler or more general form"**
>
> **그 예시로 어떤 복잡한 수학문제를 다른 비슷한 문제로 변경해서 (더 간단하게만드려고) 푸는방법을 수학에서는 reduction이라고도 합니다.** > **"In mathematics, reduction refers to the rewriting of an expression into a simpler form."**
>
> **그런의미에서 완벽히 번역은 힘들지만 reduce는 "고쳐나간다" (간단하게만들기위해서, 혹은 특정규칙을 적용하기위해서) 라고 생각해보면 좋을것같습니다. 따라서, 주어진 상태를 고쳐나가는게 함> 수형 프로그래밍에서 자주보이는 reduce()함수입니다. [주어진상태].reduce([특정규칙]) => 변경된상태.**
>
> **즉, 리덕스에서의 reduce()는 현재상태(previousState)를 새로운상태(newState)로 변경할때 쓰는 함수가됩니다.**

<br>

_References_ <br>
[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
<br>
[https://css-tricks.com/understanding-how-reducers-are-used-in-redux/#:~:text=A%20reducer%20is%20a%20function,so%20that%20they%20behave%20consistently.](https://css-tricks.com/understanding-how-reducers-are-used-in-redux/#:~:text=A%20reducer%20is%20a%20function,so%20that%20they%20behave%20consistently.)
<br>
[https://devlog.jwgo.kr/2018/08/23/redux-which-is-weird-term/#:~:text=%EB%A6%AC%EB%93%80%EC%84%9C%EB%9D%BC%E2%80%A6%20%EB%A6%AC%EB%93%80%EC%8A%A4Reduce,%EC%A4%84%EC%9D%B4%EB%8A%94%20%EC%97%AD%ED%95%A0%EC%9D%84%20%ED%95%9C%EB%8B%A4%EA%B3%A0%20%EB%B3%B4%EB%A9%B4..](https://devlog.jwgo.kr/2018/08/23/redux-which-is-weird-term/#:~:text=%EB%A6%AC%EB%93%80%EC%84%9C%EB%9D%BC%E2%80%A6%20%EB%A6%AC%EB%93%80%EC%8A%A4Reduce,%EC%A4%84%EC%9D%B4%EB%8A%94%20%EC%97%AD%ED%95%A0%EC%9D%84%20%ED%95%9C%EB%8B%A4%EA%B3%A0%20%EB%B3%B4%EB%A9%B4..)
