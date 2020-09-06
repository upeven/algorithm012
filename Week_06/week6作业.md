---
title: week6作业
created: '2020-09-06T13:33:28.636Z'
modified: '2020-09-06T13:51:59.908Z'
---

# week6作业
## 1、回文子串：给定一个字符串，你的任务是计算这个字符串中有多少个回文子串。

具有不同开始位置或结束位置的子串，即使是由相同的字符组成，也会被视作不同的子串。

```Java
class Solution {

    int sum = 0;
    public int countSubstrings(String s) {
       
        for(int i =0; i<s.length(); i++) {
            count(s,i,i);
            count(s,i,i+1);
        }
        return sum;
    }
    
    public void count(String s, int start, int end){
        while(start >= 0 && end <s.length() && s.charAt(start) == s.charAt(end)){
            sum++;
            start--;
            end++;
        }
    }

}
```
## 2、任务调度器：给定一个用字符数组表示的 CPU 需要执行的任务列表。其中包含使用大写的 A - Z 字母表示的26 种不同种类的任务。任务可以以任意顺序执行，并且每个任务都可以在 1 个单位时间内执行完。CPU 在任何一个单位时间内都可以执行一个任务，或者在待命状态。

然而，两个相同种类的任务之间必须有长度为 n 的冷却时间，因此至少有连续 n 个单位时间内 CPU 在执行不同的任务，或者在待命状态。

你需要计算完成所有任务所需要的最短时间。
```Java
class Solution {
    public int leastInterval(char[] tasks, int n) {
        int[] count = new int[26];
        for(int i = 0; i < tasks.length; i++){
            count[tasks[i] - 'A']++;
        }
        Arrays.sort(count);
        int maxCount = 0;
        for(int i = 25; i>= 0; i--){
            if(count[i] != count[25]){
                break;
            }
            maxCount++;
        }

        return Math.max((count[25] -1) * (n +1) + maxCount,tasks.length);

    }
}
```

