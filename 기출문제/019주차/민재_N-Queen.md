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
