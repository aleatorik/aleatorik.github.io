---
layout: post
title: github pull origin 관련 에러해결
category: Git
tags: Git
---

##### 에러내용 :

기존에 작업하던 repository에 추가 기능을 넣고 push했지만 원격저장소에 올라가질 않아
pull origin을 했더니 아래와 같은 에러가 발생했다.

```
error: The following untracked working tree files would be overwritten by merge:
Please move or remove them before you can merge.
Aborting
```

##### 해결사항 :

pull origin 명령을 했을 때, 기존에 있던(마지막에 푸시된)코드, 정확히 말하면 해당 저장소의 버전과 일치하지 않은 코드 또는 새로운 파일('untracked working tree files')이 잡히는 경우, 동기화하기 전에 제거하라는 뜻으로 보인다.

추가된 코드를 따로 복사하여 기존의 코드와 분리한 후, pull origin 명령을 실행. (에러발생X)
복사했던 코드를 다시 기존 코드에 붙인 후 commit 그리고 push하니 문제없이 추가된 코드가 원격저장소에 올라갔다.

기존 저장소 위에 코딩을 하기 전에 **'git pull'** 을 먼저할 것.
