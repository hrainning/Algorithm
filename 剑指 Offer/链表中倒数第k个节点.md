## 题目描述

输入一个链表，输出该链表中倒数第k个结点。

## 解题思路

注意：当k超过链表长度或head==null，返回null。

思路1：设置两个节点a，b，起点为首节点，让a先走k步，然后两个开始一起走，直到a为null，b则为倒数第k个节点。

思路2：用递归/栈，先全部压栈，再返回至第k个。

## 代码

**code 1**

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        ListNode a,b;
        a = b = head;
        for (int i = 0; i < k  ; i++) {
            if (a == null) {
                return null;
            }
            a = a.next;
        }
        while (a != null) {
            a = a.next;
            b = b.next;
        }
        return b;
    }
}
```

**code 2**

```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
import java.util.*;
public class Solution {
    public ListNode FindKthToTail(ListNode head,int k) {
        Stack<ListNode> stack=new Stack<ListNode>();
        while(head != null ) {
            stack.push(head);
            head = head.next;
        }
        if (k > stack.size()) {
            return null;
        }
        while(k-- > 0) {
            head = stack.pop();
        }
        return head;
    }
}
```

