# 二叉树

1. 了解二叉树的相关术语
2. 掌握二叉树实现方式
3. 学会遍历、不同视角

## 总结

> [!note]
>
> 1. 是否可以通过遍历解决
> 2. 如果能用遍历，在每个节点需要做什么，在什么时候做
> 3. 或者使用分解子问题的思维模式
>     1. 写出这个递归函数的定义
> 4. 每个节点要做的内容：必须结合多种情况，例如叶子节点、中间节点、根节点
>     ==多考虑几种情况，才能知道具体细节，防止出现bug==

针对二叉树的问题，解题之前一定要想清楚究竟是前中后序遍历，还是层序遍历。

1. 节点边界问题，空节点判断



##  遍历

1. DFS前中后序、递归或者栈迭代
    1. 每次访问1个节点
    2. 每次访问2个子节点
    3. 每次访问2个相邻的节点

2. BFS层序遍历

```java
//dfs
void dfs(TreeNode root) {
    if (root == null) return;
    // 前序位置
    traverse(root.left);
    // 中序位置
    traverse(root.right);
    // 后序位置
}
```

```java
// 层序遍历
void levelOrderTraverse(TreeNode root) {
    if (root == null) return;
    Queue<TreeNode> q = new LinkedList<>();
    q.offer(root);
    while (!q.isEmpty()) {
        TreeNode cur = q.poll();
        // 访问 cur 节点
        System.out.println(cur.val);
        // 把 cur 的左右子节点加入队列
        if (cur.left != null) {
            q.offer(cur.left);
        }
        if (cur.right != null) {
            q.offer(cur.right);
        }
    }
}
```



存储方式

1. 链表
2. 数组

定义方式

```java
struct TreeNode{
    int val;
    TreeNode* left,right;
    TreeNode(t):
}
```



### [144. 二叉树的前/后序遍历](https://leetcode.cn/problems/binary-tree-preorder-traversal/)

```c++
// 递归
void mypreorder(TreeNode* root, vector<int> & pre){
    if(root == nullptr) return;
    pre.push_back(root->val);
    mypreorder(root->left, pre);
    mypreorder(root->right, pre);
}
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> pre;
    mypreorder(root, pre);
    return pre;
}
```

```c++
//迭代
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> pre;
    stack<TreeNode*> s;
    if(root != nullptr) s.push(root);
    while(!s.empty()) {
        TreeNode * p = s.top();
        s.pop();
        pre.push_back(p->val);

        if(p->right)s.push(p->right);
        if(p->left)s.push(p->left);
    }
    return pre;
}
// 后序遍历是前序遍历翻转左右，再进行整体翻转，中左右->中右左->左右中
// 具体为以下三行代码
if(p->left)s.push(p->left);
if(p->right)s.push(p->right);
reverse(pre.begin(),pre.end());
```

### [94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)

```c++
vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> s;
        TreeNode* p = root;
        while(p != nullptr || !s.empty()){
            // 将所有左孩子依次入栈
            while(p != nullptr){
                s.push(p);
                p = p -> left;
            }
            p = s.top();
            res.push_back(p->val);
            s.pop();
            p = p -> right;
        }
        return res;
    }
```



### 递归计算深度

```c++
return root == nullptr ? 0 : 1 + max(maxDepth(root->left),maxDepth(root->right));
```

深度优先搜索，使用递归实现

### bfs计算深度

```c++
int maxDepth(TreeNode* root) {
    queue<TreeNode*> q;
    int depth = 0;
    if (root != nullptr) q.push(root);
    else return 0;

    while(!q.empty()) {
        int n = q.size();
        for(int i = 0; i < n; i++){
            TreeNode* node = q.front();
            if(node->left != nullptr) q.push(node -> left);
            if(node -> right != nullptr) q.push(node -> right);
            q.pop();
        }
        depth++;
    }
    return depth;
}
```

1. 用队列实现bfs
2. 假设队列中的数都是同一层级的数，每次保存该层节点数量(即队列的长度)，每次同时处理该层的所有节点，将下一层的所有节点进队
3. 处理完毕后，深度+1
4. 直到队列中为空，说明上一轮没有新加入节点



- 第一次处理第一层，深度 = 1
- 如果第二层没有节点，队列长度为0，循环结束
- 第n次循环处理第n层节点，深度=n

### 计算中序遍历序列

```c++
vector<int> inorderTraversal(TreeNode* root) {
        vector<int> res;
        stack<TreeNode*> s;
        TreeNode* p = root;
        while(p != nullptr || !s.empty()){
            // 将所有左孩子依次入栈
            while(p != nullptr){
                s.push(p);
                p = p -> left;
            }
            // 取出最后一个左孩子并输出
            p = s.top();
            res.push_back(p->val);
            s.pop();
            // 迭代为他的右孩子
            p = p -> right;
        }
        return res;
    }
```

