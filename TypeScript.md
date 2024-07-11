<details>
<summary>1. 특징</summary>
<div markdown="1">

## 1. 특징

- 자바스크립트에 타입을 부여한 언어
- 컴파일 언어
- 객체 지향 프로그래밍 지원
  
</div>
</details>

<details>
<summary>2. 타입</summary>
<div markdown="1">

## 2. 타입

- ‘: TYPE’ 형태로 타입 선언

```tsx
let num: number // number
let str: string // string
let b: boolean // boolean
```

- 배열

```tsx
// 문자만
let s: string[] = ['apple', 'banana']
let s: Array<string> = ['apple', 'banana']

// 숫자만
let n: number[] = [1, 2, 3]
let n: Array<number> = [1, 2, 3]

// 문자, 숫자 둘 다
let arr: (string | number)[] = ['apple', 1, 2, 'banana']
let arr: Array<string | number> = ['apple', 1, 2, 'banana']

// 배열을 가짐
let arr: unknown[] = [1, {}, [], 'str', false]
```

- 인터페이스, 커스텀 타입

```tsx
interface User {
	name: string,
	age: number,
	b: boolean
}

let user: User[] = [
	{
		name: 'Kim'
		age: 5
		b: true
	},
	{
		name: 'Lee'
		age: 6
		b: false
	},
	{
		name: 'Park'
		age: 7
		b: true
	}
]
```

- Tuple
    - 고정된 길이 배열로 표현

```tsx
// Variables
let id: number = 1234
let name: string = 'Kim'
let valid: boolean = true

// Tuple
let user: [number, string, boolean] = [1234, 'Kim', true]
console.log(user[0]) // 1234
console.log(user[1]) // 'Kim'
console.log(user[2]) // true
```

- Enum

```tsx
enum Week {
	Sun = 0,
	Mon = 1,
	Tue = 2,
	Wed = 3,
	Thu = 4,
	Fri = 5,
	Sat = 6
}

console.log(Week.Mon); // 1
```

- Any
    - 모든 타입

```tsx
let any: any = 123
any = 'a'
any = {}
any = null

const l: any[] = [1, true, 'a']
```

- Unknown
    - 알 수 없는 타입

```tsx
let a: any = 123
let b: unknown = 123

let v1: boolean = a // 어디든 할당 가능
let v2: number = b // any 타입을 제외한 다른 타입에 할당 가능
let v3: any = b // OK
let v4: number = b as number **// 타입을 단언하면 할당할 수 있습니다.**
```

- Object

```tsx
let obj: object = {}
let arr: object = []
let func: object = function () {}
let n: object = null
let date: object = new Date()
```

- Null, Undefined
    - 각 타입에 할당 가능, 서로의 타입에도 할당 가능

```tsx
let und: undefined = null
let n: null = undefined

let voi: void = null
let voi: void = undefined
```

- Void

```tsx
function hello(msg: string): void {
	console.log(`Hello ${msg}`)
}

const hi: void = hello('world') // Hello world
console.log(hi) // undefined
```

- Never
    - 절대 발생하지 않을 값, 어떠한 타입도 적용 불가

```tsx
function error(msg: string): never {
	throw new Error(msg)
}

const never: [] = []
never.push(3) // Error - TS2345: Argument of type '3' is not assignable to parameter of type 'never'.
```

- Union
    - 2개 이상의 타입 허용

```tsx
let union: (string | number)
union = 'str'
union = 1
```

- Intersection
    - &를 사용하여 2개 이상의 타입을 조합

```tsx
interface User {
	name: string
	age: number
}

interface B {
	b: boolean
}

const kim: User = {
	name: 'Kim'
	age: 5
}

const lee: User & B = {
	name: 'Lee'
	age: 6
	b: true
}
```

- Function

