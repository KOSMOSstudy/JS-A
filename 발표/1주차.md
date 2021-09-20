# vanilaJS 1장

[Codebox](https://codesandbox.io/) 사용하여 console에 "Hello JavaScript" 출력

## 변수

**변수:** 바뀔 수 있는 값 (한 번 값을 선언하고 나서 바꿀 수 있음)

변수 선언 시 let 키워드 사용

한 번 선언하면 똑같은 이름으로 선언할 수 없음

*단, 다른 블록 범위 내에서는 똑같은 이름으로 사용 가능

**상수:** 한 번 선언하고 값이 바뀌지 않는 고정된 값

상수 선언 시 const 키워드 사용

한 번 선언하면 똑같은 이름으로 선언할 수 없음

- 변수 선언하는 다른 방법?

  var ⇒ 똑같은 이름으로 여러 번 선언 가능

- var과 let의 차이?

  사용범위가 다름

- 구형 브라우저에서는 let과 const를 사용할 수 없어서 var 사용하게 될 수도 있으나 거의 없음

**데이터타입**

- 숫자
- 문자열(큰 or 작은 따옴표로 감싸서 선언)
- boolean(true, false)
- 없음(null: 값이 없다는 고의적 설정 & undefined: 값이 아직 설정되지 않은 경우)

## 연산자

**산술 연산자:** 사칙연산을 하는 연산자 (+, -, *, /, ++, —)

**대입 연산자:** 특정 값에 연산을 한 값을 바로 설정할 때 사용할 수 있는 연산자 (+=, -=, *=, /=, =)

**논리 연산자:** boolean 타입을 위한 연산자

- !: not → true는 false로, false는 true로
- &&: and → 둘 다 true일 때만 true, 나머지는 false
- ||: or → 하나라도 true일 때 true, 둘 다 false면 false

<연산 순서>

not → and→or

**비교 연산자:** 두 값을 비교할 때 사용

- ===: 타입까지 같은지 확인

- ==: 값만 같은지 확인(타입 검사X)

  ex) 1 == '1' : true, 0 == 'false': true, null == undefined: true

- !==: 타입까지 다른지 확인

- !=: 타입 검사X

- <, >

*주석:  / / or */ / *

*문자열 붙이기: +

## 조건문

- **if문**

  조건 만족 시 실행시킬 코드가 {}로 감싸져있음 ⇒ 코드블럭, 참일 때 코드 실행

- **if-else문**

  특정 조건이 만족할 때와 만족하지 않을 때 서로 다른 코드를 실행해야 된다면 사용

- **if-else if문**

  여러 조건에 따라 다른 작업을 해야할 때 사용

- **switch/case문**

  특정 값이 무엇이냐에 따라 다른 작업을 하고 싶을 때 사용

```jsx
switch("특정값"){
	case "값1":
		"실행할 식"
		break;
	case "값2":
		"실행할 식"
		break;
.
	default:
		"default 식"
}
```

⇒ case에 실행할 코드를 작성하고 마지막에 break 쓰지 않으면 그 다음 case의 코드까지 실행

⇒ default는 case로 준비하지 않은 값이 특정 값인 경우 실행

## 함수

**함수 :** 특정 코드를 하나의 명령으로 실행할 수 있게 하는 기능

- function 키워드: 함수 만들 때
- 매개변수: 함수가 어떤 값을 받을지
- return 키워드: 함수의 결과물 지정 & return 시 함수 종료

```jsx
function hello(name){
	console.log("Hello, " + name + "!");
} 
hello("javascript"); // "Hello, javascript!"
```

⇒ 위의 코드에서 사용한 문자열 연결 방법: +

⇒ ES6(js 버전)의 템플릿 리터럴 문법 사용으로 더 편하게 조합 가능

```jsx
function hello(name) {
	console.log(`Hello, ${name}!`);
}
hello("javascript");
```

**화살표 함수**

- fuction 키워드 대신 화살표(⇒) 사용
- 화살표 좌측 - 함수의 파라미터
- 화살표 우측 - 코드 블럭

```jsx
const add = (a, b) => {
  return a + b;
};

console.log(add(1, 2));
//위의 코드처럼 코드 블록 내부에서 바로 return 하는 경우 아래처럼 변환 가능
const add = (a, b) => a + b;
console.log(add(1, 2));
```

