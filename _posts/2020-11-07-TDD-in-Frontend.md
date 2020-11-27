---
layout: post
title: 프론트엔드에서 TDD를 어떻게 적용할 것인가
category: TDD
tags: TDD
---

# TDD란 무엇인가?

<br>

Test-driven development (TDD) is a software development process that relies on the repetition of a very short development cycle: requirements are turned into very specific test cases, then the code is improved so that the tests pass. This is opposed to software development that allows code to be added that is not proven to meet requirements.<br>

<div style="text-align: right"> 출처: https://en.wikipedia.org/wiki/Test-driven_development </div>
<br>

위키피디아의 정의에 따르면, TDD는 매우 짧은 개발주기를 반복하는 소프트웨어 개발 프로세스로, 상세한 테스트 케이스가 요구됨으로써 코드의 향상을 기대할 수 있고 최종적으로 테스트들이 통과되는 형식이다. TDD의 줄임말 'Test Driven Development' 단어 그대로 테스트 주도 방식의 개발방법론이고 Test First Programming 이라고도 부른다. 즉, 테스트 코드를 먼저 작성하면서 시작하는 것이다.

<br>

# 왜 TDD가 필요한가?

<br>

테스트란 단어를 들었을 때, 우리에게 일반적으로 생각나는 것은 '무언가 검증하는 것'이다.<br>
프로그래밍에서도 마찬가지이다. **유저가 어플리케이션을 이용할 때, 프로그래머가 설계한 대로 제대로 동작하는 지 확실시 하기 위해 테스트를 도입하는 것이다.**
그럼 여기서 벌써 유추할 수 있는 TDD의 중요한 핵심 중 하나는 프로그램 설계를 잘 해야 한다는 것이다. 우리가 **만들고자 하는 어플리케이션의 결과를 명확하게 알고, 그러기 위해 적어놓고(문서화) 또한 그 결과를 내는 과정을 공고하게 해두는 것**, 즉 '이러이러한 과정을 거치면 이렇게 나온다'를 코드로 옮겨 적는 것이 TDD이다.

<br>

알려진 바에 따르면, TDD의 도입은 비용이 매우 높다고 한다. 그래서 실제로 많은 기업에서 TDD의 필요성은 이미 잘 알고 있으면서도, 서비스 출시와 관련하여 현실적인 비용을 고려했을 때, TDD를 선뜻 적용하기 어려워한다고 들었다. TDD를 도입하지 않은 기존 프로젝트 진행 방식으로 소요되는 개발기간보다 훨씬 길어지고, 그에 따른 개발인력비용이 상승하기 때문이다. 그렇다면 **TDD는 처음부터 꼭 프로젝트 전체에 적용되어야 하는 것인가?**

<br>

# TDD를 어떻게 적용할 것인가?

_(필자가 본 바로는 TDD에 관한 많은 포스팅은 백엔드 사이드 관점에서 서술되어 있었다. TDD를 제창한 미국의 소프트웨어 개발자 Kent Beck가 기대한 '클린코드'를 그럼 TDD가 적용되는 백엔드 사이드에만 가능한 것인가? 당연히 아닐 것 같다! 그래서 이 포스트에서는 프론트엔드 개발 관점에서 TDD를 적용하는 것에 관해 글을 이어나갈 것이다.)_
<br>

## TDD에서 중요한 포인트(정리)

- 코드 테스팅의 첫 번째 목적은 코드 리팩토링 시 테스트를 다시 짜지 않기 위해 유지보수를 용이하게 하는 것.<br>(Ease of maintenance, not having to rewrite tests when you refactor)
- 코드 테스팅의 두 번째 목적은 테스트가 fail 시, 통과하지 못한 테스트들에 대한 간편한 진단에 있다.<br>왜냐하면, 우리는 테스트 실패 시 원인분석을 위해 테스트 코드나 프로덕션 코드를 세세히 파고드는 데 많은 시간을 소모하길 웒치 않기에..<br>(Easy diagnosis of failing tests)
- 테스트 작성의 전제조건은 요구사항이 명확해야 함(역으로도 성립, 테스트를 통해 요구사항이 더 명확해짐)
- 의존성이 생기지 않게 해야 테스트를 쉽게 작성 가능
- 컴포넌트를 작게 작게 만들어야 테스트가 용이해진다
- 자주 바뀔만한, 가령 UI적인 부분은 테스트 하지 않는다
- 테스트를 해야하는 부분과 하지 않아도 될 부분을 구분하고, 테스트 할 부분을 늘려가는 것이 바람직하다
- 프로그램의 구조가 좋으면 테스트가 훨씬 수월하다
- 최근의 프론트엔드 프레임워크는 개발을 쉽고 용이하게 할 뿐 아니라 테스트 역시 수월하게 해준다
- TDD의 최종목표는 한 마디로 '잘 동작하는 클린코드'이다.
- 올바르게 동작하는 경우에 어떤 결과를 내는가를 테스트코드로 명확히 적는 것이다
- TDD를 통해 기대할 수 있는 두 가지 장점은 '품질'과 '유연함'이다
- 각 테스트코드가 예제(examples)로서 스펙(specification)을 더욱 공고히 함으로써 품질이 향상된다
- 프로젝트에 있어서 먼저 테스트코드를 작성하면 의존관계라든가 잠재적인 복잡한 문제들을 일찍 발견할 수 있다.
- 완성된 하나의 어플리케이션이 거대한 프로그램이라면, 유닛 테스트코드는 하나의 굉장히 작은 프로그램이다.

(마지막 업데이트: 2020.11.25)