```tsx
function add(a: number, b: number): number {
	return a + b
}

// 화살표 함수 1
let func: (a: number, b: number) => number 
func = function (x, y) {
	return x + y
}

// 화살표 함수 2
let func: () => void
func = function () {
	console.log('hi')
}

// 비동기 함수 (제네릭으로 반환 타입 지정)
type Movie = {
	title: string
	poster: string
}
async function getMovie(title: string): Promise<Movie[]> {
	const res = fetch(`https://gettitles.movie/${title}`)
	return await res.json()
}
```
  
</div>
</details>

<details>
<summary>3. 타입 추론, 단언</summary>
<div markdown="1">

## 3. 타입 추론, 단언

- 명시적으로 타입 선언이 되어있지 않은 경우, 타입 추론

```tsx
let num = 1
num = 'str' // error
```

- 추론하지 않도록 지시하는 것, 타입 단언

```tsx
function func(val: string | number, isNumber: boolean) {
	if (isNumber) {
		// 1. 변수 as 타입
		(val as number).toFixed(2)
		
		// 2. <타입>변수
		// (<number>val).toFixed(2)
	}
}
```
  
</div>
</details>

<details>
<summary>4. Non-null 단언 연산자</summary>
<div markdown="1">

## 4. Non-null 단언 연산자

```tsx
function func(x: number | null | undefined) {
	return x!.toFixed(2) // x가 null, undefined가 아니다
}
```
  
</div>
</details>

<details>
<summary>5. 타입 가드</summary>
<div markdown="1">

## 5. 타입 가드

```tsx
function func(val: string | number, isNumber: boolean) {
	if (isNumber) {
		(val as number).toFixed(1)
		isNaN(val as number)
	} else {
		(val as string).split('')
	}
}

// typeof
function func(val: string | number) {
	if (typeof val === 'number') {
		val.toFixed(1)
		isNaN(cal)
	} else {
		val.split('')
	}
}

// in
function func(val: any) {
	if ('toFixed' in val) {
		val.toFixed(1)
		isNaN(val)
	} else if ('split' in val) {
		val.split('')
	}
}

//instanceof
class Cat {
	meow() {}
}
class Dog {
	woof() {}
}
function sounds(ani: Cat | Dog) {
	if (ani instanceof Cat) {
		ani.meow()
	} else {
		ani.woof()
	}
}
```
  
</div>
</details>

<details>
<summary>6. 타입 만족</summary>
<div markdown="1">

## 6. 타입 만족

- satisfies : 타입이 만족하는지 확인

```tsx
interface User {
	name: string
	age: number
}

// satisfies
const userA = {
	name: 'Kim'
} satisfies User // error

