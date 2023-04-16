* 수열문제인듯
```java
class Solution {
    final int div = 1_000_000_007;
    public int solution(int n) {
        int[] arr ={1,2,0};

        if(n < 3)
            return arr[n];

        for(int i = 2; i < n; i++){
            arr[i % 3] = (arr[(i + 1) % 3] + arr[(i + 2) % 3]) % div;
        }
        
        return arr[(n - 1) % 3];
    }
}
```
![image](https://user-images.githubusercontent.com/92290312/232289531-595a89b7-ce57-4be1-8ec4-d0c69766f568.png)
