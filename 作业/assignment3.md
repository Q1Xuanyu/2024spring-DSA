# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by ==祁轩宇、经济学院==

**说明：**

1）The complete process to learn DSA from scratch can be broken into 4 parts:
- Learn about Time and Space complexities
- Learn the basics of individual Data Structures
- Learn the basics of Algorithms
- Practice Problems on DSA

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。

**编程环境**

==（请改为同学的操作系统、编程环境等）==

操作系统：Windows 11, version 23H2

Python编程环境：VSCode 1.87.1

C/C++编程环境：

## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/

思路：

感觉是找一个最长的递减的子序列，但是穷举的话太暴力了。最后看了群里dp的解法。

##### 代码

```python
# dp算法

n = int(input())
arr = [*map(int,input().split())]
dp = [1 for _ in range(n)]
for i in range(1, n):
    for j in range(i):
        if arr[i] <= arr[j]:
            dp[i] = max(dp[j] + 1, dp[i])
print(max(dp))
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 0](../images/c75f9dbe2e1847cc62e853cd49a1b207f8876d6623aabb6dd6f2edc561acd6a7.png)  

**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147

思路：

应该是用递归的方法做，但自己写的时候有点无从下手，看了题解之后又想了一遍递归的写法。

##### 代码

```python
# 将编号为numdisk的盘子从init杆移至desti杆 
def moveOne(numDisk : int, init : str, desti : str):
    print("{}:{}->{}".format(numDisk, init, desti))

#将numDisks个盘子从init杆借助temp杆移至desti杆
def move(numDisks : int, init : str, temp : str, desti : str):
    if numDisks == 1:
        moveOne(1, init, desti)
    else: 
        # 首先将上面的（numDisk-1）个盘子从init杆借助desti杆移至temp杆
        move(numDisks-1, init, desti, temp) 
        
        # 然后将编号为numDisks的盘子从init杆移至desti杆
        moveOne(numDisks, init, desti)
        
        # 最后将上面的（numDisks-1）个盘子从temp杆借助init杆移至desti杆 
        move(numDisks-1, temp, init, desti)

n, a, b, c = input().split()
move(int(n), a, b, c)
```

代码运行截图 ==（至少包含有"Accepted"）==
![图 1](../images/1db0101b421092c726baba08450aa4d2853fe0f01890cf6444e84111e68dc13e.png)  

**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253

思路：

##### 代码

```python
def solution(l,n,m,index=0):
    if len(l)>1:
        print(l[(index+m-1)%n],end=',')
        l.pop((index+m-1)%n)
        N=(index+m-1)%n
        return solution(l,n-1,m,N)
    else:
        return l[0]

while True:
    n,p,m = map(int,input().split())
    if (n,p,m)==(0,0,0):
        break
    else:
        l=list(range(1,n+1))
        print(solution(l,n,m,p-1))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 2](../images/16c723b778279ab69b8fba8ecec50352e26fc818764bd76e786924ce25566a7c.png)  

**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554

思路：

##### 代码

```python
n=int(input())
T=[*map(int,input().split())]
T=[(T[i],i+1) for i in range(n)]
T=sorted(T,key=lambda x:x[0])

wait=0
for i in range(n):
    print(T[i][1],end=' ')
    wait+=T[i][0]*(n-1-i)
print(f'\n{wait/n:0.2f}')
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 5](../images/a7c5a237ddd65b961489ed94a4e45dcb4c421db28e6d41ce5df4e9b194293bc8.png)  

**19963:买学区房**

http://cs101.openjudge.cn/practice/19963

思路：

##### 代码

```python
n=int(input())
pairs = [i[1:-1] for i in input().split()]
dis=[sum(map(int,i.split(','))) for i in pairs]
price=[*map(int,input().split())]
val=[dis[i]/price[i] for i in range(n)]
house=[(dis[i],price[i]) for i in range(n)]

val.sort()
price.sort()
if n%2==1:
    val_mid=val[(n-1)//2]
    price_mid=price[(n-1)//2]
else:
    val_mid=(val[n//2]+val[n//2-1])/2
    price_mid=(price[n//2]+price[n//2-1])/2

count=0
for i in house:
    if (i[0]/i[1]>val_mid) & (i[1]<price_mid):
        count+=1
print(count)
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 4](../images/eca453ff81dc91f21766d4708053cd012325512a58302e91d5850ef3d87f4fe6.png)  

**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300

思路：

##### 代码

```python
n=int(input())
l=[]
for i in range(n):
    l.append(input().split('-'))
l.sort(key=lambda x:(x[0],-ord(x[1][-1]),eval(x[1][0:-1])))

dic={}
for i in l:
    if i[0] in dic:
        dic[i[0]].append(i[1])
    else:
        dic[i[0]]=[i[1]]

for k,v in dic.items():
    print(k,end=': ')
    print(', '.join(v))
```

代码运行截图 ==（AC代码截图，至少包含有"Accepted"）==
![图 3](../images/490a4eb12928838725acedea42676737955b4b75b709b9e4081c41f45f7708fc.png)  

## 2. 学习总结和收获

1. 拦截导弹是一道典型的dp问题，对我来说是比较新奇的解法，看了题解和群里的几种写法之后感觉颇受启发。
2. 汉诺塔问题主要考察递归的方法，不过想到方法之后具体的代码实现部分还需要加强熟练度。
3. 约瑟夫问题No.2和约瑟夫问题大同小异，直接把之前的函数搬过来用了。约瑟夫问题主要是花了比较长的时间来理清楚索引值应该怎么变。
4. 后面3题解法比较直接，主要练习了一下语法和敲键盘。

OJ上的每日选做做了30道左右，后面打算加快一下进度，希望通过练习掌握好这两周新讲的内容。此外了解了一些包比如collection, bisect, permutations等等，可能在简化和优化代码上有用。
