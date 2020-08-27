---
layout: post
title: 협업을 위한 기본 Git Flow
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

```
1.
git clone 클론할 레포지토리 주소

2.
npm install (package.json 안에 있는 모든 패키지들을 설치함)

3.
git branch 브랜치 이름
(클론하면 마스터브랜치 밖에 없기 때문에 멤버들은 branch 생성
-- ex: git branch feature/daseulsong)

4.
git checkout master -- 업데이트 된 내역 받아오기 위해, 마스터(remote)브랜치로 간다
(conflict 날 때마다 마스터에서 업데이트 내역 받아옴)

5.
git pull origin master -- 다른 사람의 업데이트, 작업한 것의 싱크를 맞추기 위해서
마스터브랜치의 최신코드를 받아온다

6.
git checkout feature/daseulsong
본인 작업 브랜치로 다시 이동

7.
git (pull) merge master
master 브랜치 merge 하기 (충돌발생 시 충돌해결)

8.
git add
git commit
git push (본인의 작업 브랜치에서 push
-- ex: git push origin feature/daseulsong)

9.
깃허브 해당 레포지토리에서 pull request를 날린다

10.
(리뷰받기)
(리뷰 후 수정사항 있으면 본인 작업 브랜치에서 해당 작업 후 다시 add, commit, push)
(고칠 내용이 없다면, merge 될 것임)

```
