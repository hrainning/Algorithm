## 题目描述

定义栈的数据结构，请在该类型中实现一个能够得到栈中所含最小元素的min函数（时间复杂度应为O（1））。 

  注意：保证测试中不会当栈为空的时候，对栈调用pop()或者min()或者top()方法。

## 解题思路

错误思路：设置一个变量存最小元素。这个思路有个问题，当栈顶的最小元素弹出时，要返回最小元素，那么这个变量中的值将无值可取。

思路：设置一个辅助的最小栈，每次压栈时若入栈的元素比min中的栈顶元素小或等于则入栈，否则不如栈。弹出时，若两个站顶相同时，则一起弹出。

这个机制保证了辅助最小栈中任一个元素在最小栈中的位置始终小于等于在原始栈中的位置，确保了在原始栈中有元素时也能每次都弹出最小栈。

举例：

data中依次入栈：5，2，1，4，7，1

则min依次入栈 ：5，2，1，no,no,1

## 代码

```java
import java.util.Stack;

public class Solution {

    Stack<Integer> stack = new Stack<Integer>();
    Stack<Integer> min = new Stack<Integer>();
    public void push(int node) {
        stack.push(node);
        if(min.isEmpty()) {
            min.push(node);
        } else if(node <= min.peek()) {
            min.push(node);
        }
    }
    
    public void pop() {
        if(stack.peek() == min.peek()) {
            min.pop();
        }
        stack.pop();
    }
    
    public int top() {
        return stack.peek();
    }
    
    public int min() {
        return min.peek();
    }
}
```

