---
layout: post
title: git rebase & sqaush 사용법과 명령어
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

<br>
프로젝트 협업 상황에서 git merge형태의 작업 히스토리 관리 방식에서 git rebase 방식으로
바꿈으로써 merge에 따른 수 많은 커밋들을 '압축'하고 꼭 필요한 커밋과 메세지(히스토리)만 남겨,
프로젝트 git log 유지보수를 용이하게 할 수 있다.

이를 위한 순차적인 깃 명령어들과 주의사항을 아래와 같이 정리하면 다음과 같다.

## **rebase 작업을 위한 전제조건**

1. 본인 작업 브랜치 history에는 저장이 안되어있는데 마스터 브랜치의 파일은 변경되어있는 경우
   즉, 로컬마스터에서의 충돌이 없는 상태여야함.

2. 다른사람과 공유하지 않은 커밋들에 대해서만 rebase 해야함
   git pull을 한 뒤에 그 이후에 만들어진 커밋들에 대해서 리베이스 작업을 하고
   깃 푸시를 하는데, 깃 푸시를 한 다음에는 그 푸시를 통해서 이미 올라가서 다른사람들이 공유했을 만한 것들은
   손대면 안 된다.

---

```
1. 로컬 마스터 브랜치와 최신화
$ git checkout master
$ git pull origin master

! 현재 시점에서 본인 작업브랜치 내용이 리모트 마스터의 내용과 다른게 없다면,
본인 작업 브랜치에서 바로 pull 받아도 무방.
(현재 브랜치가 본인 작업 브랜치 상태에서) git pull origin master

(하지만 다른게 있다면, 그 부분은 pull 할 시 사라짐!)


2. 본인 작업 브랜치에 git 변경사항들을 모두 add/ commit 한 뒤에
$ git add
$ git commit


3. 현재 본인 작업 브랜치에서 rebase 시작
$ git checkout 작업브랜치이름
$ git rebase -i master


4. (여기서 터미널 환경이 바뀌는데)
맨위에 'pick'을 빼고 난 나머지 pick을 's'로 바꾼다(이게 squash 명령어)
그리고 :wq(세미콜론 + wq입력)로 저장 후 해당 화면에서 빠져나온다.


5-1. conflict 처리 단계
rebase가 4번단계에서 끝나면, conflict가 일어나거나 commit 메세지를
입력하라는 text 들이 뜨게된다.
conflict는 이전에 merge 관련 이벤트를 처리하듯 해결하고,
$ git add .
$ git rebase --continue


5-2. 4번단계 후 conflict가 없다면
(--abort, --continue 명령어 사용할 필요가 없는 경우)
4번단계에서 :wq 입력 후 다른 터미널 환경으로 바로 이동된다.

거기서 '#' 표시된 부분은 모두 주석처리된 부분이므로 신경쓰지말고
본인이 rebase, squash하여 압축한 그 커밋에 대한 메세지를 작성한 다음에
:wq로 동일하게 빠져나온다.


6. 마스터로 git push

$ git push origin 작업브랜치이름 --force

(--force 하는 이유는 아래와 같다)
rebase과정을 통해 수정된 commit을 remote 저장소에 push 하면 에러 발생.
이유는 rebase sqaush 등을 통해 여러개의 히스토리 commit을 인위적으로 합치는 과정을 거쳐
git history를 수정했기 때문.

인위적으로 history가 수정된 상태인 branch에 대해 --force 옵션을 더하면
remote 저장소에 원하는 branch를 반영할 수 있게된다.
```
