---
layout: post
title: Pull request 삭제 방법
category: Git
tags: Git
---

<br>

# 들어가기에 앞서

<br>

어떤 이유로든 fork한 repo(repository)에 PR(Pull request)한 내용을 삭제하고 싶을 수 있다.
가령, 프로젝트 진행에 따라 일전에 한 커밋내용들이 더이상 유효하지 않을 수 있고 그것이 없는게 더 바람직할 수 도 있다.

하지만 안타깝게도 공식적으로 **본인이 PR한 내용을 삭제할 수 있는 방법은 없는 것**으로 알려져 있다.
repo 주인과 PR한 당사자는 PR을 'close'할 수는 있지만 이 경우, **커밋로그는 여전히 남아있다!**

이는 개발에서 발생하는 어떤 사건 또는 기록을 거부하거나 숨기는 것을 지양하는 깃허브 서비스 약관에 의거한 정책이라고 한다. 다만 민감하고 심각한 이슈와 관련하여 삭제가 필요한 예외적인 경우에는 깃허브 측에서 직접 해당 문제를 처리해준다고 하니*support@github.com*에 이메일을 넣어보는 것도 나쁘지 않을 것 같다.

<br>

# 깃허브의 이메일 기다리는 것 외에는 정말 방법이 없을까?

<br>

결론적으로 이 포스팅에서는 'close'했다는 내역 자체는 삭제 못하지만, **그 안의 모든 커밋로그를 지울 수 있는 방법**을 다룬다.

다행이도 `git revert` , `git rebase` 등등 이를 위한 여러가지 기술적인 차선책들이 인터넷 상에 많이 소개되어있지만, 본 포스팅에서는 필자가 직접 테스트 해 본 방법을 소개한다.

<br>

# PR의 모든 커밋로그를 삭제하는 방법

<br>

```jsx
1. 이미 해당 PR을 closed한 상태면 reopen 한다.

2. 로컬에서 checkout 명령어로 PR한 브랜치로 이동한다.

3. `git reset --hard` 명령어로
remote로 pushed된 모든 이 전 커밋들을 커밋 하기 전 상태로 돌려놓는다.

(어떤 특정 커밋로그까지만 삭제할 떄는 `git log` 통해서 해당 커밋의 id를 확인 후
`git reset --hard <sha1-commit-id>`를 실행한다)

4. `git push origin HEAD --force`로 기존의 모든 커밋이 푸시되기 전 상태를
remote로 푸시한다.

5. 본인 깃허브 계정으로 가서 PR을 날린 해당 repo를 삭제한다.
```

<br>

모든 로그가 아닌 **일부 로그만 지우고 싶은 경우**는 이 [링크](https://stackoverflow.com/questions/36168839/how-to-remove-commits-from-a-pull-request)를 참조하기 바란다.

<br>

#### Reference

[https://stackoverflow.com/questions/18318097/delete-a-closed-pull-request-from-github](https://stackoverflow.com/questions/18318097/delete-a-closed-pull-request-from-github)<br>
[https://articles.assembla.com/en/articles/2941346-how-to-delete-commits-from-a-branch-in-git](https://articles.assembla.com/en/articles/2941346-how-to-delete-commits-from-a-branch-in-git)
