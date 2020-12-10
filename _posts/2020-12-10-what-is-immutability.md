---
layout: post
title: 불변성이란 무엇이고 왜 중요한가?
category: Javascript
tags: Javascript
---

## 들어가기에 앞서

불변성이라는 단어를 들었을 때 떠오르는 건 '데이터'(원본 유지), '상태의 변경' 등이다.
어떤 데이터가 있을 때, 그 데이터를 불변하게 하여 원본이 훼손되는 것을 막는다는 것이 포인트다.

아래의 예시 코드의 결과를 예측할 수 있다면, 불변성을 어느정도 잘 이해한 것으로 생각해도 될 것이다.

```jsx
var n1 = 1;
var n2 = 1;
console.log(n1 === n2);
=> true입니다. 당연합니다.

var o1 = {name:'kim'}
var o2 = {name:'kim'}
console.log(o1 === o2);
=> false 입니다. 조금 애매하죠. JavaScript는 값이 바뀌지 않는 원시 데이터 타입과 값이 바뀔 수 있는 객체를 다르게 취급합니다.

var o1 = {name:'kim'}
var o2 = o1;
o2.name = 'lee';
console.log(o1.name);
=> lee 입니다. o1은 영문도 모르고 자신이 가르키고 있는 name의 값이 바뀌어 버렸습니다.

var o1 = {name:'kim'}
var o2 = Object.assign({}, o1); // 빈 객체에 o1을 복사합니다.
o2.name = 'lee';
console.log(o1.name);
=> kim입니다. o2를 변경해도 o1이 영향을 받지 않습니다. o2에 대해서 o1은 불변한 상태를 유지할 수 있게 됩니다.

var o1 = {score:[1,2]}
var o2 = Object.assign({}, o1);
o2.score.push(3);
console.log(o1.score)
=> [1,2,3] 입니다. 영문도 모르고 o1이 또 바뀌었습니다. score는 객체의 일종인 배열이기 때문입니다.

var o1 = {score:[1,2]}
var o2 = Object.assign({}, o1);
o2.score = o2.score.concat(); // 배열을 복사합니다.
o2.score.push(3);
console.log(o1.score)
=> [1,2] 입니다.

다른 방법도 있습니다. 몽땅 다 복사를 하는 것입니다.
var o1 = {score:[1,2]}
var o2 = JSON.parse(JSON.stringify(o1));
o2.score.push(3);
console.log(o1.score)
=> [1,2] 입니다.

원본이 바뀌지 않게 조심하는 것도 좋지만, 원본이 아예 안 바뀌게 하는 것도 가능합니다.
var o1 = {name:'kim'}
Object.freeze(o1);
o1.name = 'lee';
console.log(o1.name);
=> 'kim' 입니다.

하지만 객체는 이게 안됩니다.
var o1 = {score:[1,2]}
Object.freeze(o1);
o1.score.push(3);
console.log(o1.score);
// [1,2,3] 입니다.

방어적으로 냉동을 해야 합니다.
var o1 = {score:[1,2]}
Object.freeze(o1);
Object.freeze(o1.score);
o1.score.push(3);
console.log(o1.score);
// 변경이 안됩니다. 심지어 항의성 에러를 발생시켜버립니다.
```

## 불변성을 이해하기 위한 배경지식

상태의 변경이라는 행위를 제대로 이해하기 위해서는 **컴퓨터가 값을 어떤 방식으로 메모리에 저장하고 접근**하는지에 대한 간단한 지식이 필요하다.

변수라는 것은 메모리에 저장되어 있는 어떠한 값에 접근하는 일종의 단축어같은 개념이며, 만약 변수가 없다면 우리는 일일히 0x0018fa와 같은 메모리 주소를 사용하여 메모리에 값을 저장할 공간을 마련하고 값을 저장하거나 접근해야한다는 것이다. 만약 필자가 a = 2처럼 해당 변수의 값을 다시 할당한다면, 0x0018fa라는 주소를 가진 메모리 공간에 저장되어 있는 값을 변경하는 것이며, 상태를 변경하는 행위라고 말할 수 있는 것이다.

