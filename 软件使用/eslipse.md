[[Java考试-判断题|java]]的一个开发环境IDE，也可以开发python（不好用）
# 一、 输入联想
1.打开软件Eclipse -> Window -> Perferences
![[Pasted image 20230326094017.png]]
2.找到Java -> Editor ->Content Assist
![[Pasted image 20230326094032.png]]
3.将5中的方框内成改
~~~
.abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
~~~

# 二、 快捷输入
检查快捷键设置
![[Pasted image 20230326095313.png]]
输入syso后按Alt+/  就可以看到了

## 1. 输出
~~~java
sysout
syso
System.out.println();
~~~

## 2. main方法
~~~java
main
public static void main(String[] args) {

}
~~~
## 3. for遍历
~~~java
for
for (int i = 0; i < args.length; i++) {
   String string = args[i];
}
~~~

# 三、快捷键
## 1. 快速补全
Alt+/
## 2. 格式化代码
ctrl+shift+F
## 3. 自动生成getter/setter/构造器
alt+shift+s
## 4. 快速运行当前程序
ctrl+F11