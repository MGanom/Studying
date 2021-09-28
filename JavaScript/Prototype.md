# Prototype (프로토타입)

## Prototype이란?
자바스크립트는 객체지향프로그래밍 언어이다.  
하지만 Java, Python, Ruby 등 다른 객체지향프로그래밍 언어들과는 다르게 클래스(Class) 기반의 언어가 아니다.  
자바스크립트는 클래스 문법이 추가된 ECMA6 전까지는 이 문법 조차 존재하지 않았었다.  
그렇다면 자바스크립트는 무엇을 기반으로 객체지향프로그래밍을 하고 있는걸까?  
그것은 바로 프로토타입(Prototype)이다.  

자바스크립트의 모든 객체들은 메서드와 속성들을 상속 받기 위한 프로토타입 객체(prototype object)를 가진다.  
그리고 그 프로토타입 객체 또한 객체이기 때문에 또 다시 상위 프로토타입 객체가 존재할 수 있으며 이는 끝없이 연결될 수 있는데,  
이를 프로토타입 체인(prototype chain)이라고 부른다. 이러한 구조를 통해 객체지향프로그래밍이 가능해지기에  
자바스크립트는 프로토타입 기반 언어(prototype-based language)라고 불린다.  

다시 말해 우리가 메서드를 사용하거나 속성에 접근하는 등의 행동을 하면 자바스크립트는 이 프로토타입 체인을 타고 올라가며  
메서드와 속성을 탐색해 이들이 정의된 생성자(constructor)의 프로토타입을 찾게 되는 것이다.  

## Prototype의 필요성
```jsx
function Example() {
    this.a = 1;
    this.b = 4;
}

const ex1 = new Example();
const ex2 = new Example();

console.log(ex1.a); // result 1
console.log(ex2.b); // result 4
```
앞서 말했듯이 자바스크립트는 클래스 기반의 언어가 아니다. 하지만 이처럼 함수(function)를 통해 클래스를 흉내내는 것은 가능하다.  
하지만 이렇게 코드를 짤 경우 ex1과 ex2는 같은 함수를 상속했음에도 불구하고 함수 내의 a와 b에 대한 정보가 각각 상속 되어  
메모리에는 a 2개, b 2개, 총 4개의 변수가 할당되게 된다. 즉, 이 방법은 메모리 낭비를 초래하여 성능을 저하시킬 수 있다는 뜻이 된다.  

그렇다면 이를 어떻게 개선할 수 있을까?  
자바스크립트는 해답을 프로토타입에서 찾았다.

```jsx
function Example() {}

Example.prototype.a = 1;
Example.prototype.b = 4;

const ex1 = new Example();
const ex2 = new Example();

console.log(ex1.a); // result 1
console.log(ex2.b); // result 4
```

우선 Example이라는 함수가 생성되는 순간 Example 함수는 constructor를 갖게 되고, 그렇기 때문에 new를 사용할 수 있게 된다.  
그리고 .prototype으로 함수 내의 프로토타입을 정의해주고 new를 사용하여 변수에 할당해주면 이전의 코드와는 다르게  
메모리에 a와 b가 새로 할당되는 것이 아닌 보이지 않는 Object 안에서 프로토타입을 통해 하나씩 꺼내오는 방식으로 작동하게 된다.  
즉, 메모리 관리에도 용이하고 좀 더 체계적인 환경이 갖춰지게 되는 것이다.

## Prototype의 원리
