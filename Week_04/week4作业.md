---
title: week4作业
created: '2020-08-11T12:09:13.751Z'
modified: '2020-09-06T13:30:45.205Z'
---

# week4作业
## 1、作业
1、柠檬水找零：在柠檬水摊上，每一杯柠檬水的售价为 5 美元。

顾客排队购买你的产品，（按账单 bills 支付的顺序）一次购买一杯。

每位顾客只买一杯柠檬水，然后向你付 5 美元、10 美元或 20 美元。你必须给每个顾客正确找零，也就是说净交易是每位顾客向你支付 5 美元。

注意，一开始你手头没有任何零钱。

如果你能给每位顾客正确找零，返回 true ，否则返回 false 。

```Java
class Solution {
    public boolean lemonadeChange(int[] bills) {
         int five = 0,ten = 0;
         for(int i: bills) {
             if (i == 5) five++;
             else if (i == 10) {five--;ten++;}
             else if (ten > 0) {ten--; five--;}
             else five -=3;
             if (five < 0) return false;
         }

         return true;
    }
}
```
2、岛屿数量:给你一个由 '1'（陆地）和 '0'（水）组成的的二维网格，请你计算网格中岛屿的数量。

岛屿总是被水包围，并且每座岛屿只能由水平方向或竖直方向上相邻的陆地连接形成。

此外，你可以假设该网格的四条边均被水包围。
```Java
class Solution {
    public int numIslands(char[][] grid) {
        int islandNum = 0;
        for(int i = 0; i< grid.length;i++){
            for (int j = 0; j< grid[0].length;j++){
                if(grid[i][j] == '1'){
                    infect(grid,i,j);
                    islandNum++;
                }
            }
        }
        return islandNum;
    }

    public void infect(char[][] grid, int i, int j){
        if(i<0||i>=grid.length||
           j<0 ||j>=grid[0].length || grid[i][j]!='1') {
               return;
           }
        grid[i][j] = '2';
        infect(grid,i+1,j);
        infect(grid,i-1,j);
        infect(grid,i,j+1);
        infect(grid,i,j-1);
    }
}

```

## 2、学习总结
pass

