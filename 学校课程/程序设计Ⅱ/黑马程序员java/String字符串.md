# 一、String
1. Strin是Java定义好的一个类。定义在java.lang包中，所以使用的时候不需要导包。
2. Java程序中的所有字符串文字（例如“三连投币”）都被实为此类的对象。
3. 字符串的内容是不会发生改变的，它的对象在创建后不能被更改。
## 1. 创建String对象的方式

### Ⅰ. 直接赋值
~~~java
string name ="ABC";
~~~
当使用双引号直接赋值时，系统会检查该字符串在串池中是否存在。
不存在：创建新的
存在：复用

### Ⅱ. new
~~~java
public string()创建空白字符串，不含任何内容
public string(string original)根据传入的字符串，创建字符串对象
public string(char[] chs)根据字符数组，创建字符串对象
public string(byte[] chs)根据字节数组，创建字符串对象

string s2 = new String();

char[ ] chs = { 'a' ,' b' ,'c' ,'d'};s
tring s = new string(chs);
system.out.println(s) ; / /abcd
//给一个新的字符串，在堆内存里面的不一样，所以地址值也不一样

byte[ ] bytes = {97,98,99,100};
string s = new string(bytes);
system.out.println(s);  / /abcd
//传递一个字节数组，根据字节数组的内容再创建一个新的字符串对象
//应用场景:以后在网络当中传输的数据其实都是字节信息
//我们一般要把字节信息进行转换，转成字符串，此时就要用到这个构造了。
~~~
## 2. 字符串的比较
~~~java
boolean   equals(要比较的字符串)
完全一样结果才是true，否则为false
boolean   equalslgnoreCase(要比较的字符串)
忽略大小写的比较

boolean result2 = s1.equalsIgnorecase( s2);
比较s1和s2
~~~

## 3. 字符串的遍历
~~~java
public class Test2字符串直接遍历 {
    public static void main(String[] args) {
        //两个方法：
        //charAt()：会根据索引获取对应的字符
        //length(): 会返回字符串的长度

        //1.键盘录入一个字符串
        Scanner sc = new Scanner(System.in);
        System.out.println("请输入字符串");
        String str = sc.next();
        System.out.println(str);
        //2.遍历
        for (int i = 0; i < str.length(); i++) {
            //i 依次表示字符串的每一个索引
            //索引的范围：0 ~  长度-1
            //根据索引获取字符串里面的每一个字符
            //ctrl + alt + V 自动生成左边的接受变量
            char c = str.charAt(i);
            System.out.println(c);
        }
    }
}
~~~
## 4. 字符串的截取

**String substring(int beginIndex, int endIndex)**截取

注意点:包头不包尾，包左不包右
只有返回值才是截取的小串
~~~java
public class 字符串的截取 {  
    public static void main(String[] args) {  
        String phoneNumber = "18048818847";  
        String qian = phoneNumber.substring(0, 3);  
        String hou = phoneNumber.substring(7);  
        System.out.println(qian+"******"+hou);  
    }  
}
python可以用-4但是这里是java只能用7，一直到最后
~~~

## 5. 字符串的替换
String replace(I旧值,新值)替换
注意点:只有返回值才是替换之后的结果
~~~java
public class 字符串的替换 {  
    public static void main(String[] args) {  
        String talk = "666TMD";  
        String replace = talk.replace("TMD", "***");  
        System.out.println(replace);  
    }  
}
666***
public class 字符串的替换 {  
    public static void main(String[] args) {  
        String talk = "SB666TMD";  
        String[] arr={"TMD","NND","SB"};  
        for (int i = 0; i < arr.length; i++) {  
            talk= talk.replace(arr[i], "***");  
        }  
        System.out.println(talk);  
    }  
}
			***666***
~~~

# 二、StringBuilder
## 1. 基础

