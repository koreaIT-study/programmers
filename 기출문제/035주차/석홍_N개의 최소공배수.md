![image](https://github.com/koreaIT-study/programmers/assets/67637716/f5a0a8cb-02b1-4f8c-b736-0d7f8f8be7a3)  



```
import java.util.Arrays;

class Solution {

    public int solution(int[] arr) {
        int answer = 1;

        for(int i = arr.length-1;i>=0;i--) {
            if(answer % arr[i] != 0) {
                answer = getLCM(answer, arr[i]);
            }
        }

        return answer;
    }

    /**
     * 최소 공배수
     * 
     * @param a
     * @param b
     * @return
     */
    private int getLCM(int a, int b) {
        return (a * b) / getGCD(a, b);
    }

    /**
     * 최대공약수
     * 
     * @param a
     * @param b
     * @return
     */
    private int getGCD(int a, int b) {
        int r = a % b;

        if (r == 0)
            return b;

        return getGCD(b, r);
    }
}
```   
