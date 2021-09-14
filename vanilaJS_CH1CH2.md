# vanilaJS 2장

## 삼항연산자

<br>
삼항연산자: 특정 조건에 따라 text의 값이 달라야 하는 상황 등 (ES6 문법X)

```
조건 ? true일때 : false일때
```

if) 라인이 길어진다면

```jsx
const array = [];
let text =
  array.length === 0 ? "배열이 비어있습니다" : "배열이 비어있지 않습니다.";

console.log(text);
```

if) 중첩해서 쓴다면 ⇒ 가독성이 떨어지기 때문에 if문 등으로 바꾸는 게 나음

```jsx
const condition1 = false;
const condition2 = false;

const value = condition1 ? "와우!" : condition2 ? "blabla" : "foo";

console.log(value);
```

## Truthy and Falsy

<br>

자바스크립트 문법은 아님 But! 알아둬야 하는 개념

**Truthy:** true 같은 것 (true로 인정되는 것들)

**Falsy:** false 같은 것 (false로 인정되는 것들)

[ex]

```jsx
//print 함수에 값을 넣지 않고 비워진 상태에서 실행될 경우
function print(person) {
  console.log(person.name);
}

const person = {
  name: "John",
};

print();
```

```
<오류 발생>
TypeError: Cannot read property 'name' of undefine
```

```jsx
//만약 object값이 주어지지 않았을 때 문제가 있음을 콘솔에 출력하려면
function print(person) {
  if (person === undefined) {
    return;
  }
  console.log(person.name);
}
```

```jsx
//만약 null값을 전달한다면
function print(person) {
  if (person === undefined) {
    console.log("person이 없네요");
    return;
  }
  console.log(person.name);
}

const person = null;
print(person);
```

```
<오류 발생>
TypeError: Cannot read property 'name' of null
```

```jsx
//print함수 조건 추가로 해결
function print(person) {
  if (person === undefined || person === null) {
    console.log("person이 없네요");
    return;
  }
  console.log(person.name);
}
```

⇒ person === undefined || person === null인 경우를 대비하여 코드 작성

1. **Falsy한 값 전부**

```jsx
//위와 같이 undefined나 null의 경우를 축약하면
function print(person) {
  if (!person) {
    console.log("person이 없네요");
    return;
  }
  console.log(person.name);
}
```

- WHY?

  undefined & null 모두 Falsy한 값 → !(Falsy) = true

```jsx
//Falsy한 값
console.log(!0);
console.log(!"");
console.log(!NaN);
//결과 = true
```

2. **Truthy한 값 예시** (Falsy 다섯 가지 이외의 모든 값)

```jsx
console.log(!3);
console.log(!"hello");
console.log(!["array?"]);
console.log(![]);
console.log(!{value: 1});
//결과 = false
```

💡팁

```jsx
const value = {a: 1};
const truthy = !!value;
//value = true, !value = false, !!value = truthy = true
```

## 단축 평가 논리 계산법

<br>
만약 파라미터에 제대로된 객체가 주어지지 않으면? 에러 발생

만약 animal 값이 제대로 주어지면 name을 조회하고 아니면 undefined를 반환하고 싶으면?

```jsx
//animal이 주어지지 않아도 에러 발생X -> 논리연산자 사용하면 코드 단축 가능
const dog = {
  name: "멍멍이",
};

function getName(animal) {
  if (animal) {
    return animal.name;
  }
  return undefined;
}

const name = getName();
console.log(name);
```

**&& 연산자로 코드 단축시키기**

```jsx
const dog = {
  name: "멍멍이",
};

function getName(animal) {
  return animal && animal.name;
}

const name1 = getName();
console.log(name1); // undefined

const name2 = getName(dog);
console.log(name2); // 멍멍이
```

→ A && B 연산자 사용 시 A가 Truthy한 값이면 B가 결과 값

A가 Falsy한 값이면 A가 결과 값

```jsx
//틀릴 수 있는 조건
console.log("hello" && "bye"); // a가 falsy한 5가지 내에 들어가지 않기 때문에 true로 가정하면 b 값이 출력: bye
```

**|| 연산자로 코드 단축시키기:** 어떤 값이 Falsy하다면 사용할 값을 지정해줄 때 유용하게 사용

```jsx
const namelessDog = {
  name: "",
};

function getName(animal) {
  const name = animal && animal.name;
  return name || "이름이 없는 동물입니다.";
}

const name = getName(namelessDog);
console.log(name); // 이름이 없는 동물입니다.
```

→ A || B 연산자 사용 시 A가 Truthy할 경우, A가 결과 값

A가 Falsy하다면 B가 결과 값

## 함수의 기본 파라미터

ex) 원의 넓이를 구하는 함수

- Math.PI = 원주율 파이 값

