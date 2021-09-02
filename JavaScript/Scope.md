
```jsx
let name = 'moon';

function log() {
  console.log(name);
} // name = moon을 의미

function wrapper() {
  name = 'ganom';
  log(); //name = moon을 호출, name = ganom로 재할당
  console.log(name);
}

log(); // 선언됐던 moon을 호출
wrapper(); // 재할당된 ganom을 호출
log(); // wrapper()로 인해 재할당된 ganom을 호출

console.log('=============');

let name2 = 'moon';
function log2() {
  console.log(name2);
} // name2 = moon을 의미

function wrapper2() {
  let name2 = 'ganom';
  log2(); // name2 = moon을 호출
  console.log(name2); // 함수 내에서 선언된 name2 = ganom을 호출
}
log2(); // 할당됐던 moon을 호출
wrapper2(); // 전역변수 name2 = moon과 함수 내에 선언된 name2 = ganom을 호출
log2(); // 할당됐던 moon을 호출
```

![image](https://user-images.githubusercontent.com/80687334/122420160-6af75380-cfc6-11eb-9678-578a5651b841.png)

[리스트로 돌아가기](https://github.com/MGanom/Studying)
