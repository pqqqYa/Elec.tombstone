自己设计类
三大特征：封装、继承、多态

# 一、设计对象并使用

## 1. 类和对象
* 类:是对象共同特征的描述（设计图）
* 对象:是真实存在的具体东西
java中先设计类，才能获得对象

定义类，得到对象（Javabean类）
~~~java
public class 类名{
	成员变量(代表属性，名词)
	成员方法(代表行为，动词)
	构造器
	代码块
	内部类
}
~~~
例子
~~~java
public class PC {
    String brand;  //(修饰符 )数据类型 变量名称( = 初始化值);
    double price;
     public void chat(){  
         System.out.println("chat");  
    }  
    public void playGame(){  
        System.out.println("game");  
    }  
}
~~~
创建对象
~~~java
类名 对象名 = new 类名();
~~~
使用对象
~~~java
访问属性:对象名.成员变量
访问行为:对象名.方法名(……)
~~~

## 2. 类的几个补充注意事项
①用来描述一类事物的类，专业叫做:Javabean类，不写main方法
②在以前，编写main方法的类，叫做测试类。我们可以在测试类中创建javabean类的对象并进行赋值调用
③类名首字母建议大写，需要见名知意，驼峰模式
④一个Java文件中可以定义多个class类，且只能一个类是public修饰，而且public修饰的类名必须成为代码文件名，最好还是一个文件一个class类
⑤成员变量的完整定义格式是︰
修饰符 数据类型 变量名称 = 初始化值; 
一般无需指定初始化值，存在默认值。

# 二、封装
* 告诉我们，如何正确设计对象的属性和方法

* 对象代表什么，就得封装对应的数据，并提供数据对应的行为
eg：人用电脑玩游戏，玩游戏封装在电脑的游戏里，因为游戏自己在被玩

* 封装的好处：
对象代表什么，就得封装对应的数据，并提供数据对应的行为
联想python的库类似

# 三、this关键字
区分局部变量和成员变量
就近原则，离的近的变量同名，谁进用谁
加一个this，使用成员变量里面的那个
~~~java
public class demo {  
    private int size;  
    public void demoSize() {
        int size = 3;  
        System.out.println(this.size);  //打印成员变量size
        System.out.println(size);  //打印局部变量3
    }  
}
~~~

~~~java
public class demo {  
    private int size; 
    public void demoSize(int size) {  
	    //局部变量表示测试类中调用方法传递过来的值
	    //等号左边表示成员位置的size
        this.size = size;
        //这样就可以赋值给成员位置的name，也就是最上面那一个
        System.out.println(size);
    }  
}

~~~

# 四、构造方法
构造方法也叫作构造器、构造函数。
创造对象的时候，虚拟机会自动调用构造方法，给成员变量进行初始化
## 1. 作用：在创建对象的时候给成员变量进行初始化(赋值)的。
格式
~~~java
public class dome{
	修饰符 类名(数据类型 参数,数据类型 参数,……){
		方法体;
	}
}
~~~
## 2. 特点
1. 方法名与类名相同，大小写也要一致
2. 没有返回值类型，连void都没有
3. 没有具体的返回值（不能由retrun带回结果数据)

## 3. 执行时机
1. 创建对象的时候由虚拟机调用，不能手动调用构造方法
2. 每创建“次对象，就会调用一次构造方法

## 4. 构造方法的定义
1. 如果没有定义构造方法，系统将给出一个默认的无参数构造方法
2. 如果定义了构造方法，系统将不再提供默认的构造方法,所以写的时候

## 5. 构造方法的重载
带参构造方法，和无参数构造方法，两者方法名相同，但是参数不同，这叫做构造方法的重载

无论是否使用，都手动书写无参数构造方法，和带全部参数的构造方法
~~~java
public class Student {  
    private String name;  
    private int age;  
  
    public Student(){  
        System.out.println("空参构造运行了");  
    }  
    //空参构造
    public Student(String name,int age){  
        this.name=name;  
        this.age=age;  
    }  
    //带参构造  
    public String getName() {  
        return name;  
    }  
  
    public void setName(String name) {  
        this.name = name;  
    }  
  
    public int getAge() {  
        return age;  
    }  
  
    public void setAge(int age) {  
        this.age = age;  
    }  
}
~~~

~~~java
public class StudentTest {  
    public static void main(String[] args) {  
        //创建对象  
        //空格没写，调用空参构造  
        //写了就是对Student里面的成员变量进行赋值  
        Student s = new Student("AAA",100);  
        System.out.println(s.getName());  
        System.out.println(s.getName());  
        //直接就可以打印赋进去的成员变量  
    }  
}
~~~

# 五、标准JavaBean
1. 类名需要见名知意
2. 成员变量使用private修饰
3. 提供至少两个构造方法
	无参构造方法
	带全部参数的构造方法
3. 成员方法
	提供每一个成员变量对应的setXxx()/getXxx()
	如果还有其他行为，也需要写上


# 六、对象内存图
## 1. 一个对象的内存图
~~~java
Student s = new Student();
~~~
1. 在栈内存中加载class文件
	在方法区
2. 在方法区申明局部变量
	Student s
	把这个类扔到方法区里面
3. 在堆内存中开辟一个空间
	new Student()的成员变量、成员方法放进去，生成成员方法的地址
4. 默认初始化
	堆内存里面赋值(默认值)
5. 显示初始化
	如果本省就写了成员变量的值，就用这个替换默认值
6. 构造方法初始化
	分有参无参来继续
7. 将堆内存中的地址值赋值给局部变量

## 2. 多个对象的内存图
一个对象的内存图一样，但2个互相独立，互不干扰

## 3. 两个变量指向同一个对象内存图
2个变量地址一样，指向了同一个对象

## 4. this的内存原理
this的作用:区分局部变量和成员变量
this的本质:所在方法调用者的地址值


## 5. 基本数据类型&引用数据类型
* 基本数据类型：
	存储在栈内存里面的
	数据值是存储在自己的空间中，赋值给其他变量，也是赋的真实的值。

* 引用数据类型：
	栈内存记录用地址值，引用堆内存里面的数据
	数据值是存储在其他空间中,自己空间中存储的是地址值。


# 七、成员变量&局部变量的区别
成员变量：类的里面，方法的外面；堆内存；整个类有效
局部变量：方法里面；栈内存；只在当前方法有效
