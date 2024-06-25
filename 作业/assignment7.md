# Assignment #7: April 月考

Updated 1557 GMT+8 Apr 3, 2024

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

### 27706: 逐词倒放

http://cs101.openjudge.cn/practice/27706/

思路：

代码

```python
l=input().split()
for i in l[::-1]:
    print(i,end=' ')
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 0](../images/24b1acb79a12a330be65ebafb2657b28beacefb34f9e7813daed11e100dad5b2.png)  

### 27951: 机器翻译

http://cs101.openjudge.cn/practice/27951/

思路：

代码

```python
M,N=map(int,input().split())
queue=[-1]*M
l=input().split()
translate=0
for i in range(N):
    if l[i] in queue:
        continue
    else:
        queue.pop(0)
        queue.append(l[i])
        translate+=1
print(translate)
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 1](../images/eea58682b1b965c9ccd0bdba6f4cdcd6c4455b24741f5d323334edd867f5eb4b.png)  

### 27932: Less or Equal

http://cs101.openjudge.cn/practice/27932/

思路：

代码

```python
n,k=map(int,input().split())
arr=[int(i) for i in input().split()]
arr.sort()
if k==n:
    print(arr[k-1])
elif k==0:
    if arr[0]>1:
        print(1)
    else:
        print(-1)
elif arr[k-1]<arr[k]:
    print(arr[k-1])
else:
    print(-1)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 2](../images/f0faa8f12ecee15a719fd94083383d5b54d421a8c56d4684618637503f6ed0fd.png)  

### 27948: FBI树

http://cs101.openjudge.cn/practice/27948/

思路：

代码

```python
class Node():
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def build(S):
    n=len(S)
    if ('0' in S)&('1' in S):
        node=Node('F')
    elif '0' in S:
        node=Node('B')
    else:
        node=Node('I')
    if n>1:
        S1=S[:n//2]
        S2=S[n//2:]
        node.left=build(S1)
        node.right=build(S2)
    return node
    
def postorder(node):
    if node.left:
        postorder(node.left)
    if node.right:
        postorder(node.right)
    print(node.val,end='')

N=int(input())
S=input()
root=build(S)
postorder(root)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 3](../images/4414c9a7a145f1dd683daeb1bba83d8f93a562255894eab8a83f48c7fb492931.png)  

### 27925: 小组队列

http://cs101.openjudge.cn/practice/27925/

思路：

代码

```python
# 

```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

### 27928: 遍历树

http://cs101.openjudge.cn/practice/27928/

思路：

代码

```python
# 

```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==

## 2. 学习总结和收获

感觉题目思路基本还算清楚，但是实际编程中还是遇到了很多问题。Less or Equal的边界条件错了好几次，FBI树一开始忘记整除和除的区分了，小组队列知道思路但是自己写的时候有点迷，还是Runtime Error了。总体上感觉就是练的不够多，之后有时间的话再刷刷题吧。
