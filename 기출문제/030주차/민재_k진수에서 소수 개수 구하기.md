```java
class Solution {
    public int solution(int n, int k) {
        int answer = 0;
        String[] nums = Integer.toString(n, k).split("0");

        for (String num : nums) {
            if (num.equals(""))
                continue;

            if (isPrime(num))
                answer++;
        }
        return answer;
    }

    private boolean isPrime(String num) {
        long parseInt = Long.parseLong(num);

        if (parseInt == 2)
            return true;
        else if (parseInt == 1 || parseInt % 2 == 0)
            return false;

        for (int i = 3; i <= Math.sqrt(parseInt); i += 2)
            if (parseInt % i == 0)
                return false;

        return true;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/aac2a91c-ffb9-4185-ace0-052006df52e5)
