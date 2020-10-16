---
layout: post
title: 1차 팀 프로젝트 후기(feat. SpaceX)
category: Etc
tags: Etc
---

<br>

# 프로젝트 소개:

> 엘론머스크가 설립한 민간 우주기업 Space X 웹사이트 클론 프로젝트

<br>

# 개발 인원

프론트엔드: [송다슬](https://github.com/aleatorik)(PM), [이호현](https://github.com/LeeHoHyun-hemtory), [황연욱](https://github.com/younuk23)<br>
백엔드: [김기욱](https://github.com/keywookkim), [이지연](https://github.com/leejirun)

- Github [FrontEnd] [Repository](https://github.com/wecode-bootcamp-korea/11-DevX-frontend)
- Github [Backend] [Repository](https://github.com/wecode-bootcamp-korea/11-DevX-backend)

<br>

# 데모 영상

<iframe
  src="https://www.youtube.com/embed/gG9l7pZVQ4Y"
  style="width:100%; height:400px;"
></iframe>

<br>

# 기간

2020.08.18 - 2020.08.28 (약 2주)

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
