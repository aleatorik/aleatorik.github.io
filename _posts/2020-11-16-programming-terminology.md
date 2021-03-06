---
layout: post
title: 개발용어정리
category: Etc
tags: Etc
---

## Literal (리터럴)

1. 변수나 상수 등 어떠한 값을 명칭하는 것이 아니라 변수 및 상수에 **저장되는 '값 자체'**를 일컫는 말.
   변수나 상수가 메모리에 할당된 '공간'이라면 리터럴은 이 공간에 저장되는 '값'이다. 컴파일 시 프로그램 내에 정의되어 있는 그대로 정확히 해석되어야할 값을 의미.
2. 코드 상에서 데이터를 표현하는 방식으로도 표현됨. 리터럴 표기법이라고 하며, 변수를 선언함과 동시에 그 값을 지정해주는 표기법.

```jsx
const a = 1;
const object = { name: "daseul", age: "20" };
```

## API

함수들의 묶음을 주로 라이브러리라고 하고, api는 어떠한 기능을 호출하는 방법 (interface)인거고, 즉 그 api를 통해 라이브러리의 기능(함수)를 이용

- **Web API** : 자바스크립트에 포함된 게 아닌 브라우저가 제공하는 그래서 브라우저가 이해하는 API

## 라이브러리

- 라이브러리는 일반적으로 API형태로 제공이 된다.
- 인터페이스는 프로그램제공자가 사용자에게 사용을 위해 열어둔 영역을 말합니다.
- 라이브러리는 이와는 직접적인 관련은 없으나, 일반적으로 라이브러리 배포자는, 자신의 라이브러리가 요래요래 사용될 수 있게끔 인터페이스를 구성합니다. 따라서 라이브러리의 사용자는 가능하다면, 라이브러리 제공자가 제공하는 인터페이스를 통해서 라이브러리를 컨트롤 하시는 것이 가장 좋은 방향일 것입니다.

## SPA (Single Page Application)

전통적으로 웹 페이지는 모든 페이지마다 HTML, CSS, Javascript 파일을 각기 가지고 있어야 했고, 따라서 페이지 간 이동을 할 때마다 HTML, CSS, Javascript 파일을 서버와 주고받았기 때문에 속도가 느릴 수 밖에 없었다. Single Page Application은 HTML, CSS, Javascript 파일을 최초 1회만 로드하고, 이후에는 자바스크립트 파일을 통해 DOM 또는 필요한 HTML 파일을 조작하는 방식을 취한다.

## CI (Continuous Integration)

지속적 통합(Continuous Integration)으로, 모든 개발이 끝난 이후에 코드 품질을 관리하는 고전적 방식의 단점을 해소하기위해 나타난 개념이다. 말그대로 개발을 하면서 ‘코드에대한 통합’을 ‘지속적’으로 진행함으로써 품질을 유지하자는 것

## CD (Continuous Deploy)

CD란 지속적 배포(Continuous Deploy 또는 Delivery)로써, 소프트웨어가 항상 신뢰 가능한 수준에서 배포될 수 있도록 지속적으로 관리하자는 개념이다. 사실 어려울 것 없이 그냥 CI의 연장선으로 생각하면 된다. 배포 이전에 테스트와 빌드는 필수적이기 때문에, 사실상 CD가 되려면 항상 CI가 선행되어야 한다고 봐도 무방하다.

즉, CI 프로세스를 통해 개발중에 지속적으로 빌드와 테스트를 진행하고, 이를 통과한 코드에 대하여 테스트서버와 운영서버에 곧바로 그 내용을 배포해 반영하는 것이다. 이상적인 환경이라면 테스트와 빌드가 ‘지속적’으로 이루어지기 때문에, 배포 또한 자연스럽게 ‘지속적’으로 이루어지게 된다.

[참고자료](https://itholic.github.io/qa-cicd/)

![전통적인 개발 플로우](/public/img/withoutCiCd.png)
**(전통적인 개발주기를 나타낸 그림)**

![CI & CD 방식](/public/img/cicd.png)
**(CI & CD 형태의 개발 프로세스 그림)**<br>
_[이미지 출처](https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch)_

## Lexical scoping

(**스코프는 함수를 호출할 때가 아니라 선언할 때 생긴다**)

어떤 스코프(유효범위) 밖에서 정의된 한 변수가 그 스코프 안으로 접근가능한 것을 뜻한다.

```jsx
let str = "JavaScript";

const lexicalScope = () => {
  console.log(str);
};
lexicalScopeun();

// output: JavaScript
```

추가 설명을 위한 예시)

```jsx
var name = "dan";
function log() {
  console.log(name);
}

function wrapper() {
  var name = "alex";
  log();
}
wrapper();
```

log 안의 name은 wrapper 안의 지역변수 name이 아니라, 전역변수 name을 가리키고 있는 것이다. 이런 것을 lexical scoping이라고 한다.

함수를 처음 선언하는 순간, 함수 내부의 변수는 자기 스코프로부터 가장 가까운 곳(상위 범위에서)에 있는 변수를 계속 참조하게 된다. 위의 예시에서는 log 함수 안의 name 변수는 선언 시 가장 가까운 전역변수 name을 참조하게 된다. 그래서 wrapper 안에서 log를 호출해도 지역변수 name='alex'를 참조하는 게 아니라 그대로 전역변수 name의 값인 dan이 나오는 것이다.
<br>

[자료출처](https://www.zerocho.com/category/Javascript/post/5740531574288ebc5f2ba97e)

<br>
(마지막 업데이트 : 2020.12.27)
