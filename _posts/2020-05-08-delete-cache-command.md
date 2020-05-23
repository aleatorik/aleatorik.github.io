---
layout: post
title: 깃 캐시(Cache) 삭제 명령어
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

<br>
터미널에서 아래의 명령어로 캐시 삭제를 수행할 수 있다.

```

git rm -r --cached .
git add .
git commit -m "cache clear"

```

삭제 명령어인 만큼 위의 동작을 실행 전 로컬과 원격 저장소 동기화를 해주는 것이 안전할 것을 보임
