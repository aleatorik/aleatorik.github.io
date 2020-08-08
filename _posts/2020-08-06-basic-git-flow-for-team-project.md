---
layout: post
title: 협업을 위한 기본 Git Flow
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

```
git clone
npm install 패키지명

(클론하면 마스터브랜치 밖에 없기 때문에) 멤버들은 branch 생성
add
commit
push (origin feature/daseulsong)


git checkout master -- 마스터(remote)로 돌아가서 업데이트 된 내역 받아옴
<conflict 날 때마다 마스터에서 업데이트 내역 받아옴>
git pull origin master (다른 사람의 업데이트, 작업한 것의 싱크를 맞추기 위해서 )

git pull merge master (충돌발생)
(충돌해결)

add
commit
push
pull request
(리뷰받기)
(수정작업)->현재위치 feature

```
<br>

```
작업순서
git branch feature/jun <- 항상 작업하기 전에 자신의 브랜치에서!
git pull origin master 명령어로 최신 코드를 받아온다
코드를 작업한다. 최대한 기능별로 쪼개서 작업하기
프로젝트 상위 디렉토리로 가서 git add . 명령어로 내가 수정한 코드를 git stage 에 올린다
git status add가 잘 되었는지 확인하기
git commit -m "commit message" <- commit message는 팀원과 상의한 후에 slack 에 공유한다.
git push origin feature/jun <- 본인 브랜치에서 작업한 내용을 원격 리포지토리에 올리기!
```