⇒ 여러 줄로 구성되어있는 경우는 코드 블럭을 만들어야 함

- 화살표 함수 vs 일반 function 함수

  : this가 다름

## 객체

**객체:** 변수 혹은 상수를 사용하게 될 때 하나의 이름에 여러 종류의 값을 넣을 수 있게 함

```jsx
const dog = {
	name: "멍멍이",
	age: 2
};
console.log(dog.name); //멍멍이
console.log(dog.age); //2
```

선언 시 { } 안에 원하는 값을 넣기 ⇒ 키: 원하는 값

- 키에 해당하는 부분: 공백이 없어야 함

  if) 공백 존재해야 한다면? "key with space": true

**함수에서 객체를 파라미터로 받기**

```jsx
const ironMan = {
  name: '토니 스타크',
  actor: '로버트 다우니 주니어',
  alias: '아이언맨'
};

const captainAmerica = {
  name: '스티븐 로저스',
  actor: '크리스 에반스',
  alias: '캡틴 아메리카'
};

function print(hero) {
  const text = `${hero.alias}(${hero.name}) 역할을 맡은 배우는 ${
    hero.actor
  } 입니다.`;
  console.log(text);
}

print(ironMan); //아이언맨(토니 스타크) 역할을 맡은 배우는 로버트 다우니 주니어 입니다.
```

**객체 비구조화 할당**

- print(): 파라미터로 받아온 hero 내부의 값을 조회할 때마다 hero.~ 입력

객체 비구조화 할당 문법 사용 시 → 더 짧고 간결하게 가능 (= 객체 구조 분해)

```jsx
function print(hero) {
  const { alias, name, actor } = hero;
  const text = `${alias}(${name}) 역할을 맡은 배우는 ${actor} 입니다.`;
  console.log(text);
}
//객체에서 값을 추출하여 새로운 상수로 선언하는 것 
const { alias, name, actor } = hero;
//파라미터 단계에서 객체 비구조화 할당 가능
function print({ alias, name, actor }) {
  const text = `${alias}(${name}) 역할을 맡은 배우는 ${actor} 입니다.`;
  console.log(text);
}
```

**객체 안에 함수 넣기**

```jsx
const dog = {
  name: '멍멍이',
  sound: '멍멍!',
  say: function say() {
    console.log(this.sound);
  }
};

dog.say(); //멍멍
```

함수 → 객체 안으로 들어가면 this = 자신이 속해있는 객체

```jsx
//함수 선언 시 이름 없어도 돼
const dog = {
  name: '멍멍이',
  sound: '멍멍!',
  say: function() {
    console.log(this.sound);
  }
};

dog.say(); //멍멍
```

객체 안에 함수를 넣을 때, 화살표 함수로 선언하면 제대로 작동 X

**WHY?**

: funtion으로 선언한 함수는 this가 제대로 자신이 속한 객체를 가리키게 되는데 화살표 함수는 그렇지 않음

**Getter 함수와 Setter 함수**

객체 내의 값은 수정 OK

Getter 함수 & Setter 함수 ⇒ 특정 값을 바꾸려고 하거나, 특정 값을 조회하려고 할 때 원하는 코드 실행 가능

- Getter 함수: 특정 값을 조회할 때 우리가 설정한 함수로 연산된 값 반환

  함수 앞 부분에 get 키워드

```jsx
const numbers = {
  a: 1,
  b: 2,
  get sum() {
    console.log('sum 함수가 실행됩니다!');
    return this.a + this.b;
  }
};

console.log(numbers.sum);
numbers.b = 5;
console.log(numbers.sum);
```

- Setter 함수: 특정 값을 바꾸려고 할 때

  함수 앞 부분에 set 키워드

```jsx
const numbers = {
  _a: 1,
  _b: 2,
  sum: 3,
  calculate() {
    console.log('calculate');
    this.sum = this._a + this._b;
  },
  get a() {
    return this._a;
  },
  get b() {
    return this._b;
  },
  set a(value) {
    console.log('a가 바뀝니다.');
    this._a = value;
    this.calculate();
  },
  set b(value) {
    console.log('b가 바뀝니다.');
    this._b = value;
    this.calculate();
  }
};

console.log(numbers.sum);
numbers.a = 5;
numbers.b = 7;
numbers.a = 9;
console.log(numbers.sum);
console.log(numbers.sum);
console.log(numbers.sum);

```

