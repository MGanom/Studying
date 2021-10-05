# Types(타입)
## Primitive Type (원시 타입)
### 원시 타입의 종류
number, string, boolean, bigint, symbol, null, undefined 등
### 자주 쓰이는 원시 타입
- number: `1`, `2`, `3`과 같은 숫자를 의미한다.
```jsx
const num: number = 1;
```
- string: `'hello'`와 같은 문자열을 의미한다.
```jsx
const str: string = 'hello';
```
- boolean: `true`와 `false`로 참, 거짓을 판단하는 것을 의미한다.
```jsx
const bool: boolean = true;
```
- null: 말 그대로 텅 비었다는 의미를 가진 상태를 의미한다.
```jsx
const example: null; // 권장하지 않음
example = null;
example = 1; // error

const example2: string | null; // 어떤 데이터 타입이 있느냐 혹은 없느냐라는 optional 선언
example2 = null;
example2 = 'hello'
```
- undefined: 값이 있는지 없는지 결정이 되지 않은 상태를 의미한다.
```jsx
let bad: undefined; // 권장하지 않음
bad = 'hello'; // error

let good: number | undefined; // 어떤 데이터가 number로 결정됐거나 혹은 결정되지 않아 undefined라는 optional 선언
good = undefined;
good = 1;
```

## Object Type (객체 타입)
### 객체 타입의 종류
function, array, object 등

## Other Type (기타 타입)
### 종류
unknown, any, void, never, object 등
- unknown: 어떤 데이터 타입이 담길 지 알 수 없는 상태를 의미한다. 되도록이면 사용하지 않는 게 좋다.
```jsx
let notSure: unknown = 0;
notSure = 'sure';
notSure = true;
```
- any: 어떤 데이터 타입이든지 담을 수 있는 상태를 의미한다. 되도록이면 사용하지 않는 게 좋다.
```jsx
let anything: any = 0;
anything = 'hello';
anything = 1;
```
- void: 아무것도 반환 하지 않는 상태를 의미로 생략을 할 때도 많다.
```jsx
function print(): void {
  console.log('hello');
  return;
}
```
- never: 함수에서 절대 리턴할 수 없는 상태를 의미한다.
```jsx
function throwError(message: string): never {
  // message -> server (log)
  throw new Error(message);
}
```
- object: 원시 타입을 제외한 모든 객체 타입을 담을 수 있는 상태를 의미한다. 되도록이면 사용하지 않는 게 좋다.
```jsx
let obj: object;
function someObject(obj: object) {}
someObject({ name: 'moon' });
someObject({ age: 100 });
```
