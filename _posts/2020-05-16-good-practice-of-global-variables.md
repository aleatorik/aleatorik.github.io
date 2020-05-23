---
layout: post
title: 올바른 전역변수 사용법
category: TIL (Today I Learned)
tag: [TIL (Today I Learned)]
---

<br>
오늘의 학습주제는 Block Scope와 관련한 **전역변수 사용의 올바른 practice**에 대한 내용이다.
<hr/>
먼저, block scope는 블록 단위의 유효범위를 뜻하는 말로 **변수의 접근가능한 범위**를 일컫는다.
<br>
이 유효범위(scope)에는 global scope와 local scope가 있는데, 간단히 말해 global 범위는 어느 곳에서나
접근이 가능한 것이고, local 범위는 특정 block('{}' <- 이러한 괄호 안에 있는 변수)안에서만 접근이 유효하다.

```
let globalName = "global name";
{
  let localName = "daniel";
  console.log(localName);
  localName = "alex";
  console.log(localName);
  console.log(globalName);
}
console.log(globalName);
console.log(localName);
```

위의 코드 실행 결과,<br>
아래와 같이 코드 맨 마지막 줄의 변수 'localName'이 정의되지 않았다는 에러메세지가 출력된다.
<br>

![](/public/img/global.png)

<hr/>

전역변수(glbal variable)는 **어플리케이션이 실행되는 순간부터 끝날 때까지 항상 메모리에 탑재** 되어있기 때문에
**촤소한**으로 쓰는 것이 좋다. 가능하면 **클래스나 함수, if, for문 등으로 필요한 부분에서만 정리해서 쓰는 것**이 권장된다.
