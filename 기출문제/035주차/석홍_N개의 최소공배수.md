![image](https://github.com/koreaIT-study/programmers/assets/67637716/a3c2cc94-6f82-4b46-ba05-f2536493997d)  


```
import java.util.Arrays;

class Solution {

    public int solution(int[] arr) {
        int answer = 0;
        Arrays.sort(arr);

        if (arr.length == 1)
            return arr[0];
        
        answer = getLCM(arr[arr.length-1], arr[arr.length-2]);

        for(int i = arr.length-3;i>=0;i--) {
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
