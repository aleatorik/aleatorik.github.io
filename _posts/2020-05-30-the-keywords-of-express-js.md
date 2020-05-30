---
layout: post
title: Express. js 키워드 정리
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

_~~중간에 다른 할 일들이 생겨서 도중에 Node.js 학습을 잠시 중단했었다~~_

## 오늘은 기존에 학습했던 Node.js 관련 내용들을 복습하는 차원에서 **Express.js** 에 대한 키워드를 몇 가지 정리해본다.

- Server

  > Node.js

  > Babel

  > Nodemon

- Npm

- Middleware

  > Morgan : _logger middleware returning a string that will be the log line or undefined / null to skip logging_

  > Helmet : _secure Express apps_

  > Cookie parser : _keep information in cookies for user authentication_

  > Body parser : _check content that users send a website as forms, e.g. JSON, HTML_

- Router

- MVC Pattern
  <br>

- Pug : view engine from express handling View from MVC of Express, which shows HTML with CSS by `res.render` instead of `res.send` 🔑layouts, partials —> divide components of websites 🔑how to apply JavaScript code in pug —> `#{}` put JS code in the bracket
