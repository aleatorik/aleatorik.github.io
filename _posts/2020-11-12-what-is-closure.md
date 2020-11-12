---
layout: post
title: 클로저란 대체 무엇인가?
category: Javascript
tags: Javascript
---

## 클로저란

- 함수와 함수가 접근할 수 있는 스코프가 클로적 관계를 맺는다.
- 여러 함수형 프로그래밍 언어에서 나타나는 보편적 특성이다.
- 함수를 선언할 때 만들어지는 유효범위가 사라진 후에도 호출할 수 있는 함수이다.
- 로컬 변수를 참조하고 있는 함수 내의 함수.
- 함수와 그 함수가 선언될 당시의 lexical environment의 상호관계에 따른 현상.
- 어떤 함수에서 선언한 변수를 참조하는 내부함수에서만 발생하는 현상.

```jsx
for(var i = 0; 1 < 100; i++) {
	setTimeout(function() {
		console.log(i);
	}, i * 1000);
}
//비동기 함수 안의 변수는 '실행'될 때 값이 결정된다.

결과는 '100'만 1초마다 계속 찍힌다
(왜냐하면, 반복문 연산은 0.xxxx1초만에 끝나서 이미 100이기 때문에)
//위 코드의 컴퓨터 실제 동작은 아래처럼

setTimeout(function() {
	console.log(i);
}, 0 * 1000);
//아래 i가 0 * 1000이 되고 난 뒤에 console.log(i)를 실행(이미 100)

setTimeout(function() {
	console.log(i);
}, 1 * 1000);
//아래 i가 1 * 1000이 되고 난 뒤에 console.log(i)를 실행(이미 100)

setTimeout(function() {
	console.log(i);
}, 2 * 1000);
//아래 i가 2 * 1000이 되고 난 뒤에 console.log(i)를 실행(이미 100)

	.

	.

	.

setTimeout(function() {
	console.log(i);
}, 99 * 1000);
```

## 중요 포인트

1. 클로저는 그 본질이 메모리를 계속 차지하는 개념이므로 더는 사용하지 않게 된 클로저에 대해서는 메모리를 차지하지 않도록 관리해줄 필요가 있다.
2. 실제로 클로저는 어떤 상황에 쓰이는가?
   - 1). 콜백 함수 내부에서 외부 데이터를 사용하고자 할 때
   - 2). 접근 권한 제어(정보 은닉): JS는 변수 자체에 접근 권한을 직접 부여하도록 설계돼 있지 않음. 하지만 클로저를 통해 함수 차원에서 public한 값과 private한 값을 구분하는 것이 가능.

_(정보은닉이란 어떤 모듈의 내부 로직에 대해 외부로의 노출을 최소화해서 모듈 간의 결합도를 낮추고 유연성을 높이고자 하는 현대 프로그래밍 언어의 중요한 개념\_ 접근 권한의 세 종류로는 'public', 'private', 'protected'가 있다)_

1-1) 예시

```jsx
function outerFunction(url) {
  fetch(url).then(() => {
    console.log(url);
  });
}
// arrow function(내부함수)은 'outerFunction'(부모함수)의 모든 scope에 접근 가능
```
