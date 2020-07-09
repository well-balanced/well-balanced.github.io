---
title: "[JavaScript] Array methods, 배열 함수"
excerpt: "JavaScript에서 유용하게 사용할 수 있는 배열함수에 대해서 알아보자."

categories:
    - development
tags:
    - JavaScript
    - js
    - array
    - array methods
---
![array methods](/assets/images/array.jpg)

> 해당 글은 유튜버 '드림코딩 엘리'님의 영상을 참조하여 공부하면서 작성하였습니다.


# JavaScript Array methods


## reverse

`reverse` 메소드는 배열의 순서를 뒤집어준다.
```js
const arr = [1, 2, 3]; 
const newArr = arr.reverse()
console.log(arr) // [3, 2, 1]
console.log(newArr) // [3, 2, 1]
```

## slice & splice

`slice` 메소드는 인자로 주어진 인덱스로 새로운 배열을 만들고 원본 배열의 항목들은 유지한다.

`splice` 메소드는 역시 인자로 주어진 인덱스로 새로운 배열을 만들지만, 기존 배열의 항목들을 삭제한다.

`slice`와 `splice`는 메소드명과 기능이 비슷해서 처음에는 좀 헷갈릴 수 있다. 아래 예제를 보자.

```js
const arr = [1, 2, 3, 4, 5];

const slicedArr = arr.slice(0,2);
console.log(slicedArr); // [1, 2]
console.log(arr); // [1, 2, 3, 4, 5]

const splicedArr = arr.splice(0,2);
console.log(splicedArr); // [1, 2]
console.log(arr); // [3, 4, 5]
```

## find

`find` 메소드는 callback function의 인자로 들어오는 항목들을 활용하여 가장 먼저 True를 리턴하는 값을 반환한다. 

```js
class Student {
    constructor(name, age, enrolled, score) {
        this.name = name;
        this.age = age;
        this.enrolled = enrolled;
        this.score = score;
    }
}

const students = [
    new Student('Merry', 24, true, 45),
    new Student('Ben', 25, false, 80),
    new Student('Jully', 28, true, 90),
    new Student('Woosik', 26, false, 66),
    new Student('Tom', 30, true, 88),
];

// find a student with the score 90
const result = students.find((student, index) => student.score === 90);

console.log(result); // Student {name: "Jully", age: 28, enrolled: true, score: 90}
```
## filter

`filter` 메소드는 단일값을 리턴하는 `find` 메소드와는 다르게 특정 조건에 `True`를 리턴한다면 해당하는 모든 값들을 배열형태로 리턴한다.

```js
// make an array of enrolled students
const result = students.filter((student) => student.enrolled);
console.log(result);
/*
[Student, Student, Student]
0: Student {name: "Merry", age: 24, enrolled: true, score: 45}
1: Student {name: "Jully", age: 28, enrolled: true, score: 90}
2: Student {name: "Tom", age: 30, enrolled: true, score: 88}
*/
```
## map

`map` 메소드는 배열 안에 있는 값들을 특정 조건을 주어서 각각 다른 값으로 변환하여 새로운 배열을 반환한다. 

```js
// make an array containing only the students' scores
const result = students.map((student) => student.score);
console.log(result); // [45, 80, 90, 66, 88]
```

## some

`some` 메소드는 배열의 요소 중에서 callback function의 리턴값 중 `True`가 되는 항목이 있는지 없는지 체크해준다.

```js
// check if there is a student with the score lower than 50
const result = students.some((student) => student.score < 50);
console.log(result); // true
```
## every

`every` 메소드는 `some` 메소드와 반대로 callback function에 인자로 들어오는 모든 값들이 `True`를 리턴하는지 확인하여 만약 그렇다면 `True`를 그렇지 않다면 `False`를 리턴한다.

```js
const result = students.every((student) => student.score < 50);
console.log(result); // false
```
## reduce

`reduce` 메소드는 배열에 있는 모든 값들을 누적하여 이를 리턴한다. 두번째 인자에 값을 넣으면 `Initial value`를 설정할 수 있다. 이 함수는 어떻게 활용하냐에 따라 높은 확장성을 가질 수 있다.

```js
// compute students' average score
const result = students.reduce((prev, curr, idx, arr) => prev + curr.score, 0);
const averageScore = result / students.length;
console.log(averageScore); // 73.8
```

## sort

`sort` 메소드는 배열의 항목들을 정렬해준다. 리턴값에 따라서 오름차순 혹은 내림차순으로 정렬할 수 있다.

```js
// sorted in ascending order by score
const result = students.map(student => student.score)
.sort((a, b) => a - b);
console.log(result) // [45, 66, 80, 88, 90]

// sorted in descending
const result = students.map(student => student.score)
.sort((a, b) => b - a);
console.log(result) // [90, 88, 80, 66, 45]
```

## 마치며
배열함수의 퍼포먼스에 대해서 정리해둔 좋은 글을 공유하고자 한다. 아래에 링크해놓으니 참고하고 싶은 사람은 들어가서 공부하면 좋을 것이다.

[https://daesuni.github.io/Loop-performance/](https://daesuni.github.io/Loop-performance/)