## 배열

객체: 한 변수 or 상수에 여러가지 정보를 담기 위함

**배열**

- 여러 개의 항목들이 들어있는 리스트
- [ ]로 감싸주기

```jsx
const array = [1, 2, 3, 4, 5];
```

- 어떤 값이든 넣을 수 있음 (객체 배열도 가능)

```jsx
const objects = [{name: "멍멍이"}, {name: "야옹이"}];
```

- 조회: 배열이름[n];
- 첫 번째 항목: n = 0

**배열에 새 항목 추가하기**

→ push 함수(내장 함수) 사용

```jsx
const objects = [{ name: '멍멍이' }, { name: '야옹이' }];

objects.push({
  name: '멍뭉이'
});

console.log(objects);
```

**배열 크기 알아내기**

→ 배열의 length 값 확인

```jsx
console.log(objects.length);
```

## 반복문

**반복문:** 특정 작업을 반복적으로 할 때 사용할 수 있는 구문

**for문:** 특정 값에 변화를 줘가면서 우리가 정한 조건이 만족된다면 계속 반복

```
for (초기 구문; 조건 구문; 변화 구문){
	코드
}
```

- 변화 구문에 증감 모두 가능
- 숫자에 변화를 주어가며 반복적으로 작업 실행

**배열과 for:** for문 사용하여 배열의 내용 정렬 가능

**while문:** 특정 조건이 참이면 계속 반복하는 반복문, 조건을 확인만 하며 반복

↔ for문: 특정 숫자를 가지고 숫자 값 비교, 증감하면서 반복

```
let 변수 = 0;
while (조건){
	코드
	변화구문
}
```

⇒ 조건문이 언젠가는 false가 되도록 설정해야함 (if not 무한반복)

**for...of문:** 배열에 관한 반복문을 돌리기 위해서 만들어진 반복문 (많이 사용X)

```jsx
let numbers = [10, 20, 30, 40, 50];
for (let number of numbers) {
  console.log(number);
}
```

**객체를 위한 반복문 for...in문**

객체의 정보를 배열 형태로 받아올 수 있는 함수

```jsx
const doggy = {
  name: '멍멍이',
  sound: '멍멍',
  age: 2
};

console.log(Object.entries(doggy));
console.log(Object.keys(doggy));
console.log(Object.values(doggy));
```

- Object.entries: [ [ 키, 값 ], [ 키, 값 ] ] 형태의 배열로 변환

- Object.keys: [ 키, 키, 키 ] 형태의 배열로 변환

- Object.values: [ 값, 값, 값 ] 형태의 배열로 반환

  ⇒ 객체가 지니고 있는 값에 대하여 반복을 하고 싶다면 위 함수들 사용 OK

```jsx
const doggy = {
  name: '멍멍이',
  sound: '멍멍',
  age: 2
};

for (let key in doggy) {
  console.log(`${key}: ${doggy[key]}`);
}
```

**break 와 continue:** 반복문 벗어나거나 그 다음 루프를 돌게 함

- continue: 다음 루프를 실행 (해당하는 루프의 continue 밑의 나머지 코드는 실행하지 않고 넘어감)
- break: 반복문 끝내기

## 배열 내장함수

**forEach**

- for문 대체 가능

```jsx
const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];

//for문 사용
for (let i = 0; i < superheroes.length; i++) {
  console.log(superheroes[i]);
}

//forEach문 사용
superheroes.forEach(hero => {
  console.log(hero);
});
```

- forEach 함수의 파라미터: 각 원소에 대해 처리하고 싶은 코드

  ex) hero → superheroes 내의 원소 각각

*콜백함수: 함수형태의 파라미터를 전달하는 것

**map:** 배열 안의 각 원소를 반환할 때 사용 → 새로운 배열 생성

ex) 배열 안의 모든 숫자를 제곱해서 새로운 배열을 만들고 싶다면?

```jsx
const array = [1, 2, 3, 4, 5, 6, 7, 8];

//for문 사용
const squared = [];
for (let i = 0; i < array.length; i++) {
  squared.push(array[i] * array[i]);
}

//forEach문 사용
const squared = [];
array.forEach(n => {
  squared.push(n * n);
});

//map 사용
const square = n => n * n;
const squared = array.map(square);

//함수 이름 붙여 선언할 필요X
const squared = array.map(n => n * n);

console.log(squared);
```

