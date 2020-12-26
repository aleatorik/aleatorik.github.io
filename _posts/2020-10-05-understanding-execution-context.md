---
layout: post
title: 실행 컨텍스트에 대한 이해
category: Javascript
tags: Javascript
---

## 실행 컨텍스트란?

자바스크립트가 브라우저 내부에서 어떻게 동작하는지 알려면, 실행 컨텍스트에 대해 공부해야 한다.
실행 컨텍스트와 콜스택은 다른 자바스크립트의 주요한 개념들, 이를테면 호이스팅, 스코프 그리고 클로저 등을 이해하는 데 필수이다.

본론으로 돌아가서, 실행 컨텍스트란 간단하게 말하면 자바스크립트 코드가 실행되는 환경을 나타내는 추상적 개념이다. 자바스크립트 안에서 실행되는 모든 코드들은 어떤 실행 컨텍스트에서 돌아가고 있는 것이다.

## 실행 컨텍스트의 종류

- 전역공간에서 자동으로 생성되는 전역 컨텍스트(global execution context)
- 함수 실행에 의한 컨텍스트
- ~~eval 함수 실행에 의한 컨텍스트(여기서는 다루지 않음)~~

## 컨텍스트의 원칙 네 가지

- 먼저 전역 컨텍스트 하나 생성 후, 함수 호출 시마다 컨텍스트가 생김
- 컨텍스트 생성 시 컨텍스트 안에 변수객체(arguments, variable), scope chain, this가 생성
- 컨텍스트 생성 후 함수가 실행되는데, 사용되는 변수들은 변수 객체 안에서 값을 찾고, 없다면 스코프 체인을 따라 올라가며 찾음
- 함수 실행이 마무리되면 해당 컨텍스트는 사라집니다.(클로저 제외) 페이지가 종료되면 전역 컨텍스트가 사라짐

> 스코프 체인 : 전역변수와 지역변수의 관계에서 스코프 체인(scope chain)이란 개념이 나옴. 즉 내부 함수에서는 외부 함수의 변수에 접근 가능하지만 외부 함수에서는 내부 함수의 변수에 접근할 수 없다. 꼬리를 물고 계속 범위를 넓히면서 찾는 관계를 스코프 체인이라고 부릅니다.

## 콜스택

컨텍스트 스택은 아래와 같이 형성된다.
![](https://miro.medium.com/max/3600/1*ACtBy8CIepVTOSYcVwZ34Q.png)

<center>An Execution Context Stack for the above code.</center>
<br>
1. 실행 가능한 코드로 컨트롤이 이동하면 논리적 스택 구조를 가지는 빈 실행 컨텍스트 스택이 생성된다.
2. 전역 코드로 컨트롤이 이동하면 전역 실행 컨텍스트(Global EC)가 생성되고 스택에 쌓인다. 이 전역 실행 컨텍스트는 App 종료 시기까지 유효하다.
3. 함수를 호출하면 해당 함수의 코드로 컨트롤이 이동하고, 함수의 실행 컨텍스트가 생성되고 스택에 쌓인다.
4. 함수 실행이 끝나면 해당 함수의 실행 컨텍스트가 파기되고, 직전 실행 컨텍스트로 컨트롤이 이동한다.

<br>

~~내용 추가 예정~~

참고자료 : <br>[https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0](https://blog.bitsrc.io/understanding-execution-context-and-execution-stack-in-javascript-1c9ea8642dd0), [https://www.zerocho.com/category/JavaScript/post/5741d96d094da4986bc950a0](https://www.zerocho.com/category/JavaScript/post/5741d96d094da4986bc950a0)
