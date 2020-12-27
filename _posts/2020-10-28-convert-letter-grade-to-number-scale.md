---
layout: post
title: 알파벳 평점에서 숫자 단위 평점으로의 변환 알고리즘
category: Algorithm
tags: Algorithm
---

<br>
The first input variable name 'scores' has a number of properties and name of them can be different.
A value of each object in the scores has one of those letters. <br>
('A+', 'A', 'B+', 'B', 'C+', 'C', 'D+', 'D', 'F')

The second, 'requiredClasses' is an array consisting of following string. <br>
['Enlgish', 'Math', 'History', 'Art', 'Physics', 'German']

1. Convert letter grade to number scale in Object
2. If there's a property from requiredClass, which doesn't exist in scores, that property must be included with a value '0' in a new array. Otherwise a key and value set of properties is appended to the new array with their own data.

## Example :

A+ => 4.5 <br>
A => 4 <br>
B+ => 3.5 <br>
B => 3 <br>
C+ => 2.5 <br>
C => 2 <br>
D+ => 1.5 <br>
D => 1 <br>
F => 0 <br>

(1) 'scores'

```jsx
{
  'Enlgish': 'C',
  'Math': 'B',
  'History': 'B+',
  'Art': 'D+'
}
```

(2) 'requiredClasses'

```jsx
["Enlgish", "Math", "History", "Art", "Physics", "German"];
```

## My Solution

```jsx
const scores = {
  Enlgish: "C",
  Math: "B",
  History: "B+",
  Art: "D+",
};

const requiredClasses = [
  "Enlgish",
  "Math",
  "History",
  "Art",
  "Physics",
  "German",
];

const getExamResult = (scores, requiredClasses) => {
  const result = {};
  const gradeWithNum = {
    "A+": 4.5,
    A: 4.0,
    "B+": 3.5,
    B: 3.0,
    "C+": 2.5,
    C: 2.0,
    "D+": 1.5,
    D: 1,
    F: 0,
  };
  //console.log(Object.entries(gradeWithNum));

  for (let key in scores) {
    //console.log(scores[key]); //scores 객체의 value
    for (let i = 0; i < 9; i++) {
      if (scores[key] === Object.keys(gradeWithNum)[i]) {
        result[key] = Object.values(gradeWithNum)[i]; //숫자로 치환된 값을 result[key]에 넣기
      }
    }
    //console.log(result[key]);
  }

  for (let i in requiredClasses) {
    const courseName = requiredClasses[i];
    const currentSubject = Object.keys(scores); //이미 scores에 담긴 과목명
    //console.log(`현재 포함된 과목: ${currentSubject}`);
    if (!currentSubject.includes(courseName)) {
      console.log(currentSubject.includes(courseName));
      result[courseName] = 0;
      //
    }
  }
  return result;
};
getExamResult(scores, requiredClasses);
```

( expected output )

```jsx
 {
  'Enlgish': 2,
  'Math': 3,
  'History': 3.5,
  'Art': 1.5,
  'physics': 0,
  'German': 0
}
```
