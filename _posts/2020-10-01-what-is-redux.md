---
layout: post
title: Redux(리덕스)란 무엇인가?
category: Javascript
tags: Javascript
---

<br>
먼저 리덕스는 명시적으로 리액트하고만 연동되게끔 디자인된 기술이 아니다.

리액트 라이브러리 자체는 유저 인터렉션을 핸들링하며 화면에 콘텐츠를 렌더링하는 것이 가장 핵심이다.
그러므로 리액트의 가장 주요한 목표가 사실 데이터의 유지, 업데이트를 다루는 것에 있지 않다.
리덕스는 상태 관리 라이브러리로 리액트가 컴포넌트 안에서 state를 유지 관리하는 것을
리덕스가 대신 리액트 앱 안에서 처리한다.

하지만 기본적으로 리액트 자체로 상태관리가 가능하므로, 모든 프로젝트마다 리덕스를 사용할 필요는 없다.
리덕스 외에도 Context API, MobX 등의 상태관리가 있으며,
리액트 16.3이후 버전에서는 그래도 Context API가 개선되어 사용하기 좋아졌다.
다만, 프로젝트의 규모가 클 경우에는 리덕스 사용을 통해 미들웨어 기능(효율적인 비동기 작업), 강력한 개발자 도구, 높은 코드 유지보수성 등의 도움을 받을 수 있다.

![Redux Cycle](https://res.cloudinary.com/practicaldev/image/fetch/s--xM9toia4--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/i/vfx1vv0byq66m2sjep5f.PNG)

이미지 출처: [리덕스 사이클\_이미지](https://dev.to/geeuho/redux-makes-things-more-complicated-and-then-easier-3n3i)

(마지막 업데이트 : 2020. 11. 30)