const userB = {
	name: 'Kim'
} as User // 타입 단언으로 안전하지 않지만 에러 발생 X
```

</div>
</details>

<details>
<summary>7. 인터페이스</summary>
<div markdown="1">

## 7. 인터페이스

- 여러 객체를 정의하는 구조

```tsx
interface User {
	name: string,
	age: number,
	isAdult: boolean
	
interface User {
	name: string,
	age: number,
	isAdult?: boolean // 필수가 아닌 속성

interface User {
	readonly name: string, // 읽기 전용
	age: number,
	isAdult: boolean
```

- 함수 타입

```tsx
interface User {
	name: string
}

interface GetUser {
	(name: string): User
}

const getUser: GetUser = function (n) {
	return user
}
getUser('Kim')
```

- 클래스 타입

```tsx
interface IUser {
 name: string
 getName(): string
}

class User implements IUser {
	constructor(public name: string) {}
	getName() {
		return this.name
	}
}

const kim = new User('Kim')
kim.getName() // Kim
```

- 인덱싱 가능 타입

```tsx
interface Item {
	[intemInd: number]: string | boolean | number[]
}
let item: Item = ['Hi', false, [1, 2, 3]]
console.log(item[0]) // Hi
console.log(item[1]) // false
console.log(item[2]) // [1, 2, 3]
```

- keyof
    - 유니온 타입으로 적용

```tsx
interface Countries {
	KR: '대한민국'
	US: '미국'
	CP: '중국'
}
let country: keyof Countries // 'KR' | 'US' | 'CP'
country = 'KR'

interface Countries {
	KR: '대한민국'
	US: '미국'
	CP: '중국'
}
let country: Countries[keyof Countries] // Countries['KR' | 'US' | 'CP']
country = '대한민국'
```

- 인터페이스 확장

```tsx
interface Animal {
	name: string
}
interface Cat extends Animal {
	meow(): string
}
class Cat implements Cat { // Error - TS2420: Class 'Cat' incorrectly implements interface 'ICat'. Property 'name' is missing in type 'Cat' but required in type 'ICat'.
	meow() {
		return 'Meow'
	}
}
```

</div>
</details>

<details>
<summary>8. 타입 별칭</summary>
<div markdown="1">

## 8. 타입 별칭

- type 키워드를 사용해  새로운 타입 조합을 만들 수 있음

```tsx
type Str = string;
type SNum = string | number;

let name: Str = "Kim";
let num: SNum = "a1"
num = 1
```

</div>
</details>

<details>
<summary>9. 제네릭</summary>
<div markdown="1">

## 9. 제네릭

- 사용 시점에 타입을 선언

```tsx
function toArray<T>(a: T, b:T): T[] {
	return [a, b]
}

toArray<number>(1, 2)
toArray<string>('1', '2')
toArray<string | number>(1, '2')
```

- 조건부 타입

```tsx
type U = string | number | boolean

// type 식별자 = 타입 구현
type MyType<T> = T extends U ? string : never

// interface 식별자 { 타입 구현 }
interface User<T> {
	name: string
	age: T extends U ? number : never
}
```

</div>
</details>

<details>
<summary>10. this</summary>
<div markdown="1">

## 10. this

```tsx
const obj = {
	a: 'Hi',
	b: function () {
		console.log(this.a) // obj.a
		
		function b() {
			console.log(this.a) // global.a
		}
	}
}
```

- bind 메소드
    - this를 직접 연결해 주는 방법

```tsx
obj.b() // Hi

const b = obj.b.bind(obj)
b() // Hi

function f(cb: any) {
	cb()
}
f(obj.b.bind(obj)) // Hi

setTimeout(obj.b.bind(obj), 100) // Hi
```

- 화살표 합수
    - 콘텍스트를 유지하며 메소드 호출

```tsx
obj.b() // Hi

const b = () => obj.b()
b() // Hi

function f(cb: any) {
	cb()
}

f(() => obj.b()) // Hi

setTimeout(() => obj.b(), 100) // Hi
```

- 명시적 this

```tsx
interface Cat {
	name: string
}

const cat: Cat = {
	name: 'Kim'
}

function f(this: Cat, greeting: string) {
	console.log(`${greeting} ${this.name}`) // ok
}
f.call(cat, 'Hi') // Hi Kim
```

- 오버로드

```tsx
function add(a: string, b: string): string
function add(a: number, b: number): number
function add(a: any, b: any): any {
	return a + b
}

add('hello ', 'world')
add(1, 2)
add('hello ', 2)
```

</div>
</details>

<details>
<summary>11. 클래스</summary>
<div markdown="1">

## 11. 클래스

```tsx
class Animal {
  public name: string
  constructor(name: string) {
    this.name = name
  }
}
class Cat extends Animal {
  getName(): string {
    return `Cat name is ${this.name}.`
  }
}
let cat = new Cat('Lucy')
console.log(cat.getName()) // Cat name is Lucy.

cat.name = 'Tiger'
console.log(cat.getName()) // Cat name is Tiger.
```

- 추상 클래스

```tsx
abstract class Animal {
  abstract name: string
  abstract getName(): string

  protected constructor(public legs: string) {}
  getLegs() {
    return this.legs
  }
}
```

</div>
</details>

<details>
<summary>12. Optional</summary>
<div markdown="1">

## 12. Optional

- 매개 변수

```tsx
function add(x: number, y?: number): number {
	return x + (y || 0)
}
const sum = add(2)
console.log(sum)
```

- 속성, 매소드

```tsx
interface User {
	name: string
	age: number
	isAdult?: boolean
}

let user: User = {
	name: 'Kim',
	age: 123
}
```

</div>
</details>

<details>
<summary>13. 모듈</summary>
<div markdown="1">

## 13. 모듈

```tsx
// 내보내기
// myType.ts
export interface User {
	name: string
	age: number
}

export type MyType = string | number

// 가져오기
import type { User, MyType } from './myType'

const user: User = {
	name: 'Kim'
	age: 12
}
```

</div>
</details>
