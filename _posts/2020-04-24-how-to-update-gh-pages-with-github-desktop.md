---
layout: post
title: 코드 변경 시, Github-page에 업데이트 하는 순서(feat. Github desktop)
category: Git
tags: Git
---

아래의 설명은 Github-Desktop 이라는 GUI 기반 프로그램 사용을 기준으로 함.
<br>

```
1. 에디터에서 코드수정
2. Current Branch를 gh-pages에서 master로 변경
3. Commit 클릭
4. Current Branch를 master에서 gh-pages로 변경
5. 상단 바 Branch 메뉴에서 Update from master를 실행
6. Current Branch를 master로 변경 후 Push origin을 클릭
7. Current Branch를 gh-pages로 변경 후 마찬가지로 Push origin 클릭
```

4번 단계에서 에디터로 보면 코드 변경 전의 모습으로 돌아간다. 이는 gh-pages branch가 master branch보다 뒤에 있기 때문이며,
5번단계에서 update from master를 실행하면 두 브랜치는 같은 시점에 놓이게 되므로 에디터에서도 코드변경 후 모습으로 바뀐다.

<br>
추가로, 로컬작업영역에서는 잘 작동되는 것이 gh-pages에서는 에러가 나는 경우가 종종 있는데 대표적인 예로는

- gh-pages는 **index.html**이 없으면 실행되지 않음

* 작업폴더 내의 images나 css 폴더의 이름의 **앞글자가 대문자**인 경우('I'mages, 'C'ss)
