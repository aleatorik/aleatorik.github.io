---
layout: post
title: REST API 이해를 돕기 위한 쉬운 설명
category: Web
tags: Web
---

<br>

# REST API란

<br>
**정보를 주고받는 form,형식**
~~(어떤 기술이나 제품이 아님)~~

일상에서 접하는 API 중에는
TV 리모컨, 자판기 버튼, 컴퓨터 키보드/마우스 -> 인터페이스(기계와 인간의 소통창구) 등이 있다.

## 소프트웨어 영역에서는?

프로그램을 원하는대로 제어하고 정보를 볼 수 있도록
버튼,스크롤바,슬라이더,브라우저 창 소프트웨어 장치들이 마련되어있음 -> UI

**기계와 기계, 소프트웨어와 소프트웨어 사이의 수 많은 요청과 정보 교환에 필요한 소통창구 => API**

---

### _예시: 기상청 서버와 기상청에서 제공된 정보를 사용하는 프로그램들_

프로그램이 기상청에게 정보를 요청하는 지정된 형식
`"date:191031|place:seoul|which:temperature"`
이렇게 표시해서 이 주소로 정보를 요청하면 "17degree" 이렇게 답이 올거라는 메뉴얼

**이처럼 소프트웨어가 다른 소프트웨어로부터 지정된 형식으로 요청, 명령을 받을 수 있는 수단을 API(Application programming interface)라고 한다.**

네트워크 상에만 api가 있는 것은 아니다

로컬 웹브라우저는 Web Api를 통해 자바스크립트로부터 특정 동작들을 지시 받는다

윈도우 운영체제에서는 시스템이나 하드웨어에 대한 지식 없어도
지정된 명령어로 윈도우에서 동작을 수행할수 있도록 소프트웨어를 짤 수 있는 Widonws API를 제공. (이 함수를 넣으면 윈도우가 이렇게 해준다를 알면 개발자는 그 명령어들로 코드를 짜면 됨)

---

## 그럼 REST API란?

프론트엔드 웹에서 서버에 데이터를 요청하거나
배달 앱에서 서버에 주문을 넣거나 하는 등이
REST란 형식의 API의 예시이다. (과거의 SOAP이란 복잡한 형식을 대체한 것)

가장 중요한 특성은 **각 요청이 어떤 동작이나 정보를 위한 것인지를 그 요청의 모습 자체로 추론 가능하다는 것.**

포인트는 서비스를 개발자 혼자 만드는게 아니기에
해당 API를 사용해서 제품을 만들 **다른 개발자들이 RESTful하게 만든 API를 통해 요청을 보내는 주소만으로도 대략 이게 뭘하는 요청인지 파악이 가능해야함.**

---

### _예시: 학원 DB에게 정보를 보내달라는 요청을 할 때_

https://(도메인)/classes -> 이처럼 classes를 보고 아마도 학원의 반들 목록을 받아오는 요청임을 짐작가능

```
{
"results" : [
		{"idx": 1, "name": "예비반"},
		{"idx": 2, "name": "중급반"},
		{"idx": 3, "name": "고급반"},
	    ]
}
```

`https://(도메인)/classes/2`
_그 반들 중 인덱스 번호가 이 숫자인 반의 정보가 오는 것 역시 짐작 가능_

`https://(도메인)/classes/2/students`

```
{
"results" : [
		{"idx": 1, "name": "홍길동", "gender: male"},
		{"idx": 2, "name": "김철수"},"gender: male"},
		{"idx": 3, "name": "김미애"},"gender: female"},
	    ]
}
```

`https://(도메인)/classes/2/students/1`

```
{
"results" : [
		{"idx": 1, "name": "홍길동", "gender: male"},
	    ]
}
```

**위 코드처럼 자원을 구조와 함께 나타내는 이런 형태의 구분자를 URI라고 한다**
위의 예시코드는 CRUD 중 READ에 해당함.

한 편, **서버에 REST API로 요청을 보낼 때는 HTTP규약에 따라 신호를 전송.**
우편에도 택배,등기,일반우편 등의 다양한 형식이 있듯이, HTTP로 요청을 보낼 때도 여러 **메소드**가 있음 (GET, POST, PUT, DELETE 등등)

### POST, PUT, PATCH에는 BODY라는 주머니가 있어서 GET, DELETE보다 정보를 많이 그리고 비교적 안전하고 감춰서 실어보낼 수 있다.

**GET- 정보조회, POST(create)- 새로운 정보를 추가**
ex:) `http://(도메인)/classes/2/students`를 날리고 BODY에 새 학성 정보를 넣는다 -> `{"idx":11, "name": "이순신", "gender": "male"}`,
(하지만 위의 인덱스는 보통 정보가 추가되면서 생성되기 때문에 POST에는 안 넣어도 되지만 이 인덱스를 가진 학생의 정보가 변경된 경우는 PUT 메소드로 URI에 변경할 학생의 인덱스까지 명기한 다음에 보내야한다.

`http://(도메인)/classes/2/students/14`
`{"idx":14, "name": "강감찬", "gender": "male"}` <- 이처럼 업데이트된 정보를 BODY에 실어 보낸다.

통상적으로 put은 정보를 통재를 갈아끼울 때, patch는 정보 중 일부를 특정 방식으로 변경할 때 사용

어떤 학생이 그만두면 DELETE를 사용.

마지막으로, POST로도 CRUD 기능을 아래처럼 사용할 수 있지만,

- POST http://(도메인)/classes/2/students/create
- POST http://(도메인)/classes/2/students/read
- POST http://(도메인)/classes/2/students/update
- POST http://(도메인)/classes/2/students/delete

구분을 위해 URI에 이들의 동작까지 명기해야 할 것이다.
이는 보기에 깔끔하지 않기에 이런 것을 지양하기 위해 **REST 규칙은 URI는 동사가 아닌 명사**들로 이루어져야 한다는 게 있다.

<br>

## 간단히 요약하면

REST API란 HTTP요청을 보낼 때, 어떤 URI에 어떤 메소드를 사용할 지(+기타) 개발자들 사이에 널리 지켜지는 약속. 단 형식이기 때문에, 기술(언어,프레임워크,라이브러리)에 구애받지 않는다. 즉 앱이든 웹이든, 어떤 언어로 만들든간에 소프트웨어간 HTTP로 정보를 주고받는 부분이 있다면, 위의 형식, 규칙들을 준수해서 RESTful한 서비스를 만드는 게 중요하다.

위의 내용은 RESTful API에 기초에 해당하는 내용이기에
더 자세한 것은 'restful api design guidelines'같은 키워드로 검색해보기를 바란다.

용도에 따라 REST API의 대안으로 떠오르는 GraphQL도 알아보면 좋을 것 같다.