```jsx
function calculateCircleArea(r) {
  return Math.PI * r * r;
}

const area = calculateCircleArea(4);
console.log(area); // 50.26548245743669
```

**if) r 값을 넣어주지 않으면**

결과 → NaN(Not a Number, WHY? undefined \* undefined)

**r 값이 주어지지 않았다면 기본 값을 1로 설정하도록 설정**

- ES5

```jsx
function calculateCircleArea(r) {
  const radius = r || 1;
  return Math.PI * radius * radius;
}

const area = calculateCircleArea();
console.log(area); // 3.141592653589793
```

- ES6

```jsx
function calculateCircleArea(r = 1) {
  return Math.PI * r * r;
}
```

- 화살표 함수

```jsx
const calculateCircleArea = (r = 1) => Math.PI * r * r;
```

## 조건문 더 스마트하게 쓰기

**특정 값이 여러 값 중 하나인지 확인해야할 때**

```jsx
function isAnimal(text) {
  return (
    text === "고양이" || text === "개" || text === "거북이" || text === "너구리"
  );
}

console.log(isAnimal("개")); // true
console.log(isAnimal("노트북")); // false
```

→ 비교해야할 값이 많아질 수록 코드는 길어짐

<간단히 해결할 수 있는 방법>

- 배열을 만들고 배열의 includes 함수를 사용하는 것

```jsx
function isAnimal(name) {
  const animals = ["고양이", "개", "거북이", "너구리"];
  return animals.includes(name);
}
```

- 배열 선언하는 것 생략 & 화살표 함수로 작성

```jsx
const isAnimal = (name) => ["고양이", "개", "거북이", "너구리"].includes(name);
```

⇒ 코드가 짧다고 해서 무조건 좋은 것은 아니며 짧으면서도 읽었을 때 어떤 역할을 하는지 이해가 될 수 있어야 함

**값에 따라 다른 결과물을 반환해야할 때**

[ex]

- if문

```jsx
function getSound(animal) {
  if (animal === "개") return "멍멍!";
  if (animal === "고양이") return "야옹~";
  if (animal === "참새") return "짹짹";
  if (animal === "비둘기") return "구구 구 구";
  return "...?";
}

console.log(getSound("개")); // 멍멍!
console.log(getSound("비둘기")); // 구구 구 구
```

- switch/case문

```jsx
function getSound(animal) {
  switch (animal) {
    case "개":
      return "멍멍!";
    case "고양이":
      return "야옹~";
    case "참새":
      return "짹짹";
    case "비둘기":
      return "구구 구 구";
    default:
      return "...?";
  }
}

console.log(getSound("개")); // 멍멍!
console.log(getSound("비둘기")); // 구구 구 구
```

→ return할 때에는 break 생략 가능

- 깔끔하게 코드 작성하는 방법

```jsx
function getSound(animal) {
  const sounds = {
    개: "멍멍!",
    고양이: "야옹~",
    참새: "짹짹",
    비둘기: "구구 구 구",
  };
  return sounds[animal] || "...?";
}

console.log(getSound("개")); // 멍멍!
console.log(getSound("비둘기")); // 구구 구 구
```

- 값에 따라 실행해야 하는 코드 구문이 다를 때? 객체에 함수를 넣으면 돼

```jsx
function makeSound(animal) {
  const tasks = {
    개() {
      console.log("멍멍");
    },
    고양이() {
      console.log("고양이");
    },
    비둘기() {
      console.log("구구 구 구");
    },
  };
  if (!tasks[animal]) {
    console.log("...?");
    return;
  }
  tasks[animal]();
}

getSound("개");
getSound("비둘기");
```

## 비구조화 할당 문법

비구조화 할당 문법 ⇒ 객체 안에 있는 값을 추출해서 변수 or 상수로 선언 가능

```jsx
const object = {a: 1, b: 2};

const {a, b} = object;

console.log(a); // 1
console.log(b); // 2

// 함수의 파라미터에서도 비구조화 할당 가능
const object = {a: 1, b: 2};

function print({a, b}) {
  console.log(a);
  console.log(b);
}

print(object);
// 1
// 2

// b 값이 주어지지 않았다고 가정
print(object);
// 1
// undefined
```

**비구조화 할당 시 기본값 설정**

```jsx
// 함수의 파라미터
const object = {a: 1};

function print({a, b = 2}) {
  console.log(a); //
  console.log(b);
}

// 함수의 파라미터에서만 가능한 것은 X
const object = {a: 1};

const {a, b = 2} = object;

console.log(a); // 1
console.log(b); // 2
```

**비구조화 할당 시 이름 바꾸기**

```jsx
const animal = {
  name: "멍멍이",
  type: "개",
};

// nickname != name: 비구조화 할당 사용할 수 X
// 대신 :을 사용해서 이름을 바꿀 수 있음
// 'animal 객체 안에 있는 name을 nickname이라고 선언하겠다'
const {name: nickname} = animal;
console.log(nickname); // 멍멍이
```

