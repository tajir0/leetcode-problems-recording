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

树形dp 

****[2646. 最小化旅行的价格总和](https://leetcode.cn/problems/minimize-the-total-price-of-the-trips/)****

## 图
权重图用二维矩阵，index i 和 j 表示两个node， 值表示两个两个node的权重

[307. 区域和检索 - 数组可修改](https://leetcode.cn/problems/range-sum-query-mutable/description/)

无权重图用邻接表，index i 表示node，对应的矩阵存放node的邻接节点

[207. 课程表](https://leetcode.cn/problems/course-schedule/?envType=study-plan-v2&envId=top-100-liked)

另外，关于表示已访问节点的visited数组，如果node可以变色（改变值），可以用变色节省数组的开销  

这道题为用dfs来计算总路径开销提供了新的思路：从每条边上的开销来思考 

[2477. 到达首都的最少油耗](https://leetcode.cn/problems/minimum-fuel-cost-to-report-to-the-capital/description/?envType=daily-question&envId=2023-12-05)。

有向图用邻接表vector<vector<pair<int, bool>>>，index i 表示node，对应的矩阵存放node的邻接节点和方向

[1466. 重新规划路线](https://leetcode.cn/problems/reorder-routes-to-make-all-paths-lead-to-the-city-zero/)


要用 queue 实现 Dijkstra 算法，可以采用 优先队列（Priority Queue，也称为最小堆）来维护未处理的节点。下面是基本步骤：

初始化：将起始节点的距离设为 0，其余节点设为无穷大。创建一个优先队列，用于存储节点及其当前距离。

处理队列：每次从队列中取出距离最小的节点，更新该节点的邻居节点的距离。

更新邻居节点：如果发现通过当前节点能到达某个邻居节点的距离更短，则更新该节点的最短距离，并将其重新放入队列。

重复操作：直到队列为空。

在优先队列中，节点按距离排序，从而确保总是处理距离最小的节点。这样，Dijkstra 算法能在 O((V + E) log V) 的时间复杂度下运行。
```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <unordered_map>
#include <climits>

using namespace std;

// 优先队列中的元素 (distance, node)
typedef pair<int, int> PII;

void dijkstra(int start, vector<vector<PII>>& graph, vector<int>& dist) {
    priority_queue<PII, vector<PII>, greater<PII>> pq;  // 最小堆
    pq.push({0, start});  // 起点，距离为0
    dist[start] = 0;

    while (!pq.empty()) {
        auto [currentDist, u] = pq.top();  // 当前距离最近的节点
        pq.pop();

        if (currentDist > dist[u]) continue;  // 若当前距离已经不是最短，跳过

        // 遍历邻居
        for (auto [v, weight] : graph[u]) {
            int newDist = currentDist + weight;
            if (newDist < dist[v]) {  // 找到更短路径
                dist[v] = newDist;
                pq.push({newDist, v});
            }
        }
    }
}

int main() {
    int n = 5;  // 节点数
    vector<vector<PII>> graph(n);  // 图的邻接表
    vector<int> dist(n, INT_MAX);  // 最短距离初始化为无穷大

    // 示例图 (u, v, weight)
    graph[0].push_back({1, 2});
    graph[0].push_back({2, 4});
    graph[1].push_back({2, 1});
    graph[1].push_back({3, 7});
    graph[2].push_back({4, 3});
    graph[3].push_back({4, 1});

    int start = 0;  // 起点
    dijkstra(start, graph, dist);

    // 输出从起点到其他节点的最短距离
    for (int i = 0; i < n; ++i) {
        cout << "Distance from " << start << " to " << i << ": " << dist[i] << endl;
    }

    return 0;
}
```
Dijkstra 用于带权图，寻找最短路径，使用优先队列根据当前最短距离选择节点。

BFS 通常用于无权图，寻找最短路径，使用普通队列按层顺序遍历。

```cpp
void BFS(int start, vector<vector<int>>& graph) {
    queue<int> q;
    vector<bool> visited(graph.size(), false);
    
    q.push(start);                // 将起点加入队列
    visited[start] = true;        // 标记起点为已访问
    
    while (!q.empty()) {
        int node = q.front();     // 取出队列头部的节点
        q.pop();
        
        // 处理节点 node
        
        for (int neighbor : graph[node]) {   // 遍历邻居
            if (!visited[neighbor]) {        // 如果邻居未访问
                q.push(neighbor);            // 加入队列
                visited[neighbor] = true;    // 标记为已访问
            }
        }
    }
}

```
[127.单词接龙](https://leetcode.cn/problems/word-ladder/description/?envType=study-plan-v2&envId=top-interview-150)


