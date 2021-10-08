# LeetCode - 54. Spiral Matrix

https://leetcode.com/problems/spiral-matrix/
  
주어진 배열을 나선형으로 돌았을 때, 그 순서를 반환하기.

```Java

class Solution {
    int[][] mtrx;
    boolean[][] visit;
    List<Integer> output;
    int idx;
    
    public List<Integer> spiralOrder(int[][] matrix) {
        mtrx = matrix;
        int x = 0, y = 0;
        visit = new boolean[matrix.length][matrix[0].length];
        // output = new int[matrix.length*matrix[0].length];
        output = new ArrayList<Integer>();
        
        moveRight(x, y);
        
        return output;
    }
    
    public void moveRight(int x, int y) {
        if(x >= mtrx.length || y >= mtrx[0].length)
            return;
        int i = y;
        while(true) {
            if(visit[x][i] == false) {
                visit[x][i] = true;
                output.add(mtrx[x][i]);
                System.out.println("경로 : " + mtrx[x][i]);
                if(i<mtrx[0].length-1 && visit[x][i+1] == false)
                    i++;
            }
            else {
                break;
            }
        }
        if(x+1 > mtrx.length-1 || visit[x+1][i] == true)
            return;
        moveDown(x+1, i);
        return;
    }
    
    public void moveDown(int x, int y) {
        if(x >= mtrx.length || y >= mtrx[0].length)
            return;
        int i = x;
        while(true) {
            if(visit[i][y] == false) {
                visit[i][y] = true;
                output.add(mtrx[i][y]);
                System.out.println("경로 : " + mtrx[i][y]);
                if(i<mtrx.length-1 && visit[i+1][y] == false)
                    i++;
            }
            else {
                break;
            }
        }
        if(y-1 < 0 || visit[i][y-1] == true)
            return;
        moveLeft(i, y-1);
        return;

    }
    
    public void moveLeft(int x, int y) {
        if(x >= mtrx.length || y >= mtrx[0].length)
            return;
        int i = y;
        while(true) {
            if(visit[x][i] == false) {
                visit[x][i] = true;
                output.add(mtrx[x][i]);
                System.out.println("경로 : " + mtrx[x][i]);
                if(i<mtrx[0].length-1 && i > 0 && visit[x][i-1] == false)
                    i--;
            }
            else {
                break;
            }
        }
        if(x-1 < 0 || visit[x-1][i] == true)
            return;
        moveUp(x-1, i);
        return;
    }
    
    public void moveUp(int x, int y) {
        if(x >= mtrx.length || y >= mtrx[0].length)
            return;
        int i = x;
        while(true) {
            if(visit[i][y] == false) {
                visit[i][y] = true;
                output.add(mtrx[i][y]);
                System.out.println("경로 : " + mtrx[i][y]);
                if(i > 0 && i < mtrx.length-1 && visit[i-1][y] == false)
                    i--;
            }
            else {
                break;
            }
        }
        if(y+1 > mtrx[0].length-1 || visit[i][y+1] == true)
            return;
        moveRight(i, y+1);
        return;
    }
}

```

시간복잡도 : O(N)
모든 배열을 1회만 탐색하기 때문에 O(N) 안에 끝낼 수 있다.
<br />