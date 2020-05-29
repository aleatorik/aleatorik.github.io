---
layout: post
title: 내 컴퓨터에서 작업한 내용을 원격저장소로 업로드하기
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

### ~~(Git 프로그램이 PC에 설치 되어있는 가정 하에 진행)~~

1. **깃허브 상의 저장소 주소(~~깃허브 주소창 위의 URL 아님!~~)를 복사한다**

   ![](/public/img/1.jpg)

2) **깃 디렉토리 생성(관리 할 프로젝트가 위치 할 디렉토리)**

   ```
   git init
   ```

3) **깃허브 상에 있는 저장소를 PC로 복제(clone)**

   ```
   git clone git@github.egoing/welcome.git .
   // 'clone'다음에 복사한 주소 붙여넣음
   // 마지막 '.' <- 현재디렉토리(위치)를 말함
   ```

4) **(저장소 내 코드 수정 후) 마지막 버전 이후에 내가 수정한 것이 무엇인지 보여주기**

   ```
   git diff
    //몇 번째 줄의 코드가 바뀌고 삭제되었는지 등 파악가능
    git status
    //해당 파일이 staged,nonstaged 중 어느 곳에 현재 위치하는지 파악할 때 주로 사용
   ```

5) **수정한 내용을 포함하여 버전 만들기(commit 하기)**

   ```
   git add 수정한 파일명
    // ex) git add file3.txt
    git commit -m "커밋메시지(작업내용)"
    // 수정된 내용을 '커밋메시지'라는 이름의 버전으로 만들기
    git log
    // 깃 히스토리 열람
   ```

6) **컴퓨터에서 만든 버전을 깃허브로 업로드해서 두 개의 상태가 같도록 동기화하기**

   ```
   git push
   ```

   <br>
   _참고자료: [클릭이동](https://opentutorials.org/module/4636)_
