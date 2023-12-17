```js
function solution(arr) {
    let answer = 1;
    
    arr.forEach((el)=>{
        answer = getLcm(answer, el);
    })

    return answer;
}

const getGcd = (a, b) => b === 0 ? a : getGcd(b, a % b);

const getLcm = (a, b) => (a * b) / getGcd(a, b);

```
