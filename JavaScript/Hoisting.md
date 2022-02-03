# Hoisting이란?
Hoisting이란 변수 생성이나 함수선언식 생성 시 선언 단계가 코드의 맨 위로 끌어올려지는 것을 의미한다. <br />
특히 var의 경우 이렇게 호이스팅이 되면 변수나 함수를 선언하기 전에 호출을 해도 호출이 가능하다.

# 선언, 초기화, 할당
Hoisting이 일어나는 과정을 이해하기 위해선 자바스크립트의 변수와 함수의 생성 과정을 이해해야 한다. <br />
자바스크립트에서 변수나 함수가 생성될 때, 내부적으로는 선언, 초기화, 할당 총 3단계에 걸쳐 생성이 이루어 진다.<br />
<br />
예를 들어,

```jsx
var a = 10
```

처럼 변수를 생성하는 경우, 자바스크립트 내부적으로는 

```jsx
var a; // 변수 선언
a = undefined; // 초기화
a = 10 // 할당
```

과 같은 과정에 걸쳐 생성이 된다. <br />
여기에서 변수 선언 부분이 호이스팅이 발생하여 맨 코드의 맨 위로 끌어올려지게 된다는 것인데, 그렇기 때문에

```jsx
console.log(a); // undefined
var a = 10;
console.log(a); // 10
```

과 같은 코드는 내부적으로

```jsx
var a;
a = undefined;
console.log(a); // undefined
a= 10;
console.log(a); // 10
```

처럼 작동하게 된다는 것이다. 그런데 위에서 선언 단계가 끌어올려진다고 했는데 왜 초기화 단계도 같이 끌어올려 진 것일까? <br />
그것은 var이 let과 const와는 다른 특성을 갖고 있기 때문이다.

# var, let, const의 차이
var의 경우, 선언 단계와 초기화 단계가 하나로 묶여있는 반면에, let과 const는 그렇지 않다. <br />
다시 말해 var의 경우

```jsx
var a;
a = undefined;
```

가 사실상 하나로 묶여있기 때문에

```jsx
var a;
```

는 위의 코드와 똑같은 역할을 하고 있다고 볼 수 있는 것이다. 즉,

```jsx
console.log(a);
var a;
```
는 ```undefined``` 가 나오게 된다.

반면에 let이나 const의 경우

```jsx
let b;
b = undefined;
```

가 분리되어 있기 때문에

```jsx
let b;
```

는 아무런 할당이 이루어지지 않아 ```ReferenceError: b is not defined``` 가 나온다.

[리스트로 돌아가기](https://github.com/MGanom/Studying)
