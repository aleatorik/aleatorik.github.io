---
layout: post
title: 1차 팀 프로젝트 후기(feat. SpaceX)
category: Etc
tags: Etc
---

<br>

# 프로젝트 소개:

> 엘론머스크가 설립한 민간 우주기업 Space X 웹사이트 클론 프로젝트

- 개발 기간 : 2020년 8월 18일 ~ 2020년 8월 28일(약 2주)<br>
- 개발 인원 : Front-end 3명, Back-end 2명<br>
- [Github 주소](https://github.com/aleatorik/devx)

<br>

# 프로젝트 목적

1. **Scrum** - 스크럼 진행 방식에 대해서 이해했고 Trello 와 같은 tool 을 활용하여 스크럼 방식 아래 프로젝트 진행할 수 있다
2. **Standup Meeting** - 매일 아침 미팅을 통해 어제 한 일, 오늘 할 일, blocker 세 가지를 공유하며 팀원들과 미팅을 진행할 수 있다.
3. **Communication** - 팀원들과 소통이 필요한 경우 올바른 방법을 통해 의견을 주고 받으며 조율할 수 있다.
4. **Git** - 기본적인 Flow에 따라 Git을 사용할 수 있으며, brach를 생성하고 올바른 이름과 내용을 commit message를 작성할 수 있다.
5. **문제 해결 능력** - 모르는 과제를 마주하는 경우 Google 검색, stackoverflow 등을 활용하여 문제를 해결할 수 있다.
6. **Q&A** - 스스로 문제 해결이 잘 안 되는 경우, 혹은 누군가가 도움을 요청하는 경우 동기, 혹은 멘토와 올바른 방법으로 질문과 대답을 주고 받을 수 있다.

## ☑️ 프론트엔드

[✅] CRA 초기 세팅을 나 혼자서도 어느 정도 할 수 있다.<br>
[✅] Routes.js에 라우트를 추가할 수 있다.<br>
[✅] Pages, Components의 차이점을 알고 어디에 어떤 컴포넌트를 만들어야 하는지 안다.<br>
[✅] event handler를 정의해서 특정 이벤트에 부여할 수 있다.<br>
[✅] 포스트맨을 사용하여 api를 호출하고, 응답을 확인할 수 있습니다.<br>
[✅] fetch나 axios를 사용하여 백앤드에 api를 호출하고,<br>
[✅] 응답받은 데이터를 활용하여 화면에 보여줄 수 있다.<br>
[✅] 로그인 사용자의 token을 왜 localStorage에 저장하는지 설명할 수 있다.<br>
[✅] map을 사용해서 jsx 리턴하여 목록을 구현할 수 있을 것 같다.<br>
[✅] 자식컴포넌트에서 부모컴포넌트에 어떻게 데이터를 넘겨야 하는지 알고 있다.<br>
[✅] scss를 왜 쓰는지 알고, scss의 mixin 기능 등을 자유자재로 활용할 수 있다.<br>

<br>

# 데모 영상

<iframe
  src="https://www.youtube.com/embed/gG9l7pZVQ4Y"
  style="width:100%; height:400px;"
></iframe>

<br>

# 사용 기술

## 공통

1. HTTP

2. Git

3. Linux

4. VScode

5. Trello - 프로젝트 스크럼 툴 ([링크](https://trello.com/b/7GVBeJ4W/wespace))

6. PostMan - API 테스트 및 결과 내용 공유
7. AWS

- AWS EC2 서버 배포
- AWS RDS 구축
- AWS S3 구축 및 이미지 업로더 연결

## 프론트엔드

**1. React.js**

- react-router-dom : 브라우저에서 사용되는 리액트 라우터
- node-sass : Sass(.scss) 파일을 css 파일로 컴파일

**2. SCSS**

- SASS의 모든 기능을 지원하면서 CSS 구문과 완전히 호환됨

## 백엔드

**1. Python**

- BeautifulSoup : 웹 크롤링 및 파싱
- Selenium : 내장 기능을 활용해 다수의 웹 데이터를 효율적으로 크롤링
- List comprehension : 코드실행 효율 향상
- Pandas : 간편한 csv파일 저장 및 열람
- ast : list_eval 기능 사용

**2. Django**

- Bcrypt, PyJWT : 회원가입 시 기입한 비밀번호 암호화 및 토큰 발행
- UnitTest : 클래스 단위 코드 디버깅
- LoginDecorator : 발행한 토큰을 통한 등록회원 인증/인가
- Endpoint : User, Product, Order

**3. MySQL**

- DB 구축 및 데이터 업로더 제작

<br>

# 주요기능

> 직접 구현한 기능은 ✅, 팀원이 구현한 기능은 ✔️로 표시

1. ✔️ 회원가입 & 로그인
2. ✔️ 제품소개 페이지
3. ✅ 상품 페이지

   - Map 함수를 통한 상품 리스트 구현
   - Fetch를 통한 API 호출
   - 동적 라우팅

4. ✅ 상품 상세 페이지

   - 모달창
   - SVG 컴포넌트화
   - 장바구니 추가 기능(토큰안중 후 페이지 이동 함수)

5. ✔️ 장바구니 페이지

<br>

# 구현과정

Fetch를 통한 API 호출 / 동적 라우팅 / SVG 컴포넌트화 / 모달창 / Map 함수를 통한 상품 리스트 구현 / 장바구니 추가 기능(토큰인중 후 페이지 이동 함수)

<br>

# 마무리 하며..
