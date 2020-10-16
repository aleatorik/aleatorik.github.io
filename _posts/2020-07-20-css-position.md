---
layout: post
title: CSS의 Position 속성
category: CSS
tags: CSS
---

# Position이란?

HTML에서 element를 배치하는 방법을 지정하는 속성이다. position 속성에 쓸 수 있는 값은 static, relative, absolute, fixed, sticky 5개가 있다.

![Position image](https://www.bapugraphics.com/multimediacoursetips/wp-content/uploads/2017/05/Explain-Absolute-Relative-Fixed-Positioning-Difference.jpg)

## 1. static

html에 정의된 순서대로 브라우저에 자연스럽게 보여지는 것으로 positon의 default값이다. 그러므로 컨테이너에 위치를 바꿔주려면 position을 static에서 다른 걸로 바꿔줘야 한다.

## 2. relative

원래 있어야 하는자리(static)에서 top, right, down, left 속성 값을 줌으로써 위치를 움직인다.

## 3. absolute

static 속성을 가지고 있지 않은 부모를 기준으로 움직인다. 만약 부모 중에 포지션이 relative, absolute, fixed인 태그가 없다면 가장 위의 태그(body)가 기준이 되며, 아이템이 담겨있는(즉 상위태그), 해당 아이템과 가장 가까이에 있는(상위태그라도 직속 상위태그) 박스 안에서 위치변경이 발생한다.

## 4. fixed

fixed 속성의 element는 상자에서 완전히 벗어나서 브라우저의 window 페이지상에서 움직인다. 즉, 보이는 일반적인 페이지 흐름에서 벗어나 우리가 화면에서 보는 것들에서 고정적인 위치에 놓이게 된다. 그러므로 스크롤링은 이 위치에 전혀 영향을 주지 못한다.

![fixed 속성](/public/img/position-fixed.gif)

## 5. sticky

sticky 속성 인자는 처음에 마치 `position: relative`처럼 기존 자리에 위치하지만, 스크롤링이 될 때, 마치 `position: fixed`처럼 행동한다. 즉, 스크롤링 되어도 없어지지 않고 기존 위치에 붙어있는다. 이 속성값은 원위치가 화면 상단에서 멀리 떨어져 있는 요소에 적용할 때 유용하다. 참고로 top, left 값을 지정해줘야 sticky 속성이 작동한다.

![sticky 속성](/public/img/position-sticky.gif)

<br>

자료출처:
[상위 이미지](https://www.bapugraphics.com/multimediacoursetips/explain-absolute-relative-fixed-positioning-difference/) , [fixed & sticky 이미지](https://coder-coder.com/css-position-layout/)