map 함수의 파라미터: 변화를 주는 함수 (변화함수)

ex) square(변화함수): 파라미터 n을 받아와서 제곱

[array.map](http://array.map/) 함수를 사용할 때 square 변화함수를 사용하여 내부의 모든 값에 대하여 제곱하여 새로운 배열 생성

**indexOf:** 원하는 항목이 몇 번째 원소인지 찾아주는 함수

```jsx
const superheroes = ['아이언맨', '캡틴 아메리카', '토르', '닥터 스트레인지'];
const index = superheroes.indexOf('토르');
console.log(index); //2
```

**findIndex:** 배열 내의 값이 객체 or 배열일 때 몇 번째 원소인지 찾아주는 함수

↔ indexOf: 배열 내의 값이 숫자, 문자열, 또는 불리언일 때 찾고자 하는 항목이 몇 번째 원소인지 찾아주는 함수

```jsx
const todos = [
  {
    id: 1,
    text: '자바스크립트 입문',
    done: true
  },
  {
    id: 2,
    text: '함수 배우기',
    done: true
  },
  {
    id: 3,
    text: '객체와 배열 배우기',
    done: true
  },
  {
    id: 4,
    text: '배열 내장함수 배우기',
    done: false
  }
];

const index = todos.findIndex(todo => todo.id === 3);
console.log(index); //2
```

**find:** 찾아낸 값이 몇 번째인지 알아내는 것이 아니라 찾아낸 값 자체를 반환 (findIndex와 비슷)

```jsx
const todo = todos.find(todo => todo.id === 3);
console.log(todo); //{id: 3, text: "객체와 배열 배우기", done: true}
```

**filter:** 배열에서 특정 조건을 만족하는 값들만 따로 추출하여 새로운 배열 생성

```jsx
const tasksNotDone = todos.filter(todo => todo.done === false);
//동일한 코드
const tasksNotDone = todos.filter(todo => !todo.done);
console.log(tasksNotDone); //[{id: 4, text: '배열 내장 함수 배우기', done: false }];
```

→ filter 함수에 넣는 파라미터: 조건을 검사하는 함수

함수의 파라미터: 각 원소의 값

**splice:** 배열에서 특정 항목을 제거할 때 사용

```jsx
const numbers = [10, 20, 30, 40];
//삭제할 항목의 index찾기
const index = numbers.indexOf(30);
numbers.splice(index, 1);
console.log(numbers); //[10,20,40]
```

→ splice 사용 시 첫 번째 파라미터: 어떤 인덱스부터 지울지

두 번째 파라미터: 그 인덱스부터 몇 개를 지울지

**slice:** 배열 잘라낼 때 사용, 기존의 배열은 건드리지 않음

```jsx
const sliced = numbers.slice(0, 2); // 0부터 시작해서 2전까지

console.log(sliced); // [10, 20]
console.log(numbers); // [10, 20, 30, 40]
```

→ slice 사용 시 첫 번째 파라미터: 어디서부터 자를지

두 번째 파라미터: 어디까지 자를지

**shift와 pop**

- shift: 첫 번째 원소를 배열에서 추출 (추출 과정 - 배열에서 해당 원소 사라짐)
- pop: 배열의 마지막에 항목 추출 (push: 배열 마지막에 항목 추가)

**unshift (↔ shift):** 배열의 맨 앞에 원소 추가, 파라미터에는 추가하고 싶은 원소

**concat:** 여러 개의 배열을 하나의 배열로 합치기

```
첫 번째.concat(두 번째);
```

→ 배열에 변화를 주지 X

**join:** 배열 안의 값들을 문자열 형태로 합치기

```jsx
const array = [1, 2, 3, 4, 5];
console.log(array.join()); // 1,2,3,4,5 -> 공식 문서에 표기되어있음
console.log(array.join(' ')); // 1 2 3 4 5
console.log(array.join(', ')); // 1, 2, 3, 4, 5
```

**reduce**

```jsx
//초기에는 이런 식
const numbers = [1, 2, 3, 4, 5];
let sum = array.reduce((accumulator, current) => accumulator + current, 0);
console.log(sum);
```

→ 첫 번째 파라미터: accumulator(누적된 값)와 current를 파라미터로 가져와 결과 반환하는 콜백함수

두 번째 파라미터: reduce 함수에서 사용할 초깃값

ex)

