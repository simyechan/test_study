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
