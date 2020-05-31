---
layout: post
title: Express. js 키워드 정리
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

_~~중간에 다른 할 일들이 생겨서 도중에 Node.js 학습을 잠시 중단했었다~~_

## 오늘은 기존에 학습했던 Node.js 관련 내용들을 복습하는 차원에서 **Express.js** 에 대한 키워드를 몇 가지 정리해본다.

- ## Server

  > Node.js

  > Babel

  > Nodemon

- ## Npm

- ## Middleware

  > Morgan : _logger middleware returning a string that will be the log line or undefined / null to skip logging_

  > Helmet : _secure Express apps_

  > Cookie parser : _keep information in cookies for user authentication_

  > Body parser : _check content that users send a website as forms, e.g. JSON, HTML_

- ## Router

- ## MVC Pattern

- ## Pug
  : view engine from express handling View from MVC of Express, which shows HTML with CSS by **res.render** instead of **res.send**

> Layouts, Partials : _divide components of websites, how to apply JavaScript code in pug —> `#{}` put JS code in the bracket_

> Mixins : _allow you to create reusable blocks of Pug. 각각 다른 정보를 가지지만 같은 구조를 가지는 데이터를 표시하기 위한 코드를 캡슐화 —> 단순 복사-붙여넣기 대신 웹사이트에서 반복되는 코드를 재활용하기 위해 Block 단위로 코드 작성하여 필요한 곳에서 `include mixins/'name of mixins file'`통해 사용._

```jsx
mixin videoBlock(video = {})
	h1 = video.title
	p = video.description

// Here's how you can apply the codes above

include mixins/videoBlock
block content
	.videos
		each item in videos
			+videoBlock({
				title: item.title
				description: item.dscription
			})
```

<br>

_~~내용 업데이트 계속 이어짐~~_
