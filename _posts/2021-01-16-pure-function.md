---
layout: post
title: 순수함수
category: Javascript
tags: Javascript
---

## 순수함수랑 순수하지 않은 함수

<br>

- 함수는 입력 값을 받고 그에 상응하는 출력 값을 내보낸다.
- 순수함수는 같은 입력값이 들어왔을 때, 항상 같은 출력이 나온다.
- 순수함수는 어떤 외부 상태도 변환하지 않는다.(side-effect 만들지 않는다)

<br>

```jsx
const pureFunction = (x: number, y: number) => x + y;
```
_(순수함수의 예시)_

<br>

```jsx
let globalVariable = 10;

const impureFunction = (x: number, y: number) => x + y + globalVariable;

function main() {
  console.log(impureFunction(1, 2)); // 13
  globalVariable = 20;
  console.log(impureFunction(1, 2)); // 23
}

main();
```
_(순수함수가 아닌 예시 1)_ => 순수 함수라면 동일 입력 시 동일 출력을 보장해야 하지만 globalVariable이라는 변수의 변화에 영향을 받음

<br>

```jsx
let globalVariable = 10;

const impureFunction = (x: number, y: number) => {
  globalVariable = y;
  return x + y;
};

function main() {
  console.log(impureFunction(1, 2)); // 3
  console.log(impureFunction(1, 2)); // 3
  // 둘의 결과는 같으나, globalVariable의 값이 변경됨.
}

main();
```
_(순수함수가 아닌 예시 2)_ => 순수 함수는 부수 효과를 가지지 않는다. 하지만 위의 예시는 전역 변수 globalVariable의 값이 변경됨.
