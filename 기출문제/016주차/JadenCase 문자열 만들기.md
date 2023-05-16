```java
import java.util.Arrays;

import static java.lang.Integer.parseInt;

class Solution {
    public String solution(String s) {
        final StringBuilder sb = new StringBuilder();
        final String[] split = s.split(" ");
        
        for (int i = 0; i < split.length; i++) {
            final String e = split[i];
            System.out.println(e.length());

            if (e.length() == 0) {
                sb.append(" ");
                continue;
            }
            if (i == split.length - 1) 
                sb.append(e.substring(0, 1).toUpperCase()).append(e.substring(1).toLowerCase());
            else
                sb.append(e.substring(0, 1).toUpperCase()).append(e.substring(1).toLowerCase()).append(" ");
        }

        if(s.endsWith(" "))
            sb.append(" ");
        
        return sb.toString();
    }
}
```

<img width="294" alt="image" src="https://github.com/koreaIT-study/programmers/assets/82895809/98b8be1a-ecf0-4765-9470-daa01d7893a7">