**배열 비구조화 할당:** 객체 뿐만 아니라 배열에서도 가능, 배열 안에 있는 원소를 다른 이름으로 새로 선언해주고 싶을 때 사용하면 유용

```jsx
const array = [1, 2];
const [one, two] = array;

console.log(one); // 1
console.log(two); // 2
```

- 기본값 지정 가능

```jsx
const [one, two = 2] = array;
```

**깊은 값 비구조화 할당:** 객체의 깊숙한 곳에 들어있는 값을 꺼내는 방법

```jsx
const deepObject = {
  state: {
    information: {
      name: "velopert",
      languages: ["korean", "english", "chinese"],
    },
  },
  value: 5,
};
```

if) name, languages, value 값을 밖으로 꺼내주고 싶다면?

- 비구조화 할당 문법 두 번 사용

```jsx
const {name, languages} = deepObject.state.information;
const {value} = deepObject;

// [1] 이 코드와
const extracted = {
  name,
  languages,
  value,
};

// [2] 이 코드는 동일
const extracted = {
  name: name,
  languages: languages,
  value: value,
};

console.log(extracted); // {name: "velopert", languages: Array[3], value: 5}
```

→ [1] key 이름으로 선언된 값이 존재하면 바로 매칭: ES6의 object-shorthand 문법

- 한 번에 모두 추출

```jsx
const {
  state: {
    information: {name, languages},
  },
  value,
} = deepObject;

const extracted = {
  name,
  languages,
  value,
};

console.log(extracted);
```

→ state나 information는 추출되지 않음

## spread와 rest 문법

ES6에서 도입

**spread 문법:** 객체 or 배열을 펼칠 수 있음 (...으로 구현)

⇒ 기존의 것을 건드리지 않고 새로운 객체를 만드는 것

```jsx
const slime = {
  name: "슬라임",
};

const cuteSlime = {
  ...slime, //
  attribute: "cute",
};

const purpleCuteSlime = {
  ...cuteSlime,
  color: "purple",
};

console.log(slime); //Object {name: "슬라임"}
console.log(cuteSlime); //Object {name: "슬라임", attribute: "cute"}
console.log(purpleCuteSlime); //Objcet {name: "슬라임", attribute: "cute", color: "purple"}
```

- 배열 가능

```jsx
const animals = ["개", "고양이", "참새"];
const anotherAnimals = [...animals, "비둘기"]; // '개', '고양이', '참새', '비둘기'
```

- 여러 번 사용 가능

```jsx
const numbers = [1, 2, 3, 4, 5];
const spreadNumbers = [...numbers, 1000, ...numbers]; // 1, 2, 3, 4, 5, 1000, 1, 2, 3, 4, 5
```

**rest:** 객체, 배열, 함수 파라미터에서 사용 가능

↔ spread와 생김새는 비슷하지만 역할이 매우 다름

- 객체에서의 rest: 비구조화 할당 문법에 함께 사용 (주로 rest 키워드 사용)

```jsx
const purpleCuteSlime = {
  name: "슬라임",
  attribute: "cute",
  color: "purple",
};

const {color, ...cuteSlime} = purpleCuteSlime;
console.log(color); //purple
console.log(cuteSlime); //Object {name: "슬라임", attribute: "cute"}

//attribute까지 없앤 객체
const {attribute, ...slime} = cuteSlime;
console.log(slime); //Object {name: "슬라임"}
```

- 배열에서의 rest: 배열 비구조화 할당을 통하여 원하는 값을 밖으로 꺼내고 나머지 값을 rest 안에 넣음

```jsx
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, ...rest] = numbers;

console.log(one); // 0
console.log(rest); // [1, 2, 3, 4, 5, 6]
```

\*단, 비구조화 할당 시에 거꾸로 인자를 넣을 수 X

```jsx
const [...rest, last] = numbers;
```

- 함수 파라미터에서의 rest: 함수의 파라미터가 몇 개가 될 지 모르는 상황에서 사용하면 유용

```jsx
// result 값 확인해보기
function sum(...rest) {
  return rest;
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // [1, 2, 3, 4, 5, 6]: 함수에서 받아온 파라미터들로 이루어진 배열

// sum() 구현하기
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const result = sum(1, 2, 3, 4, 5, 6);
console.log(result); // 21
```

**함수 인자와 spread**

- 파라미터: 함수에서 값을 읽을 때 그 값
- 인자: 함수에 값을 넣어줄 때 그 값