1. 

### 108. 将有序数组转换为二叉搜索树

1. 二叉搜索树的中序遍历是升序序列
2. 每次选择升序序列中的中间数字，保证建立出来的二叉树是平衡的
3. 

### 101. 对称二叉树

- 一个树的左子树与右子树镜像对称，那么这个树是对称的。

1. 它们的两个根结点具有相同的值
2. 每个树的右子树都与另一个树的左子树镜像对称(递归)





### 105. 从前序与中序遍历序列构造二叉树

-  前中后序遍历序列就是DFS，只是在不同位置打印
- 

### 98.验证二叉搜索树

1. 使用递归从根节点开始验证每个节点是否满足小于小值大于大值

```c++
public:
bool myisValidBST(TreeNode* root, long long lower, long long upper){
    if(root == nullptr) return true;
    if(root->val >= upper || root->val <= lower) return false;
    return myisValidBST(root->left, lower , root->val) && myisValidBST(root->right, root->val, upper);
}
bool isValidBST(TreeNode* root) {
	return myisValidBST(root, LONG_MIN, LONG_MAX);
}
```

### 226. 翻转二叉树

1. 从root开始将每个节点的左右孩子交换即可(左右孩子交换的过程中，子孩子也会交换)
2. 同理，可以用层序遍历遍历每个节点，交换左右孩子即可
3. 本体重点在于发现反转二叉树就是依次将每个节点的左右孩子节点交换，进而演变成如何依次遍历每个节点

```c++
// 递归交换
TreeNode* invertTree(TreeNode* root) {
    if(root == nullptr) return root;
    swap(root->left,root->right);
    invertTree(root->left);invertTree(root->right);
    return root;
}
```

```c++
// 层序遍历交换
TreeNode* invertTree(TreeNode* root) {
    queue<TreeNode*> q;

    if(root != nullptr) q.push(root);
    while(!q.empty()) {
        TreeNode* p = q.front();
        q.pop();
        swap(p->left, p->right);
        if(p->left !=nullptr)q.push(p->left);
        if(p->right != nullptr)q.push(p->right);
    }
    return root;
}
```

### 找二叉树左下角的值

- 递归中的回溯
- 

```
int Depth = INT_MIN;
int result;
```



## 22

### [226. 翻转二叉树](https://leetcode.cn/problems/invert-binary-tree/)

直接可以通过遍历每个节点解决
对于每个节点：交换左右子树

### [116. 填充每个节点的下一个右侧节点指针](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node/)

> [!caution]
>
> 如果每次只遍历一个节点，只能把相同父节点的两个节点穿起来
>
> 因为对于不是同一个父节点的两个节点，由于需要跨越的层次更深（超过了1层），不能同时取到这两个节点

每次访问左右相邻的两个节点

通过转换后，可以抽象理解为遍历一颗三叉树





### [114. 二叉树展开为链表](https://leetcode.cn/problems/flatten-binary-tree-to-linked-list/)

> [!caution] 
>
> 题目希望我们在原地把二叉树拉平成链表。这样一来，没办法通过简单的二叉树前序遍历来解决这道题了

题目要求拉成前序遍历顺序的单链表，
那么我们就反过来按照后序遍历

```java
dfs(root.left);
dfs(root.right);
if(root.left != null){
  TreeNode left = root.left;
  TreeNode right = root.right;
  // 将left子树接到root的直接右子节点
  root.left = null;
  root.right = left;
  // 将原先的右子树的根节点 移动到左子树的尾节点的右子节点
  TreeNode tail = root;
  while(tail.right != null) tail = tail.right;
  tail.right = right;
}
```

## 后序位置

# 二叉树

1. 一般来说，DFS 的递归边界是空节点。在什么情况下，要额外把叶子节点作为递归边界？
2. 在什么情况下，DFS 需要有返回值？什么情况下不需要有返回值？
3. 在什么情况下，题目更适合用自顶向下的方法解决？什么情况下更适合用自底向上的方法解决？

## recursion递归

要分析题目什么时候可以用递，什么时候用归

1. 确定递归顺序
2. 确定状态传递方式
3. 确定是否要完全递归/不完全递归

- 递，值在递的过程中向下传递
    - 使用参数传递值
    - 一般返回值为空
    - 结果判断一般是在过程中，对外部全局变量进行更新
- 归，值在归的过程中向上传递
    - 使用返回值传递值