使用stringBuilder的场景:
1. 字符串的拼接
2. 字符串的反转
StringBuilder可以看成是一个容器，创建之后里面的内容是可变的
作用:提高字符串的操作效率
~~~java
public StringBuilder()
创建一个空白可变字符串对象，不含有任何内容
public StringBuilder(String str)
根据字符串的内容，来创建可变字符串对象
public StringBuilder append(任意类型)
添加数据，并返回对象本身
public StringBuilder reverse()
反转容器中的内容
public int length()
返回长度（字符出现的个数)
public String toString(
通过toString()就可以实现把StringBuilder转换为String
~~~
~~~java
public class StringBuilderDemo {  
    public static void main(String[] args) {  
        //1. 创建对象  
        StringBuilder sb = new StringBuilder("abc");  
        //添加元素  
        sb.append(1);  
        sb.append(2.3);  
        sb.append(true);  
        //反转  
        sb.reverse();  
        //获取长度  
        int length = sb.length();  
  
        System.out.println(sb);  
        System.out.println(length);  
  
        //变成字符串  
        String str = sb.toString();  
        System.out.println(str);  
    }  
}
eurt3.21cba
11
eurt3.21cba
~~~
## 2. 链式编程
当我们在调用一个方法的时候，不需要用变量接收他的结果，可以继续调用其他方法
~~~java
import java.util.Scanner;  
public class StringBuilderDemo2 {  
    public static void main(String[] args) {  
        int len = getString().substring(1).replace("A", "Z").length();  
        System.out.println(len);  
    }  
    public static String getString(){  
        Scanner sc =new Scanner(System.in);  
        String s = sc.next();  
        return s;  
    }  
}
~~~
可以用于简化StringBulider的代码
~~~java
public class StringBuilderDemo2 {  
    public static void main(String[] args) {  
        StringBuilder sb = new StringBuilder("aaa");  
        sb.append("bbb").append("ccc");  
        String s = sb.toString().replace("aaa","AAA");  
        System.out.println(s);  
    }  
}
AAAbbbccc
~~~

# 三、StringJonier
StringJoiner跟StringBuilder一样，也可以看成是一个容器，创建之后里面的内容是可变的。
作用:提高字符串的操作效率，而且代码编写特别简洁，但是目前市场上很少有人用。
JDK8以后才有
~~~java
public StringJoiner (间隔符号)
创建一个StringJoine，指定拼接时的间隔符号
public StringJoiner (间隔符号，开始符号，结束符号)
创建一个StringJoine，指定拼接时的间隔符号、开始符号、结束符号
public StringJoiner add (添加的内容)
添加数据，并返回对象本身
public int length()
返回长度(（字符出现的个数)
public String toString()
返回一个字符串(该字符串就是拼接之后的结果)
~~~
~~~java
import java.util.StringJoiner;  
public class StringJonierDemo1 {  
    public static void main(String[] args) {  
        StringJoiner sj = new StringJoiner(",","[","]");  
        String str = sj.add("aaa").add("bbb").add("ccc").toString();  
        System.out.println(str);  
    }  
}
[aaa,bbb,ccc]
~~~

# 四、字符串相关的底层原理

## 1. 字符串存储的内存原理
   String s = “abc”；直接赋值
   特点：
   ​    此时字符串abc是存在字符串常量池中的。
   ​    先检查字符串常量池中有没有字符串abc，如果有，不会创建新的，而是直接复用。如果没有abc，才会创建一个新的。
   所以，直接赋值的方式，代码简单，而且节约内存。
## 2. new出来的字符串
   看到new关键字，一定是在堆里面开辟了一个小空间。
   String s1 = new String（“abc”）；
   String s2 = “abc”；
   s1记录的是new出来的，在堆里面的地址值。
   s2是直接赋值的，所以记录的是字符串常量池中的地址值。
## 3. = =号比较的到底是什么？
   如果比较的是基本数据类型：比的是具体的数值是否相等。
   如果比较的是引用数据类型：比的是地址值是否相等。
   结论：= =只能用于比较基本数据类型。不能比较引用数据类型。

# 五、练习题
## 1. 用户登录
~~~java
import java.util.Scanner;  
public class PassWord {  
    public static void main(String[] args) {  
        String rightUsername="zhangsan";  
        String rightPassword="123456";  
        int sum = 1;  
        while (sum<=3){  
            System.out.println("输入用户名");  
            Scanner sc = new Scanner(System.in);  
            String username=sc.next();  
            System.out.println("输入密码");  
            String password=sc.next();  
            if(username.equals(rightUsername) & password.equals(rightPassword)){  
                System.out.println("登录成功");  
                break;            }else {  
                if(3-sum== 0){  
                    System.out.println("登录失败，账户被锁定，请联系客服");  
                }else {  
                    System.out.println("登录失败，还有"+(3-sum)+"次机会");  
                }  
            }  
            sum++;  
        }  
    }  
}  
///已知正确的用户名和密码，请用程序实现模拟用户登录。  
// 总共给三次机会，登录之后，给出相应的提示
~~~
## 2. 遍历字符串
fori正着遍历
forr反着遍历
~~~java
import java.util.Scanner; 
public class 遍历字符串 {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        String str = sc.next();  
        for (int i = 0; i < str.length(); i++) {  
            char c = str.charAt(i);  
            System.out.println(c);  
        }  
    }  
}
~~~
## 3. 统计大小写和数字个数
~~~java
import java.util.Scanner;  
  
