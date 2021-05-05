# leetcode-problems-recording
Catergorization of typical problems 

## 双指针
### 滑动窗口
```cpp
vector<int> map(128,0);
int i =  0, j = 0 len = 0; //len和题目要求的结果相关
while (j < s.size()) {
    m[s[j]]++; //先更新表
    while (需要窗口缩小的条件发送时）{
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
### 词典
1. [面试题 17.13. 恢复空格](https://leetcode-cn.com/problems/re-space-lcci/)
2. [139. 单词拆分](https://leetcode-cn.com/problems/word-break/)
3. [140. 单词拆分 II](https://leetcode-cn.com/problems/word-break-ii/)
### 匹配
1. [44. 通配符匹配](https://leetcode-cn.com/problems/wildcard-matching/)
2. [剑指 Offer 19. 正则表达式匹配](https://leetcode-cn.com/problems/zheng-ze-biao-da-shi-pi-pei-lcof/)

## 回溯
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

