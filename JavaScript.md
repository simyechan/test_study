<details>
<summary>특징</summary>
<div markdown="1">

## 1. 특징
- 객체 기반의 스크립트 언어
- 동적이며, 타입을 명시할 필요가 없는 인터프리터 언어
- 객체 지향형 프로그래밍과 함수형 프로그래밍을 모두 표현 가능

</div>
</details>

<details>
<summary>변수와 상수</summary>
<div markdown="1">
  
## 2. 변수와 상수

- var : 중복 선언 가능
- let : 중복 선언 불가능, 재할당 가능
- const : 중복 선언 불가능, 재할당 불가능

</div>
</details>

<details>
<summary>타입</summary>
<div markdown="1">
  
## 3. 타입

```jsx
var num = 10; // number
var str = "문자열"; // string
var b = true; // boolean
var arr = [0]; // array
var ob = document.querySelector('h1'); // object
```

- null : 값이 정해지지 않음
- undefined : 타입이 정해지지 않음

```jsx
null == undefined; // true
null === undefined; // false
```

- 묵시적 타입 변환 (implicit type conversion)

```jsx
10 + "문자열"; // 10이 문자열로 변환
"2" * "3"; // 숫자로 변환
1 - "문자열"; // NaN
```

- 명시적 탕입 변환 (explicit type conversion)

```jsx
Number("10"); // 숫자 10
String(true); // 문자열 "true"
Boolean(0); // false
Object(3); // new Number(3)과 동일 숫자 3
```

</div>
</details>

<details>
<summary>연산자</summary>
<div markdown="1">

## 4. 연산자

- 일치 연산자

```jsx
alert( 0 == false ); // true
alert( '' == false ); // true

alert( 0 === false ); // false, 형이 다름
```

- typeof 연산자

```jsx
typeof 10; // number
typeof NaN; // number
typeof "문자열"; // string
typeof true; // boolean
typeof undefined; // undefined
typeof new Date(); // object
typeof null // object
```

- instanceof 연산자
    - 피연산자인 객체가 특정 객체의 인스턴스인지를 확인

```jsx
var str = new String("문자열");

str instanceof Object; // true
str instanceof String; // true
str instanceof Array; // false
str instanceof Number; // false
str instanceof Boolean; // false
```

- nullish 병합 연산자 ‘??’

```jsx
// 두 코드가 같음
x = a ?? b

x = (a !== null && a !== undefined) ? a : b;
```

</div>
</details>

<details>
<summary>함수</summary>
<div markdown="1">

## 5. 함수

- 함수 선언

```jsx
function name (parameter1, parameter2, ... parameterN) {
  // 함수 본문
}

name();
name(parameter1, parameter2, ... parameterN);
```

- 함수 선언문, 함수 표현식

```jsx
// 함수 선언문
function sum (a, b) {
  return a + b;
}

// 함수 표현식
let sum = function(a, b) {
  return a + b;
};
```

- 화살표 함수

```jsx
let func = (arg1, arg2, ... argN) => expression

let func = function(arg1, arg2, ... argN) {
  return expression;
};

async ()=>{
	
}
```

</div>
</details>

<details>
<summary>맵, 셋</summary>
<div markdown="1">

## 6. 맵, 셋

- 맵
    - 키가 있는 값이 저장된 컬렉션

```jsx
let map = new Map();

map.set('1', 'str1'); // 문자형 키
map.set(1, 'num1'); // 숫자형 키
map.set(true, 'bool1'); // 불린형 키

alert(map.get(1)); // 'num1'
alert(map.get('1')); // 'str1'
alert(map.size); // 3
```

- 맵 반복

```jsx
let recipeMap = new Map([
	['cucumber', 500],
	['tomatoes', 350],
	['onion', 50]
]);

for (let vegetable of recipeMap.keys()) {
	alert(vegetable); // cucumber, tomatoes, onion
}

for (let amount of recipeMap.values()) {
	alert(amount); // 500, 350, 50
}

for (let entry of recipeMap) {
	alert(entry); // cucumber, 500 ... 키, 값 쌍으로 순회
}

// forEach
recipeMap.forEach((value, key, map) => {
	alert(`${key}: ${value}`); // cucumber: 500 ...
});
```

- Object.entries

