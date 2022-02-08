# React Hook
## React Hook란?
React는 기본적으로 클래스형 컴포넌트와 함수형 컴포넌트로 이루어져 있으나 과거엔 함수형 컴포넌트는 거의 사용되지 않고 클래스형 컴포넌트만 주로 사용됐었다. 그 이유는 바로 함수형 컴포넌트에선 State 관리와 Lifecycle(생명주기) 메서드 사용이 불가능 하기 때문인데, 그렇다는 건 코드를 원하는 시점에 실행할 수 없어 정교한 작업이 불가능하다는 의미이기 때문이다.  
하지만 React 16.8 버전이 되면서 함수형 컴포넌트에서도 State 관리는 물론 생명주기 메서드와 같은 동작을 가능하게 하는 React Hook이 도입되었고, 마침내 State Hook과 Effect Hook 등을 통해 더욱 간결하고 직관적인 코딩이 가능해졌다.

## 대표적으로 사용되는 Hooks
### 1. useState
```jsx
const [number, setNumber] = useState(0)
```
함수형 컴포넌트에선 이렇게 useState를 사용하여 state 변수를 선언할 수 있고 이 state는 컴포넌트가 다시 렌더링 되어도 유지가 된다.  
우선 이 코드에서 `number`는 현재의 state 값을 의미하고 `setNumber`는 이 값을 업데이트하는 함수를 의미한다. 그리고 useState 안에 있는 `0`은 `number`의 초기값을 의미한다. 사용자는 `number`의 초기값인 `0`을 `setNumber(5)`와 같은 방법으로 `5`로 업데이트할 수 있다. 여기에서 주의할 점은 `setNumber` 뒤에 오는 숫자는 현재 `number`의 값을 '덮어쓴다'는 점이다. 즉 객체나 배열을 다룰 때 ...(spread operator)를 적극적으로 사용해야 데이터를 제대로 다룰 수 있다.

### 2. useEffect
```jsx
useEffect(() => {
  // 실행할 코드
  return () => {
    // 실행할 코드
  }
},[dependency(의존성)])
```
useEffect는 함수형 컴포넌트에서 클래스 컴포넌트 생명주기 메서드인 componentDidMount, componentDidUpdate, componentWillUnmount의 역할을 한다.  
우선 React가 DOM을 바꾼 뒤에 컴포넌트가 마운트 되면서 코드가 실행되어 componentDidMount와 같은 작동을 하고, DOM이 업데이트가 되면 componentDidUpdate와 같은 작동을 하며 실행되고, 마지막으로 마운트 해제가 될 때 componentWillUnmount와 같은 작동을 하며 return 안의 코드가 실행된다.

#### 2-1. Clean-up을 이용하는 Effects


