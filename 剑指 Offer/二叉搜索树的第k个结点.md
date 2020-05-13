## 题目描述

给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）  中，按结点数值大小顺序第三小结点的值为4。

## 解题思路

二叉搜索树，中序遍历即是从小到大排序。

非递归总序步骤：

1. 申请一个栈，令cur = heard
2. cur压入栈中，不断的将cur.left压入栈，直到null，转3
3. 从stack中弹出一个结点node，打印结点，并令cur = node.right，转2.
4. 最终cur为null且栈为空

参考：https://www.cnblogs.com/hengzhezou/p/11027190.html

或者：https://blog.csdn.net/zgaoq/article/details/79089819

```c++
/*
struct TreeNode {
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) :
            val(x), left(NULL), right(NULL) {
    }
};
*/
class Solution {
public:
     TreeNode* KthNode(TreeNode* pRoot, int k)
     {
          stack<TreeNode*> stacks;
          if (k < 1 || pRoot == NULL) {
               return NULL;
          }
          while (pRoot!=NULL||!stacks.empty()) {
               if (pRoot!=NULL) {
                    stacks.push(pRoot);
                    pRoot = pRoot->left;
               }
               else {
                    pRoot = stacks.top();
                    stacks.pop();
                    k--;
                    if (k == 0) {
                         return pRoot;
                    }  
                    pRoot = pRoot->right;
               }
          }
          return NULL;
     }
};
```