```jsx
// 객체 -> 맵
let obj = {
	name: "John",
	age: 30
};

let map = new Map(Object.entries(obj));

alert(map.get('name')); // John
```

- Object.fromEntries

```jsx
// 맵 -> 객체
let map = new Map();
map.set('banana', 1);
map.set('orange', 2);
map.set('meat', 4);

let obj = Object.fromEntries(map.entries()); // 맵을 객체로 변환

alert(obj.orange); // 2
```

- 셋
    - 중복이 없는 값이 저장된 컬렉션

```jsx
let set = new Set();

let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

set.add(john);
set.add(pete);
set.add(mary);
set.add(john);
set.add(mary);

alert( set.size ); // 3

for (let user of set) {
	alert(user.name); // John, Pete, Mary 순으로 출력
}
```

- 셋 반복

```jsx
let set = new Set(["oranges", "apples", "bananas"]);

for (let value of set) alert(value);

set.forEach((value, valueAgain, set) => {
	alert(value);
});
```

</div>
</details>

<details>
<summary>구조 분해 할당</summary>
<div markdown="1">

## 7. 구조 분해 할당

- 배열 분해

```jsx
let arr = ["Bora", "Lee"]

let [firstName, surname] = arr;

alert(firstName); // Bora
alert(surname); // Lee

let [firstName, surname] = "Bora Lee".split(' ');
```

- 객체 분해

```jsx
let options = {
	title: "Menu",
	width: 100,
	height: 200
};

let {title, width, height} = options;

alert(title); // Menu
alert(width); // 100
alert(height); // 200

let {title, width, height} = {title: "Menu", height: 200, width: 100}
```

- 중첩 구조 분해

```jsx
let options = {
	size: {
		width: 100,
		height: 200
	},
	items: ["Cake", "Donut"],
	extra: true
};

let {
	size: {
		width,
		height
	},
	items: [item1, item2],
	title = "Menu"
} = options;

alert(title); // Menu
alert(width); // 100
alert(height); // 200
alert(item1); // Cake
alert(item2); // Donut
```
</div>
</details>

<details>
<summary>Date 객체와 날짜</summary>
<div markdown="1">

## 8. Date 객체와 날짜

- 객체 생성

```jsx
let now = new Date();
alert(now);
```

- 날짜 구성요소
    - getFullYear() : 연도를 반환
    - getMonth() : 월을 반환
    - getDate() : 일을 반환
    - getHours(), getMinutes(), getSeconds(), getMilliseconds() : 시, 분, 초, 밀리초를 반환
    - getDay() : 요일을 반환
    - getTime() : 시간을 반환
    - getTimezoneOffset() : 현지 시간과 표준 시간의 차이를 반환

- 날짜 구성요소 설정

```jsx
let today = new Date();

today.setHours(0);
alert(today); // 시를 0으로 변경

today.setHours(0, 0, 0, 0);
alert(today); // 시, 분, 초 변경
```

</div>
</details>

<details>
<summary>async, await</summary>
<div markdown="1">

### 9. async, await

- async 함수

```jsx
async function f() {
	return 1;
}

f().then(alert); // 1
```

- 명시적 프라미스 반환

```jsx
async function f() {
	return Promise.resolve(1);
}

f().then(alert); // 1
```

- await

```jsx
async function f() {
	let promise = new Promise((resolve, reject) => {
		setTimeout(() => resolve("완료!"), 1000)
	});
	
	let result = await promise; // 프라미스가 이행될 때까지 기다림
	
	alert(result); // "완료1"
}

f();
```

- 에러 핸들링

```jsx
async function f() {
	await Promise.reject(new Error("에러 발생!");
}

async function f() {
	throw new Error("에러 발생!");
}
```

- try-catch

```jsx
async function f() {

  try {
    let response = await fetch('http://유효하지-않은-주소');
  } catch(err) {
    alert(err); // TypeError: failed to fetch
  }
}

f();

async function f() {

  try {
    let response = await fetch('http://유효하지-않은-주소');
    let user = await response.json();
  } catch(err) {
  
    alert(err);
  }
}

f();

async function f() {
  let response = await fetch('http://유효하지-않은-주소');
}

f().catch(alert); // TypeError: failed to fetch
```

</div>
</details>
