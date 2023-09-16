业界使用较多的是[[IDEA]]
~~~java
system.exit(0);//停止虚拟机运行
~~~
# 一.入门
先用记事本来写，再用IDEA

## 1. 写好代码
写好了文件名为  .java
~~~java
public class HelloWorld {
    public static void main(String []args) {
    //叫做main方法，表示程序的主入口
       System.out.println("你好");
       	/*叫做输出语句
		可以输出小括号里面的*/
    }
}
~~~

## 2. cmd找到文件所在地
![[cmd找到文件所在地.png]]
有[[cmd操作#2. 进入文件夹|2种方法]]进入

## 3. 用javac编译
javac是[[JDK和JRE#JDK|JDK]]提供的编译工具，把当前路径下的编译成class文件
![[控制台编译java.png]]
中间没有东西，说明编译成功，不然出来的就是错误提示
![[Java代码和编译结果.png]]
这个时候会多出来一个文件（class文件）给系统运行的时候用的

## 4. 用java运行
java也是[[JDK和JRE]]提供的一个运行代码的工具
![[控制台运行java.png]]
注意和[[#3. 用javac编译|上面]]的区别，这是是不带后缀的文件
命令也成了 **java 文件名**
[[各种编程语言的不同#高级语言的编译运行方式|关于这几步到底是在干啥]]

# 二. Notepad++
* 不用IDEA不用vscode,直接记事本写
* 为了可以打印中文，记得[[Notepad++#使用中文|修改设置]]
* 可以直接打开**命令行**开始编译
![[Notepad++快速打开控制台.png]]

# 三. 注释
~~~
单行注释  //注释信息
多行注释  /*注释信息*/
文档注释  /**注释信息*/
~~~
编译后class文件里面没有注释

# 四. 关键字
被java赋予了特殊含义的英文单词
关键字的字母全部小写
常用的代码编辑器，针对关键字有特殊的颜色标记，非常直观

## 1. class
用于(创建/定义）一个类
类是Java最基本的组成单元
~~~java
public class 类名 {
}
~~~
HelloWorld就是类的名字
{  }里面就是类的范围

## 2. void
void关键字，它代表的意思是什么也不返回
如一个方法不需要返回值时可以使用void关键字，在main方法中也是void关键字。

## 3. public
权限修饰符，和private相反

## 4. private
私有关键字
* private关键字是一个权限修饰符
* 可以修饰成员（成员变量和成员方法)
* 被private修饰的成员只能在本类中才能访问
* 针对private修饰的成员变量，如果需要被其他类使用，提供如下操作
	提供“setXxx(参数)”方法，用于给成员变量赋值，方法用public修饰
	提供“getXxx()”方法，用于获取成员变量的值，方法用public修饰

举个例子：只输出合理尺寸
~~~java
public class Pc {  
    private int size;  
    //set赋值  
    public void setSize(int x) {  
        //判断是否合理  
        if (x <= 22 && x >= 11) {  
            size = x;  
        } else {  
            System.out.println("尺寸不合理");  
        }  
    }  
    //get获取  
    public int getSize() {  
        return size;  
    }  
}
~~~

~~~java
public class PcTest {  
    public static void main(String[] args) {  
        Pc diannao = new Pc();  
        diannao.setSize(11);  
        int size = diannao.getSize();  
        if (size != 0) {  
            System.out.println(size);  
        }  
    }  
}
~~~

# 五. 字面量
告诉程序员:数据在程序中的书写格式
## 1. 字面量类型
1. 整数类型
2. 小数类型
3. 字符串类型
	* 双引号括起来的类型“你好”
4. 字符类型---单引号括起来的，内容只能有一个
	* ‘A’,‘0’,‘我’
	* 不存在‘abc’这种，会报错的
5. 布尔类型
	* 布尔值，表示真假，只有2个值：true，false
6. 空类型
	* 一个特殊的值，空值，值是：null
~~~java
public class ValueDemo {
    public static void main(String []args) {
       System.out.println(666);
       System.out.println("你好世界");
       System.out.println(true);
       System.out.println(false);
       System.out.println(null);//这一行会报错，nill不能直接打印
    }
}
~~~
空类型不能打印
## 2. 特殊字面量
~~~
\t 制表符
~~~
在打印的时候，把前面字符串的长度补齐到8，或者8的整数倍。最少补1个空格，最多补8个空格。
~~~java
public class ValueDemo {
    public static void main(String []args) {
    //"name"+"\t"这这一个整体有8字符串的长度
       System.out.println("name"+"\t"+"age");
       System.out.println("tim"+"\t"+"19");
    }
}
~~~
就不会挤在一起，打印表格数据可以用


# 六. 变量
放数据的小箱子

## 1. 定义格式
***数据类型 变量名 = 数据值；***

## 2. 使用方法
~~~java
public class ValueDemo{
    public static void main(String[] args){
       int a=10,c=10
       int b=20;
       System.out.println(a);
       //不在a=20前不加int ，因为这样会重复定义变量，报错
       a=20;
       System.out.println(a+b+c);
    }
}
10
50
~~~

## 3. 成员变量和局部变量
### I. 区别
成员变量：
	类的里面，方法的外面，可以用public,protected,private,static修饰
局部变量：
	方法中定义的变量或方法的参变量，无法被修饰
### II.共同点
都可以用final修饰(定义为常量)
### II. 成员变量的分类
* 类变量（静态变量）
用static修饰的成员变量
* 实例变量
没有使用static修饰的成员变量
~~~java
class A {
	float x ;//实例变量
	static int B ;//类变量
}
~~~
* 注意
**类变量**和该类所创建的所有对象相关联
**实例变量**和不同对象的**实例变量**互不相同
实例是指类创建的变量，类与基本类型一样，可以创建变量

## 6. 注意事项
1. 只能存一个值
2. 变量名不允许重复定义
3. 一条语句可以定义多个变量
4. 变量在使用之前一定要进行赋值
5. 变量的作用域范围

# 七. 常量
## 1. 直接常量:
~~~java
'a',1,10.3,false
~~~
## 2. 符号常量
被final修饰的，在声明时就要初始化。
* 对于基本数据类型，表示永不改变的编译时常量
* 对于普通对象，表示该引用恒定不变，不能指向另外一个对象，但是该对象本身是可以进行修改的
~~~java
final int MAX=10;
final String MAJOR="信管"
~~~


# 八. 数据存储
在java中不同进制开头不同（JDK7以后的才有）
* 二进制:代码中以0b开头
* 十进制:前面不加任何前缀
* 八进制:代码中以0开头
* 十六进制:代码中以Ox开头

# 九. 数据类型
[[Java面向对象#5. 基本数据类型和引用数据类型|基本数据类型和引用数据类型的根本区别]]
## 1. 基本数据类型

### 1. 整数
1. byte
2. short
3. int（默认）
4. long
	在定义long类型是，加"L"作为结尾(大小写都可以)

### 2. 浮点数
1. float
	在定义float类型是，加"F"作为结尾(大小写都可以)
2. double（默认）
**整数和小数取值范围大小关系:**
double > float > long > int > short > byte

### 3. 字符
* char

### 4. 字符串
* String
[[String字符串|详细说明]]

### 5. 布尔
* boolean
![[java数据类型.png]]
~~~java
public class ValueDemo{
    public static void main(String[] args){
       String name="ikun";
       boolean heizi=true;
       System.out.println("姓名:"+name);
       System.out.println("是不是黑子:"+heizi);
    }
}
~~~

## 2. 引用数据类型
除了了基本数据类型以外的其他

# 十. 标识符(变量名)
给[[#11. 类|类]]，[[#15. 方法|方法]]，变量等起的名字 (一个统称)

## 1.行业常见

## 2. 硬性要求
1. 由数字、字母、下划线(__)和美元符($)组成
2. 不能以数字开头
3. 不能是关键字
4. 区分大小写

## 3. 建议
做到***见名知意***
### Ⅰ. 小驼峰命名法：方法、变量
* 规范1;标识符是一个单词的时候，全部小写
	范例1: name
* 规范2:标识符由多个单词组成的时候，第一个单词首字母小写，其他单词首字母大写
	范例2: firstName
### Ⅱ.大驼峰命名法:类名
* 规范1∶标识符是一个单词的时候，首字母大写
	范例1:Student
* 规范2:标识符由多个单词组成的时候，每个单词的首字母大写
	范例2: GoodStudent
	
# 十一. 类
API & 面向对象
## 1. 使用步骤
* step1：导包
Scanner这个类在哪里
* 创建类像
表示准备开始用这个类了
* 接收数据
真正开始干活了

## 2. 键盘录入
### Ⅰ. 格式
第一套体系:
nextInt();    接收整数
nextDouble();     接收小数
next();    接收字符串
遇到空格，制表符，回车就停止接受。这些符号后面的数据就不会接受了而是由下一个来接收（如果有的话）

第二套体系:
nextLine();    接收字符串
可以接收空格，制表符，遇到回车才停止接受数掘

2套体系不能混用

### Ⅱ. 流程
在IDEA可以写键盘录入的时候可以利用自动导包
有一个叫做Scanner的类，可以接受键盘输入的数字
1. 导包
Scanner这个类在哪里
~~~java
import java.util.Scanner;   导包的动作必须出现在类定义的上边。
~~~
2. 创建类像
表示准备开始用Scanner
~~~java
Scanner sc = new Scanner(System.in);
上面这个格式里面，只有sc是变量名，可以变，其他的都不允许变。
~~~
3. 接收数据
真正开始干活了
~~~java
int i = sc.nextInt();
左面这个格式里面，只有i是变量名，可以变，其他的都不允许变。
int是接受整数
~~~
就相当于python里面的input()
~~~java
import java.util.Scanner;
public class demo1 {
    public static void main(String []args) {
         Scanner sc = new Scanner(System.in);
         System.out.println("请输入一个数字");
         int i = sc.nextInt();
         System.out.println(i);
    }
}
~~~
## 3. 随机数生成
Java写好一个类叫Random，这个类就可以生成一个随机数。
1. 导包
~~~java
import java.util.Random;   导包的动作必须出现在类定义的上边。
~~~
2. 创建对象
~~~java
Random r = new Random();
~~~
3. 接收数据
~~~java
int number = r.nextInt(随机数的范围)
~~~
范围的数字默认0开始一直到所写的范围

生成7-15那么就写8，最后结果输出再加上7
~~~java
import java.util.Random;  
public class 获取7到15的随机数 {  
    public static void main(String[] args) {  
        Random r = new Random();  
        int number = r.nextInt(8);   
        System.out.println(number+7);  
    }  
}
~~~
# 十二.运算符
![[java运算符.png]]
## 1.算术运算符

### Ⅰ. 基本
加减乘除
%取模（取余）
~~~java
import java.util.Scanner;
"求各位置上的数值
public class 数值拆分 { 
        public static void main(String []args) {
             try (Scanner sc = new Scanner(System.in)) {
                System.out.println("请输入一个三位数");
                int i = sc.nextInt();
                System.out.println("个位："+i%10);
                System.out.println("十位："+i/10%10);
                System.out.println("百位："+i/100%10);
            }
        }
    }
~~~
纯整数的计算不会得出小数
~~~java
System.out.println(10.0/3);
System.out.println(10/3);
3.3333333333333335
3
~~~
### Ⅱ. 进阶
数字进行运算时，数据类型不一样，要先转再计算
#### ①. 隐式转换(自动类型提升)
* 取值范围:
[[#2. 浮点数|byte < short < int < long < float< double]]
* 什么时候转换?
数据类型不一样，不能进行计算，需要转成一样的才可以进行计算。
~~~java
int a = 10;
double b = a;
System.out.println(b)
10.0
~~~
* 转换规则1:
取值范围小的，和取值范围大的进行运算，小的会先提升为大的，再进行运算
~~~java
int a = 10;
double b = 12.3;
System.out.println(a+b)
22.3
~~~
* 转换规则2:
byte short char三种类型的数据在运算的时候，都会直接先提升为int，然后再进行运算
~~~java
byte a = 10;
byte b = 20;
int c=a+b
System.out.println(c)
30
~~~

#### ②. 强制转换(手动转换)
大范围变小范围
* 如果把一个**取值范围大**的数值，赋值给**取值范围小**的变量。是不允许直接赋值的。如果一定要这么做就需要加入强制转换
* 格式：**目标数据类型变量名 =（目标数据类型）被强转的数据**；
* 数据过大会出现错误
~~~java
int b = (int)(a+c);
~~~

#### ③. 字符串的相加
* 当“+”操作中出现字符串时，这个“+”是字符串连接符，而不会将前后的数据进行拼接，并产生一个新的字符串。
* 有字符串就是拼接
~~~java
int age = 18;
System.out.println("我的年龄是"+age+"岁");//"我的年龄是18岁"
System.out.println("我的年龄是"+"age"+"岁");//"我的年龄是age岁"
//下面这一行特别注意
System.out.println(1 + 2+"abc"+ 2 +1);// "3abc21"
~~~

## 2. 自增自减运算符

### Ⅰ. 单独使用
* ++变量值加一
* - -变量的值减一
++和--无论是放在变量的前边还是后边，单独写一行结果是一样的。
~~~java
int a = 10;
a++;(++a;都可以)
System.out.println(a); //11
~~~

### Ⅱ. 参与计算
* a++和++a**不一样**，从左到右，先用或者先加
* 一般都是单独写一行(单独使用)
~~~java
int a = 10;
int b = a++
a=11 b=10
~~~

## 3. 赋值运算符
底层隐藏了一个强制类型转换
![[java赋值运算符.png]]
~~~java
int a = 10;
int b = 20;
a += b;
//把a+b，再把结果赋值给左边的变量a
//等同于a = (int)(a + b);
~~~

## 4. 关系运算符
关系运算符的结果都是boolean类型
![[java关系运算符.png]]
~~~java
boolean a=b>c
System.out.println(a);
//如果b真的大于c，a就会被赋值ture
ture
~~~

## 5. 逻辑运算符

### Ⅰ. 分类
![[java逻辑运算符分类.png]]
~~~java
System.out.println(!ture)
false
~~~
### Ⅱ. 短路逻辑运算符
![[java短路运算符.png]]
* &&短路与
与单个&是一样的
平替逻辑或，但一个符合时就不会再看下一个，提高执行效率
~~~java
int a = 10;
int b = 10;
boolean result = ++a<5 && ++b < 5;
System.out.println(result);
System.out.println(a);
System.out.println(b);
false
11
10
~~~
~~~java
int a = 10;
int b = 10;
boolean result = ++a<5 & ++b < 5;
System.out.println(result);
System.out.println(a);
System.out.println(b);
false
11
11
~~~

## 6. 三元运算符

### Ⅰ. 格式
关系表达式？表达式1：表达式2；

### Ⅱ. 计算规则
* 首先计算关系表达式的值
* 如果值为true，表达式1的值就是运算结果
* 如果值为false，表达式2的值就是运算结果

## 7. 条件运算符
可以根据条件进行计算。
~~~java
关系或逻辑表达式（条件） ? 表达式1 : 表达式2

找出整型数a和b中的大值：
int max=a>b?a:b;
~~~

## 8. 运算符优先级
![[java运算符优先级.png]]
其实就是加小括号（）
# 十三.流程控制语序
![[java流程控制语序.png]]
## 1. 顺序结构
顺序结构语句是Java程序默认的执行流程
按照代码的先后顺序，从上到下依次执行

## 2. 分支结构

### Ⅰ. If语句

#### ①. if语句的格式
~~~java
if (关系表达式1) {
    语句体1；
} else if(关系表达式2){
      语句体2；
}
    ……
} else if(关系表达式n){
      语句体n；
}
  else{
     语句体n+1；
}
~~~
#### ②.if的注意点:
1. 大括号的开头可以另起一行书写，但是建议写在第一行的末尾
2. 在语句体中，如果只有一句代码，大括号可以省略不写(最好不要省略)
3. 如果对一个布尔类型的变量进行判断，不要用= =号，或者直接写在括号里
4. 可以用逻辑运算符（和python里面的and or 一样）
~~~java
boolen flag = ture
if(flag){
语句体
}
~~~
#### ③.练习案例：酒量比较
~~~java
import java.util.Scanner;  
public class DrinkWine {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        System.out.println("请输入你的酒量：");  
        int wine = sc.nextInt();  
        if (wine < 0 | wine >=100 ){  
            System.out.println("不可能");  
        }else{  
            if (wine == 2 ) {  
                System.out.println("一般般");  
            }  
            if (wine > 2 ) {  
                System.out.println("你很勇嘛");  
            }else {  
                System.out.println("你8行嘛！");  
            }  
        }  
    }  
}
~~~

### Ⅱ. switch语句

#### ①.switch语句格式
~~~java
switch(表达式) {
	case 值1,值2,值3;
		语句体1；
		break;
	case 值4;
	case 值5;
	case 值6;
		语句体2；
		break；
	……
	default:
		语句体n+1；
		break；
}
~~~
JDK12以后可以用下面的方式避免[[#5. case|case穿透]]
~~~java
switch(表达式) {
	case 值1 ->{
		语句体1;
	}
	case 值1 ->{
		语句体1;
	}
	……
	default ->{
		语句体n；
	}
}
~~~

#### ②. 执行流程
1. 首先计算表达式的值。
2. 依次和case后面的值进行比较，如果有对应的值，就会执行相应的语句，在执行的过程中，遇到break就会结束。
4. 如果所有的case后面的值和表达式的值都不匹配，就会执行default里面的语句体，然后结束整个switch语句。

#### ③.格式说明
1. 表达式:(将要匹配的值)取值为byte、short、int、char、JDK5以后可以是枚举，JDK7以后可以是String
2. case:后面跟的是要和表达式进行比较的值（被匹配的值)
3. break:表示中断，结束的意思，用来结束switch语句
4. default:表示所有情况都不匹配的时候，就执行该处的内容，和if语句的else相似
5. case后面的值只能是字面量，不能是变量
6. case给出的值不允许重复

#### ④. defaule的位置和省略
1. 位置: defaule不一定是写在最下面的，我们可以写在任意位置。只不过习惯会写在最下面
2. 省略: defaule可以省略，语法不会有问题，但是不建议省略。

#### ⑤. case
1. case穿透：break省略了会导致case穿透，直接把后面的给一起运行
2. 执行流程:
	1. 首先还是会拿着小括号中表达式的值跟下面每一个case进行匹配
	2. 如果匹配上了，就会执行对应的语句体
	3. 如果此时发现了break，那么结束整个switch语句
	4. 如果没有发现break，那么程序会继续执行下一个case的语句体，一直遇到break或者右大括号为止。



#### ⑥练习  翻译1-3
~~~java
import java.util.Scanner;  
public class translation1to3 {  
    public static void main(String[] args) {  
        Scanner sc =new Scanner(System.in);  
        int number = sc.nextInt();  
        switch (number){  
            case 1:  
                System.out.println("one");  
                break;            
            case 2:  
                System.out.println("two");  
                break;  
            case 3:  
                System.out.println("three");  
                break;           
            default:  
                System.out.println("other");  
                break;        }  
    }  
}
~~~

## 3. 循环结构

### Ⅰ. for循环

#### ①. for格式
~~~java
for(初始化语句;条件判断语句;条件控制语句){
循环体语句;
}
~~~
#### ②.执行流程:
1. 执行初始化语句(只执行1次)
2. 执行条件判断语句，看其结果是true还是false
	如果是false，循环结束
	如果是true，执行循环体语句
3. 执行条件控制语句
4. 回到 2.继续执行条件判断语句

### Ⅱ. while循环
#### ①. while格式
~~~java
初始化语句;
while(条件判断语句){
	循环体语句;
	条件控制语句;
}
~~~
#### ②.for和while的对比
1. 相同点：
	运行规则都是一样的
2. 区别:
	for循环中:知道循环次数或者循环的范围
	while循环:不知道循环的次数和范围，只知道循环的结束条件。

#### ③. 练习 回文数
需求:给你一个整数x 。  
如果×是一个回文整数，打印true ，否则，返回false 。  
解释:回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。  
例如，121是回文，而123不是。
~~~java
import java.util.Scanner;  
public class 回文数 {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        int num = 0;  
        int x = sc.nextInt();  
        int temp = x;  
        while(x!=0){  
            int ge = x % 10;//提取个位  
            x=x/10;//去掉个位  
            num = num * 10+ge;//加起来，等于把原来的数字倒过来  
        }  
        if(num==temp){  
            System.out.println("ture");  
        }else {  
            System.out.println("false");  
        }  
    }  
}  
~~~
### Ⅲ. do...while循环
#### ①. 格式
~~~java
初始化语句;
do{
	循环体语句;
	条件控制语句;
}while(条件判断语句);
~~~
#### ②. 注意
先执行后判断
![[java循环判断语序.png]]

### Ⅳ. 无限循环
循环一直停不下来
 下面不能写代码，因为上面的不会停下来，下面的就不会被执行到
1. for
~~~java
for(;;){
	循环体语句;
}
~~~
2. while
~~~java
while(ture){
	循环体语句;
}
~~~
3. do……while
~~~java
do{
	循环体语句;
}while(ture)
~~~

#### ⑤. 跳转控制语句
在循环的过程中，跳到其他语句上执行。
~~~java
public class 五个包子不吃第三个 {  
    public static void main(String[] args) {  
        for (int i = 1; i <= 5; i++) {  
            if(i==3){  
                continue;  //结束本次循环继续下次循环
            }  
            System.out.println("在吃第"+i+"个包子");  
        }  
    }  
}
~~~
continue结束本次循环继续下次循环
~~~java
public class 五个包子只吃前三个 {  
    public static void main(String[] args) {  
        for (int i = 1; i <= 5; i++) {  
            if(i==4){  
                break;  //结束整个循环
            }  
            System.out.println("在吃第"+i+"个包子");  
        }  
    }  
}
~~~
break结束循环
## 4. 转移语句
return语句
~~~java
return [返回值];
~~~
break语句和continue语句
~~~java
break;              		//退出循环
continue;                  	//继续下一次循环
~~~

# 十四. 一维数组
注意区分数组和[[集合|集合]]的区别

## 1. 数组介绍
一种容器，可以用来存储同种数据类型的多个值
数组容器在存储数据的时候，需要结合隐式转换考虑。
## 2. 数组的定义
1. 格式一
~~~java
数据类型 []数组名
int [ ]array
~~~
2. 格式二
~~~java
数据类型 数组名[]
int array[]
~~~

## 3. 数组的静态初始化
在内存中，为数组容器开辟空间，并将数据存入容器中的过程。
手动指定数组元素，系统会根据元素个数，计算出数组的长度。
* 完整格式
~~~java
数据类型[] 数组名 = new 数据类型[]{元素1,元素2,元素3……};
int[] array1 = new int[]{11,22,33};
double[] array2 = new double[]{ 11.1,22.2,33.3};
~~~
* 简写格式
~~~java
数据类型[]数组名={元素1,元素2,元素3...};
int[] array3 = {11,22,33};
~~~

## 4. 数组动态初始化
初始化时只指定数组长度，由系统为数组分配初始值。
~~~java
数据类型[] 数组名 = new 数据类型[数组长度];
int[] arr = new int[3];

public class Main {
	public static void main(String[] args) {
		String[] arr = new String[3];
		arr[0]="A";
		arr[1]="B";
		arr[2]="C";
		for (int i = 0; i < arr.length; i++) {
			String string = arr[i];
			System.out.println(string);
		}
	}
}
A
B
C
长度为3，所以只能放3个进去，索引就是0，1，2
~~~
数组默认初始化值的规律
* 整数类型:默认初始化值0
* 小数类型:默认初始化值0.0
* 字符类型:默认初始化值' /ua800'空格
* 布尔类型:默认初始化值 false
* 引用数据类型:默认初始化值 null

填入内容
~~~java
String[] arr = new String[3]
arr[0]="A"
~~~

## 5. 数组的地址值
表示数组在内存中的位置
~~~java
int[] arr = {1,2,3,4,5};
system.out.println(arr); //[I@6d83e736  地址值
~~~
地址值的格式含义
【表示当前是一个数组
I:表示当前数组里面的元素都是int类型的
@:表示一个间隔符号(固定格式）
6d83e736才是数组真正的地址值，(十六进制)
平时我们习惯性的会把这个整体叫做数组的地址值。

## 6. 数组元素访问
python的[[程序设计I#4. 索引|索引]]在思路上类似

### Ⅰ. 获得数组里的元素
~~~java
数组名[索引];
int[] arr = {1,2,3,4,5};
int a = arr[0]//这时a就等于1
System.out.ptintln(arr[0]);//直接打印1
~~~
### Ⅱ. 把数据纯存储到数组中
~~~java
数组名[索引] = 具体数据/变量;
~~~
 一旦覆盖之后，原来的数据就不存在了。

## 7. 数组的长度
在Java当中，关于数组的一个长度属性
调用方式
~~~java
数组名.length
system.out.println(arr.length);//打印这个数组的长度
~~~

## 8. 数组遍历
* 将数组中所有的内容取出来，取出来之后可以（打印，求和，判断..)
* 遍历指的是取出**数据**的过程，不要局限的理解为遍历就是打印
* 自动快速生成数组的遍历方式IDEA才有，直接输入数组名.fori


## 9. 数组内存图
参考[[Java的内存分配]]
变量是栈内存中存储真实的数据
数组就是存储数据在堆内存里面的地址值，通过索引找到这个地址的某个真实数据
2个数当两个数组指向同一个小空间时，其中一个数组对小空间中的值发生了改变，那么其他数组再次访问的时候都是修改之后的结果了。

## 10. 数组常见问题
索引越界 
当访问了数组中不存在的索引，就会引发索引越界异常。

## 11. 数组常见操作
1. 求最值
~~~java
public class 固定数组求最值 {  
    public static void main(String[] args) {  
        int[] arr = {33,5,22,44,55};  
        int max = arr[0];  
        int min = arr[0];  //不用0，防止数组里有复数的情况
        for (int i = 0; i < arr.length; i++) {  
            if (arr[i]>max){  
                max=arr[i];  
            }  
        }  
        for (int i = 0; i < arr.length; i++) {  
            if (arr[i]<min){  
                min=arr[i];  
            }  
        }  
        System.out.println("最小值"+max);  
        System.out.println("最大值"+min);  
    }  
}
~~~
2. 求和等相关问题
~~~java
import java.util.Random;  

public class 十个随机数求和求平均等 {  
    public static void main(String[] args) {  
        int[] arr =new int[10];  
        for (int i = 0; i < 10; i++) {  
            Random r = new Random();  
            int temp= r.nextInt(100);  
            int number = temp + 1;//生成1~100的随机数  
            arr[i] = number;  
        }  
        //数组生成完毕  
        int sum = 0;  
        for (int i = 0; i < 10; i++) {  
            sum = sum + arr[i];  
        }  
        System.out.println("所有数据的和"+sum);  
        int average = sum/arr.length;  
        System.out.println("所有数据的平均数"+average);  
        int time = 0 ;  
        for (int i = 0; i < 10; i++) {  
            if(arr[i]>average){  
                time=time+1;  
            }  
        }  
        System.out.println("有"+time+"个数据比平均值小");  
        for (int i = 0; i < 10; i++) {  
            System.out.print(arr[i]+",");//用print就是不换行的  
        }  
    }  
}
~~~
3. 交换数据
定义一个数组，存入1,2,3,4,5。按照要求交换索引对应的元素。  
交换前:1,2,3,4,5交换后:5,2,3,4,1
~~~java
public class 交换数组中的数据 {  
    public static void main(String[] args) {  
        int[] arr = {1,2,3,4,5};  
        int temp = 0;  
        for (int i = 0; i < (arr.length)/2; i++) {  
            temp=arr[i];  
            arr[i]=arr[(arr.length)-1-i];  
            arr[(arr.length)-1-i]=temp;  
        }  
        for (int i = 0; i < 5; i++) {  
            System.out.print(arr[i]+",");  
        }  
    }  
}
~~~
4. 打乱顺序
需求:定义一个数组，存入1~5。要求打乱数组中所有数据的顺序。
~~~java
import java.util.Random;  
  
public class 打乱数组中的数据 {  
    public static void main(String[] args) {  
        int[] arr = {1,2,3,4,5};  
        Random r = new Random();  
        for (int i = 0; i < 5; i++) {  
            int temp = r.nextInt(arr.length);  
            int a = arr[i];  
            arr[i] = arr[temp];  
            arr[temp] = a;  
        }  
        for (int i = 0; i < 5; i++) {  
            System.out.print(arr[i]+",");  
        }  
    }  
}
~~~

# 十五. 二维数组
## 1. 数组的定义
1. 格式一
~~~java
数据类型 [][]数组名
int [][]array
~~~
2. 格式二
~~~java
数据类型 数组名[][]
int array[][]
~~~
## 2. 二维数组的创建
~~~java
new 数据类型[行数][列数];
~~~
* 简单情况
~~~java
表示数组a有3行，每行有4个元素
a = new int[3][4];
~~~
* 复杂情况
Java二维数组允许每一行的元素个数不同。
~~~java
创建数组有3行，每行的元素个数分别为5、10、20
int x[][]=new int[3][];
x[0]=new int[5];
x[1]=new int[10];
x[2]=new int[20];

~~~
## 3. 二维数组元素的访问
~~~java
二维数组名[][]
二维数组的行数，用length属性。

a.length 表示二维数组a的行数
a[i].length  表示二维数组a的第i行元素的个数
~~~
# 十六. 成员方法
## 1. 成员方法的声明
~~~java
[修饰符] [<泛型>] 返回值类型 方法名([形式参数列表]) [throws 异常类]
{
    语句序列;
    [return  [返回值]];
}
~~~
* 方法不能独立定义，只能在类体里定义
* 永远不能独立执行方法
## 2. 成员方法的分类
类方法
     用关键字static修饰的成员方法
实例方法
     没有使用static修饰的成员方法
**实例方法**必须通过对象来调用
**类方法**可以通过类名或者对象调用
## 3. 成员方法的定义
~~~java
public class MyDate{//类声明
    int year,month,day;//成员变量：年、月、日
    void set(int y, int m, int d){//成员方法，设置日期值
          year = y;
          month = m;
          day = d;
    } 
}
~~~
## 4. 成员方法的重载
方法重载
     指一个类中可以声明多个同名、但参数列表不同的成员方法
参数不同
     或者是参数的个数不同
     或者是参数的类型不同
返回类型和参数的名字不参与比较
~~~java
void set(int y, int m, int d) 
void set(int m, int d)      //重载方法，参数个数不同
void set(int y, int m,float d)      //重载方法，参数类型不同
void set(MyDate date)   //重载方法，参数的数据类型不同

void set(int m, int d, int y)  语法错//参数列表相同
int set(int m, int d, int y) 语法错//参数列表相同，不考虑返回类型
void set(int y=0, int m=0, int d=0)  语法错//参数不能指定默认值
~~~

# 十七. 类方法
程序的最小执行单元

## 1. 简单定义调用
* 定义
~~~java
public class PackageDemo {  
        public static void 方法名() {  
            方法体(就是打包起来的代码);  
        }  
}
~~~
* 调用
~~~java
方法名();
~~~

## 2. 带参数的方法的定义和调用
* 定义
~~~java
public static void 方法名(类型 形参1,类型 形参2,……) { 
    //只定义，不赋值 
    方法体(就是打包起来的代码);  
    //使用上面的变量
}  
~~~
* 调用
~~~java
方法名(数值1,数值2,……);
~~~
* 注意
方法调用时，形参和实参必须一一对应,否则程序将报错。
* 形参和实参
形参:全称形式参数，方法定义中的参数
实参:全称实际参数，方法调用中的参数

## 3. 带返回值的方法的定义和调用
* 定义
~~~java
public static 返回值类型 方法名(类型 形参1,类型 形参2,……) { 
    方法体;
    return 返回值;
} 
~~~
* 直接调用
~~~java
方法名(实参);
~~~
* 赋值调用:
~~~java
整数类型 变量名 = 方法名 (实参);
~~~
* 输出调用:
~~~java
system.out.println(方法名(实参));
~~~
## 4. 注意事项
1. 方法不调用就不执行
2. 方法与方法之间是平级关系，不能互相嵌套定义
3. 方法的编写顺序和执行顺序无关
4. 方法的返回值类型为void，表示该方法没有返回值，没有返回值的方法可以省略return语句不写。如果要编写return，后面不能跟具体的数据
5. return语句下面，不能编写代码，因为永远执行不到，属于无效的代码
6. return[[#5. 关键字|关键字]]方法没有返回值:可以省略不写。如果书写，表示结束方法

## 5. 方法的重载
同一个类中，方法名相同，参数不同的方法。与返回值无关。
Java虚拟机会通过参数的不同来区分同名的方法

## 6. 方法的内存
参考[[Java的内存分配]]
对比[[#9. 数组内存图|数据的内存]]类似

1. 方法调用的基本内存原理
按顺序挨个存到栈内存里面，然后运行

2. 方法传递基本数据类型的内存原理
[[#1. 基本数据类型|基本数据类型]]
变量中存储的是真实的数组
数据值是存储在自己的空间中
特点:赋值给其他变量，也是赋的真实的值。

3. 方法传递引用数据类型的内存原理
[[#2. 引用数据类型|引用数据类型]]
举个例子，数组，栈内存存地址，地址指向堆内存中的数据
数据值是存储在其他空间中,自己空间中存储的是地址值。
特点:赋值给其他变量，赋的地址值，不改变堆内存中的值
~~~java
int[] arr1 = {1,2,3}
int[] arr2 = arr1
~~~
![[java堆内存和栈内存.png]]

## 7. 方法的值的传递
* 传递基本数据类型时，传递的是真实的数据，形参的改变，不影响实际参数的值，所以需要return的存在
* 传递引用数据类型时，传递的是地址值，形参的改变，影响实际参数的值(改变了堆内存里面的值，所以实参会改变)


# 十八. 输出语句
## 1.0
~~~java
System.out.println("Hello World");
~~~

## 2.0
~~~java
System.out.print(111);
System.out.print(222);
//输出111222
~~~
同一行输出，配合循环结构

## 3.0
~~~java
System.out.printf("Hello %s","AAA");
//输出Hello AAA
~~~
联想python的F格式，就是可以插入不同的东西
~~~java
printf
%d:输出整型
%c:输出char型
%f:输出浮点型，小数部分最多保留6位
%.nf:输出浮点型，小数部分保留n位
%s:输出字符串
~~~

## 4.0
对上方的3.0进行拓展
~~~java
System.out.printf("%s Hello %s","AAA","BBB");
//输出AAA Hello BBB
~~~