+ 휴.. 겨우 품
```java
class Solution {
    int cnt;
    public int solution(int n) {
        boolean[][] board = new boolean[n][n];
        dfs(board, 0);
        return cnt;
    }

    private void dfs(boolean[][] board, int row){
        if(board.length == row){
            cnt++;
            return;
        }

        for(int i= 0; i < board[0].length; i++){
            if (check(board, row, i)) {
                board[row][i] = true;
                dfs(board, row+1);
                board[row][i] = false;
            }
        }

    }

    private boolean check(boolean[][] board, int row, int col){
        int len = board.length;
        for(int i = 0; i < len; i++){
            if(i == row) continue;
            if(board[i][col]) return false;
        }
        for(int i = 0; i < len; i++){
            if(i == col) continue;
            if(board[row][i]) return false;
        }

        int tempY = row;
        int tempX = col;
        while(!isOver(len, --tempY, --tempX)){
            if(board[tempY][tempX]) return false;
        }

        tempY = row;
        tempX = col;
        while(!isOver(len, ++tempY, --tempX)){
            if(board[tempY][tempX]) return false;
        }

        tempY = row;
        tempX = col;
        while(!isOver(len, --tempY, ++tempX)){
            if(board[tempY][tempX]) return false;
        }

        tempY = row;
        tempX = col;
        while(!isOver(len, ++tempY, ++tempX)){
            if(board[tempY][tempX]) return false;
        }
        return true;
    }

    private boolean isOver(int len, int y, int x){
        return x < 0 || x >= len || y < 0 || y >= len;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/94278ded-347b-44fe-ba48-ba53956623be)

+ 다른사람 풀이
```
class Solution {
    int cnt;
    public int solution(int n) {
        NQueen nq = new NQueen();
        return nq.nQueen(n);
    }
}

class NQueen {
    public int nQueen(int n) {
        int result = 0;
        int[] cols = new int[n];
        result = backTrack(0, cols, n);

        return result;
    }

    public int backTrack(int level, int[] cols, int n) {
        int sum = 0;
        if (level == n) {
            return 1;
        } else {
            for (int i = 0; i < n; i++) {
                cols[level] = i;
                if (possible(level, cols)) {
                    sum += backTrack(level + 1, cols, n);
                }
            }
        }
        return sum;
    }


    public boolean possible(int level, int[] cols) {
        for (int i = 0; i < level; i++) {
            if (cols[i] == cols[level] || Math.abs(level - i) == Math.abs(cols[i] - cols[level])) {
                return false;
            }
        }
        return true;
    }
}
```
![image](https://github.com/koreaIT-study/programmers/assets/92290312/f5d5e993-4335-4874-832b-12c69f0b9c9c)
