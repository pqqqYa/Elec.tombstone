# 1. 判断字符类型
## 1.无脑的方式
```python
	words = input()
	a,b,c,d,e=0,0,0,0,0
	for word in words:
	if 'a' <= word <= 'z':
	        a += 1
	    elif 'A' <= word <= 'Z':
	        b += 1
	    elif '0' <= word <= '9':
	        c += 1
	    elif word==' ':
	        d+=1
	    else:
	        e+=1
	print('{} {} {} {} {}'.format(a, b, c, d, e))
```
## 2. [[#5. is函数|is函数]]
```python
a=input()
x,y,z=0,0,0
for b in a:
  if b.isalpha():
     x+=1
  elif b.isdigit():
     y+=1
  else:z+=1
print("letter = {}, digit = {}, other ={}".format(x,y,z))
```
# 2. 格式化输出
## 1. 有效数字
用到了[[程序设计I#2. type.format|format完整使用]]
```python
print("{:.3f}".format(a))  #保留3位有效数字
```
## 2. 在同一行输出
如果里面为空白就没有间隔
```python
for i in range(1,4)
print(i,end='<任意字符串>')
#1+2+3
```
## 3. 相加 
*s=s+1和s+=s是一个相同的*
## 4. print里面的组合
用<,>是有一个空格的
用<+>是没有空格的
```python
print("1"+"2"+"3")
print("1","2","3")
#123
#1 2 3
```
# 3. for循环
```python
for i in range (1，10):#左开右闭
    print(i,end=" ")
#1 2 3 4 5 6 7 8 9
#for i in range(起始值(默认0)，终值，步长):步长默认为1 
``` 
可以利用步长[[#3. 倒序输出|倒序输出]]
```python
for i in range(1，4，-1):     
print("1",i)     
#1 3  
#1 2
#1 1
```

# 4. 索引
## 1. 索引
print(x[1])#第二个
```python
n=int(input())
a='人生苦短我用python'
for i in range (n):
    print('{}'.format(a[i]),end=', ')
```
## 2. 切片
print(x[0:4])#第一个到第5个不包括第五个（切片）
## 3. 倒序输出 
print(x[::-1])倒着输出，最后一个是步长

# 5.数据类型转化
## 1. eval评估函数  
```python
x=eval(input())  
y=eval(input())  
print(x+y)
#写出x+y=z而不是xy
```
## 2. int强行取整
## 3. float浮点数
## 4. str字符串类型
# 6.数学函数
## 1. 次方
```python
print(pow(x,y))   #x的y次方
```
# 7.自定义一个函数
```python
def print_wt(a,b)
    c=a*int(b)
    print(c)
    
x=input()
y=input()
print_wt(x,y)#打印b次a
```
# 8. if函数
## 1. 原理
```python
if <>or<> (<>and<>):
elif < >:
else:
```
## 2. 实例：判断闰年
使用了[[程序设计I#7.自定义一个函数|自定义函数]]
注意返回值不是数字是true或者false
```python
def rn (n):
    if (n%4==0 and n%100!=0) or (n%400==0):
        return True
    else:
        return False#让外面的if函数可以判断对错
N=eval(input())
if rn(N):
    print(True)
else :
    print(False)
```
# 9. format格式
## 1. type.f
```python
print(f'苹果{x}只，橙子{y}只，李子{z}只。')
```
## 2. type.format
```python
print('苹果{}只，橙子{}只，李子{}只。'.format(x,y,z))
```
{}里面可以添加字符，指定加入后面的哪一个字符
## 3. type.%
```python
print("%.2f"%h2," ","%.2f"%h1)
```
# 10. 各种“小”函数
## 1. len函数
统计字符串中有多少个元素
统计英文句子中单词数目
```python
s=input()
A=len(s.split(' '))
print(A)
```
## 2. max函数min函数
```python
print(max(a,b,c))
print(min(a,b,c))
```
求abc里面的最小值
## 3. 分割函数split()
用到了[[#1. type.f|f格式]]
```python
zs,xs=input().split('.')
print(f'整数部分是{zs},小数部分是{xs}')
```
## 4. 大小写互换
字符串替换，有大写P改成小写p
用到了[[#2. 在同一行输出|end=“”]]
```python
x=input()
y=len(x)
for i in range(y):
    if x[i] == 'p':
        print(x[i].upper(),end="")
    else:
        print(x[i],end="")
```
## 5. is函数
```python
a=input()
for i in a:
    if i.isalpha():
        if i.isupper():
            print("大写字母")
        elif i.islower():
            print("小写字母")
    elif i.isdigit():   #数字
        if isinstance(a, int):
            print('整数')
        elif isinstance(a, float):
                print('浮点数')
        else:print("复数")
    else:
        print("其他符号")
```
## 6. map函数
输入x,y
先用[[#3. 分割函数split()|split]]分开，再用map加载到里面(嵌套了一个int)
```python
x,y= map(int,input().split(","))
```
## 7. try 分段函数计算
当try里面的无法运行时(报错)时，运行except里面的内容
```python
try:
    x=eval(input())
    if x>0:
    print("输入正确")#如果x没有输入一个数字会直接报错
except:
    print("输入错误")
```
# 11. 列表
用到了[[#1. 索引|索引]]
```python
s=int(input())
z=['一','二','三','四','五','六','七','八','九','十','十一','十二']
print(z[s-1]+'月份')
```
# 12.数学题
## 1. 蒙特卡洛法
使用蒙特卡洛法求出曲线y=x*x与x轴之间在0-1范围内的面积‪‬‪‬‪‬‪‬‪‬‬‫‬‪‬‪‬‪‬‪‬‪
种子数为10‪‬‪‬‪‬‪‬‪‬‬
使用100000个点进行计算
结果保留3位小数
```python
import random
m,n=100000,0.0
random.seed(10)
for i in range(1,m+1):
    x,y=random.random(),random.random()
    if y <=x*x:
        n=n+1
    s=n/m
print("{:.3f}".format(s))
```
## 2. 素数
倒着找素数，找到的第一个素数就是最大素数
```python
def isp(m):
   for i in range(n,1,-1):
       for j in range(2,i):
           if i % j == 0:
               break
           else:
               print(i)
               break
n = int(input())
isp(n)
```
## 3. 二分法求平方根
设计一个用二分法求平方根计算一个大于或等于 1 的实数 n 的平方根的函数sqrt_binary(n)，计算精度控制在计算结果的平方与输入的误差不大于1e-6。
```python
from math import sqrt
def sqrt_binary(num):
    a=1e-6
    high=num
    down=0
    while 1:
        mid=(high+down)/2
        if mid**2>num:
            x=mid**2-num
        else:
            x=num-mid**2
        if x<a:
            return mid
        else:
            if mid**2>num:
                high=mid
            elif mid**2<num:
                down=mid
num = float(input())
print(sqrt_binary(num))
print(sqrt(num))
```