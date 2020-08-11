---
title: week1作业 + 学习总结
created: '2020-08-11T12:09:13.751Z'
modified: '2020-08-11T12:37:00.043Z'
---

# week1作业 + 学习总结
## 1、作业
1、两数之和：给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。
```Java
//两遍哈希法
class Solution{
  public int[] twoSum(int[] nums, int target){
      Map<Integer,Integer> map = new HashMao()<>;
      for(int i = 0; i < nums.length; i++){
          map.put(nums[i],i);
      }

      for(int  i = 0 ; i < nums.length(); i ++){
          int complement = terget - nums[i];
          if(map.containsKey(complement) && map.get(complement) != i ){
            return new int[]{i,map.get(complement)};
          }
      }
      throw new IllegalArgumentException("No two sum solution");
  }
}
```
2、移动零:给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。
```Java
//暴力破解法
class Solution {
    public void moveZeroes(int[] nums) {
        int index = 0;
        for ( int i: nums ) {
            if ( i!= 0){
                nums[index++] = i;
            }
        }
        while ( index < nums.length ){
            nums[index++] = 0;
        }
        
    }
}

```

## 2、学习总结

Java中栈得源代码学习

```
public class Stack<T> extends Vector<T>
   {
    // We could use Vector methods internally for the following methods,
    // but have used Vector fields directly for efficiency (i.e. this
   // often reduces out duplicate bounds checking).

   /**
    * Compatible with JDK 1.0+.
    */
   private static final long serialVersionUID = 1224463164541339165L;
 
   /**
    * This constructor creates a new Stack, initially empty
    */
   public Stack()
   {
   }
 
   /**
    * Pushes an Object onto the top of the stack.  This method is effectively
    * the same as addElement(item).
    *
    * @param item the Object to push onto the stack
    * @return the Object pushed onto the stack
    * @see Vector#addElement(Object)
    */
   public T push(T item)
   {
     // When growing the Stack, use the Vector routines in case more
     // memory is needed.
     // Note: spec indicates that this method *always* returns obj passed in!
 
     addElement(item);
     return item;
   }
 
   /**
    * Pops an item from the stack and returns it.  The item popped is
    * removed from the Stack.
    *
    * @return the Object popped from the stack
    * @throws EmptyStackException if the stack is empty
    */
   public synchronized T pop()
   {
     if (elementCount == 0)
       throw new EmptyStackException();
 
     modCount++;
     T obj = elementData[--elementCount];
 
     // Set topmost element to null to assist the gc in cleanup.
     elementData[elementCount] = null;
     return obj;
   }
 
   /**
    * Returns the top Object on the stack without removing it.
    *
    * @return the top Object on the stack
    * @throws EmptyStackException if the stack is empty
    */
   public synchronized T peek()
   {
     if (elementCount == 0)
       throw new EmptyStackException();
 
     return elementData[elementCount - 1];
   }
 
   /**
    * Tests if the stack is empty.
    *
    * @return true if the stack contains no items, false otherwise
    */
   public synchronized boolean empty()
   {
     return elementCount == 0;
   }
 
   /**
    * Returns the position of an Object on the stack, with the top
    * most Object being at position 1, and each Object deeper in the
    * stack at depth + 1.
    *
    * @param o The object to search for
    * @return The 1 based depth of the Object, or -1 if the Object
    *         is not on the stack
    */
   public synchronized int search(Object o)
   {
     int i = elementCount;
     while (--i >= 0)
       if (equals(o, elementData[i]))
       return elementCount - i;
     return -1;
   }
 }