```jsx
function sum(...rest) {
  return rest.reduce((acc, current) => acc + current, 0);
}

const numbers = [1, 2, 3, 4, 5, 6];
const result = sum(
  numbers[0],
  numbers[1],
  numbers[2],
  numbers[3],
  numbers[4],
  numbers[5]
);

// 불편한 점 개선 후 인자에 spread 사용

const result = sum(...numbers);
console.log(result);
```

**퀴즈:** 함수에 n개의 숫자들이 파라미터로 주어졌을 때, 그 중 가장 큰 값을 알아내세요.

```jsx
function max(...rest) {
  return rest.reduce(
    (acc, current) => (acc > current ? acc : current),
    rest[0]
  );
}

const result = max(1, 2, 3, 4, 10, 5, 6, 7);
console.log(result);
```

## scope의 이해

**Scope:** 변수 or 함수를 선언하게 될 때 해당 변수 or 함수가 유효한 범위

1. Global Scope (전역): 코드의 모든 범위에서 사용 가능
2. Function Scope (함수): 함수 안에서만 사용 가능
3. Block Scope (블록): if, for, switch 등 특정 블록 내부에서만 사용 가능

[ex 1]

```jsx
const value = "hello!"; // Global Scope -> 어디서든 사용 가능

function myFunction() {
  console.log("myFunction: ");
  console.log(value);
}

function otherFunction() {
  console.log("otherFunction: ");
  const value = "bye!"; // Fuction Scope -> otherFunction에서만 유효 (Global Scope 선언된 value 값은 바뀌지 않음)
  console.log(value);
}

myFunction(); // myFunction: hello!
otherFunction(); // otherFunction: bye!

console.log("global scope: "); // global scope: hello!
console.log(value); //
```

[ex 2]

```jsx
const value = "hello!";

function myFunction() {
  const value = "bye!";
  const anotherValue = "world"; // myFunction() 밖에서는 anotherValue 조회 X
  function functionInside() {
    console.log("functionInside: ");
    console.log(value);
    console.log(anotherValue);
  }
  functionInside();
}

myFunction(); // functionInside: bye! world
console.log("global scope: "); // global scope:
console.log(value); // hello!
console.log(anotherValue); // 에러
```

[ex 3]

```jsx
const value = "hello!";

function myFunction() {
  const value = "bye!";
  if (true) {
    const value = "world";
    // const는 Block Scope로 선언, if문 같은 블록 내에서 새로운 변수 or 상수를 선언하면 해당 블록 내부에서만 사용 가능
    // 블록 밖의 범위에서 똑같은 이름을 가진 값이 있다고 해도 영향 X (= let으로 선언해도 동일)
    console.log("block scope: ");
    console.log(value);
  }
  console.log("function scope: ");
  console.log(value);
}

myFunction(); // block scope: world function scope: bye!
console.log("global scope: "); // global scope:
console.log(value); // hello!
```

- const로 선언 시 Block Scope, let도 마찬가지

[ex 4]

```jsx
var value = "hello!";

function myFunction() {
  var value = "bye!";
  if (true) {
    var value = "world";
    console.log("block scope: ");
    console.log(value);
  }
  console.log("function scope: ");
  console.log(value);
}

myFunction(); // block scope: world function scope: world
console.log("global scope: "); // global scope:
console.log(value); // hello!
```

- var로 선언 시 Function Scope

**Hoisting 이해하기**

Hoisting: 자바스크립트에서 아직 선언되지 않은 함수 or 변수를 "끌어올려서" 사용할 수 있는 자바스크립트의 작동 방식

[ex 1] Hoisting: 함수 선언되기 전에 작동하도록 끌어올려서 사용하는 방식

```jsx
// [1]
myFunction(); // 함수가 아직 선언되지 않았음에도 불구하고 정상적으로 작동

function myFunction() {
  console.log("hello world!");
}

// [2]
function myFunction() {
  console.log("hello world!");
}

myFunction();
// [1] 과 [2]는 동일하게 동작 ([1]에서 자바스크립트 엔진이 코드를 해석하는 과정에서 [2]와 동일하게 받아들임)
```

[ex 2]

```jsx
// [1]
console.log(number); // 오류 발생

// [2]
console.log(number); //undefined
var number = 2; // var으로 선언 시 hoisting

// [3]
var number;
console.log(number);
number = 2;

// [2]가 [3]처럼 동작
```

\*단, const와 let ⇒ hoisting 발생 X, 에러 발생

[ex 3]

```jsx
function fn() {
  console.log(a);
  let a = 2; // let으로 선언 시 hoisting X
}
fn(); // 에러 발생
```

→ hoisting

: 자바스크립트가 가지고 있는 성질

: 일부러 할 필요 X, 방지하는 것이 좋음

: hoisting 발생 코드는 이해가 어렵고 유지 보수 힘들며 의도치 않은 결과를 갖게 돼

<방지하기 위해서는,,>

- 함수: 선언 후 호출
- var 대신 const나 let 사용
