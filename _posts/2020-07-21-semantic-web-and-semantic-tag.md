---
layout: post
title: 시멘틱 웹과 시멘틱 태그
category: Web
tags: Web
---

## 왜 필요한가?

웹이 등장한 이래 웹상에 축적된 정보가 점점 방대해 짐에 따라 많은 문제에 봉착하게 되었다.
주요원인은 컴퓨터가 정보자원의 의미를 이해하지 못하는데 있다.
시맨틱 웹은 기존 웹을 확장하여 인간과 컴퓨터가 모두 이해할 수 있는 잘 정의된 의미를 기반으로 한 형태의 웹이다.

## 어떻게 구성되는가?

시멘틱 웹을 구성하기 위해 문서의 구조와 형태를 표현하는 명령어인 태그를 개선한다.

시멘틱 웹 이전의 div, span 태그를 통해 정보를 담는 예를 보면, content에 대하여 어떤 설명도 하지 않는다.

```
<body>
<div>content</div>
<span>content</span>
</body>
```

하지만 아래와 같이 '웹페이지의 구성'을 나타내는 요소로 태그를 정의해줌으로써 어떤 태그가 어느 웹페이지의 구성을 보여주는지 단 번에 알 수 있게 된다. 그리고 이러한 태그들을 'semantic tag'라고 부른다. ([더 많은 시맨틱 태그 -> 여기를 클릭](https://developer.mozilla.org/en-US/docs/Glossary/Semantics))

```
<body>
<header></header>
<nav></nav>
<main></main>
<footer></footer>
</body>
```

## 생각 해 볼 문제

사이트에 이미지를 넣는 방법은 두 가지가 있다. `<img>` 태그를 사용하는 것과 `<div>` 태그에 CSS background-image 속성을 추가하는 것.
두 가지 방법의 차이점과 각각 어떠한 경우에 사용하면 좋을까?

접근성, 성능, 사용 용도 등 다양한 기준이 있지만, 본 포스트의 주제랑 관련하여서는 'SEO'(Search Engine Optimization)를 들 수 있다. 즉, 시맨틱 요소인 이미지 태그 사용 시 태그의 ALT 속성에 이미지에 대한 추가 정보를 제공할 수 있지만, CSS를 통해 이미지를 지정할 때 이러한 정보를 제공할 수 있는 방법은 없다.

참고로 css background-image는 이미지를 다양하게 활용할 때 쓰일 수 있다. 가령, 이미지의 배경색을 바꾸거나 반복 배치, 이미지의 위치를 조정하는 등에 있어서는 img태그와 비교했을 때 강점이 있다.

**_결국, 이 두가지 방법 사이의 선택 기준은 이미지 배치 시, 그것이 콘텐츠의 일부인지 디자인의 일부인지에 따라 달리질 것이다.<br>_**

<br>

자료출처: [위키피디아](https://ko.wikipedia.org/wiki/%EC%8B%9C%EB%A7%A8%ED%8B%B1_%EC%9B%B9),
[블로그](https://poiemaweb.com/html5-semantic-web),
[영문자료](https://buildawesomewebsites.com/html-img-vs-css-background-image/)