public class 统计大小写和数字个数 {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        String str = sc.next();  
        int bigcount= 0;  
        int smallcount= 0;  
        int numbercount= 0;  
        int ohtercount= 0;  
        for (int i = 0; i < str.length(); i++) {  
            char c = str.charAt(i);  
            if (c >='a' & c <='z'){  
                bigcount++;  
            }else if (c >='A' & c<='Z'){  
                smallcount++;  
            }else if (c >='0' & c<='9'){  
                numbercount++;  
            }else{  
                ohtercount++;  
            }  
            //这里的本质是比较ascii码表里面转换后的值  
        }  
        System.out.println("大写字母有"+bigcount+"个");  
        System.out.println("小写字母有"+bigcount+"个");  
        System.out.println("数字有"+bigcount+"个");  
        System.out.println("其他符号有"+bigcount+"个");  
    }  
}
~~~
## 4. 拼接字符串
~~~java
public class 拼接字符串 {  
    public static void main(String[] args) {  
        int[] arr = {1,2,3};  
        String str = arrString(arr);  
        System.out.println(str);  
    }  
    public  static String arrString(int[] arr){  
        if(arr==null){  
            return "";  
        }  
        if (arr.length==0){  
            return "[]";  
        }  
        String result= "[";  
        for (int i = 0; i < arr.length; i++) {  
            if(i==arr.length-1){  
                result = result + arr[i];  
            }else {  
                result = result + arr[i]+",";  
            }  
        }  
        result = result +"]";  
        return result;  
    }  
}  
//拼接字符串  
//定义一个方法，把int数组中的数据按照指定的格式拼接成一个字符串返回，调用该方法，并在控制台输出结果。  
//例如:  
//数组为int[] arr = {1,2,3};  
//执行方法后的输出结果为:[1,2,3]
~~~
## 5. 反转字符串
~~~java
import java.util.Scanner;  
public class 字符串的反转 {  
    public static void main(String[] args) {  
        Scanner sc= new Scanner(System.in);  
        String str = sc.next();  
        for (int i = str.length()-1; i >= 0; i--) {  
            char c = str.charAt(i);  
            System.out.print(c);  
        }  
    }  
}  
//字符串反转  
//定义一个方法，实现字符串反转。  
//键盘录入一个字符串，调用该方法后，在控制台输出结果例如，键盘录入abc，输出结果cba
~~~
## 6. 金额转换
~~~java
import java.util.Scanner;  
public class 金额转换 {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        int money ;  
        while (true){  
            System.out.println("请输入一个7位数以下的整数金额");  
            money = sc.nextInt();  
            if(money>=0 & money<9999999){  
                break;  
            }else {  
                System.out.println("输入的金额无效");  
            }  
        }  
        String moneyStr = "";  
        while (true){  
            int ge = money%10;  
            money=money/10;  
            String upperNumber = getUpperNumber(ge);  
            moneyStr=upperNumber+moneyStr;  
            if (money==0){  
                break;  
            }  
        }  
        int count = 7-moneyStr.length();  
        for (int i = 0; i < count; i++) {  
            moneyStr="零"+moneyStr;  
        }  
        String result = "";  
        String[] arr = {"佰","拾" ,"万","仟","佰","拾","元"};  
        for (int i = 0; i < moneyStr.length(); i++) {  
            char c = moneyStr.charAt(i);  
            result = result+c+arr[i];  
        }  
        System.out.println(result);  
  
    }  
    public static String getUpperNumber(int number){  
        String[] arr = {"零" ,"壹" ,"贰" ,"参","肆", "伍","陆","束" ,"搠","玫"};  
        return arr[number];  
    }  
}
123456
零佰壹拾贰万参仟肆佰伍拾陆元
~~~
## 7. 身份证信息查看
~~~java
public class 身份证信息查看 {  
    public static void main(String[] args) {  
        String id = "511181200401020012";  
        String year = id.substring(6,10);  
        String month = id.substring(10,12);  
        String day = id.substring(12,14);  
        char gender = id.charAt(16);  
        System.out.println("人物信息为:");  
        System.out.println("出生年月日:"+year+"年"+month+"月"+day+"日");  
        int num = gender - 48;  
        if(num%2!=0){  
            System.out.println("性别为:男");  
        }else {  
            System.out.println("性别为:女");  
        }  
    }  
}  
//7-14位:出生年、月、日  
//17位:性别（奇数男性，偶数女性)  
//人物信息为:  
//出生年月日:XXXX年X月X日  
// 性别为:男/女
~~~
## 8. 对称字符串
~~~java
public class 对称字符串 {  
    public static void main(String[] args) {  
        String str1 = getString();  
        String str2= new StringBuilder().append(str1).reverse().toString();  
        if (str1.equals(str2)){  
            System.out.println("Yes");  
        }else {  
            System.out.println("No");  
        }  
    }  
    public static String getString(){  
        Scanner sc = new Scanner(System.in);  
        String str = sc.next();  
        return str;  
    }  
}  
//对称字符串  
//需求:键盘接受一个字符串，程序判断出该字符串是否是对称字符串，并在控制台打印是或不是  
//对称字符串:123321、111  
//非对称字符串:123123
~~~
## 9. 转换罗马数字
~~~java
import java.util.Scanner;  
public class 转换罗马数字 {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        String str;  
        while (true) {  
            System.out.println("输入一个数字");  
            str = sc.next();  
            boolean flag = checkStr(str);  
            if(flag){  
                break;  
            }else{  
                System.out.println("输入的不符合规则，请重新输入");  
                continue;            }  
        }  
        StringBuilder sb = new StringBuilder();  
        for (int i = 0; i < str.length(); i++) {  
            char c = str.charAt(i);  
            int number = c-48;  
            if(i==str.length()-1){  
                sb.append(changeLuoMa(number));  
            }else {  
  
                sb.append(changeLuoMa(number)).append(",");  
            }  
        }  
        String s = sb.toString();  
        System.out.println(s);  
    }  
        public static String changeLuoMa( int number) {  
        String[] arr = {"","I","II","III","IV","V","VI","VII","VIII","IX"};  
        return arr[number];  
    }  
    public  static boolean checkStr(String temp){  
        if (temp.length()>9){  
            return false;  
        }  
        for (int i = 0; i < temp.length(); i++) {  
            char c = temp.charAt(i);  
            if (c < '0' || c > '9'){  
                return false;  
            }  
        }  
        return true;  
    }  
}  
567
V,VI,VII
//键盘录入一个字符串  
// 要求1:长度为小于等于9  
// 要求2:只能是数字  
//将内容变成罗马数字  
//下面是阿拉伯数字跟罗马数字的对比关系:  
//l -1、l -2、III - 3、V - 4、V - 5、VI-6、VII- 7、VII - 8、IX - 9注意点:  
//罗马数字里面是没有0的  
//如果键盘录入的数字包含0，可以变成””(长度为0的字符串)
~~~
上面用的asc码表，可以用switch来操作代替，避免字符串和数字的转换
