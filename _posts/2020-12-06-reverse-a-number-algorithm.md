---
layout: post
title: 숫자 뒤집기
category: Algorithm
tags: Algorithm
---

## Examples

```
x: 1234
return: 4321

```

```
x: -1234
return: -4321

```

```
x: 1230
return: 321

```

## My Solution

```jsx
const reverse = (x) => {
  let arr = x.toString().split("");
  let result = "";

  for (let i = arr.length - 1; i >= 0; i--) {
    result += arr.pop();

    if (result.includes("-")) {
      result = `-${result.slice(0, -1)}`;
    }
  }
  return parseInt(result);
};

let x = -1234;
reverse(x);
```

<br>
> 1. 주어진 숫자를 toString()메소드로 str타입으로 변경
> 2. '' 기준으로 배열에 담는다(split)
> 3. 순서를 뒤집어서 담을 빈 배열을 만든다
> 4. for loop로 안에 pop을 통해 뒤에서 부터 엘리먼트를 하나씩 또 하나의 변수에 담는다
> 5. 누적

<br>
## Another Solution

```jsx
function reverse(x) {
  let minus = false;

  if (x < 0) {
    x *= -1;
    minus = true;
  }

  let numText = x.toString();
  let result = "";

  for (let i = numText.length - 1; i >= 0; i--) {
    result += numText[i];
  }

  result = minus ? result * -1 : Number(result);

  return result;
}
```

### Note

- 변수를 최소한으로 선언하고, 기존 변수 선언자 (let)를 재활용(덮어씌우기)하여 여러 조건들을 만족시키기.
- 필요한 조건별로 변수를 계속 생성하게 되면 scope문제 발생확률이 높아지고, 그에 따라 console.log로 테스트도 많이 찍게된다.<br>
  (예시-> `result = -${result.slice(0, -1)}`; )
