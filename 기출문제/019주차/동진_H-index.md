
<img width="388" alt="스크린샷 2023-06-22 오후 9 07 51" src="https://github.com/koreaIT-study/programmers/assets/82895809/00881d61-8180-4e21-823a-19e081cd4dce">

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;

        Arrays.sort(citations);
        for (int i = 0; i < citations.length; i++) {
//            System.out.println(citations[i]);
            int h = citations.length - i;
            if(citations[i] >= h){
                answer = h;
                break;
            }
        }
        return answer;
    }
}
```

<img width="371" alt="스크린샷 2023-06-22 오후 9 08 47" src="https://github.com/koreaIT-study/programmers/assets/82895809/4aff00ec-5a3e-4ff6-a147-f2f8e53c9b41">

```java
import java.util.*;

class Solution {
    public int solution(int[] citations) {
        int answer = 0;

        Arrays.sort(citations);
        for (int i = 0; i < citations.length; i++) {
//            System.out.println(citations[i]);
            answer = citations.length - i;
            if(citations[i] >= answer)
                break;
        }
        return answer;
    }
}
```
