---
title: week7作业
created: '2020-09-06T13:53:18.936Z'
modified: '2020-09-06T14:02:55.459Z'
---

# week7作业

## 1、爬楼梯：假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。
```Java
class Solution {
    public int climbStairs(int n) {
        int p = 0, q = 0, r = 1;
        for (int i = 1; i <= n; ++i){
            p = q;
            q = r;
            r = p + q;
        }

        return r;

    }
}
```
##2、括号生成
数字 n 代表生成括号的对数，请你设计一个函数，用于能够生成所有可能的并且 有效的 括号组合。
```Java
class Solution {
    List<String> res = new ArrayList<>();
    public List<String> generateParenthesis(int n) {
        
       
            dfs(n,n,"");
            return res;
        
    }

    private void dfs(int left,int right,String curStr){
        if(left == 0 && right ==0){
            res.add(curStr);
            return;
        }

        if(left>0){
            dfs(left -1,right,curStr + "(");
        }
        if(right > left){
            dfs(left,right -1, curStr + ")");
        }
    }
}
```
