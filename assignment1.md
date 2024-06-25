# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by ==祁轩宇、经济学院==

- [Assignment #1: 拉齐大家Python水平](#assignment-1-拉齐大家python水平)
  - [1. 题目](#1-题目)
    - [20742: 泰波拿契數](#20742-泰波拿契數)
        - [代码](#代码)
    - [58A. Chat room](#58a-chat-room)
        - [代码](#代码-1)
    - [118A. String Task](#118a-string-task)
        - [代码](#代码-2)
    - [22359: Goldbach Conjecture](#22359-goldbach-conjecture)
        - [代码](#代码-3)
    - [23563: 多项式时间复杂度](#23563-多项式时间复杂度)
        - [代码](#代码-4)
    - [24684: 直播计票](#24684-直播计票)
        - [代码](#代码-5)
  - [2. 学习总结和收获](#2-学习总结和收获)

**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora <https://typoraio.cn> ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, <https://pku.instructure.com>, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。

**编程环境：**

==（请改为同学的操作系统、编程环境等）==

操作系统：Windows 11, version 23H2

Python编程环境：VSCode 1.87.1

C/C++编程环境：

## 1. 题目

### 20742: 泰波拿契數

<http://cs101.openjudge.cn/practice/20742/>

思路：

##### 代码

```python
n=int(input())
List=[0,1,1]
if n>=3:
    for i in range(3,n+1):
        List.append(List[i-3]+List[i-2]+List[i-1])
print(List[n])
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 0](../images/2cce0c5ca9e82a43b98d38744c0c66d7c67ac7deb22d3f21c59fe449889725de.png)  

### 58A. Chat room

greedy/strings, 1000, <http://codeforces.com/problemset/problem/58/A>

思路：

##### 代码

```python
s=input()
l=[]
for char in s:
    l.append(char)

word='hello'
check='NO'
for i in range(len(word)):
    while len(l)>0:
        if word[i]!=l[0]:
            l.pop(0)
        else:
            l.pop(0)
            if i==len(word)-1:
                check='YES'
            break
print(check)
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 4](../images/ba3b24a81e6fe398aae3b3d8114923bbe3de78add77ec8dd65be1f2b2c2c91ce.png)  

### 118A. String Task

implementation/strings, 1000, <http://codeforces.com/problemset/problem/118/A>

思路：

##### 代码

```python
s=input()
s=s.lower()
Vowels='aoyeui'

l=[]
for char in s:
    if char in Vowels:
        continue
    else:
        l.append('.'+char)

print(''.join(l))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 5](../images/ea06fbca821481ef383c45ad29dc0fb469ba66b62d48a648052e20d11f14c1b7.png)  

### 22359: Goldbach Conjecture

<http://cs101.openjudge.cn/practice/22359/>

思路：

##### 代码

```python
def IsPrime(n):
    check=1
    for i in range(2,int(n**0.5)+1):
        if n%i==0:
            check=0
    return(check)

n=int(input())
for a in range(2,round(n/2)):
    if IsPrime(a)&IsPrime(n-a):
        print(a,n-a)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 1](../images/7430f4cf55b4ee2fbe70aafbcd4359d448d368b665ac5fee9e96b82a66aacd84.png)  

### 23563: 多项式时间复杂度

<http://cs101.openjudge.cn/practice/23563/>

思路：

##### 代码

```python
List=input().split("+")
Max=0
for i in List:
    a=i.split("^")[0]
    b=int(i.split("^")[1])
    if a[0]=='0':
        continue
    if b>Max:
        Max=b
print(f'n^{Max}')
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 2](../images/f7ee363f01abb4136d1146a4e363dcfee81b7e5c5a1b89ab524e82d40ab7836d.png)  

### 24684: 直播计票

<http://cs101.openjudge.cn/practice/24684/>

思路：

##### 代码

```python
List=list(map(int,input().split()))
Set=set(List)
Count={}
for i in Set:
    if List.count(i) in Count:
        Count[List.count(i)]+=[i]
    else:
        Count[List.count(i)]=[i]
Max=Count[max(Count.keys())]
Max.sort()
print(" ".join(map(str,Max)))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 3](../images/f5414fd45f345993845fc1767cfada2c8555af16fe491b40200b19e92a360079.png)  

## 2. 学习总结和收获

因为忘记了做题用的时间所以没有标，不过第一周的题目只要熟悉python的语法应该没有什么难度。

本人之前选的是计概C的python，所以虽然自认为基础的语法还算熟悉，但是算法方面的基础可以说是空白 X_X ，一开始看到群里说的贪心，dfs什么的一脸懵（）。看到上学期计概B的内容以及群里大佬的解法之后觉得自己提升空间很大hh。

目前是努力跟进OJ每日选做的内容，虽然做了20道之后开始感到吃力了x，之后的题目大概就是对我来说比较新的内容吧，算是边做边学。毕竟自己基础有限，高年级还要兼顾课程外的一些事情，希望就是能在这门课上学有所成吧。
