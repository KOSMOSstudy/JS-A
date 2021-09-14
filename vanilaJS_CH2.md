삼항연산자

삼항연산자: 특정 조건에 따라 text의 값이 달라야 하는 상황 등 (ES6 문법X)

```
조건 ? true일때 : false일때
```

if) 라인이 길어진다면

```jsx
const array = [];
let text = array.length === 0 
  ? '배열이 비어있습니다' 
  : '배열이 비어있지 않습니다.';

console.log(text);
```

if) 중첩해서 쓴다면 ⇒ 가독성이 떨어지기 때문에 if문 등으로 바꾸는 게 나음

```jsx
const condition1 = false;
const condition2 = false;

const value = condition1 
  ? '와우!' 
  : condition2 
    ? 'blabla' 
    : 'foo';

console.log(value);
```