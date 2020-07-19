---
title: week2作业 + 学习总结
created: '2020-07-19T05:42:39.176Z'
modified: '2020-07-19T07:07:42.866Z'
---

# week2作业 + 学习总结

### 1、两数之和
给定一个数组Nums和一个目标值，请你再该数组中找出和为目标值的那两个整数，并返回它们的小标。
```
 //暴力破解法
  public class Solution(){
      public int[] twoSum(int[] nums, int target){
        for (int i = 0; i < nums.length; i++){
          for (int j = 1; j < nums.length; j++) {
            if(nums[j] == target - nums[i]) {
              return new int[] {i,j};
            }
          }
        }
         throw new IllegalArgumentException("No two sum solution");
      }
  }

  //一遍哈希表法（空间换时间）
  class Solution() {
    public int[] twoSum( int[] nums, int target){
      Map<Integer, Integer> map = new HashMap<>();
      for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if ( map.containsKey(complement)) {
          return new int[] {map.get(complement), i};
        }
        map.put(nums[i],i);
      }

       throw new IllegalArgumentException("No two sum solution");
    }
  }
  
```

### 2、N叉树的前序遍历
给定一个N叉树，返回其节点值得前序遍历

```
 class Solution {
   public List<Integer> preorder(Node root) {
     LinkedList<Node> stack = new LinkedList<>();
     LinkedList<Integer> output = new LinkedList<>();
     if(root == null ) {
       return output;
     }

     stack.add(root);
     while(!stack.isEmpty()) {
        Node node = stack.pollLast();
        output.add(node.val);
        Collections.reverse(node.children);
        for(Node item : node.children) {
          stack.add(item);
        }

     }

     return output;
   }
 }
  
```

### 3、HahMap学习总结（初步接触，暂时不深入）
哈希表是一种非常重要的数据结构。Java中的HashMap是一个用于存储key-value键值对的集合，每一个键值对也叫做Entry。这些键值对分散存储在一个数组中，这个数组就是HashMap使用的主要数据结构，另一种为链表。其中数组中每一个元素的初始值都是null。对于HashMap我们常用的方法为:get 和 put。
##### 1、put方法的原理
比如调用hashMap.put("apple,0)，插入一个key为”apple“的元素，这时候我们需要利用一个hash函数来确定Entry的插入位置。

> ` index = Hash("Apple") `

假设最后计算出的Index是2，那么这个Entry就会插入到第二个索引上。但是这里就出现一个问题，随着Entry的增多，必然会出现哈希冲突，导致存储不均匀。此时，HashMap引入了链表来解决这个问题。特点如下：数组中的每一个元素不止是一个Entry对象，而是一个链表的头节点。每一个Entry对象通过next指针指向它的下一个节点。当信赖的Entry映射到冲突的数组位置时，只需要插入到对于的链表即可。

##### 2、get方法的原理

当我们需要从hashMap中获取一个Entry时，首先会对Key做一次Hash映射，得到对应的Index

> ` index = hash(key)`

最后根据获取的key取出相应的值，但是如果数组中每一个元素是一个链表头节点的话，就需要对该链表进行遍历，取出与目标值相同的Entry。这里有一个重点，就是后插入的Entry总是离头节点最近，因为HashMap的发明者认为，最后插入的被查找的可能性更大。

##### 3、深入理解HashMap的几个知识点

1、HashMap的初始长度是多少？为什么这么规定？
> HashMap的初始长度是16，并且每次自动扩展或是手动初始化时，长度必须是2的幂。之所以选择16，是为了服务于从key映射到Index的hash算法。为了实现搞笑的Hash算法，HashMap的发明者采用了位运算的方式。
` index = HashCode(key) & (length - 1) `

2、高并发情况下，为什么HashMap会出现死锁？
> HashMap中有一个重要的函数Rehash，这个函数在并发情况下会形成链表环。

