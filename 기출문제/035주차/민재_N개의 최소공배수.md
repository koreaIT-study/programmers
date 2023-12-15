```java
class Solution {
    public int solution(int[] arr) {
        int answer = 1;
        int GCD = 0;

        for (int i = 0; i < arr.length; i++) {
            GCD = GCD(answer, arr[i]);
            answer *= arr[i] / GCD;
        }

        return answer;
    }

    private int GCD(int num1, int num2){
        int big = num1 > num2 ? num1 : num2;
        int small = num1 > num2 ? num2 : num1;

        while(small != 0){
            int r = big % small;
            big = small;
            small = r;
        }
        return big;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/dbfb4be3-0333-48a5-b386-9b8c31df0565)
