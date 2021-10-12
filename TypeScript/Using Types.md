# Using Types
## Basic
> JavaScript
```jsx
function jsCode(num1, num2) {
  return num1 + num2;
}
```
자바스크립트에서는 인자로 들어오는 num1과 num2에 정확히 어떤 타입의 값이 들어오고,  
또 return값으로 어떤 타입의 값이 반환되는지 곧장 알기 힘들다.

```jsx
function jsFetch(id) {
  // fetch code
  // fetch code
  // fetch code
  return new Promise((resolve, reject) => {
    resolve(100);
  });
}
```
이 코드 또한 fetch를 통해 어떤 코드가 반환되는지 한 눈에 알기 힘들고, 코드 전체를 들여다봐야만  
반환값이 무엇인지 알 수 있다.

> TypeScript
```jsx
function tsCode(num1: number, num2: number): number {
  return num1 + num2;
}
```
타입스크립트에서는 인자로 들어오는 num1과 num2에 대한 타입이 명시되어 있고,  
또 return값으로 어떤 타입의 값이 반환되는지도 명시되어 있기 때문에 코드를 한눈에 이해할 수 있다.


```jsx
function tsFetch(id: string): Promise<number> {
  // fetch code
  // fetch code
  // fetch code
  return new Promise((resolve, reject) => {
    resolve(100);
  });
}
```
이 코드에선 인자로 string을 받아서 Promise를 반환하며 fetch가 완료된 다음에는  
number 타입을 반환한다는 것을 첫 줄에서 바로 알 수 있다.

## Optional, Default, Rest
### Optional Parameter
```jsx
function printName(firstName: string, lastName: string) {
  console.log(firstName);
  console.log(lastName);
}
printName('Ga', 'Moon');
printName('Ga'); // error: Expected 2 arguments, but got 1.
```
타입스크립트에서는 함수에 인자 두 개를 정해줬을 때, 인자를 하나만 넣었을 경우 오류가 발생하게 된다.  
하지만 인자가 하나가 들어가는 경우에도 코드가 실행되게 하고 싶은 경우 optional 인자를 사용할 수 있다.

```jsx
function printName(firstName: string, lastName?: string) { // ? 를 추가하여 optional 인자로 설정했다.
  console.log(firstName);
  console.log(lastName);
}
printName('Ga', 'Moon');
printName('Ga');
printName('Ga', undefined);
```
이렇게 하면 두번째 인자가 전달될 수도, 되지 않을 수도 있다는 코드가 된다. 따라서 인자를 입력하지 않아도 실행이 되고  
undefined를 전달해도 문제 없이 실행이 된다.

### Default Parameter
```jsx
function printMessage(message: string = 'default message') { // = 으로 default 인자를 추가해주었다.
  console.log(message);
}
printMessage();
```
인자에 아무것도 전달하지 않았을 때 기본값이 존재하길 원하는 경우 default 인자를 활용하면 된다.  
이렇게 할 경우 인자에 아무것도 전달하지 않아도 `'default message'`가 출력된다.  
Optional 인자에서는 아무것도 전달하지 않을 경우 `undefined`가 반환되는 것과 차이가 있다.

### Rest Parameter
```jsx
function addNumbers(...numbers: number[]): number { // 전개 구문을 활용하여 number타입으로 이루어진 배열이라는 rest 인자를 추가했다.
  return numbers.reduce((a,b) => a + b);
}
console.log(addNumbers(1,2)); // 3
console.log(addNumbers(1,2,3)); // 6
console.log(addNumbers(1,2,3,4)); // 10
```
인자에 전달하고 싶은 값의 개수가 상황에 따라 다르다면 rest 인자를 활용하면 된다.  
`...`(전개 구문, Spread Syntax)를 활용하여 인자에 전달되는 numbers는 number로 이루어진 배열([])이라고 설정해주면  
인자에 들어오는 number값들이 배열화되고 그 안에 들어오는 값이 몇 개든 활용할 수 있게 된다.

[리스트로 돌아가기](https://github.com/MGanom/Studying)
