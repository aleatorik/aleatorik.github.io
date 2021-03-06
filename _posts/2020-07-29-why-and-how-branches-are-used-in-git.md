---
layout: post
title: 깃 브랜치 사용법
category: Git
tags: Git
---

아래 본문은 깃 브랜치에 관한 해당 영문자료(['Using Branches In Git'](https://uoftcoders.github.io/studyGroup/lessons/git/branches/lesson/))를 번역한 내용입니다.

## 들어가기에 앞서

Git은 버전관리시스템으로 파일의 변경 사항을 관리하는 데 도움을 준다. 예를 들어, 당신이 공동 연구 프로젝트에서 어떤 기능을 추가하거나 당신의 코드에 어떤 실험적인 변경 사항을 덧붙이고 싶으나, 기존 원본 코드는 건들고 싶지 않을 수 있다. 이 때 필요한 것이 바로 브랜치('branch')다.

<br>

## 깃 브랜치는 무엇인가?

간단하게 말하자면, 깃 브랜치는 깃 저장소('git repository')안에 있는 개별 프로젝트들이다. 하나의 깃 저장소(이하 '저장소')의 서로 다른 브랜치들은 완전히 다른 파일과 폴더를 갖고 있거나, 한 파일의 몇 줄의 코드 라인을 제외한 같은 내용의 것을 가지고 있다.

<br>

- ### 깃 브랜치의 이용 사례

  1. 어떤 학술지에 기고한 연구자료를 독자의 의견을 반영하기 위해 수정요청을 받은 상황이다. 해당 연구자료를 수정하는 방법에는 몇 가지 방법이 있는데, 가령 원본자료를 바꾸는 대신, 당신의 원본자료가 담긴 저장소에다 '수정본'이라는 브랜치를 새로 생성할 수 있다. 이 브랜치에서 독자들의 의견을 반영하기 위한 새로운 작업('변경작업')을 한다. 작업이 완료된 후, 수정본 브랜치를 원본 브랜치('master' 브랜치로 불린다)와 병합한 후, 변경작업내용이 반영된 연구자료를 제출한다.

  2. 버그가 확인되거나 누락된 기능이 발견되는 것은 소프트웨어 개발 분야에서 자주 있는 일이다. 이 사례에서 어떤 소프트웨어는 이미 유저들이 신뢰하고 사용하는 안정된 제품사용 단계에 있다. 그러한 이유로 당신은 버그를 고치거나 기능을 추가하기 위해서 당장 바로 메인 소프트웨어(이하 '제품')의 코드를 변경할 수 없다. 이 때 'hotfix' 또는 'feature'라는 이름의 브랜치를 생성하고, 이 브랜치 안에서 위의 문제들을 해결한 후에 해당 제품의 다음 버전으로서 원본 브랜치와 병합한다. 이를 통해, 버그를 고칠 때 기존의 작성된 다른 사람의 코드를 망가뜨릴 수 있는 사고를 미연에 방지할 수 있다.

<br>

## 브랜치에서 사용되는 명령어들

아래에는 **`branch`**, **`checkout`**, **`merge`** 세 개의 명령어들이 무엇을 하는지 알기 위해 여러분들이 직접 시도해볼 수 있는 코드들이 일련의 작업 순서대로 나열되어있다.

```
cd ~/Desktop
mkdir git-branches
cd git-branches
git init # 깃으로 관리를 시작
git add .
git commit -m "First commit" # make the first commit
git branch testBranch # 브랜치 생성
git checkout testBranch # 브랜치를 옮김
## can also do git checkout -b testBranch
echo "Some text" > file.txt
git add file.txt
git commit -m "Added a file with text"
git checkout master
echo "Text in another file" > new-file.txt
git add new-file.txt
git commit -m "Added another file"
git log --graph --oneline --decorate --all
# 'aliases' 사용해서 위와 같이 긴 명령어를 아래처럼 축약할 수 있다.
git config --global alias.lg 'log --graph --oneline --decorate --all'
git merge testBranch
git lg # 위에서 긴 명령어를 'lg'로 축약함
git branch -d testBranch # 브랜치를 삭제
```

### 명령어 설명

- cd - 디렉토리 변경
- directory - 폴더와 같은 개념
- mkdir - 디렉토리 생성
- echo - 화면에 메세지를 표시
- git init - 깃 저장소를 시작하거나 초기화
- git add - 파일을 staging 지역에 위치시킴으로써 깃이 해당 파일을 추적할 수 있게 함
- git commit - staging에 있는 파일을 히스토리로 보냄
- git log --graph --oneline --decorate --all - 저장소와 브랜치에 있는 커밋 내역(commit history)을 하나의 라인으로서 보기
- git branch - 다른 브랜치와 구별되는 파일들을 갖고 있는 커밋 히스토리 라인
- git checkout - 다른 브랜치로의 이동
- git merge - 브랜치들을 병합