```jsx
//배열 내의 모든 원소의 합 구하기
const numbers = [1, 2, 3, 4, 5];
let sum = numbers.reduce((accumulator, current) => {
  console.log({ accumulator, current });
  return accumulator + current;
}, 0);

console.log(sum);
```

1. 배열을 처음부터 끝까지 반복하면서 전달한 콜백한 함수 호출

2. 첫 accumulator 값 = 0

   WHY? 두 번째 파라미터인 초깃값을 0으로 설정

   [1] 첫 콜백함수 호출 시, 0 + 1 = 1 (accumulator) 반환

   [2] 그 다음 콜백함수 호출 시, 1 + 2 = 3 (accumulator) 반환

   .

   .

   결과: 15

## 프로토타입과 클래스

**객체 생성자:** 함수를 통해서 새로운 객체를 만들고 그 안에 넣고 싶은 값 혹은 함수들을 구현할 수 있게 함

- 객체 생성자 사용 시 보통 함수의 이름 = 대문자
- new 키워드: 새로운 객체를 만들 때
- 프로토타입: 같은 객체 생성자 함수를 사용하는 경우, 특정 함수 or 값을 재사용할 수 있음

```jsx
function Animal(type, name, sound) {
  this.type = type;
  this.name = name;
  this.sound = sound;
  this.say = function() {
    console.log(this.sound);
  };
}

const dog = new Animal('개', '멍멍이', '멍멍');
const cat = new Animal('고양이', '야옹이', '야옹');

dog.say(); //멍멍
cat.say(); //야옹
```

**프로토타입**

- .prototype.[원하는키] = 코드

```jsx
function Animal(type, name, sound) {
  this.type = type;
  this.name = name;
  this.sound = sound;
}

Animal.prototype.say = function() {
  console.log(this.sound);
}; //재사용을 위해서 프로토타입으로 선언
Animal.prototype.sharedValue = 1;

const dog = new Animal('개', '멍멍이', '멍멍');
const cat = new Animal('고양이', '야옹이', '야옹');

dog.say(); //멍멍
cat.say(); //야옹

console.log(dog.sharedValue); //1
console.log(cat.sharedValue); //1
```

**객체 생성자 상속받기**

```jsx
function Animal(type, name, sound) {
  this.type = type;
  this.name = name;
  this.sound = sound;
}

Animal.prototype.say = function() {
  console.log(this.sound);
};
Animal.prototype.sharedValue = 1;

function Dog(name, sound) {
  Animal.call(this, '개', name, sound);
}
Dog.prototype = Animal.prototype;

function Cat(name, sound) {
  Animal.call(this, '고양이', name, sound);
}
Cat.prototype = Animal.prototype;

const dog = new Dog('멍멍이', '멍멍');
const cat = new Cat('야옹이', '야옹');

dog.say();
cat.say();
```

- 새로 만든 Dog와 Cat 함수에서 [Animal.call](http://animal.call/) 호출
- 첫 번째 인자: this, 이후: Animal 객체 생성자 함수에서 필요로 하는 파라미터
- prototype을 공유해야하기 때문에 상속받은 객체 생성자 함수를 만들고 나서는 prototype 값을 Animal.prototype으로 설정

**클래스:** ES6에서 추가 - 객체 생성자로 구현했던 코드를 명확하고 깔끔하게 구현 가능 + 상속

```jsx
class Animal {
  constructor(type, name, sound) {
    this.type = type;
    this.name = name;
    this.sound = sound;
  }
  say() {
    console.log(this.sound);
  }
}

const dog = new Animal('개', '멍멍이', '멍멍');
const cat = new Animal('고양이', '야옹이', '야옹');

dog.say(); //멍멍
cat.say(); //야옹
```

- 메서드: 클래스 내부 함수 ⇒ 만들면 자동으로 prototype으로 등록
- 상속이 쉬움

```jsx
class Dog extends Animal {
  constructor(name, sound) {
    super('개', name, sound);
  }
}

class Cat extends Animal {
  constructor(name, sound) {
    super('고양이', name, sound);
  }
}

const dog = new Dog('멍멍이', '멍멍');
const cat = new Cat('야옹이', '야옹');
```

- extends 키워드: 상속 받을 때
- constructor에서 사용하는 super()함수: 상속받은 클래스의 생성자

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
