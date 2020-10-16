---
layout: post
title: CSS ::placeholder Selector(-webkit-input-placeholder)
category: CSS
tags: CSS
---

# 문제점

: **Input 태그의 placeholder 텍스트의 중앙정렬을 하면 사용자가 입력하는 값 역시 중앙에서 시작됨**

<br>

# 해결방안

: **사용자가 입력하는 값이 input 박스의 왼쪽 가장자리('initial' 위치)로 가야함**

> 1. 해당 input 태그의 class명으로 css에서 'text-align: center'로 주면 placeholder의 text와 사용자가 타이핑하는 값 모두 중앙에 위치하게 된다.
>
>    **2. `::-webkit-input-placeholder`을 사용하면, input태그의 placeholder 텍스트 값의 위치만 따로 설정할 수 있다.**
>
> - 여기서 -webkit은 Safari / Chorome을 위한 HTML, CSS 웹 브라우저 렌더링 엔진이다. 그러므로 다른 브라우저 위에서 동작하기 위해서는 아래와 같이 webkit자리에 그에 맞는 코드를 써야한다.

  <br>
  ```
  ::-webkit-input-placeholder { /* Chrome/Opera/Safari */
  color: pink;
  }
  ::-moz-placeholder { /* Firefox 19+ */
  color: pink;
  }
  :-ms-input-placeholder { /* IE 10+ */
  color: pink;
  }
  :-moz-placeholder { /* Firefox 18- */
  color: pink;
  }
  ```
  <br>

- 주의할 점은 아래와 같이 해당 input태그에 적용된 다른 속성값들과 같이 묶어서 적용할 경우, 해당 속성값들이 동작을 안하므로

 <br>

```
.search__bar::-webkit-input-placeholder {
text-align: center;
padding: 0px 24px;
margin-top: 8px;
}
```

<br>
- 아래처럼 `::-webkit-input-placeholder{}`만 별도로 사용해야한다.

<br>

```
.search__bar::-webkit-input-placeholder {
text-align: center;

.search__bar {
  padding: 0px 24px;
  margin-top: 8px;
}
```
