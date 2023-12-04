# leetcode-problems-recording
Catergorization of solved problems 
Account: tajiro
## 双指针
### 滑动窗口
```cpp
vector<int> map(128,0);
int i =  0, j = 0 len = 0; //len和题目要求的结果相关
while (j < s.size()) {
    m[s[j]]++; //先更新表
    while (需要窗口缩小的条件发生时）{
        m[s[i]]--;
        i++;
        ... //和更新结果相关的操作
    }
    j++; //窗口扩大                 
}
return len;
```  
1. 76
2. 3/剑指offer48
 
## 动态规划
给数组dp[i][j]赋值时，要从小的span（i，j的间距小）开始赋值。
### 词典
1. [面试题 17.13. 恢复空格](https://leetcode-cn.com/problems/re-space-lcci/)
2. [139. 单词拆分](https://leetcode-cn.com/problems/word-break/)
3. [140. 单词拆分 II](https://leetcode-cn.com/problems/word-break-ii/)
### 匹配
1. [44. 通配符匹配](https://leetcode-cn.com/problems/wildcard-matching/)
2. [剑指 Offer 19. 正则表达式匹配](https://leetcode-cn.com/problems/zheng-ze-biao-da-shi-pi-pei-lcof/)

## 回溯
模版
```cpp
int main(vector<int>& nums) {
        ...
        backtrack(..., track, visited);
        return 0;
    }
    void backtrack(..., vector<int> track, vector<bool>& visited) {
        if (track.size() == N) { //track满足条件
            res.push_back(track); 
            return;
        }
				//剪枝
        for (int j = ...; j < N; j++) {  //开始回溯
            if (visited[j]) continue;    //条件在刚进入for，backtrack之前判断
            track.push_back(...);     //更新track、visited状态
            visited[j] = true;
            backtrack(..., track, visited);
            visited[j] = false;  //track、visited恢复成原来的状态
            track.pop_back();
        }        
    }
```
### 数组元素之和
1.[18. 四数之和](https://leetcode-cn.com/problems/4sum/)

## 贪心
### 区间问题
1. 435
2. 452
3. 1024

## 单调栈
单调栈的用途：找到左/右方向上第一个比下标为栈顶的元素小/大的下标。
单调栈的特点：栈尾总是最大/小的元素的下标（常用双向队列实现)。栈顶是左方向上第一个比正在遍历的元素小/大的元素的下标。
1. [84. 柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)
遍历一次用一个栈就能找到左右两个方向第一个比某下标元素小/大的元素下标。
2. [239. 滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum/)
栈尾总是最大/小的元素的下标（常用双向队列实现)。
3. [739. 每日温度](https://leetcode-cn.com/problems/daily-temperatures/)

## 树
****[366. 寻找二叉树的叶子节点](https://leetcode.cn/problems/find-leaves-of-binary-tree/)****

****[333. 最大 BST 子树](https://leetcode.cn/problems/largest-bst-subtree/)****

这两题都是通过后序遍历做的

关键是当前结点的信息要通过左右子树的返回值得到

int l = recursion(root→left)

int r = recursion(root→right)

递归函数中，传参的方式会让信息从上往下流，传返回值会从下往上流

关于BST：

用中序遍历验证二叉搜索树，一般用prev记录前驱节点，保证中序遍历中val是单调递增的。

用后序遍历验证二叉搜索树，一搬记录子树的val的区间[l, r], 来保证子树的[l, r]和cur→val的关系。

****[1257. 最小公共区域](https://leetcode.cn/problems/smallest-common-region/)****

****[1273. 删除树节点](https://leetcode.cn/problems/delete-tree-nodes/)****

求出树的edges数组（index为parent，值为childs），再dfs

## 图
权重图用二维矩阵，index i 和 j 表示两个node， 值表示两个两个node的权重

[307. 区域和检索 - 数组可修改](https://leetcode.cn/problems/range-sum-query-mutable/description/)

无权重图用邻接表，index i 表示node，对应的矩阵存放node的邻接节点

[207. 课程表](https://leetcode.cn/problems/course-schedule/?envType=study-plan-v2&envId=top-100-liked)

关于表示已访问节点的visited数组，如果node可以变色（改变值），可以用变色节省数组的开销