- 递和归结合，既有值向下传递，也有值向上传递
    -

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<Integer> res = new ArrayList<>();

    public List<Integer> preorderTraversal(TreeNode root) {
        recursion(root);
        return res;
    }
    public void recursion(TreeNode root){
        if(root == null) return;
        res.add(root.val);
        recursion(root.left);
        recursion(root.right);
    }
}
```

- 只要在递归开始对root判空，剩余地方就不用再判断了
- 减去多余的判断：如果该判断能在下一次递的过程中return，就不用再多余判断了
- 判断叶子节点：`node.left == node.right`，因为node是对象，只有两个同时为null时才相等
- 判断应该涵盖所有可能的节点，即递归的过程不能被中断

## [104. 二叉树的最大深度](https://leetcode.cn/problems/maximum-depth-of-binary-tree/description/)

```java
class Solution {
    public int maxDepth(TreeNode root) {
        return recursion(root);
    }
    public int recursion(TreeNode root){
        if(root == null) return 0;
        return Math.max(recursion(root.left), recursion(root.right)) + 1;
    }
}
```

## 111. 二叉树的最小深度

如果节点为空，创建立即数0返回
如果左子树为空，
如果右子树为空，

```java
class Solution {
    public int minDepth(TreeNode root) {
        if(root == null) return 0;
        if(root.left == null) return minDepth(root.right) + 1;
        if(root.right == null) return minDepth(root.left) + 1;
        return Math.min(minDepth(root.left), minDepth(root.right)) + 1;
    }
}
```


## 112. 路径总和

```java
class Solution {
    public boolean hasPathSum(TreeNode root, int targetSum) {
        return recursion(root, 0, targetSum);
    }
    public boolean recursion(TreeNode root, int cnt, int targetSum){
        if(root == null) return false;
        cnt += root.val;
        if(root.left == root.right) {
            return cnt == targetSum;
        }
        return recursion(root.left, cnt, targetSum) ||  recursion(root.right, cnt, targetSum);
    }
}
```

### 129. 求根节点到叶节点数字之和

```java
class Solution {
    public int res = 0;
    public int sumNumbers(TreeNode root) {
        recursion(root, 0);
        return res;
    }
    public void recursion(TreeNode root, int cnt){
        if(root == null) return ;
        cnt = cnt * 10 + root.val;
        if(root.left == root.right){
            res += cnt;
        }
        recursion(root.left, cnt);
        recursion(root.right, cnt);
    }
}
```


## 归

## 965. 单值二叉树

```java
class Solution {
    public boolean isUnivalTree(TreeNode root) {
        if(root == null) return false;
        int target = root.val;
        return dfs(root, target);
    }
    public boolean dfs(TreeNode root, int target){
        if(root == null) return true;
        if(root.val != target) return false;
        return dfs(root.left, target) && dfs(root.right, target);
    }
}
```

### 100. 相同的树

```java
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        // if(p == null || q == null) return p == q;
        if(p == q) return true;
        if(p == null || q == null) return false;
        if(p.val != q.val) return false;
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    }
}
```

### 110. 平衡二叉树

```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        return getHeight(root) != -1;
    }
    public int getHeight(TreeNode root){
        if(root == null) return 0;
        int left = getHeight(root.left);
        if(left == -1) return -1;
        int right = getHeight(root.right);
        if(right == -1 || Math.abs(right - left) > 1) return -1;
        // 计算深度
        return Math.max(getHeight(root.left), getHeight(root.right)) + 1;
    }
}
```

### 199. 二叉树的右视图

1. 如何把答案记下来
2. 如何判断节点是否需要记录

```java
class Solution {
    public List<Integer> res = new ArrayList<>();

    public List<Integer> rightSideView(TreeNode root) {
        dfs(root, 1);
        return res;
    }
    public void dfs(TreeNode root, int depth){
        if(root == null) return ;
        //  记录
        if(res.size() < depth)
            res.add(root.val);
        dfs(root.right, depth + 1);
        dfs(root.left, depth + 1);
    }
}
```

## 构建二叉树

### 654. 最大二叉树

```java
class Solution {
    public TreeNode constructMaximumBinaryTree(int[] nums) {
        TreeNode root = new TreeNode();
        root = construct(nums, 0, nums.length - 1);
        return root;
    }
    public TreeNode construct(int[] nums, int l, int r){
        if(l > r) return null;
        int max = l;
        for(int i = l; i <= r; i++){
            if(nums[i] > nums[max]) max = i;
        }
        TreeNode root = new TreeNode();
        root.val = nums[max];
        root.left = construct(nums, l, max - 1);
        root.right = construct( nums, max + 1, r);
        return root;
    }
}
```

## 105. 从前序与中序遍历序列构造二叉树

还是递归
关键是要找到每次的子前序和子中序序列
