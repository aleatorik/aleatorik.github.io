---
layout: post
title: 소프트웨어에서 파이프라인이란?
category: Etc
tags: Etc
---

<br>
자 먼저, 파이프를 설명하기 전에 파이프가 대체 무엇인지부터 짚고 넘어가자. “파이프” 라는 단어를 들었을 때 무슨 이미지가 먼저 연상되는가? 아마도 방금 내가 생각한 것처럼 천장에 연결된 가스 배관과 같은 파이프들을 떠올렸을 수도 있다. 혹은 땅 속에 묻힌 수도 배관을 떠올렸을지도 모르겠다.

## 그래서 우리가 아는 그 파이프랑 비슷한 건가?

그렇다 :)

파이프는 단방향 통신을 위한 용도로 사용된다. 하나의 파이프는 그 이전 파이프에서 전달된 결과를 파라미터로 삼아 또 다른 결과를 내놓는다.
주로 이런 배관들은 A 에서 B 라는 지점으로 자원을 보내는 용도로 많이 사용된다. 그래서 단순히 터널과 같은 공간의 개념이라고 생각하면 된다.

---

## 그럼 소프트웨어 분야에서의 파이프라인은 어떤 의미?

아래는 소프트웨어 분야에서 사용되는 파이프라인 용어가 어떻게 쓰이는지 파악하기 위해 일부 영문자료에서 발췌하여 번역해보았다.

pipeline that will build a “staging” version of an app and push it in the proper hosting slot for testing purposes.
=> **"파이프라인은 앱의 스테이징 버전을 빌드하고 테스트를 위해 그것을 적당한 호스팅 영역에 푸시하는 것을 뜻한다."**

_(참고: 'staging 버전'이란 소프트웨어 테스트 목적으로 만든 개발 버전(production version)의 복제버전이다. 구체적으로는 애플리케이션 배포 전 실제 개발 환경처럼 코드 테스트, 빌드, 품질을 보장하기 위한 업데이트들을 위해 설계된다.)_

''When'' a developer tries to push their code to the common codebase,<br>
''then'' a set of unit tests need to pass.

you can name those scenarios pipelines.

=> **"예를 들어, 개발자가 그가 작성한 코드를 공용 코드베이스(ex: 깃허브)에 푸시할 때, 한 유닛 테스트 단이 통과되어야 하는 이런 시나리오를 파이프라인이라 부를 수 있다."**

In order to run a particular pipeline, we need some kind of kickstart — or a trigger — to be initiated. These could be: <br>
=> **"특정 파이프라인을 구동하기 위해 그것이 시작될 수 있게하는 트리거가 필요하다. 이를 테면 다음과 같다"**

A timer trigger (“Build a staging version of the app everyday at 6:00 p.m.”)<br>
=> **"타이머 트리거: 매일 오후 6시마다 스테이징 버전의 앱을 빌드하라"**

A code repository trigger (“Run unit tests every time a new pull request has been published.”)<br>
=> **"코드 레포지토리 트리거: 새로운 풀리퀘스트가 발행될 때마다 유닛테스트를 구동하라"**

A manual trigger (“Project manager starts the app building process and deploys to production.”)<br>
=> **"메뉴얼 트리거: 프로젝트 매니저가 어플리케이션의 빌드 프로세스를 시작하고 제품을 배포한다"**

It’s possible to invoke particular pipelines from other ones as well, especially when we need to integrate a complex application consisting of many subparts that are being built separately.<br>
**("다른 것들에서 특정 파이프라인들을 불러일으키는 것도 가능하다. 이를테면 따로따로 만들어지고 있는 여러 하부부분들로 구성된 복잡한 어플리케이션을 통합하고자 할 때 등이다.")**

[참고자료](https://blog.logrocket.com/from-front-end-developer-to-a-devops-an-intro-to-ci-cd-7a8a8713fb34/)
