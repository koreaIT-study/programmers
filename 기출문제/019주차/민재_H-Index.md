+ 내풀이
```java
class Solution {
    public int solution(int[] citations) {
        int answer = 0;
        int len = citations.length;
        int[] cnts = new int[len];

        for(int citation : citations){
            int temp = citation > len ? len : citation;
            if(temp == 0)
                continue;
            cnts[temp - 1]++;
        }

        for(int i = len - 2; i >= 0; i--){
            cnts[i] += cnts[i+1];
        }
        
        for(int i = 0; i < len; i++){
            if(i+1 > cnts[i]){
                break;
            }
            answer = i+1;
        }

        return answer;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/96965021-209b-4478-bc2b-0769331669d1)

+ 다른사람 풀이

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        Arrays.sort(citations);

        int max = 0;
        for(int i = citations.length-1; i > -1; i--){
            int min = (int)Math.min(citations[i], citations.length - i);
            if(max < min) max = min;
        }

        return max;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/cb1b7ca2-5ed8-497b-9b1a-7c95a5bd9249)
