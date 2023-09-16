# 开荒
## 1. 自动导包设置
![[Pasted image 20221224214346.png]]
##  2. 提示忽略大小写
![[Pasted image 20221224214534.png]]
## 3. 背景
![[Pasted image 20221224220033.png]]

## 4.  配置环境变量
和python相比，java在安装的自动配置了java javac javaw jshell
如果需要其他的还需要单独配置环境变量
为了后续的其他软件的方便，改一下默认的环境变量

### 1. 新建一个新的系统变量
新建一个叫做   JAVA_HOME   的变量
用 C:\Program Files\Java\jdk-19\   的变量，也就是JDK的安装路劲
![[Pasted image 20221221204200.png]]

### 2. 在Path里面引用
![[Pasted image 20221221204404.png]]

### 3. 偷懒方法(BUG处理方法)
直接在Path里面加C:\Program Files\Java\jdk-19\Bin
但用其他软件的时候会改变这个路径下的文件，可能出问题
但是如果出现了重启就没了环境变量的时候就用这个方法
但JAVA_HOME要照做，其他开发中的软件依然依赖这个JAVA_HOME

# 一、 IDEA项目结构
project(项目)
module(模块)
package(包)---文件夹
class(类)

# 二、 快捷键
ctrl+alt+L自动格式化代码
Ctrl+Alt+V自动补全左侧语句
Ctrl+Alt+T快捷布置循环（选中后）

# 三、 快捷代码
vscode也有
## 1. psvm/main
~~~java
public static void main(String[] args) {    
}
~~~
## 2.soup
~~~java
System.out.println();
~~~
## 2.sout
~~~java
System.out.print();
~~~

# 四、 项目和模块的操作
## 1. 类的操作
* 删除类
	delete
* 修改类名
	refactor-rename
* 新建类
## 2. 模块的操作
1. 新建模块
2. 删除模块
3. 修改模块
4. 导入模块
## 3. 项目的操作
1. 关闭项目
2. 新建项目
3. 打开项目
4. 修改项目