그렇다면 우리가 변수를 재할당하지만 않는다면 불변이라는 개념을 지킬 수 있는 것일까?

No

**값에 의한 호출**과 **참조에 의한 호출**은 특정 컨텍스트에서 다른 컨텍스트에게 변수를 넘길 때 어떤 방식으로 값을 넘겨줄 것인지에 대한 방법들이다. 컨텍스트 간 변수를 넘기는 상황은 함수 외부의 스코프에서 함수에게 인자를 넘겨주는 상황으로 많이 표현되며, 또 실제로도 그런 상황이 대부분이다

자바스크립트에서 string, number, boolean과 같이 **원시 자료형을 사용하는 변수들은 모두 값에 의한 호출 방식**을 사용한다.

값에 의한 호출 방식은 함수의 인자로 어떤 변수를 넘길 때 해당 변수가 가지고 있는 값을 그대로 복사하여 함수에게 넘겨주는 방식을 의미하기 때문에,기존에 str 변수가 가리키고 있는 메모리 공간에 있는 값을 함수에 인자로 넘기는 것이 아니라 **그 값을 복사하여 새로운 메모리 공간에 저장하고나서 넘겨준다**는 뜻이다.

```jsx
const str = "Hello, World!";

function foo(s) {
  s = "재할당합니다";
  return s.substring(0, 2);
}

foo(str);
console.log(str);
```

```
Hello, World!
```

foo 함수는 인자로 넘어온 변수에 값을 재할당했음에도 함수 외부에 있는 str 변수의 값은 변하지 않았다.

즉, 불변성을 유지한다는 것은 단순히 “함수의 인자를 변경하지 않는다”라던가 “변수를 재할당하지 않는다”는 개념이 아닌 것이다. 포인트는 **메모리에 이미 담겨있는 값을 변경하지 않는 것**이다.

함수의 인자로 변수를 넘길 때 값을 복사하여 새로운 공간에 저장한 후 넘겨주는 값에 의한 호출 방식과 다르게, **참조에 의한 호출 방식은 “변수가 가리키고 있는 메모리 공간의 주소”를 넘기는 방식**이다.

```jsx
function bar(a) {
  a.push("hi");
  return arr;
}
```

```jsx
const array = [];
bar(array);

console.log(array);
// ['hi']
```

즉, bar 함수의 인자로 받은 배열은 참조에 의한 호출 방식을 사용하는 객체이기 때문에, 함수 내에서 이 배열을 지지고 볶아 버린다면 원본 배열 자체가 지지고 볶아지는 것이다. 이 경우에는 메모리 공간에 저장되어있던 배열을 직접 변경해버리는 것이므로, 상태가 변경되었다고 말할 수 있고, 불변성이 깨져버린 것이다.

이 경우에는 메모리 공간에 저장되어있던 배열을 직접 변경해버리는 것이므로, 상태가 변경되었다고 말할 수 있고, 불변성이 깨져버린 것이다.

똑같이 함수의 내부에서 인자를 수정하는 행위지만 인자가 값에 의한 호출 방식을 사용하는 자료형인지 참조에 의한 호출 방식을 사용하는 자료형인지에 따라 결과는 큰 차이가 나기 때문에, 불변성을 지키고 싶다면 항상 이 점을 염두에 두고 코드를 작성해야한다.

## 불변성을 왜 유지 해야하는가?

결론적으로 말해서, **데이터를 불변하게 다루면 데이터들간의 간섭으로 인한 버그의 가능성을 낮출 수 있기 때문**.
즉 데이터의 무분별한 상태 변경을 막음으로써 개발자가 현재 프로그램이 어떻게 돌아가는지 변화를 추론하기가 수월해진다.

