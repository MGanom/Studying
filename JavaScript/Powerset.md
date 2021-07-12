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
