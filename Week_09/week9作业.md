---
title: week9作业
created: '2020-09-08T14:14:12.691Z'
modified: '2020-09-08T14:25:49.655Z'
---

# week9作业
## 1、字符串中的第一个唯一字符
给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。
```Java
class Solution {
    public int firstUniqChar(String s) {
        for ( int i = 0; i<s.length(); i++) {
            int first = s.indexOf(s.charAt(i));
            int last = s.lastIndexOf(s.charAt(i));
            if(first == last){
                return i;
            }
        }
        return -1;

    }
}
```

## 2、仅仅反转字母：给定一个字符串 S，返回 “反转后的” 字符串，其中不是字母的字符都保留在原地，而所有字母的位置发生反转。
```Java
class Solution {
    public String reverseOnlyLetters(String S) {
        char[] chars = S.toCharArray();
        int sIndex = 0, eIndex = chars.length -1;
        while(sIndex < eIndex){
            if(!Character.isLetter(chars[sIndex])){
                sIndex++;
            }
            if(!Character.isLetter(chars[eIndex])){
                eIndex--;
            }
            if(Character.isLetter(chars[sIndex])&& Character.isLetter(chars[eIndex])) {
                char tmp = chars[sIndex];
                chars[sIndex] = chars[eIndex];
                chars[eIndex] = tmp;
                sIndex++;
                eIndex--;
            }
        }
        return new String(chars);
    }
}
```
