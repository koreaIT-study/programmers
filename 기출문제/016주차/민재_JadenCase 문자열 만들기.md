* 예외케이스 때문에 시간이 좀 걸림
```java
class Solution {
    public String solution(String s) {
        String[] st = s.split(" ");
        StringBuilder sb = new StringBuilder();
        boolean isLastBlank = s.charAt(s.length()-1) == ' ';

        for(String word : st){
            if(!word.equals("")){
                sb.append(word.substring(0, 1).toUpperCase())
                    .append(word.substring(1).toLowerCase());
            }
            sb.append(' ');
        };

        if(!isLastBlank){
            sb.deleteCharAt(sb.length()-1);
        }
        return sb.toString();
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/ace4bcdb-fd52-48c4-8202-e99bc2af23f4)
