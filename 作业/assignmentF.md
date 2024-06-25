# Assignment #F: All-Killed 满分

Updated 1844 GMT+8 May 20, 2024

2024 spring, Complied by ==祁轩宇、经济学院==

**说明：**

1）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

2）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

3）如果不能在截止前提交作业，请写明原因。

**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：Windows 11, version 23H2

Python编程环境：VSCode 1.87.1

C/C++编程环境：

## 1. 题目

### 22485: 升空的焰火，从侧面看

http://cs101.openjudge.cn/practice/22485/

思路：

代码

```python
from collections import deque

def right_view(n, tree):
    queue = deque([(1, tree[1])])  # start with root node
    right_view = []

    while queue:
        level_size = len(queue)
        for i in range(level_size):
            node, children = queue.popleft()
            if children[0] != -1:
                queue.append((children[0], tree[children[0]]))
            if children[1] != -1:
                queue.append((children[1], tree[children[1]]))
        right_view.append(node)

    return right_view

n = int(input())
tree = {1: [-1, -1] for _ in range(n+1)}  # initialize tree with -1s
for i in range(1, n+1):
    left, right = map(int, input().split())
    tree[i] = [left, right]

result = right_view(n, tree)
print(' '.join(map(str, result)))
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 1](../images/7791ffd3e1aad88663931f89a50bd0e2f61f2b407d46806ad1b37052ce214f02.png)  


### 28203:【模板】单调栈

http://cs101.openjudge.cn/practice/28203/

思路：

代码

```python
n = int(input())
ans = [0 for _ in range(n)]
l = list(map(int, input().split()))
stack = []
i = 0
while i < n:
    while stack and l[i] > l[stack[-1]]:
        ans[stack.pop()] = i + 1
    stack.append(i)
    i += 1
print(*ans)

```

代码运行截图 ==（至少包含有"Accepted"）==
![图 2](../images/e7384646a007c1768e9646356063c54dd9fceb8f34eeb6012d7dc9f5ad5cfa41.png)  

### 09202: 舰队、海域出击！

http://cs101.openjudge.cn/practice/09202/

思路：

代码

```python
from collections import defaultdict

def dfs(p):
    vis[p] = True
    for q in graph[p]:
        in_degree[q] -= 1
        if in_degree[q] == 0:
            dfs(q)

for _ in range(int(input())):
    n, m = map(int, input().split())
    graph = defaultdict(list)
    in_degree = [0] * (n + 1)
    vis = [False] * (n + 1) 
    for _ in range(m):
        x, y = map(int, input().split())
        graph[x].append(y)
        in_degree[y] += 1
    for k in range(1, n + 1):  
        if in_degree[k] == 0 and not vis[k]:  
            dfs(k)
    flag = any(not vis[i] for i in range(1, n + 1))  
    print('Yes' if flag else 'No')

```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 3](../images/5a09ddaeaab04ed99c1797d4a4c3dd2fd7ec60d76447920b71e07b1230ad40bd.png)  

### 04135: 月度开销

http://cs101.openjudge.cn/practice/04135/

思路：

代码

```python
n,m = map(int, input().split())
expenditure = []
for _ in range(n):
    expenditure.append(int(input()))

def check(x):
    num, s = 1, 0
    for i in range(n):
        if s + expenditure[i] > x:
            s = expenditure[i]
            num += 1
        else:
            s += expenditure[i]
    
    return [False, True][num > m]

# https://github.com/python/cpython/blob/main/Lib/bisect.py
lo = max(expenditure)
# hi = sum(expenditure)
hi = sum(expenditure) + 1
ans = 1
while lo < hi:
    mid = (lo + hi) // 2
    if check(mid):      # 返回True，是因为num>m，是确定不合适
        lo = mid + 1    # 所以lo可以置为 mid + 1。
    else:
        ans = mid    # 如果num==m, mid就是答案
        hi = mid
        
#print(lo)
print(ans)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 4](../images/5bd2905467f8723f298e149252695f984ae041bc39a862b990329f50aeb882f3.png)  

### 07735: 道路

http://cs101.openjudge.cn/practice/07735/

思路：

代码

```python
# 

```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

### 01182: 食物链

http://cs101.openjudge.cn/practice/01182/

思路：

代码

```python
# 

```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

## 2. 学习总结和收获

完成的时候已经考完机考了，主要是参考了题解。最近所有精力都在保研上面，最后一次作业没能及时完成，有点可惜。

整个学期下来算是跟着Github的课件和作业学了一遍，群里的学习氛围也非常浓厚，大一同学们的学习劲头让我有点自愧不如（），也能看到闫老师在教学上花了很多心思和时间。感谢老师的辛勤付出和同学们的互相帮助！
