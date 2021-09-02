# 멱집합 (Powerset)
## 멱집합이란?
멱집합이란 어떤 집합에 대하여 그 집합의 요소들로 만들 수 있는 모든 부분집합을 모아둔 것을 의미한다.  
다시 말해, `[1,2,3]` 이라는 집합이 있다면,  
멱집합은 `[1], [2], [3], [1,2], [1,3], [2,3], [1,2,3]` 이 되는 것이다.

## 멱집합을 구하는 코드

```jsx
function powerSet(arr) {
    let checker = new Array(arr.length).fill(0);
    let powerset = [];
    function dfs(depth) {
      if (checker.length === depth) {
        powerset.push(arr.filter((element, idx) => checker[idx]));
      } else {
        checker[depth] = 0;
        dfs(depth + 1);
        checker[depth] = 1;
        dfs(depth + 1);
      }
    }
    dfs(0);
    return powerset;
  }
  ```

## 활용
모든 부분 집합을 비교하는 알고리즘이나 각 요소에 대해  
적합성을 판별하는 알고리즘을 풀 때 활용할 수 있다.  

[리스트로 돌아가기](https://github.com/MGanom/Studying)
