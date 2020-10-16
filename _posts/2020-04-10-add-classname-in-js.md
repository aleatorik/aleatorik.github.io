---
layout: post
title: 자바스크립트 class 이름 추가
category: Javascript
tags: Javascript
---

자바스크립트의 classList.add라는 메소드를 이용하면
html 태그에 있는 기존 클래스에 classList.add 메소드의 파라미터 이름으로 된 클래스가 추가된다.
(즉, 클래스 이름이 2개가 나란히 놓인다)

예를들어, HTML h1 태그에 btn이라는 class가 있을 때, 코드는 아래와 같다.

    <h1 class="btn">example</h1> -- <h1>태그의 클래스명 "btn"

자바스크립트로 다음과 같은 코드가 실행될 때,

```
const ADDED_CLASS = "added";
function handleAdd() {
    const hasClass = title.classList.contains(ADDED_CLASS );
    if(hasClass) {
    title.classList.add(ADDED_CLASS);
    }
}
```

아래와 같이 기존 "btn" 옆에 "added"가 공백을 두고 추가된다.

    <h1 class ="btn added">example</h1>