```jsx
let sayHi = "Hi";

function setName() {
  name = "daseul";
}

setTimeout(() => {
  sayHi = "Hallo";
}, 0);

setName();
console.log(`${sayHi}, ${name}`);
```

-> 이런 상황에서는 어디서 어떤 사람이 sayHi이라는 전역 변수의 상태를 변경했는지 추적이 거의 불가능하며, 갑자기 콘솔에 Hi, daseul이 아닌 good bye, daseul이라고 출력된다고 해도 전혀 이상할 것이 없다.

## 불변성을 유지하기위한 방법

1. 전역 변수를 남용하지 않는다.
   자바스크립트에서 전역변수의 사용을 아예 금지하는 컨벤션을 추천하는 것도 바로 이 이유이다.
2. 순수 함수를 사용하라.
   불변성을 유지하며 순수 함수를 사용한다는 것은 함수 외부의 상태에 접근하여 이미 메모리에 할당되어 있는 값을 변경하지 않는다는 의미이므로,<br>이렇게 예측하지 못한 상태의 변경을 방어할 수 있다.

```jsx
function convertToAlex(person) {
  const newPerson = Object.assign({}, person);
  newPerson.name = "Alex";

  return newPerson;
}

const daseul = { name: "Daseul" };
const alex = convertToAlex(daseul);

console.log(daseul);
console.log(alex);
{
  name: "Daseul";
}
{
  name: "Alex";
}
```

-> 변경된 convertToAlex 함수는 더 이상 인자로 받은 person 객체에 직접 접근해서 값을 수정하지 않는다. 다만 Object.assgin 메소드를 사용하여 person 객체와 동일한 구조를 가진 새로운 객체를 생성하고 name 프로퍼티를 Alex으로 변경한 후 반환할 뿐이다.

위의 과정을 ES6의 spread 연산자를 사용하면 더 간단한 문법으로 변경할 수 있다.

```jsx
function convertToAlex(person) {
  return {
    ...person,
    name: "Alex",
  };
}
```

이렇게 새로운 객체를 생성하게 되면 의도하지 않은 객체의 상태 변화도 방어할 수 있고 상태 변화를 추적할 수도 있게 된다. 왜냐하면 convertToAlex 함수가 뱉어낸 객체는 daseul 객체와는 전혀 다른, 새로운 객체이기 때문이다.

```jsx
console.log(daseul === alex);
// false
```

객체의 상태를 변화시킬때, “상태가 변화된 객체”를 새로 생성한다면 우리는 이전 상태를 가진 객체와 다음 상태를 가진 객체를 비교하며 false가 나온다는 사실을 이용하며 객체의 상태가 변화되었음을 알 수 있는 것이다.

이런 원리는 웹 프론트엔드의 UI 라이브러리인 리액트(React)에서 상태의 변화를 감지하는 데에도 사용되고 있는데, 리액트는 개발자가 setState와 같은 메소드를 사용하여 상태를 변경했을 때 Object.is 메소드를 사용하여 이전 상태와 다음 상태를 비교하고 두 객체가 같지 않다고 평가되면 상태가 변이되었다고 판단하고 컴포넌트를 다시 렌더한다.

또한 상태 관리 라이브러리인 리덕스(Redux) 또한 동일한 원리로 상태의 변화를 판단하기 때문에, 리듀서를 작성할 때는 기존 state 객체의 프로퍼티를 직접 변경하지 않고 새로운 객체를 생성해서 반환해야한다.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case SET_NAME:
      return {
        ...state,
        name: action.payload,
      };
    // ...
  }
}
```

### 이 주제와 관련한 키워드

| 메모리, 데이터 타입, 복사, 순수함수, 값에 의한 호출 방식, 참조에 의한 호출 방식

<br>

_출처: [오픈튜토리얼스](https://www.opentutorials.org/module/4075),
[블로그](https://evan-moon.github.io/2020/01/05/what-is-immutable/)_
