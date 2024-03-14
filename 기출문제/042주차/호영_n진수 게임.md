```js
function solution(n, t, m, p) {
    let answer = ""; 
    let temp = "";
    
    for (let i = 0; i < t * m; i++) { 
        temp += i.toString(n).toUpperCase();
    }
    
    for (let j = p - 1; j < t * m; j += m) {
        answer += candidate[j];
    }
    
    return answer; 
}
```
