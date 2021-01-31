---
layout: post
title: 깃허브 프로필에 contribution 표시 안될 때 해결방법
category: Git
tags: Git
---

## 문제 상황

제목 그대로 어떤 커밋을 하고 깃허브에 remote 저장소에 푸시할 경우, 깃허브 메인 홈페이지의 해당 계정으로 커밋한 내용과 contribution 했다는 표시가 아래처럼 녹색으로 표시된다.<br>

![contribution](/public/img/contribution.png)
<br>

문제는 서브머신으로 어떤 레포를 클론받아 커밋했을 때, 분명 깃허브에는 푸시된 내역이 나오지만, 일명 잔디라고 불리는 contribution내역에는 반영이 되질 않는다.

## 해결 방법

git 명령어로 서브머신에서 해당 레포를 remote 연결을 잘 했음에도(`git remote add <remote repo name> <url>`) 문제가 나온 상황이어서 구글링해보니 친절하게도 아래 링크의 Github 공식 홈페이지에 발생원인에 대해 잘 설명되어 있었다.

[깃허브 공식 홈페이지](https://docs.github.com/en/github/setting-up-and-managing-your-github-profile/why-are-my-contributions-not-showing-up-on-my-profile)
<br>

페이지 중간쯤에 **'Your local Git commit email isn't connected to your account'** 로 시작하는 부분이 내가 누락한 문제의 원인이었다. 즉 서브머신에 로컬 Git 커밋 이메일주소가 본인 깃허브 계정하고 연동이 되어 있지 않아서이다.

해결방법은 -> [이 곳 링크](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/adding-an-email-address-to-your-github-account) <- 에 그림으로 잘 설명되어 있듯이 깃허브 홈페이지 본인 프로필 설정에서 이메일 을 추가하고, 해당 이메일로 오는 깃허브 인증메일에 verify만 처리하면 깃허브 리모트로 커밋, 푸시한 것에 대해 contribution이 잘 반영되는 걸 확인할 수 있다.
<br>

## 잠깐! 그래도 혹시 안된다면?

위에서 링크한 [깃허브 공식 홈페이지](https://docs.github.com/en/github/setting-up-and-managing-your-github-profile/why-are-my-contributions-not-showing-up-on-my-profile) 에는 위에 로컬 깃 이메일과 본인 깃허브 계정 연동이라는 원인 이외에 contribution이 안되는 문제를 야기시키는 몇 가지 다른 원인을 후술하고 있으니, 해당 페이지를 잘 참고하기를 바란다.

끝으로 당연한 이야기일 수도 있지만, 완전히 새로운 서브머신으로 기존 깃허브 contribution 연동을 하고자 한다면, 제일 먼저 해야할 것은 **Git 최초 설정**이다. 먼저 깃을 설치한 다음에 사용자 이름과 이메일 주소를 설정하는 것이다.<br>
<br>

```jsx
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

<br>

--global 옵션으로 설정하는 것은 딱 한 번만 하면 된다. 해당 시스템에서 해당 사용자가 사용할 때는 이 정보를 사용한다. 만약 프로젝트마다 다른 이름과 이메일 주소를 사용하고 싶으면 --global 옵션을 빼고 명령을 실행한다.
<br>

---

Reference

[깃허브 공식 홈페이지](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address#about-commit-email-addresses)<br>
[https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95](https://git-scm.com/book/ko/v2/%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-Git-%EC%B5%9C%EC%B4%88-%EC%84%A4%EC%A0%95)
