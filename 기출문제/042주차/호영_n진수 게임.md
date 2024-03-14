```js
function solution(n, t, m, p) {
    let answer = ""; 
    let temp = "";
    
    for (let i = 0; i < t * m; i++) { 
        temp += i.toString(n).toUpperCase();
    }
    
    for (let i = p - 1; i < t * m; i += m) {
        answer += temp[i];
    }
    
    return answer; 
}
```
