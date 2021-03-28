

# [Java]()

## JDK

### 什么是java

​	计算机语言是人与计算机之间通信的语言，它主要由一些指令构成，程序员可以通过这些指令来指挥计算机进行各种工作。计算机语言的种类有很多，总的来说可以分为**机器语言，汇编语言，高级语言**三大类，计算机所能识别的只有机器语言，但人们编程时所采用的语言是汇编语言和高级语言，因为机器语言都是二进制的01组成的编码。

​	java是一种高级编程语言 完全面向对象的程序设计语言

##### 版本:

Java SE(Java Platform,Standard Edition) 标准版本 ee和me都是从se上演变过来的

Java EE (Java Platform，Enterprise Edition) 企业版

Java ME(Java Platform，Micro Edition)，java的微型版本 主要用于小型数字电子设备上的软件程序的开发

### java的特点：

1. 简单性

2. 面向对象性

3. 安全性

4. 跨平台性

5. 支持多线程

### Jdk是什么

​	sun公司提供了一套java开发环境，简称jdk（java develpment kit），它是整个java的核心，其中包括，java编辑器，

java运行工具，java文档生成工具，java打包工具等等。

JRE (Java Runtime Environment) ：是Java程序的运行时环境，包含 JVM 和运行时所需要的 **核心类库** 

JDK (Java Development Kit)：是Java程序开发工具包，包含 JRE 和开发人员使用的工具



![img](https://img2018.cnblogs.com/blog/1362965/201901/1362965-20190114161305916-1522316322.png)

### Java虚拟机

​	JVM（Java Virtual Machine ）：Java虚拟机，简称JVM，是运行所有Java程序的假想计算机，是Java程序的 **运行环境**，是Java 最具吸引力的特性之一。我们编写的Java代码，都运行在 JVM 之上。

​	跨平台：任何软件的运行，都必须要运行在操作系统之上，而我们用Java编写的软件可以运行在任何的操作系 统上，这个特性称为**Java语言的跨平台特性**。该特性是由JVM实现的，我们编写的程序运行在JVM上，而JVM 运行在操作系统上。

Java的虚拟机本身不具备跨平台功能的，每个操作系统下都有不同版本的虚拟机。

**是java语言的跨平台性，而不是java虚拟机的跨平台性**

### 系统环境变量

​	在计算机操作系统中可以定义一系列变量，这些变量可供操作系统上所有的英语程序使用，被称作系统环境变量

### Java的运行机制

1. 编写为.java的文件

2. 使用编译器进行编译，生成.class的字节码文件

3. 使用java虚拟机运行程序

   java虚拟机首先将编译好的字节码文件加载到内存（类加载），由类加载器完成，虚拟机进行解释执行，便可看到运行结果。

   



## java编程基础

### 代码基础格式

java中的程序都必须放在一个类里面，用class关键字定义

```
public class HelloWorld{
    public static void main(String[] args){
         System.out.println("Hello World");
    }
```

#### java代码的基本格式

1. java中的程序代码分为结构定义语句和功能执行语句。

   结构定义语句用于声明一个类或者方法

   功能执行语句用于实现具体的方法

2. 严格区分大小写和中英文

3. 良好的编程规范习惯，空格，换行，增加可读性

#### 注释

单行 ：//代码

多行： /*

​				代码

​			*/

文档注释：/**

​					文档注释*

​					*/

#### 常量类型：

##### 1. 整型：

二进制：0b或0B开头，为了和十进制区分 	 0b01101100 	0B10110101

八进制：0开头并其后由0—7组成		0345

十进制：

十六进制：0x或0X开头		0xaf3 	0x25AF

##### 2. 浮点数：

单精度：float  结尾为f或F  			32位 （4个字节）

双精度：double 结尾为d或D		64位 （8个字节）

不添加后缀默认为双精度

##### 3. 字符：

字符常量用于表现一个字符，用‘  ’引起来，可以为英文字母，数字，标点符号以及转义序列来表示的特殊字符

‘a’	‘1’	‘&’	‘/r’

##### 4. 字符串：

用于表示一串连续的字符，用“   ”引起来，可包含一个或多个字符，也可以不包含字符，即长度为0

“hello world”

##### 5.  布尔：

true 	false

##### 6.  null

表示对象引用为空

#### 变量：

##### 定义：

在程序运行期间，随时可能产生一些临时数据，应用程序会将这些数据保存在一些数据单元中，每个内存单元都用一个标识符来标识。这些内存单元被称为变量，定义的标识符就是变量名，内存单元的数据就是变量的值。

##### 数据类型

![img](http://www.itcast.cn/files/image/201907/20190702115432288.jpg)

整型

<img src="http://www.itcast.cn/files/image/201907/20190702115507276.jpg" alt="img" style="zoom: 67%;" />

浮点型

<img src="http://www.itcast.cn/files/image/201907/20190702115547319.jpg" alt="img" style="zoom:67%;" />

在Java中，一个小数会被默认为 double类型的值，因此在为一个float类型的变量赋值时需要注意一点，**所赋值的后面一定要加上字母F(或者小写f)**，而为 double类型的变量赋值时，可以在所赋值的后面加上字符D(或小写d)，也可以不加。

字符类型
字符类型变量用于存储个单一字符，在[java](http://www.itcast.cn/)中用char表示。Java中每个char类型的字符变量都会占用**2个字节**。在给char类型的变量赋值时，需要用一对英文半角格式的单引’’号把字符括起来，如’a’，也可以将char类型的变量赋值为0~65535范围内的整数，计算机会自动将这些整数转化为所对应的字符，如数值97对应的字符为’a’。下面的两行代码可以实现同样的效果



##### 类型转换

**自动转换**（也叫隐式类型转换）需满足两种数据类型彼此兼容且目标类型的取值范围大于源类型的取值范围。

可以小转大，不能大转小。（精度更精细的可以向没有那么精细的进行自动转换）

取值范围小的类型向取值范围大的类型进行转换，编译器在赋值过程中不会造成数据丢失，所以编译器能够自动完成这种转换，在编译时不报告任何错误。

**强制类型转换**  （也叫隐式类型转换）

指的是两种数据类型之间的转换需要进行显式的说明。

#### 运算符

| 操作符 | 描述                              | 例子               |
| :----- | :-------------------------------- | :----------------- |
| +      | 加法 - 相加运算符两侧的值         | A + B 等于 30      |
| -      | 减法 - 左操作数减去右操作数       | A – B 等于 -10     |
| *      | 乘法 - 相乘操作符两侧的值         | A * B等于200       |
| /      | 除法 - 左操作数除以右操作数       | B / A等于2         |
| ％     | 取余 - 左操作数除以右操作数的余数 | B%A等于0           |
| ++     | 自增: 操作数的值增加1             | B++ 或 ++B 等于 21 |
| --     | 自减: 操作数的值减少1             | B-- 或 --B 等于 19 |

| 操作符 | 描述                                                         | 例子                           |
| :----- | :----------------------------------------------------------- | :----------------------------- |
| ＆     | 如果相对应位都是1，则结果为1，否则为0                        | （A＆B），得到12，即0000 1100  |
| \|     | 如果相对应位都是0，则结果为0，否则为1                        | （A \| B）得到61，即 0011 1101 |
| ^      | 如果相对应位值相同，则结果为0，否则为1                       | （A ^ B）得到49，即 0011 0001  |
| 〜     | 按位取反运算符翻转操作数的每一位，即0变成1，1变成0。         | （〜A）得到-61，即1100 0011    |
| <<     | 按位左移运算符。左操作数按位左移右操作数指定的位数。         | A << 2得到240，即 1111 0000    |
| >>     | 按位右移运算符。左操作数按位右移右操作数指定的位数。         | A >> 2得到15即 1111            |
| >>>    | 按位右移补零操作符。左操作数的值按右操作数指定的位数右移，移动得到的空位以零填充。 | A>>>2得到15即0000 1111         |

| 操作符  | 描述                                                         | 例子                     |
| :------ | :----------------------------------------------------------- | :----------------------- |
| + =     | 加和赋值操作符，它把左操作数和右操作数相加赋值给左操作数     | C + = A等价于C = C + A   |
| - =     | 减和赋值操作符，它把左操作数和右操作数相减赋值给左操作数     | C - = A等价于C = C -  A  |
| * =     | 乘和赋值操作符，它把左操作数和右操作数相乘赋值给左操作数     | C * = A等价于C = C * A   |
| / =     | 除和赋值操作符，它把左操作数和右操作数相除赋值给左操作数     | C / = A等价于C = C / A   |
| （％）= | 取模和赋值操作符，它把左操作数和右操作数取模后赋值给左操作数 | C％= A等价于C = C％A     |
| << =    | 左移位赋值运算符                                             | C << = 2等价于C = C << 2 |
| >> =    | 右移位赋值运算符                                             | C >> = 2等价于C = C >> 2 |
| ＆=     | 按位与赋值运算符                                             | C＆= 2等价于C = C＆2     |
| ^ =     | 按位异或赋值操作符                                           | C ^ = 2等价于C = C ^ 2   |
| \| =    | 按位或赋值操作符                                             | C \| = 2等价于C = C \| 2 |

| 运算符 | 描述                                                         | 例子             |
| :----- | :----------------------------------------------------------- | :--------------- |
| ==     | 检查如果两个操作数的值是否相等，如果相等则条件为真。         | （A == B）为假。 |
| !=     | 检查如果两个操作数的值是否相等，如果值不相等则条件为真。     | (A != B) 为真。  |
| >      | 检查左操作数的值是否大于右操作数的值，如果是那么条件为真。   | （A> B）为假。   |
| <      | 检查左操作数的值是否小于右操作数的值，如果是那么条件为真。   | （A <B）为真。   |
| >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是那么条件为真。 | （A> = B）为假。 |
| <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是那么条件为真。 | （A <= B）为真   |

| 操作符 | 描述                                                         | 例子                |
| :----- | :----------------------------------------------------------- | :------------------ |
| &&     | 称为逻辑与运算符。当且仅当两个操作数都为真，条件才为真。     | （A && B）为假。    |
| \| \|  | 称为逻辑或操作符。如果任何两个操作数任何一个为真，条件为真。 | （A \| \| B）为真。 |
| ！     | 称为逻辑非运算符。用来反转操作数的逻辑状态。如果条件为true，则逻辑非运算符将得到false。 | ！（A && B）为真。  |



#####  选择结构语句

​	1.if：

```
if（判断条件）｛

​	执行代码

｝
```



​	2.if...else：

```
if(判断条件)｛

​	执行代码1

｝else｛

​	执行代码2

｝
```



​	3.if...else  if...else：

```
if(判断条件)｛

​	执行代码1

｝else if｛

​	执行代码2

｝...

​		else{

​	执行代码n+1

}
```



switch：

```
switch（判断条件）｛

case  1 ：

​	执行代码1；

​	break；

case  2 ：

​	执行代码2；

​	break；

​	...

case  n ：

​	执行代码n；

​	break；

default：

​	执行代码n+1；

​	break；

｝
```



##### 循环结构语句

while：

```
while（循环条件）｛

​	执行语句

｝
```



do...while:

```
do{

​	执行语句

​	...

}while（循环条件）
```



for：

```
for（初始化表达式；循环条件；操作表达式）｛

​		执行语句

｝
```



##### 循环嵌套

在循环语句中嵌套其他的循环语句



##### 跳转语句：

break：

1.break用于switch语句中，终止switch语句
2.break用于循环时，跳出循环
可以标记循环体跳出多层循环

```
class ForLoop{  
    public static void main(String[] args){  
       //jump from outer loop  
        **outer**:for(int i=0;i<5;i++){  
            for(int j=0;j<10;j++){  
                if(j==5)  
                   **break outer**;  
                 System.out.print("*");    
            }  
            System.out.print("\r\n");    
        }          
    }  
}
```

continue：

1.continue用在循环中，跳出本次循环，继续执行下一次循环



#### 方法

声明格式

```
修饰符	返回值类型	方法名（参数类型  参数名1，参数类型  参数名2，...参数类型  参数名n）｛

​			执行语句

​			...

​			return 	返回值；

｝
```



##### 方法的重载

程序需要针对不同的情况定义多个名称相同的方法，但**参数的类型或个数必须不同**。



#### 数组

定义：一组数据的集合	数组下标从0开始，到length-1

例：int[] x=new int[100];

 等效于：

int[] x;

x=new int[100];

 

##### 多维数组

![image-20201015170205658](C:\Users\11\AppData\Roaming\Typora\typora-user-images\image-20201015170205658.png)



## 面向对象

### 概念

​		对对象进行操作，对象进行一系列的行为

#### 封装

​		将对象的属性和行为封装起来

#### 继承

​		类与类之间的关系，通过继承可以在无需重新编写原有类的情况下对原有类进行扩展

#### 多态

​		一个类中定义的属性和方法被其他类继承后，可以根据使用条件的不同具有不同的数据类型或表现出不同的行为，这使得同一个属性的方法在不同类中具有不同的语义



### 类与对象

#### 类的定义

​		在面向对象的思想中，最核心的就是对象，为了在程序中创建对象，首先需要定义一个类，类是对象的抽象，它用于描述一组对象的共同特征和行为。类中可以定义成员变量和成员方法，成员变量（属性）用于描述对象的特征。成员方法（方法）用于描述对象的行为。

例：

```
class 类名称
{
	// 定义属性
	数据类型 属性；      //零到多个属性
	// 定义构造函数
	类名称（参数，…）{   //零个到多个构造方法
	

	}
	// 定义方法
	返回值的数据类型 方法名称（参数1，参数2…） //零到多个方法
	{
		程序语句 ;

   	 	return 表达式 ;
	}
}
```

#### 对象的创建与使用

类名	对象名称=	new	类名（）；

#### 类的封装

​		在设计一个类时，应该对成员变量的访问做出一些限定，不允许外接随意访问，这就需要实现类的封装。

​		所谓类的封装是指在定义一个类时，将类中的属性**私有化**，即使用private关键字来修饰。私有属性只能在它所在的类中被访问，如果有外界想要访问私有属性，需要提供一些使用public修饰的的公有方法，其中包括常用的get和set方法。

#### 构造方法

​		如果需要在实例化对象的同时就**为这个对象的属性进行赋值**，可以通过构造方法来实现。构造方法是类的一个特殊成员，它会在类实例化对象时被自动调用。

##### 构造方法的定义

1. 方法名与类名相同
2. 在方法名的前面没有返回值类型声明
3. 在方法中不能使用return语句返回一个值，但是可以单独写return语句来作为方法的结束

**注意：**

​		在java中每个类至少都有一个构造方法，如果在一个类中没有定义构造方法，系统会自动为这个类创建一个构造方法，这个默认的构造方法没有参数，在其方法体重没有任何代码，即什么也不做。

但一旦自己为一个类定义了构造方法，系统就不再提供默认的构造方法了。

#### this关键字

​		为了解决成员变量和局部变量同名冲突，使用this代指成员变量（类里面定义的变量，大的）

**注意：**

​		只能在构造方法中使用this调用其他的构造函数，不能在成员方法中使用。

​		在构造方法中，使用this调用构造方法**有且只能**位于第一行，且**仅**能出现一次。

#### 垃圾回收机制

​		一个对象在成为垃圾后，会暂时的保存在内存当中，当这样的垃圾堆积到一定程度时，Java虚拟机就会启动垃圾回收器将这些垃圾对象从内存中释放，从而是程序获得更多可用的内存空间。

#### static关键字

##### 静态变量

​		在定义一个类时，只是在描述该类事物的特征和行为，并没有产生具体的数据，只有通过new实体化对象后，系统才回给每个对象分配空间，存储各自的数据。有时候开发人员希望某些特定的数据在内存中只有一份，且能被一个类的所有实例对象所共享。

​		在Java类中，static修饰的成员变量被称为静态变量，**被所有实例所共享**。

##### 静态方法

​		在实际开发时，开发人员有时候希望在**不创建对象的情况下就可以调用某个方法**，可以使该方法用static修饰

##### 静态代码块

​		当类被加载时，静态代码块会被执行，由于类只加载一次，因此静态代码块只执行一次，通常用于对类的**成员变量进行初始化**

#### 内部类

```
		允许在一个类的内部定义类，这样的类称作内部类

class Outer{
    private String str ="外部类中的字符串";
    //************************** 
    //定义一个内部类
    class Inner{
        private String inStr= "内部类中的字符串";
        //定义一个普通方法
        public void print(){
            //调用外部类的str属性
            System.out.println(str);
        }
    }
    //************************** 
    //在外部类中定义一个方法，该方法负责产生内部类对象并调用print()方法
    public void fun(){
        //内部类对象
        Inner in = new Inner();
        //内部类对象提供的print
        in.print();
    }
}
public class Test{
    public static void main(String[] args)
    {
        //创建外部类对象
        Outer out = new Outer();
        //外部类方法
        out.fun();
    }
}
```







### 类的继承

​		在Java中，类的继承是指在一个现有类的基础上去构建一个新的类，构造出来的新类被称作子类，原类被称作父类，子类会自动拥有父类**所有可继承的属性和方法**

**注意：**

1. 类只支持单继承，只能有一个直接父类
2. 多个类可以继承同一个父类，一个类可以有多个子类
3. 间接继承是可以存在的，即一个类的父类可以是另一个类的子类
4. 父子类是相对概念，也支持多层继承

#### 重写父类方法（多态）

​		有时在子类中需要对继承的方法进行一些修改，即对父类的方法进行重写。

**注意：**

​		子类重写父类方法时，不能使用比父类方法中被重写的方法更严格的访问权限，

如：父类中的方法是public，子类的方法就不能用private

#### super关键字

子类可用super关键字访问父类的成员变量和成员方法

super.成员变量

super.成员方法([参数 1,参数 2,...,参数 n])

**注意：**

1. 通过super调用父类的构造方法的代码必须位于子类构造方法的第一行且只能出现一次
2. 子类构造方法中一定会出现父类的某个构造方法，这时可以在子类的构造方法中通过super指定调用父类的哪个构造方法，如果没有指定，在实例化子类对象时，会自动调用父类的无参构造方法

#### final关键字

**特性：**

1. 修饰的类不能被继承（最终类，防止被修改）
2. 修饰的方法不能被子类重写
3. 修饰的变量（成员变量和局部变量）是常量，只能赋值一次。（一般配static）

final修饰的成员变量时，虚拟机不会对其进行初始化，因此在使用final修饰成员变量时，必须要在定义变量的同时赋予一个初值，也是终值。

### 抽象类和接口

#### 抽象类

​		当顶一个一个类时，常常需要定义一些方法来描述该类的行为特征，但有时这些方法的实现方式是无法确定的。针对这种情况，Java允许在定义方法时不写方法体。不包含方法体的方法叫抽象方法，使用abstract修饰。

**注意：**

1. 定义抽象类时需注意，包含抽象方法的类**必须**声明为抽象类，但抽象类**可以不包含**任何抽象方法
2. 抽象类本身不可被实例化，因为抽象类可能包含抽象方法，抽象方法是没有方法体的，不可被调用。若需要调用抽象类中的方法，需要在子类中将抽象方法进行实现。

#### 接口

​		如果一个抽象类中的所有方法都是抽象的，则可以定义为接口，接口是由常量和抽象方法组成的特殊类，是对抽象类的进一步抽象。

**特点**

1. 一个接口可以有多个父接口，他们之间用','隔开，一个类可以实现多个接口
2. 接口的变量默认用‘ public static final ’来修饰，即全局变量
3. 接口中定义的方法默认使用‘public static’
4. 因为接口中的方法都为抽象方法，因此不能通过实例化对象来调用接口中的方法，此时需要定义一个类，使用implement实现接口中的**所有**方法

### 多态

​		在设计方法时，通常希望该方法具有一定的通用性。在同一个方法中，由于参数类型不同而导致执行效果各异的现象就是多态。继承是多态得以实现的基础。多态不仅解决了方法同名的问题，而且还使得程序变得更加灵活，从而有效地提高了程序的可扩展性和可维护性。

#### 对象类型的转换

```
Human	son=  new	Father();//将子类对象当做父类类型来使用
```

​		将子类对象当做父类使用时不需要任何显示的声明，需要注意的是，此时**不能通过父类变量去调用子类中的特有方法**。

#### Object类

​		Object类是类层次结构的**根类**，每个类都直接或间接继承该类（使用Object作为超类），所以对象（包括数组）都实现了这个类的方法。



| 方法名称   |                                  |
| ---------- | -------------------------------- |
| equals()   | 指定他的对象和其他对象是否“相同” |
| geClass()  | 返回此Object的运行类             |
| hashCode() | 返回该对象的哈希值               |
| toString() | 返回该对象的字符创表示           |

#### 匿名内部类

**实现接口的匿名类**

```
HelloWorld frenchGreeting = new HelloWorld() {
 2    String name = "tout le monde";
 3    public void greet() {
 4          greetSomeone("tout le monde");
 5    }
 6    public void greetSomeone(String someone) {
 7         name = someone;
 8         System.out.println("Salut " + name);
 9    }
10  };
```

**匿名子类（继承父类）**

```
public class AnimalTest {
 2 
 3     private final String ANIMAL = "动物";
 4 
 5     public void accessTest() {
 6         System.out.println("匿名内部类访问其外部类方法");
 7     }
 8 
 9     class Animal {
10         private String name;
11 
12         public Animal(String name) {
13             this.name = name;
14         }
15 
16         public void printAnimalName() {
17             System.out.println(bird.name);
18         }
19     }
20 
21     // 鸟类，匿名子类，继承自Animal类，可以覆写父类方法
22     Animal bird = new Animal("布谷鸟") {
23 
24         @Override
25         public void printAnimalName() {
26             accessTest();   　　　　　　　　// 访问外部类成员
27             System.out.println(ANIMAL);  // 访问外部类final修饰的变量
28             super.printAnimalName();
29         }
30     };
31 
32     public void print() {
33         bird.printAnimalName();
34     }
35 
36     public static void main(String[] args) {
37 
38         AnimalTest animalTest = new AnimalTest();
39         animalTest.print();
40     }
41 }
```

### 异常

​		对程序员而言，还可以处理的问题，错误，不能处理的错误

​		java把异常当作对象来处理，Java中所有异常，都继承自java.lang.Throwable类。Throwable有两个直接子类，Error类和Exception类

**Exception**

​		Exception类及其子类是 Throwable 的一种形式，它指出了合理的应用程序想要捕获的条件。 

​		Exception可分为执行异常（RuntimeException）和检查异常（Checked Exceptions）两种。

**RuntimeException**

RuntimeException在默认情况下会得到自动处理。所以通常用不着捕获RuntimeException，但在自己的封装里，也许仍然要选择抛出一部分RuntimeException。

`RuntimeException`是那些可能在 Java 虚拟机正常运行期间抛出的异常的超类。可能在执行方法期间抛出但未被捕获的`RuntimeException`的任何子类都无需在`throws`子句中进行声明。（java api）

**CheckedException**

除了RuntimeException以外的异常，都属于checkedException，它们都在java.lang库内部定义。Java编译器要求程序必须捕获或声明抛出这种异常。

一个方法必须通过throws语句在方法的声明部分说明它可能抛出但并未捕获的所有checkedException

**Error**

Error 是 Throwable 的子类，用于指示合理的应用程序不应该试图捕获的严重问题。大多数这样的错误都是异常条件。虽然 ThreadDeath 错误是一个“正规”的条件，但它也是 Error 的子类，因为大多数应用程序都不应该试图捕获它。 

在执行该方法期间，无需在其 throws 子句中声明可能抛出但是未能捕获的 Error 的任何子类，因为这些错误可能是再也不会发生的异常条件。

它是uncheckedException

![img](https://img-blog.csdnimg.cn/20190612234942627.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2phdmFfY3hycw==,size_16,color_FFFFFF,t_70)



Error：是程序中无法处理的错误，表示运行应用程序中出现了严重的错误。此类错误一般表示代码运行时JVM出现问题。通常有Virtual MachineError（虚拟机运行错误）、NoClassDefFoundError（类定义错误）等。比如说当jvm耗完可用内存时，将出现OutOfMemoryError。此类错误发生时，JVM将终止线程。非代码性错误。因此，当此类错误发生时，应用不应该去处理此类错误。

Exception：：程序本身可以捕获并且可以处理的异常。

运行时异常(不受检异常)：RuntimeException类极其子类表示JVM在运行期间可能出现的错误。编译器不会检查此类异常，并且不要求处理异常，比如用空值对象的引用（NullPointerException）、数组下标越界（ArrayIndexOutBoundException）。此类异常属于不可查异常，一般是由程序逻辑错误引起的，在程序中可以选择捕获处理，也可以不处理。

非运行时异常(受检异常)：Exception中除RuntimeException极其子类之外的异常。编译器会检查此类异常，如果程序中出现此类异常，比如说IOException，必须对该异常进行处理，要么使用try-catch捕获，要么使用throws语句抛出，否则编译不通过。

#### 常见异常类型

算术异常类：ArithmeticExecption

空指针异常类：NullPointerException

类型强制转换异常：ClassCastException

数组负下标异常：NegativeArrayException

数组下标越界异常：ArrayIndexOutOfBoundsException

违背安全原则异常：SecturityException

文件已结束异常：EOFException

文件未找到异常：FileNotFoundException

字符串转换为数字异常：NumberFormatException


操作数据库异常：SQLException


输入输出异常：IOException


方法未找到异常：NoSuchMethodException

java.lang.AbstractMethodError

抽象方法错误。当应用试图调用抽象方法时抛出。

java.lang.AssertionError

断言错。用来指示一个断言失败的情况。

java.lang.ClassCircularityError

类循环依赖错误。在初始化一个类时，若检测到类之间循环依赖则抛出该异常。

java.lang.ClassFormatError

类格式错误。当Java虚拟机试图从一个文件中读取Java类，而检测到该文件的内容不符合类的有效格式时抛出。

java.lang.Error

错误。是所有错误的基类，用于标识严重的程序运行问题。这些问题通常描述一些不应被应用程序捕获的反常情况。

java.lang.ExceptionInInitializerError

初始化程序错误。当执行一个类的静态初始化程序的过程中，发生了异常时抛出。静态初始化程序是指直接包含于类中的static语句段。

java.lang.IllegalAccessError

违法访问错误。当一个应用试图访问、修改某个类的域（Field）或者调用其方法，但是又违反域或方法的可见性声明，则抛出该异常。

java.lang.IncompatibleClassChangeError

不兼容的类变化错误。当正在执行的方法所依赖的类定义发生了不兼容的改变时，抛出该异常。一般在修改了应用中的某些类的声明定义而没有对整个应用重新编译而直接运行的情况下，容易引发该错误。

java.lang.InstantiationError

实例化错误。当一个应用试图通过Java的new操作符构造一个抽象类或者接口时抛出该异常.

java.lang.InternalError

内部错误。用于指示Java虚拟机发生了内部错误。

java.lang.LinkageError

链接错误。该错误及其所有子类指示某个类依赖于另外一些类，在该类编译之后，被依赖的类改变了其类定义而没有重新编译所有的类，进而引发错误的情况。

java.lang.NoClassDefFoundError

未找到类定义错误。当Java虚拟机或者类装载器试图实例化某个类，而找不到该类的定义时抛出该错误。

java.lang.NoSuchFieldError

域不存在错误。当应用试图访问或者修改某类的某个域，而该类的定义中没有该域的定义时抛出该错误。

java.lang.NoSuchMethodError

方法不存在错误。当应用试图调用某类的某个方法，而该类的定义中没有该方法的定义时抛出该错误。

java.lang.OutOfMemoryError

内存不足错误。当可用内存不足以让Java虚拟机分配给一个对象时抛出该错误。

java.lang.StackOverflowError

堆栈溢出错误。当一个应用递归调用的层次太深而导致堆栈溢出时抛出该错误。

java.lang.ThreadDeath

线程结束。当调用Thread类的stop方法时抛出该错误，用于指示线程结束。

java.lang.UnknownError

未知错误。用于指示Java虚拟机发生了未知严重错误的情况。

java.lang.UnsatisfiedLinkError

未满足的链接错误。当Java虚拟机未找到某个类的声明为native方法的本机语言定义时抛出。

java.lang.UnsupportedClassVersionError

不支持的类版本错误。当Java虚拟机试图从读取某个类文件，但是发现该文件的主、次版本号不被当前Java虚拟机支持的时候，抛出该错误。

java.lang.VerifyError

验证错误。当验证器检测到某个类文件中存在内部不兼容或者安全问题时抛出该错误。

java.lang.VirtualMachineError

虚拟机错误。用于指示虚拟机被破坏或者继续执行操作所需的资源不足的情况。


java.lang.ArithmeticException

算术条件异常。譬如：整数除零等。

java.lang.ArrayIndexOutOfBoundsException

数组索引越界异常。当对数组的索引值为负数或大于等于数组大小时抛出。

java.lang.ArrayStoreException

数组存储异常。当向数组中存放非数组声明类型对象时抛出。

java.lang.ClassCastException

类造型异常。假设有类A和B（A不是B的父类或子类），O是A的实例，那么当强制将O构造为类B的实例时抛出该异常。该异常经常被称为强制类型转换异常。

java.lang.ClassNotFoundException

找不到类异常。当应用试图根据字符串形式的类名构造类，而在遍历CLASSPAH之后找不到对应名称的class文件时，抛出该异常。

java.lang.CloneNotSupportedException

不支持克隆异常。当没有实现Cloneable接口或者不支持克隆方法时,调用其clone()方法则抛出该异常。

java.lang.EnumConstantNotPresentException

枚举常量不存在异常。当应用试图通过名称和枚举类型访问一个枚举对象，但该枚举对象并不包含常量时，抛出该异常。

java.lang.Exception

根异常。用以描述应用程序希望捕获的情况。

java.lang.IllegalAccessException

违法的访问异常。当应用试图通过反射方式创建某个类的实例、访问该类属性、调用该类方法，而当时又无法访问类的、属性的、方法的或构造方法的定义时抛出该异常。

java.lang.IllegalMonitorStateException

违法的监控状态异常。当某个线程试图等待一个自己并不拥有的对象（O）的监控器或者通知其他线程等待该对象（O）的监控器时，抛出该异常。

java.lang.IllegalStateException

违法的状态异常。当在Java环境和应用尚未处于某个方法的合法调用状态，而调用了该方法时，抛出该异常。

java.lang.IllegalThreadStateException

违法的线程状态异常。当县城尚未处于某个方法的合法调用状态，而调用了该方法时，抛出异常。

java.lang.IndexOutOfBoundsException

索引越界异常。当访问某个序列的索引值小于0或大于等于序列大小时，抛出该异常。

java.lang.InstantiationException

实例化异常。当试图通过newInstance()方法创建某个类的实例，而该类是一个抽象类或接口时，抛出该异常。

java.lang.InterruptedException

被中止异常。当某个线程处于长时间的等待、休眠或其他暂停状态，而此时其他的线程通过Thread的interrupt方法终止该线程时抛出该异常。

java.lang.NegativeArraySizeException

数组大小为负值异常。当使用负数大小值创建数组时抛出该异常。

java.lang.NoSuchFieldException

属性不存在异常。当访问某个类的不存在的属性时抛出该异常。

java.lang.NoSuchMethodException

方法不存在异常。当访问某个类的不存在的方法时抛出该异常。

java.lang.NullPointerException

空指针异常。当应用试图在要求使用对象的地方使用了null时，抛出该异常。譬如：调用null对象的实例方法、访问null对象的属性、计算null对象的长度、使用throw语句抛出null等等。

java.lang.NumberFormatException

数字格式异常。当试图将一个String转换为指定的数字类型，而该字符串确不满足数字类型要求的格式时，抛出该异常。

java.lang.RuntimeException

运行时异常。是所有Java虚拟机正常操作期间可以被抛出的异常的父类。



java.lang.SecurityException

安全异常。由安全管理器抛出，用于指示违反安全情况的异常。

java.lang.StringIndexOutOfBoundsException

字符串索引越界异常。当使用索引值访问某个字符串中的字符，而该索引值小于0或大于等于序列大小时，抛出该异常。

java.lang.TypeNotPresentException

类型不存在异常。当应用试图以某个类型名称的字符串表达方式访问该类型，但是根据给定的名称又找不到该类型是抛出该异常。该异常与ClassNotFoundException的区别在于该异常是unchecked（不被检查）异常，而ClassNotFoundException是checked（被检查）异常。

java.lang.UnsupportedOperationException

#### try...catch和finally

​		Java中提供了一种对异常进行处理的方式——异常捕获。通常使用try...catch代码块

try代码块

```
try {
   ...  //监视代码执行过程，一旦返现异常则直接跳转至catch，
        // 如果没有异常则直接跳转至finally
} catch (SomeException e) {
    ... //可选执行的代码块，如果没有任何异常发生则不会执行；
        //如果发现异常则进行处理或向上抛出。
} finally {
    ... //必选执行的代码块，不管是否有异常发生，
        // 即使发生内存溢出异常也会执行，通常用于处理善后清理工作。
}
```

#### throws关键字

​		若是某个方法可能发生异常，但不想在当前方法中处理这个异常，则可以使用throws、throw关键字在方法中抛出异常。

​		throws通常用在声明方法时，用来制指定可能抛出的异常。多个异常可以使用逗号分隔。

​		throw关键字通常用于方法体中，并且抛出一个异常对象，这个异常并不一定发生。程序在执行到throw语句时立即终止，它后面的语句都不执行。通过throw抛出异常后，如果想在上一级代码中来捕获并处理异常，则需要在抛出异常的方法中使用throws关键字在方法的声明中指明要抛出的异常；如果要捕获throw抛出的异常，则必须使用try-catch语句块；

**throws语法格式**

```
修饰符	返回值类型	方法名	([参数 1，参数 2，...参数 n])throws ExceptionType1,ExceptionType2,...{

}
```

​		从上述语法格式中可以看出，throws关键字需要写在方法声明的后面，throws后面需要声明方法异常的类型，通常将这种做法称为方法声明抛出一个异常



throws是用来声明一个方法可能抛出的所有异常信息

throw则是指抛出的一个具体的异常类型。

通常在一个方法（类）的声明处通过throws声明方法（类）可能抛出的异常信息，而在方法（类）内部通过throw声明一个具体的异常信息。

throws通常不用显示的捕获异常，可由系统自动将所有捕获的异常信息 抛给上级方法 ；

throw则需要用户自己捕获相关的异常，而后在对其进行相关包装，最后在将包装后的异常信息抛出

例子

```java
public Test() throws RepletException {
    try {
        System.out.println("Test this Project!")
    }
    catch (Exception e) {
        throw new Exception(e.toString());
    }
```

**finalize**　　

　　finalize()是在java.lang.Object里定义的，也就是说每一个对象都有这么个方法。这个方法在gc启动，该对象被回收的时候被调用。其实gc可以回收大部分的对象（凡是new出来的对象，gc都能搞定，一般情况下我们又不会用new以外的方式去创建对象），所以一般是不需要程序员去实现finalize的。 
特殊情况下，需要程序员实现finalize，当对象被回收的时候释放一些资源，比如：一个socket链接，在对象初始化时创建，整个生命周期内有效，那么就需要实现finalize，关闭这个链接。 
　　使用finalize还需要注意一个事，调用super.finalize();

　　一个对象的finalize()方法只会被调用一次，而且finalize()被调用不意味着gc会立即回收该对象，所以有可能调用finalize()后，该对象又不需要被回收了，然后到了真正要被回收的时候，因为前面调用过一次，所以不会调用finalize()，产生问题。 所以，推荐不要使用finalize()方法，它跟析构函数不一样。



**捕获异常**

​		如果代码可能抛出多种异常，相应的我们也要使用多个catch子句进行捕获。当异常发生时，每个catch子句会被依次检查，当第一个匹配的子句被执行时，捕获结束，其他的子句将不会再检查。所以这里有一个重要原则：\**先子类后父类\**

​		finally子句是可选项，可有可无。无论出不出现异常，finally都会在try/catch之后执行。

- 不要再finally里使用return，会覆盖前面的返回值。
- 不要在finally里抛出异常，会抑制前面抛出的异常。
- 尽量不要再finally里做其他事，finally仅仅用于释放资源最合适。
- 尽量将所有的return写在方法的最后，不要写在try/catch/finally中

#### 自定义异常

​		Java运行用户自定义异常，但自定义异常类必须继承自Exception或其子类

```
throw：抛出明确的异常，throw后面的任何语句不会被执行，一般是程序员主动抛出。
throw new 具体的异常问题对象;
```



#### 访问权限

![img](https://img-blog.csdnimg.cn/20181213110043206.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQ0MDEzNzkw,size_16,color_FFFFFF,t_70)



## JavaAPI

​		API（Application Programming Interface,应用程序编程接口）是一些预先定义的函数，目的是提供应用程序与开发人员基于某软件或硬件的以访问一组[例程](https://baike.baidu.com/item/例程/2390628)的能力，而又无需访问源码，或理解内部工作机制的细节。

### String和StringBuffer

<img src="https://img-blog.csdn.net/20180411091757991?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTEwMTE3Mw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="img" style="zoom:80%;" />

**String:**

1. 是对象不是原始类型。
2. 为不可变对象,一旦被创建,就不能修改它的值。
3. 对于已经存在的String对象的修改都是重新创建一个新的对象,然后把新的值保存进去。
4. String是final类,即不能被继承。

**StringBuffer:**

1. 是一个可变对象,当对它进行修改的时候不会像String那样重新建立对象。
2. 它只能通过构造函数来建立，StringBuffer subffer=new StringBuffer();
3. 对象被建立以后,在内存中就会分配内存空间,并初始保存一个null,通过它的append方法向其赋值 subffer.append(“hello word”);

字符串连接操作中**StringBuffer**的效率要明显比**String**高;
**String**对象是不可变对象,每次操作String都会建立新的对象来保存新的值。
**StringBuffer**对象实例化后,只对这一个对象操作。

和 String 类不同的是，StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且**不产生新的未使用对象**。

StringBuilder 类在 Java 5 中被提出，它和 StringBuffer 之间的最大不同在于 StringBuilder 的方法不是线程安全的（不能同步访问）。

由于 StringBuilder 相较于 StringBuffer 有速度优势，**所以多数情况下建议使用 StringBuilder 类**。然而在应用程序要求线程安全的情况下，则必须使用 StringBuffer 类。

**三者的继承结构**

![img](https://img-blog.csdn.net/20180411092328691?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTEwMTE3Mw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**三者的区别**：

![img](https://img-blog.csdn.net/20180411092400746?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MTEwMTE3Mw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



**小结**：

（1）如果要操作少量的数据用 String；

（2）多线程操作字符串缓冲区下操作大量数据 StringBuffer；

（3）单线程操作字符串缓冲区下操作大量数据 StringBuilder。

### System类与Runtime类

#### System类

​		**getProperties()**方法，用于获取当前系统的全部信息

​		**currentTimeMills()**方法返回一个long类型的时间戳，为与1970年1月1日0时0分0秒之间的时间差，单位是ms

可以用内置的satart和endTime来求程序运行的时间

用处：

1. **用来测试程序的运行时间：**

![img](https://img-blog.csdn.net/20150116163528843?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZ2FvX2NodW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

2. **控制线程时间，刷新屏幕频率：**

```
time1 = System.currentTimeMillis();
   ------程代码段------
time2 = System.currentTimeMillis();
if (time2 - time1 < 60) {
try {
Thread.sleep(60 - (time2 - time1));
		} catch (InterruptedException e) {
	}
}
```

3. ***\*生成不重复的文件名\****

```
public String getName(){

     Stringdate1 = null;

     SimpleDateFormatsdf1 = new SimpleDateFormat("yyyyMMddHHmmssSSS");

     date1= sdf1.format(new Date(System.currentTimeMillis()))+".txt";

     return date1;

}
```



4. ***\*获取日期类型\****

```
long currentTime = System.currentTimeMillis();
SimpleDateFormat formatter = new SimpleDateFormat("yyyy年-MM月dd日-HH时mm分ss秒")
Date date = new Date(currentTime);
System.out.println(formatter.format(date));
```

运行结果如下：
当前时间:2015年-01月16日-16时42分46秒

**arraycopy**

```
public static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
```

​																源数组		源数组起始位置	 目的数组	目的数组起始位置	拷贝元素个数

### **Runtime类**

​		Runtime类用于表示虚拟机运行时的状态，它用于封装JVM虚拟机进程。每次使用java命令启用虚拟机都对应一个Runtime实例，并且只有一个实例，因此该类采用单例模式进行设计，对象不可直接实例化。

​		**唯一获取实例方式**

```
Runtime	run=  Runtime.gettime();
```

### Math类和Radom类

#### Math类

​		Math类是数学操作类，提供了一系列用于数学运算的静态方法，包括求绝对值，三角函数等基础常用方法。Math类中有两个静态常量PI和E，分别代表数学常量π和e。

#### Radom类

​		Radom类可以在指定的取值范围内随机生成数字。

系统以当前时间戳为种子产生随机数。



### 包装类

​		很多类的方法都需要接收引用类型的对象，无法将一个基本数据类型值传入，JDK中提供一系列包装类，通过这些包装类可以将基本数据类型的值包装为引用数据类型的对象。

![img](https://img-blog.csdn.net/2018090917362380?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3lhbmd5ZWNoaQ==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)



## 集合类

​		为了在在程序中可以保存这些数目不定的对象，JDK中提供了一些列特殊的类，这些类可以存储任意类型的对象，并且长度可变，在Java中这些类被统称为集合。集合类都位于java.util包中，注意使用时需导包。

​		<img src="https://img-blog.csdn.net/20180612094225630?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3poYW5ncXVuc2h1YWk=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="img" style="zoom: 50%;" />

#### 1.集合和数组的区别：

<img src="https://img-blog.csdn.net/20180803193134355?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom:67%;" />

#### 2.Collection集合的方法：

<img src="https://img-blog.csdn.net/20180803193423722?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom:67%;" />

#### 3.常用集合的分类：

**Collection 接口的接口 对象的集合（单列集合）**
**├——-List 接口：元素按进入先后有序保存，可重复**

**│—————-├ LinkedList 接口实现类， 链表， 插入删除， 没有同步， 线程不安全**

**│—————-├ ArrayList 接口实现类， 数组， 随机访问， 没有同步， 线程不安全**
**│—————-└ Vector 接口实现类 数组， 同步， 线程安全**
**│ ———————-└ Stack 是Vector类的实现类**
**└——-Set 接口： 仅接收一次，不可重复，并做内部排序**
**├—————-└HashSet 使用hash表（数组）存储元素，不安全**
**│————————└ LinkedHashSet 链表维护元素的插入次序**
**└ —————-TreeSet 底层实现为二叉树，元素排好序**

**Map 接口 键值对的集合 （双列集合）**
**├———Hashtable 接口实现类， 同步， 线程安全**
**├———HashMap 接口实现类 ，没有同步， 线程不安全-**
**│—————–├ LinkedHashMap 双向链表和哈希表实现**
**│—————–└ WeakHashMap**
**├ ——–TreeMap 红黑树对所有的key进行排序**
**└———IdentifyHashMap**



### hashmap

1.HashMap的常用方法

| 功能                               | 语法                        | 返回值、类型                                     |
| ---------------------------------- | --------------------------- | ------------------------------------------------ |
| 存入值                             | .**put**("key","value")     | 无                                               |
| 取出值                             | .**get**("key")             | Value                                            |
| 判断map是否为空                    | .isEmpty()                  | boolean                                          |
| 判断map中是否存在这个key           | .containsValue("value")     | boolean                                          |
| 判断map中是否含有value             | .containsValue("value")     | boolean                                          |
| 删除这个key值下的value             | .**remove**("key")          | Value                                            |
| 显示所有的value值                  | .values()                   | Value                                            |
| 显示map里的值得数量                | .size()                     | int                                              |
| 显示当前已存的key                  | .keySet()                   | Key的类型数组                                    |
| 显示所有的key和value               | .entrySet()                 | 返回Key=Value类型数组                            |
| 添加另一个同一类型的map            | .putAll(map)                | (参数为另一个同一类型的map)无返回值              |
| 删除这个key和value                 | .**remove**("key", "value") | (如果该key值下面对应的是该value值则删除) boolean |
| 替换这个key对应的value值(JDK8新增) | .**replace**("key","value") | 返回被替换掉的Value值的类型                      |
| 克隆Hashmap                        | .clone()                    | object                                           |
| 清空Hashmap                        | .clear()                    | 无                                               |



#### 代码解析

Node是HashMap的一个内部类，实现了Map.Entry接口，本质上是一个映射（键值对）。上图中每一个黑圆点就是一个Node对象。来看具体代码：

```
//Node是单向链表，它实现了Map.Entry接口
static class Node<k,v> implements Map.Entry<k,v> {
    final int hash;
    final K key;
    V value;
    Node<k,v> next;
    //构造函数Hash值 键 值 下一个节点
    Node(int hash, K key, V value, Node<k,v> next) {
        this.hash = hash;
        this.key = key;
        this.value = value;
        this.next = next;
    }
```



    public final K getKey()        { return key; }
    public final V getValue()      { return value; }
    public final String toString() { return key + = + value; }
     
    public final int hashCode() {
        return Objects.hashCode(key) ^ Objects.hashCode(value);
    }
     
    public final V setValue(V newValue) {
        V oldValue = value;
        value = newValue;
        return oldValue;
    }
    //判断两个node是否相等,若key和value都相等，返回true。可以与自身比较为true
    public final boolean equals(Object o) {
        if (o == this)
            return true;
        if (o instanceof Map.Entry) {
            Map.Entry<!--?,?--> e = (Map.Entry<!--?,?-->)o;
            if (Objects.equals(key, e.getKey()) &&
                Objects.equals(value, e.getValue()))
                return true;
        }
        return false;
    }
}
可以看到，node中包含一个next变量，这个就是链表的关键点，hash结果相同的元素就是通过这个next进行关联的。 

2.3.2 红黑树

```
//红黑树
static final class TreeNode<k,v> extends LinkedHashMap.Entry<k,v> {
    TreeNode<k,v> parent;  // 父节点
    TreeNode<k,v> left; //左子树
    TreeNode<k,v> right;//右子树
    TreeNode<k,v> prev;    // needed to unlink next upon deletion
    boolean red;    //颜色属性
    TreeNode(int hash, K key, V val, Node<k,v> next) {
        super(hash, key, val, next);
    }
```



    //返回当前节点的根节点
    final TreeNode<k,v> root() {
        for (TreeNode<k,v> r = this, p;;) {
            if ((p = r.parent) == null)
                return r;
            r = p;
        }
    }
}
红黑树比链表多了四个变量，parent父节点、left左节点、right右节点、prev上一个同级节点，红黑树内容较多，不在赘述。 

2.3.3 位桶
transient Node<k,v>[] table;//存储（位桶）的数组
HashMap类中有一个非常重要的字段，就是 Node[] table，即哈希桶数组，明显它是一个Node的数组。

 有了以上3个数据结构，只要有一点数据结构基础的人，都可以大致联想到HashMap的实现了。首先有一个每个元素都是链表（可能表述不准确）的数组，当添加一个元素（key-value）时，就首先计算元素key的hash值，以此确定插入数组中的位置，但是可能存在同一hash值的元素已经被放在数组同一位置了，这时就添加到同一hash值的元素的后面，他们在数组的同一位置，但是形成了链表，所以说数组存放的是链表。而当链表长度太长时，链表就转换为红黑树，这样大大提高了查找的效率。



##### **HashMap的put()和get()的实现**

**map.put(k,v)实现原理**

第一步首先将k,v封装到Node对象当中（节点）。第二步它的底层会调用K的hashCode()方法得出hash值。第三步通过哈希表函数/哈希算法，将hash值转换成数组的下标，下标位置上如果没有任何元素，就把Node添加到这个位置上。如果说下标对应的位置上有链表。此时，就会拿着k和链表上每个节点的k进行equal。如果所有的equals方法返回都是false，那么这个新的节点将被添加到链表的末尾。如其中有一个equals返回了true，那么这个节点的value将会被覆盖。

**map.get(k)实现原理**

第一步：先调用k的hashCode()方法得出哈希值，并通过哈希算法转换成数组的下标。第二步：通过上一步哈希算法转换成数组的下标之后，在通过数组下标快速定位到某个位置上。重点理解如果这个位置上什么都没有，则返回null。如果这个位置上有单向链表，那么它就会拿着参数K和单向链表上的每一个节点的K进行equals，如果所有equals方法都返回false，则get方法返回null。如果其中一个节点的K和参数K进行equals返回true，那么此时该节点的value就是我们要找的value了，get方法最终返回这个要找的value

**为何随机增删、查询效率都很高的原因是？**

**原因：**增删是在链表上完成的，而查询只需扫描部分，则效率高。

HashMap集合的key，会先后调用两个方法，hashCode and equals方法，这这两个方法都需要重写。



#### 遍历方法

方法1：使用For-Each迭代entries

这是最常见的方法，并在大多数情况下更可取的。当你在循环中需要使用Map的键和值时，就可以使用这个方法

```
Map<Integer, Integer> map = new HashMap<Integer, Integer>();
for(Map.Entry<Integer, Integer> entry : map.entrySet()){
	System.out.println("key = " + entry.getKey() + ", value = " + entry.getValue())
}
```


注意：For-Each循环是Java5新引入的，所以只能在Java5以上的版本中使用。如果你遍历的map是null的话，For-Each循环会抛出NullPointerException异常，所以在遍历之前你应该判断是否为空引用。

方法2 使用For-Each迭代keys和values
如果你只需要用到map的keys或values时，你可以遍历KeySet或者values代替entrySet

```
Map<Integer, Integer> map = new HashMap<Integer, Integer>();

//iterating over keys only
for (Integer key : map.keySet()) {
	System.out.println("Key = " + key);
}

//iterating over values only
for (Integer value : map.values()) {
	System.out.println("Value = " + value);
}
```

这个方法比entrySet迭代具有轻微的性能优势(大约快10%)并且代码更简洁

方法3 使用Iterator迭代
使用泛型

```
Map<Integer, Integer> map = new HashMap<Integer, Integer>();
Iterator<Map.Entry<Integer, Integer>> entries = map.entrySet().iterator();
while (entries.hasNext()) {
	Map.Entry<Integer, Integer> entry = entries.next();
	System.out.println("Key = " + entry.getKey() + ", Value = " + entry.getValue());
}
```


不使用泛型

```
Map map = new HashMap();
Iterator entries = map.entrySet().iterator();
while (entries.hasNext()) {
	Map.Entry entry = (Map.Entry) entries.next();
	Integer key = (Integer)entry.getKey();
	Integer value = (Integer)entry.getValue();
	System.out.println("Key = " + key + ", Value = " + value);
}
```


你可以使用同样的技术迭代keyset或者values

这个似乎有点多余但它具有自己的优势。首先，它是遍历老java版本map的唯一方法。另外一个重要的特性是可以让你在迭代的时候从map中删除entries的(通过调用iterator.remover())唯一方法.如果你试图在For-Each迭代的时候删除entries，你将会得到unpredictable resultes 异常。

从性能方法看，这个方法等价于使用For-Each迭代

方法4 迭代keys并搜索values（低效的）
Map<Integer, Integer> map = new HashMap<Integer, Integer>();
for (Integer key : map.keySet()) {
	Integer value = map.get(key);
	System.out.println("Key = " + key + ", Value = " + value);
}
这个方法看上去比方法#1更简洁，但是实际上它更慢更低效，通过key得到value值更耗时（这个方法在所有实现map接口的map中比方法#1慢20%-200%）。如果你安装了FindBugs，它将检测并警告你这是一个低效的迭代。这个方法应该避免

代码演示：
package com.gcc.interview;

import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;
/**
 * HashMap 不同遍历方法比较
 * @author gcc
 *
 * 2018年1月22日
 */
public class TestHashMap {
	public static void main(String[] args) {
		Map<Integer,String> map =new HashMap<Integer,String>();
		map.put(1, "xiao");
		map.put(2, "chao");
		map.put(3, "shang");
		map.put(4, "xue");
		//方法一
		for(Map.Entry<Integer,String> entry : map.entrySet()) {
			System.out.println("方法一：key ="+entry.getKey()+"---value="+entry.getValue());
		}
		
		//方法二
		for(Integer key:map.keySet()) {
			System.out.println("方法二：key = "+key);
		}
		
		for(String value:map.values()) {
			System.out.println("方法二：value = "+value);
		}
		//方法三
		Iterator<Map.Entry<Integer,String>> entries = map.entrySet().iterator();
		while(entries.hasNext()) {
			Map.Entry<Integer,String> entry = entries.next();
			System.out.println("方法三：key = "+entry.getKey()+"--value="+entry.getValue());
		}
		
		//方法四
		for(Integer key:map.keySet()) {
			String value = map.get(key);
			System.out.println("方法四：Key = " + key + ", Value = " + value);
		}
	
	

2.HashMap的几个重要知识点
HashMap是无序且不安全的数据结构。

HashMap 是以key–value对的形式存储的，**key值是唯一的（可以为null）**，一个key只能对应着一个value，但是value是可以重复的。

HashMap 如果再次添加相同的key值，它会覆盖key值所对应的内容，这也是与HashSet不同的一点，Set通过add添加相同的对象，不会再添加到Set中去。

HashMap 提供了get方法，通过key值取对应的value值，但是HashSet只能通过迭代器Iterator来遍历数据，找对象。

#### 二、JDK7与JDK8的HashMap区别

既然讲HashMap，那就不得不说一下JDK7与JDK8（及jdk8以后）的HashMap有什么区别：

jdk8中添加了红黑树，当链表长度**大于等于8**的时候链表会变成**红黑树**
链表新节点插入链表的顺序不同（jdk7是插入头结点，jdk8因为要把链表变为红 黑树所以采用插入尾节点）
hash算法简化 ( jdk8 )
resize的逻辑修改（jdk7会出现死循环，jdk8不会）
三、HashMap的容量与扩容机制
1.HashMap的默认负载因子
    /**

     * The load factor used when none specified in constructor.
          */
        static final float DEFAULT_LOAD_FACTOR = 0.75f;
        /**
          *默认的负载因子是0.75f,也就是75% 负载因子的作用就是计算扩容阈值用，比如说使用
          *无参构造方法创建的HashMap 对象，他初始长度默认是16  阈值 = 当前长度 * 0.75  就
          *能算出阈值，当当前长度大于等于阈值的时候HashMap就会进行自动扩容
          */
面试的时候，面试官经常会问道一个问题：为什么HashMap的默认负载因子是0.75，而不是0.5或者是整数1呢？
答案有两种：

阈值(threshold) = 负载因子(loadFactor) x 容量(capacity) 根据HashMap的扩容机制，他会保证容量(capacity)的值永远都是2的幂 为了保证负载因子x容量的结果是一个整数，这个值是0.75(4/3)比较合理，因为这个数和任何2的次幂乘积结果都是整数。

理论上来讲，负载因子越大，导致哈希冲突的概率也就越大，负载因子越小，费的空间也就越大,这是一个无法避免的利弊关系，所以通过一个简单的数学推理，可以测算出这个数值在0.75左右是比较合理的

2.HashMap的扩容机制
写数据之后会可能触发扩容，HashMap结构内，我记得有一个记录当前数据量的字段，这个数据量字段到达扩容阈值的话，它就会触发扩容的操作

阈值(threshold) = 负载因子(loadFactor) x 容量(capacity) 
当HashMap中table数组(也称为桶)长度 >= 阈值(threshold) 就会自动进行扩容。

扩容的规则是这样的，因为table数组长度必须是2的次方数，扩容其实每次都是按照上一次tableSize位运算得到的就是做一次左移1位运算，
假设当前tableSize是16的话 16转为二进制再向左移一位就得到了32 即 16 << 1 == 32 即扩容后的容量，也就是说扩容后的容量是当前
容量的两倍，但记住HashMap的扩容是采用当前容量向左位移一位（newtableSize = tableSize << 1），得到的扩容后容量，而不是当前容量x2
问题又来了，为什么计算扩容后容量要采用位移运算呢，怎么不直接乘以2呢？
这个问题就比较简单了，因为cpu毕竟它不支持乘法运算，所有的乘法运算它最终都是再指令层面转化为了加法实现的，这样效率很低，如果用位运算的话对cpu来说就非常的简洁高效。

3.HashMap中散列表数组初始长度
    /**
     * The default initial capacity - MUST be a power of two.
          */
        static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16

    /**
     * HashMap中散列表数组初始长度为 16 (1 << 4)
     * 创建HashMap的时候可以设置初始化容量和设置负载因子，
     * 但HashMap会自动优化设置的初始化容量参数，确保初始化
     * 容量始终为2的幂
     */
    老问题又来了，为啥HashMap中初始化大小为什么是16呢？

首先我们看hashMap的源码可知当新put一个数据时会进行计算位于table数组(也称为桶)中的下标：

int index =key.hashCode()&(length-1);

hahmap每次扩容都是以 2的整数次幂进行扩容

因为是将二进制进行按位于，(16-1) 是 1111,末位是1，这样也能保证计算后的index既可以是奇数也可以是偶数，并且只要传进来的key足够分散，均匀那么按位于的时候获得的index就会减少重复，这样也就减少了hash的碰撞以及hashMap的查询效率。

那么到了这里你也许会问？ 那么就然16可以，是不是只要是2的整数次幂就可以呢？

答案是肯定的。那为什么不是8,4呢？ 因为是8或者4的话很容易导致map扩容影响性能，如果分配的太大的话又会浪费资源，所以就使用16作为初始大小。

四、HashMap的结构
JDK7与JDK8及以后的HashMap结构与存储原理有所不同：
Jdk1.7：数组 + 链表 ( 当数组下标相同，则会在该下标下使用链表)
Jdk1.8：数组 + 链表 + 红黑树 (预值为8 如果链表长度 >=8则会把链表变成红黑树 )
Jdk1.7中链表新元素添加到链表的头结点,先加到链表的头节点,再移到数组下标位置
Jdk1.8中链表新元素添加到链表的尾结点
(数组通过下标索引查询，所以查询效率非常高，链表只能挨个遍历，效率非常低。jdk1.8及以
上版本引入了红黑树，当链表的长度大于或等于8的时候则会把链表变成红黑树，以提高查询效率)

五、HashMap存储原理与存储流程
1.HashMap存储原理
获取到传过来的key，调用hash算法获取到hash值

获取到hash值之后调用indexFor方法，通过获取到的hash值以及数组的长度算
出数组的下标 (把哈希值和数组容量转换为二进，再在数组容量范围内与哈希值
进行一次与运算，同为1则1，不然则为0，得出数组的下标值，这样可以保证计算出的数组下标不会大于当前数组容量)

把传过来的key和value存到该数组下标当中。

如该数组下标下以及有值了，则使用链表，jdk7是把新增元素添加到头部节点 jdk8则添加到尾部节点。

2.HashMap存储流程
前面寻址算法都是一样的，根据key的hashcode经过高低位异或之后的值，再按位与 &(table.lingth - 1),得到一个数组下标，然后根据这个数组下标内的状况，状况不同，然后情况也不同，大概分为了4种状态：

( 1.)第一种就是数组下标下内容为空：
这种情况没什么好说的，为空据直接占有这个slot槽位就好了，然后把当前.put方法传进来的key和value包装成一个node对象,放到这个slot中就好了。

( 2.)第二种情况就是数组下标下内容不为空，但它引用的node还没有链化：
这种情况下先要对比一下这个node对象的key与当前put对象的key是否完全.相等，如果完全相等的情况下，就行进行replace操作，把之前的槽位中node.下的value替换成新的value就可以了，否则的话这个put操作就是一个正儿.八经的hash冲突,这种情况在slot槽位后面追加一个node就可以了,用尾插法 ( 前面讲过，jdk7是把新增元素添加到头部节点，而jdk8则添加到尾部节点)。

( 3.)第三种就是该数组下标下内容已经被链化了：
这种情况和第二种情况处理很相似，首先也是迭代查找node，看看链表上中元素的key，与当前传过来的key是否完全一致，如果完全一致的话还是repleace操作，用put过来的新value替换掉之前node中的value，否则的话就是一致迭代到链表尾节点也没有匹配到完全一致的node，就和之前的一样，把put进来数据包装成node追加到链表的尾部，再检查一下当前链表的长度，有没有达到树化阈值，如果达到了阈值就调用一个树化方法，树化操作都是在这个方法里完成的。

( 4.)第四种情况就是冲突很严重的情况下，这个链表已经转化成红黑树了：
红黑树就比较复杂 要将清楚这个红黑树还得从TreeNode说起 TreeNode继承了Node结构，在Node基础上加了几个字段，分别是指向父节点parent字段，指向左子节点left字段，指向右子节点right字段，还有一个表示颜色的red字段，这就是TreeNode的基本结构，然后红黑树的插入操作，首先找到一个合适的插入点，就是找到插入节点的父节点，然后红黑树它又满足二叉树的所有特性，所以找这个父节点的操作和二叉树排序是完全一致的，然后说一下这个二叉树排序，其实就是二分查找算法映射出来的结构，就是一个倒立的二叉树，然后每个节点都可以有自己的子节点，本且左节点小于但前节点，右节点大于当前节点，然后每次向下查找一层就能那个排除掉一半的数据，查找效率非常的高效，当查找的过程中也是分情况的。

首先第一种情况就是一直向下探测，直到查询到左子树或者右子树位null，说明整个树中，并没有发现node链表中的key与当前put key一致的TreeNode,那此时探测节点就是插入父节点的所在了，然后就是判断插入节点的hash值和父节点的hash值大小决定插入到父节点的左子树还是右子树。当然插入会打破平衡，还需要一个红黑树的平衡算法保持平衡。

其次第二种情况就是根节点在向下探测过程中发现TreeNode中key与当前put的key完全一致，然后就也是一次repleace操作，替换value。

六、jdk8中HashMap为什么要引入红黑树？
其实主要就是为了解决jdk1.8以前hash冲突所导致的链化严重的问题，因为链表结构的查询效率是非常低的，他不像数组，能通过索引快速找到想要的值，链表只能挨个遍历，当hash冲突非常严重的时候，链表过长的情况下，就会严重影响查询性能，本身散列列表最理想的查询效率为O(1)，当时链化后链化特别严重，他就会导致查询退化为O(n)为了解决这个问题所以jdk8中的HashMap添加了红黑树来解决这个问题，当链表长度>=8的时候链表就会变成红黑树，红黑树其实就是一颗特殊的二叉排序树嘛，这个时间复杂…反正就是要比列表强很多

七、扩容后的新table数组，那老数组中的这个数据怎么迁移呢
迁移其实就是挨个桶位推进迁移，就是一个桶位一个桶位的处理，主要还是看当前处理桶位的数据状态把，这里也是分了大概四种状态：
这四种的迁移规则都不太一样

(1.)第一种就是数组下标下内容为空：
这种情况下就没什么可说的，不用做什么处理。

( 2.)第二种情况就是数组下标下内容不为空，但它引用的node还没有链化：
当slot它不为空，但它引用的node还没有链化的时候，说明这个槽位它没有发生过hash冲突，直接迁移就好了，根据新表的tableSize计算出他在新表的位置,然后存放进去就好了。

( 3.)第三种就是slot内储存了一个链化的node：
当node中next字段它不为空，说明槽位发生过hash冲突，这个时候需要把当前槽位中保存的这个链表拆分成两个链表，分别是高位链和低位链

(4.)第四种就是该槽位储存了一个红黑树的根节点TreeNode对象：



#### 红黑树

## 红黑树简介

红黑树是一种自平衡的二叉查找树，是一种高效的查找树。它是由 Rudolf Bayer 于1972年发明，在当时被称为`对称二叉 B 树(symmetric binary B-trees)`。后来，在1978年被 Leo J. Guibas 和 Robert Sedgewick 修改为如今的`红黑树`。

红黑树具有良好的效率，它可在 `O(logN)` 时间内完成查找、增加、删除等操作。因此，红黑树在业界应用很广泛，比如 Java 中的 TreeMap，JDK 1.8 中的 HashMap、C++ STL 中的 map 均是基于红黑树结构实现的。

考虑到红黑树是一种被广泛应用的数据结构，所以我们很有必要去弄懂它。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMjS6BibMM5JmzhQGKiar3MocWyficSqF5H33CAXqI8d06HEgiaVV6TKvNCQ/640?wx_fmt=jpeg)

## 红黑树的性质

学过二叉查找树的同学都知道，普通的二叉查找树在极端情况下可退化成链表，此时的增删查效率都会比较低下。为了避免这种情况，就出现了一些自平衡的查找树，比如 AVL，红黑树等。这些自平衡的查找树通过定义一些性质，将任意节点的左右子树高度差控制在规定范围内，以达到平衡状态。以红黑树为例，红黑树通过如下的性质定义实现自平衡：

> 1. 节点是红色或黑色。
> 2. 根是黑色。
> 3. 所有叶子都是黑色（叶子是NIL节点）。
> 4. 每个红色节点必须有两个黑色的子节点。（从每个叶子到根的所有路径上不能有两个连续的红色节点。）
> 5. 从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点（简称黑高）。

有了上面的几个性质作为限制，即可避免二叉查找树退化成单链表的情况。但是，仅仅避免这种情况还不够，这里还要考虑某个节点到其每个叶子节点路径长度的问题。如果某些路径长度过长，那么，在对这些路径上的及诶单进行增删查操作时，效率也会大大降低。这个时候性质4和性质5用途就凸显了，有了这两个性质作为约束，即可保证任意节点到其每个叶子节点路径最长不会超过最短路径的2倍。原因如下：

当某条路径最短时，这条路径必然都是由黑色节点构成。当某条路径长度最长时，这条路径必然是由红色和黑色节点相间构成（性质4限定了不能出现两个连续的红色节点）。而性质5又限定了从任一节点到其每个叶子节点的所有路径必须包含相同数量的黑色节点。

此时，在路径最长的情况下，路径上红色节点数量 = 黑色节点数量。该路径长度为两倍黑色节点数量，也就是最短路径长度的2倍。举例说明一下，请看下图：

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMRXQSEWvQZJw8OswD39cWcexZicqg17Oic6Eib7zIAKvPfqmqiamKadIhNA/640?wx_fmt=jpeg)

上图画出了从根节点 M 出发的到其叶子节点的最长和最短路径。这里偷懒只画出了两条最长路径，实际上最长路径有4条，分别为：

```
M -> Q -> O -> N
M -> Q -> O -> p
M -> Q -> Y -> X
M -> Q -> Y -> Z
```

长度为4，最短路径为 `M -> E`，长度为2。最长路径的长度正好为最短路径长度的2倍。

前面说了关于红黑树的一些性质，这里还需要补充一些其他方面的东西。在红黑树简介一节中说到红黑树被发明出来的时候并不叫`红黑树`，而是叫做`对称二叉 B 树`，从名字中可发现红黑树和 B 树（这里指的是2-3树）或许有一定的关联，事实也正是如此。

如果对红黑树的性质稍加修改，就能让红黑树和B树形成一一对应的关系。关于红黑树和 B 树关系的细节这里不展开说明了，有兴趣的同学可以参考《算法》第4版，那本书上讲的很透彻。

## 红黑树操作

红黑树的基本操作和其他树形结构一样，一般都包括查找、插入、删除等操作。前面说到，红黑树是一种自平衡的二叉查找树，既然是二叉查找树的一种，那么查找过程和二叉查找树一样，比较简单，这里不再赘述。

相对于查找操作，红黑树的插入和删除操作就要复杂的多。尤其是删除操作，要处理的情况比较多，不过大家如果静下心来去看，会发现其实也没想的那么难。好了，废话就说到这，接下来步入正题吧。

### 旋转操作

在分析插入和删除操作前，这里需要插个队，先说明一下旋转操作，这个操作在后续操作中都会用得到。旋转操作分为左旋和右旋，左旋是将某个节点旋转为其右孩子的左孩子，而右旋是节点旋转为其左孩子的右孩子。这话听起来有点绕，所以还是请看下图：

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgM4K2xKtllTV4N62R7dU7XvjYMUSiaNq8bM1FEic20DEibqhlyXwsD4yZJA/640?wx_fmt=jpeg)

上图包含了左旋和右旋的示意图，这里以右旋为例进行说明，右旋节点 M 的步骤如下：

1. 将节点 M 的左孩子引用指向节点 E 的右孩子
2. 将节点 E 的右孩子引用指向节点 M，完成旋转

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMtDcia0vZD3T4SpicJ27SZFbGMsG0Mzs6O6GSiakTT8nKzRJRiatsfX632w/640?wx_fmt=jpeg)

上面分析了右旋操作，左旋操作与此类似，大家有兴趣自己画图试试吧，这里不再赘述了。旋转操作本身并不复杂，这里先分析到这吧。

### 插入

红黑树的插入过程和二叉查找树插入过程基本类似，不同的地方在于，红黑树插入新节点后，需要进行调整，以满足红黑树的性质。性质1规定红黑树节点的颜色要么是红色要么是黑色，那么在插入新节点时，这个节点应该是红色还是黑色呢？

答案是红色，原因也不难理解。如果插入的节点是黑色，那么这个节点所在路径比其他路径多出一个黑色节点，这个调整起来会比较麻烦（参考红黑树的删除操作，就知道为啥多一个或少一个黑色节点时，调整起来这么麻烦了）。

如果插入的节点是红色，此时所有路径上的黑色节点数量不变，仅可能会出现两个连续的红色节点的情况。这种情况下，通过变色和旋转进行调整即可，比之前的简单多了。

接下来，将分析插入红色节点后红黑树的情况。这里假设要插入的节点为 N，N 的父节点为 P，祖父节点为 G，叔叔节点为 U。插入红色节点后，会出现5种情况，分别如下：

#### 情况一：

插入的新节点 N 是红黑树的根节点，这种情况下，我们把节点 N 的颜色由红色变为黑色，性质2（根是黑色）被满足。同时 N 被染成黑色后，红黑树所有路径上的黑色节点数量增加一个，性质5（从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点）仍然被满足。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMujXSrDlM3L1nIFribOC2QeBQiaQ1yzZt2qDnUnW8gsLJ4uoU1hFbgomQ/640?wx_fmt=jpeg)

#### 情况二：

N 的父节点是黑色，这种情况下，性质4（每个红色节点必须有两个黑色的子节点）和性质5没有受到影响，不需要调整。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMq1TkKiaAdwzZy6C4R2pJho4Q98MjG6jwwU7KWJPf08ibrlO2dqvqhhzg/640?wx_fmt=jpeg)

#### 情况三：

N 的父节点是红色（节点 P 为红色，其父节点必然为黑色），叔叔节点 U 也是红色。由于 P 和 N 均为红色，所有性质4被打破，此时需要进行调整。这种情况下，先将 P 和 U 的颜色染成黑色，再将 G 的颜色染成红色。此时经过 G 的路径上的黑色节点数量不变，性质5仍然满足。但需要注意的是 G 被染成红色后，可能会和它的父节点形成连续的红色节点，此时需要递归向上调整。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMpBUqbOGaGZwItLL5dmn8ibG2bl4HOt1UsKFS61afc4PzibPWFTSc1kHg/640?wx_fmt=jpeg)

#### 情况四：

N 的父节点为红色，叔叔节点为黑色。节点 N 是 P 的右孩子，且节点 P 是 G 的左孩子。此时先对节点 P 进行左旋，调整 N 与 P 的位置。接下来按照情况五进行处理，以恢复性质4。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgM3QtA4Hc2Zvibx2jmL3GogmsJrPILbLTwvSPxR0MXzgoiaDF3YbJbV3xg/640?wx_fmt=jpeg)

这里需要特别说明一下，上图中的节点 N 并非是新插入的节点。当 P 为红色时，P 有两个孩子节点，且孩子节点均为黑色，这样从 G 出发到各叶子节点路径上的黑色节点数量才能保持一致。既然 P 已经有两个孩子了，所以 N 不是新插入的节点。情况四是由以 N 为根节点的子树中插入了新节点，经过调整后，导致 N 被变为红色，进而导致了情况四的出现。考虑下面这种情况（PR 节点就是上图的 N 节点）：![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMOVvia6nFSCL0RCmewHIDibPC7xx0Nth9PTDAxmJ86mNphRG5LLwJVTyw/640?wx_fmt=jpeg)

如上图，插入节点 N 并按情况三处理。此时 PR 被染成了红色，与 P 节点形成了连续的红色节点，这个时候就需按情况四再次进行调整。

#### 情况五：

N 的父节点为红色，叔叔节点为黑色。N 是 P 的左孩子，且节点 P 是 G 的左孩子。此时对 G 进行右旋，调整 P 和 G 的位置，并互换颜色。经过这样的调整后，性质4被恢复，同时也未破坏性质5。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgM9M964fQZaDqyyme2V4pt4vHcLY1Zyb4MpLAoOgG487Ik3QxJQNDf4A/640?wx_fmt=jpeg)

#### 插入总结

上面五种情况中，情况一和情况二比较简单，情况三、四、五稍复杂。但如果细心观察，会发现这三种情况的区别在于叔叔节点的颜色，如果叔叔节点为红色，直接变色即可。如果叔叔节点为黑色，则需要选选择，再交换颜色。当把这三种情况的图画在一起就区别就比较容易观察了，如下图：

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMqyVpdgaat4DjFDLGtj4vAtFLicZ2vQlaDicpfC0XJRyZvANRK0B0E6ibw/640?wx_fmt=jpeg)

### 删除

相较于插入操作，红黑树的删除操作则要更为复杂一些。删除操作首先要确定待删除节点有几个孩子，如果有两个孩子，不能直接删除该节点。而是要先找到该节点的前驱（该节点左子树中最大的节点）或者后继（该节点右子树中最小的节点），然后将前驱或者后继的值复制到要删除的节点中，最后再将前驱或后继删除。

由于前驱和后继至多只有一个孩子节点，这样我们就把原来要删除的节点有两个孩子的问题转化为只有一个孩子节点的问题，问题被简化了一些。我们并不关心最终被删除的节点是否是我们开始想要删除的那个节点，只要节点里的值最终被删除就行了，至于树结构如何变化，这个并不重要。

红黑树删除操作的复杂度在于删除节点的颜色，当删除的节点是红色时，直接拿其孩子节点补空位即可。因为删除红色节点，性质5（从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点）仍能够被满足。当删除的节点是黑色时，那么所有经过该节点的路径上的黑节点数量少了一个，破坏了性质5。如果该节点的孩子为红色，直接拿孩子节点替换被删除的节点，并将孩子节点染成黑色，即可恢复性质5。但如果孩子节点为黑色，处理起来就要复杂的多。分为6种情况，下面会展开说明。

在展开说明之前，我们先做一些假设，方便说明。这里假设最终被删除的节点为`X`（至多只有一个孩子节点），其孩子节点为`N`，`X`的兄弟节点为`S`，`S`的左节点为 SL，右节点为 SR。接下来讨论是建立在节点 `X` 被删除，节点 `N` 替换`X`的基础上进行的。这里说明把被删除的节点`X`特地拎出来说一下的原因是防止大家误以为节点`N`会被删除，不然后面就会看不明白。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMkWto263Lucu4g9khuiaMy5lW7ibexf8obkKMFm0sl4PjxQ0yfib81kFHQ/640?wx_fmt=jpeg)

在上面的基础上，接下来就可以展开讨论了。红黑树删除有6种情况，分别是：

#### 情况一：

> N 是新的根。在这种情形下，我们就做完了。我们从所有路径去除了一个黑色节点，而新根是黑色的，所以性质都保持着。

上面是维基百科中关于红黑树删除的情况一说明，由于没有配图，看的有点晕。经过思考，我觉得可能会是下面这种情形：

要删除的节点 X 是根节点，且左右孩子节点均为空节点，此时将节点 X 用空节点替换完成删除操作。

可能还有其他情形，大家如果知道，烦请告知。

#### 情况二：

S 为红色，其他节点为黑色。这种情况下可以对 N 的父节点进行左旋操作，然后互换 P 与 S 颜色。但这并未结束，经过节点 P 和 N 的路径删除前有3个黑色节点（`P -> X -> N`），现在只剩两个了（`P -> N`）。比未经过 N 的路径少一个黑色节点，性质5仍不满足，还需要继续调整。不过此时可以按照情况四、五、六进行调整。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMVznNSQ0FOuwicNILIXUdaY18lVg3vHjU3NCYuL6E8hIcpmLorDEbKZg/640?wx_fmt=jpeg)

#### 情况三：

N 的父节点，兄弟节点 S 和 S 的孩子节点均为黑色。这种情况下可以简单的把 S 染成红色，所有经过 S 的路径比之前少了一个黑色节点，这样经过 N 的路径和经过 S 的路径黑色节点数量一致了。但经过 P 的路径比不经过 P 的路径少一个黑色节点，此时需要从情况一开始对 P 进行平衡处理。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgM4tvQKticHlnyAjicOK3PBJ6vicZFfDaehXNz7C1AYydFEJic3Lhqd557Yw/640?wx_fmt=jpeg)

#### 情况四：

N 的父节点是红色，S 和 S 孩子为黑色。这种情况比较简单，我们只需交换 P 和 S 颜色即可。这样所有通过 N 的路径上增加了一个黑色节点，所有通过 S 的节点的路径必然也通过 P 节点，由于 P 与 S 只是互换颜色，并不影响这些路径。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMiaiblPb2YWsOc2kERmiamkoB7yaFUwU9L78vQgG6rqRRMcgm4ibdEgEIFA/640?wx_fmt=jpeg)

这里需要特别说明一下，上图中的节点 N 并非是新插入的节点。当 P 为红色时，P 有两个孩子节点，且孩子节点均为黑色，这样从 G 出发到各叶子节点路径上的黑色节点数量才能保持一致。既然 P 已经有两个孩子了，所以 N 不是新插入的节点。情况四是由以 N 为根节点的子树中插入了新节点，经过调整后，导致 N 被变为红色，进而导致了情况四的出现。考虑下面这种情况（PR 节点就是上图的 N 节点）：

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMEIGc6or1emib4QXicGC0MMibRRdicPmVxmiaJniauJyzX9j4b1xrzUicTH5rg/640?wx_fmt=jpeg)

#### 情况五：

S 为黑色，S 的左孩子为红色，右孩子为黑色。N 的父节点颜色可红可黑，且 N 是 P 左孩子。这种情况下对 S 进行右旋操作，并互换 S 和 SL 的颜色。此时，所有路径上的黑色数量仍然相等，N 兄弟节点的由 S 变为了 SL，而 SL 的右孩子变为红色。接下来我们到情况六继续分析。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgM35hSa8icuxEI0WFr6rK3vwwJ0WOGic8zJv5N6BGbRDp4LaRGgibZibG4HA/640?wx_fmt=jpeg)

#### 情况六：

S 为黑色，S 的右孩子为红色。N 的父节点颜色可红可黑，且 N 是其父节点左孩子。这种情况下，我们对 P 进行左旋操作，并互换 P 和 S 的颜色，并将 SR 变为黑色。因为 P 变为黑色，所以经过 N 的路径多了一个黑色节点，经过 N 的路径上的黑色节点与删除前的数量一致。对于不经过 N 的路径，则有以下两种情况：

1. 该路径经过 N 新的兄弟节点 SL ，那它之前必然经过 S 和 P。而 S 和 P 现在只是交换颜色，对于经过 SL 的路径不影响。
2. 该路径经过 N 新的叔叔节点 SR，那它之前必然经过 P、 S 和 SR，而现在它只经过 S 和 SR。在对 P 进行左旋，并与 S 换色后，经过 SR 的路径少了一个黑色节点，性质5被打破。另外，由于 S 的颜色可红可黑，如果 S 是红色的话，会与 SR 形成连续的红色节点，打破性质4（每个红色节点必须有两个黑色的子节点）。此时仅需将 SR 由红色变为黑色即可同时恢复性质4和性质5（从任一节点到其每个叶子的所有简单路径都包含相同数目的黑色节点。）。

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMX5fgU1cnYOvNw9yZngDvRicwsrib4JxF55WnexhYCFKiaIbHOZTxgUvjQ/640?wx_fmt=jpeg)

#### 删除总结

红黑树删除的情况比较多，大家刚开始看的时候可能会比较晕。可能会产生这样的疑问，为啥红黑树会有这种删除情况，为啥又会有另一种情况，它们之间有什么联系和区别？

和大家一样，我刚开始看的时候也有这样的困惑，直到我把所有情况对应的图形画在一起时，拨云见日，一切都明了了。此时天空中出现了4个字，原来如此、原来如此、原来如此。所以，请看图吧：

![640?wx_fmt=jpeg](https://ss.csdn.net/p?https://mmbiz.qpic.cn/mmbiz_jpg/JfTPiahTHJhpzvvE8hlDN8OuuibbUOvSgMgxQUclC2AKzvmT4UA01VGKSbnPN32OC6qrwVbg3ib2VP1AQticJo3VJQ/640?wx_fmt=jpeg)



#### 如何应对HashMap线程不安全的问题？

hashtable  `ConcurrentHashMap`，采用分段锁机制

#### ArrayList  **CopyOnWriteArrayList**

Vector

2.1 CopyOnWriteArrayList 使用写时复制技术，读写分离

对于写操作，会使用ReentrantLock加锁，对底层数组拷贝一份，进行修改，修改完后再覆盖原来的数组

 

2.2 底层使用数组

private transient volatile Object[] array;

数据使用volatile修饰，故能保证可见性，存在happens-before关系，使得能读到最新的数据

 

2.3 使用ReentrantLock修改

所有的写操作 读会加锁保证线程安全

但读操作是没有任何锁的，故修改过程中的数据，此时另一个线程是读不到的



### 二、List和Set集合详解：

#### 1.list和set的区别：

<img src="https://img-blog.csdn.net/20180803201610610?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom:50%;" />

#### 2.List：

**（1）ArrayList**：底层数据结构是数组，查询快，增删慢，线程不安全，效率高，可以存储重复元素
**（2）LinkedList** 底层数据结构是链表，查询慢，增删快，线程不安全，效率高，可以存储重复元素
**（3）Vector**:底层数据结构是数组，查询快，增删慢，线程安全，效率低，可以存储重复元素
<img src="https://img-blog.csdn.net/20180803201736883?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom: 75%;" />
（4小结：

#### 3.Set：

**(1)HashSet**底层数据结构采用哈希表实现，**元素无序且唯一**，线程不安全，效率高，可以存储null元素，元素的唯一性是靠所存储元素类型是否重写hashCode()和equals()方法来保证的，如果没有重写这两个方法，则无法保证元素的唯一性。
具体实现唯一性的比较过程：存储元素首先会使用hash()算法函数生成一个int类型hashCode散列值，然后已经的所存储的元素的hashCode值比较，如果hashCode不相等，则所存储的两个对象一定不相等，此时存储当前的新的hashCode值处的元素对象；如果hashCode相等，存储元素的对象还是不一定相等，此时会调用equals()方法判断两个对象的内容是否相等，如果内容相等，那么就是同一个对象，无需存储；如果比较的内容不相等，那么就是不同的对象，就该存储了，此时就要采用哈希的解决地址冲突算法，在当前hashCode值处类似一个新的链表， 在同一个hashCode值的后面存储存储不同的对象，这样就保证了元素的唯一性。
Set的实现类的集合对象中不能够有重复元素，HashSet也一样他是使用了一种标识来确定元素的不重复，HashSet用一种算法来保证HashSet中的元素是不重复的， HashSet采用哈希算法，底层用数组存储数据。默认初始化容量16，加载因子0.75。
Object类中的hashCode()的方法是所有子类都会继承这个方法，这个方法会用Hash算法算出一个Hash（哈希）码值返回，HashSet会用Hash码值去和数组长度取模， 模（这个模就是对象要存放在数组中的位置）相同时才会判断数组中的元素和要加入的对象的内容是否相同，如果不同才会添加进去。
Hash算法是一种散列算法。
Set hs=new HashSet();

hs.add(o);
|
o.hashCode();
|
o%当前总容量 (0–15)
|
| 不发生冲突
是否发生冲突—————–直接存放
|
| 发生冲突
| 假（不相等）
o1.equals(o2)——————-找一个空位添加
|
| 是（相等）
不添加
覆盖hashCode()方法的原则：
1、一定要让那些我们认为相同的对象返回相同的hashCode值
2、尽量让那些我们认为不同的对象返回不同的hashCode值，否则，就会增加冲突的概率。
3、尽量的让hashCode值散列开（两值用异或运算可使结果的范围更广）
HashSet 的实现比较简单，相关HashSet的操作，基本上都是直接调用底层HashMap的相关方法来完成，我们应该为保存到HashSet中的对象覆盖hashCode()和equals()，因为再将对象加入到HashSet中时，会首先调用hashCode方法计算出对象的hash值，接着根据此hash值调用HashMap中的hash方法，得到的值& (length-1)得到该对象在hashMap的transient Entry[] table中的保存位置的索引，接着找到数组中该索引位置保存的对象，并调用equals方法比较这两个对象是否相等，如果相等则不添加，注意：所以要存入HashSet的集合对象中的自定义类必须覆盖hashCode(),equals()两个方法，才能保证集合中元素不重复。在覆盖equals()和hashCode()方法时， 要使相同对象的hashCode()方法返回相同值，覆盖equals()方法再判断其内容。为了保证效率，所以在覆盖hashCode()方法时， 也要尽量使不同对象尽量返回不同的Hash码值。

如果数组中的元素和要加入的对象的hashCode()返回了相同的Hash值（相同对象）,才会用equals()方法来判断两个对象的内容是否相同。

**(2)LinkedHashSet**底层数据结构采用链表和哈希表共同实现，链表保证了元素的顺序与存储顺序一致，哈希表保证了元素的唯一性。线程不安全，效率高。
**(3)TreeSet**底层数据结构采用二叉树来实现，元素唯一且已经排好序；唯一性同样需要重写hashCode和equals()方法，二叉树结构保证了元素的有序性。根据构造方法不同，分为自然排序（无参构造）和比较器排序（有参构造），自然排序要求元素必须实现Compareable接口，并重写里面的compareTo()方法，元素通过比较返回的int值来判断排序序列，返回0说明两个对象相同，不需要存储；比较器排需要在TreeSet初始化是时候传入一个实现Comparator接口的比较器对象，或者采用匿名内部类的方式new一个Comparator对象，重写里面的compare()方法；
（4）小结：Set具有与Collection完全一样的接口，因此没有任何额外的功能，不像前面有两个不同的List。实际上Set就是Collection,只 是行为不同。(这是继承与多态思想的典型应用：表现不同的行为。)Set不保存重复的元素。
Set 存入Set的每个元素都必须是唯一的，因为Set不保存重复元素。加入Set的元素必须定义equals()方法以确保对象的唯一性。Set与Collection有完全一样的接口。Set接口不保证维护元素的次序。

#### 4.List和Set总结：

（1）List,Set都是继承自Collection接口，Map则不是
（2）List特点：元素有放入顺序，元素可重复 ，Set特点：元素无放入顺序，元素不可重复，重复元素会覆盖掉，（注意：元素虽然无放入顺序，但是元素在set中的位置是有该元素的HashCode决定的，其位置其实是固定的，加入Set 的Object必须定义equals()方法 ，另外list支持for循环，也就是通过下标来遍历，也可以用迭代器，但是set只能用迭代，因为他无序，无法用下标来取得想要的值。）
（3）Set和List对比：
Set：检索元素效率低下，删除和插入效率高，插入和删除不会引起元素位置改变。
List：和数组类似，List可以动态增长，查找元素效率高，插入删除元素效率低，因为会引起其他元素位置改变。
（4）ArrayList与LinkedList的区别和适用场景
Arraylist：
	**优点**：ArrayList是实现了基于动态数组的数据结构,因为地址连续，一旦数据存储好了，查询操作效率会比较高（在内存里是连着放的）。
	**缺点**：因为地址连续， ArrayList要移动数据,所以插入和删除操作效率比较低。

LinkedList：
	**优点**：LinkedList基于链表的数据结构,地址是任意的，所以在开辟内存空间的时候不需要等一个连续的地址，对于新增和删除操作add和remove，LinedList比较占优势。LinkedList 适用于要头尾操作或插入指定位置的场景
	**缺点**：因为LinkedList要移动指针,所以查询操作性能比较低。
	**适用场景分析**：
当需要对数据进行对此访问的情况下选用ArrayList，当需要对数据进行多次增加删除修改时采用LinkedList。

ArrayList与Vector的区别和适用场景
ArrayList有三个构造方法：

```
public ArrayList(int initialCapacity)//构造一个具有指定初始容量的空列表。    
public ArrayList()      //默认构造一个初始容量为10的空列表。    
public ArrayList(Collection<? extends E> c)//构造一个包含指定 collection 的元素的列表123
```

Vector有四个构造方法：

```
public Vector()//使用指定的初始容量和等于0的容量增量构造一个空向量。    
public Vector(int initialCapacity)//构造一个空向量，使其内部数据数组的大小，其标准容量增量为零。    
public Vector(Collection<? extends E> c)//构造一个包含指定 collection 中的元素的向量    
public Vector(int initialCapacity,int capacityIncrement)//使用指定的初始容量和容量增量构造一个空的向量    1234
```

ArrayList和Vector都是用数组实现的，主要有这么三个区别：
*（1）*Vector是多线程安全的，线程安全就是说多线程访问同一代码，不会产生不确定的结果。而ArrayList不是，这个可以从源码中看出，Vector类中的方法很多有synchronized进行修饰，这样就导致了Vector在效率上无法与ArrayList相比；
*（2）*两个都是采用的线性连续空间存储元素，但是当空间不足的时候，两个类的增加方式是不同。
*（3）*Vector可以设置增长因子，而ArrayList不可以。
*（4）*Vector是一种老的动态数组，是线程同步的，效率很低，一般不赞成使用。
**适用场景分析**：
1.Vector是线程同步的，所以它也是线程安全的，而ArrayList是线程异步的，是不安全的。如果不考虑到线程的安全因素，一般用ArrayList效率比较高。
2.如果集合中的元素的数目大于目前集合数组的长度时，在集合中使用数据量比较大的数据，用Vector有一定的优势。

.TreeSet 是二叉树（红黑树的树据结构）实现的,Treeset中的数据是自动排好序的，不允许放入null值
2.HashSet 是哈希表实现的,HashSet中的数据是无序的，可以放入null，但只能放入一个null，两者中的值都不能重复，就如数据库中唯一约束
3.HashSet要求放入的对象必须实现HashCode()方法，放入的对象，是以hashcode码作为标识的，而具有相同内容的String对象，hashcode是一样，所以放入的内容不能重复。但是同一个类的对象可以放入不同的实例

**适用场景分析**:HashSet是基于Hash算法实现的，其性能通常都优于TreeSet。为快速查找而设计的Set，我们通常都应该使用HashSet，在我们需要排序的功能时，我们才使用TreeSet。
（5）何时使用：
<img src="https://img-blog.csdn.net/20180803204923763?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom:80%;" />

### 三、Map详解：

Map用于保存具有映射关系的数据，Map里保存着两组数据：key和value，它们都可以使任何引用类型的数据，但key不能重复。所以通过指定的key就可以取出对应的value。

（1）、**请注意！！！**， Map 没有继承 Collection 接口， Map 提供 key 到 value 的映射，你可以通过“键”查找“值”。一个 Map 中不能包含相同的 key ，每个 key 只能映射一个 value 。 Map 接口提供 3 种集合的视图， Map 的内容可以被当作一组 key 集合，一组 value 集合，或者一组 key-value 映射。
（2）Map：
![这里写图片描述](https://img-blog.csdn.net/20180803205119738?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
（3）HashMap和HashTable的比较：
<img src="https://img-blog.csdn.net/20180803205546704?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70" alt="这里写图片描述" style="zoom: 67%;" />
（4）TreeMap：
![这里写图片描述](https://img-blog.csdn.net/20180803205736499?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
（5）Map的其它类：
**IdentityHashMap**和**HashMap**的具体区别，IdentityHashMap使用 == 判断两个key是否相等，而HashMap使用的是equals方法比较key值。有什么区别呢？
		对于==，如果作用于基本数据类型的变量，则直接比较其存储的 “值”是否相等； 如果作用于引用类型的变量，则比较的是所指向的对象的地址。
		对于equals方法，注意：equals方法不能作用于基本数据类型的变量
		如果没有对equals方法进行重写，则比较的是引用类型的变量所指向的对象的地址；
		诸如String、Date等类对equals方法进行了重写的话，比较的是所指向的对象的内容。
![这里写图片描述](https://img-blog.csdn.net/20180803210616278?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2ZlaXlhbmFmZmVjdGlvbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
（6）小结：
HashMap 非线程安全
HashMap：基于哈希表实现。使用HashMap要求添加的键类明确定义了hashCode()和equals()[可以重写hashCode()和equals()]，为了优化HashMap空间的使用，您可以调优初始容量和负载因子。

TreeMap：非线程安全基于红黑树实现。TreeMap没有调优选项，因为该树总处于平衡状态。

**适用场景分析：**
HashMap和HashTable:HashMap去掉了HashTable的contains方法，但是加上了containsValue()和containsKey()方法。HashTable同步的，而HashMap是非同步的，效率上比HashTable要高。HashMap允许空键值，而HashTable不允许。

HashMap：适用于Map中插入、删除和定位元素。
Treemap：适用于按自然顺序或自定义顺序遍历键(key)。

5.线程安全集合类与非线程安全集合类
LinkedList、ArrayList、HashSet是非线程安全的，Vector是线程安全的;
HashMap是非线程安全的，HashTable是线程安全的;
StringBuilder是非线程安全的，StringBuffer是线程安全的。

数据结构
ArrayXxx:底层数据结构是数组，查询快，增删慢
LinkedXxx:底层数据结构是链表，查询慢，增删快
HashXxx:底层数据结构是哈希表。依赖两个方法：hashCode()和equals()
TreeXxx:底层数据结构是二叉树。两种方式排序：自然排序和比较器排序

## IO流

## **1、流的概念和作用**

流：代表任何有能力产出数据的数据源对象或者是有能力接受数据的接收端对象<Thinking in Java>

流的本质:数据传输，根据数据传输特性将流抽象为各种类，方便更直观的进行数据操作。 

**作用：为数据源和目的地建立一个输送通道**

### **1.2、Java IO所采用的模型**

Java的IO模型设计非常优秀，它使用**Decorator(装饰者)模式**，按功能划分Stream，您可以动态装配这些Stream，以便获得您需要的功能。

​    例如，您需要一个具有缓冲的文件输入流，则应当组合使用FileInputStream和BufferedInputStream。

### 1.3、IO流的分类

​       1.3.1、按**数据流**的方向分为 输入流、输出流

　　　此输入、输出是相对于我们写的代码程序而言，

　　　输入流：从别的地方(本地文件，网络上的资源等)获取资源 输入到 我们的程序中

　　    输出流：从我们的程序中 输出到 别的地方(本地文件)， 将一个字符串保存到本地文件中，就需要使用输出流。

　　1.3.2、按**处理数据单位**不同分为 字节流、字符流 

　　　1字符 = 2字节 、 1字节(byte) = 8位(bit) 、 一个汉字占两个字节长度

　　　字节流：每次读取(写出)一个字节，当传输的资源文件有中文时，就会出现乱码，

　　　字符流：每次读取(写出)两个字节，有中文时，使用该流就可以正确传输显示中文。

　　1.3.3、按**功能**不同分为 节点流、处理流

　　　节点流：以从或向一个特定的地方（节点）读写数据。如FileInputStream　

　　　处理流：是对一个已存在的流的连接和封装，通过所封装的流的功能调用实现数据读写。如BufferedReader。处理流的构造方法总是要带一个其他的流对象做参数。一个流对象经过其他流的多次包装，

　　　　1.3.4、4个基本的抽象流类型，所有的流都继承这四个。

　　　　　　　　　　　输入流　　　　　　输出流

　　　　　　字节流　　InputStream　　outputStream

　　　　　　字符流　　Reader　　　　　　Writer

　　　　　　inputStream：字节输入流

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530112251336-478728150.png)

　　　　　　outputStream：字节输出流

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121318274-160516931.png)

　　　　　　Reader：字符输入流

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121521321-799067835.png)

　　　　　　Writer：字符输出流

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121746211-57243059.png)

　　　　　

　　　　总结流的分类

　　　　看上面的几个分类，可能对于初次学io的同学会感觉到有些混乱，那什么时候用字节流，什么时候该用输出流呢？其实非常简单，举一个例子就学会了，

> 　　　1、首先自己要知道是选择输入流还是输出流，这就要根据自己的情况而定，如果你想从程序写东西到别的地方，那么就选择输出流，反之用输入流
>
> 　　　2、然后考虑你传输数据时，是选择使用字节流传输还是字符流，也就是每次传1个字节还是2个字节，有中文肯定就选择字符流了。（详情见1.8）
>
> 　　　3、前面两步就可以选出一个合适的节点流了，比如字节输入流inputStream，如果要在此基础上增强功能，**那么就在处理流中选择一个合适的即可。**

**字符流的由来：** Java中字符是采用Unicode标准，一个字符是16位，即一个字符使用两个字节来表示。为此，JAVA中引入了处理字符的流。因为数据编码的不同，而有了对字符进行高效操作的流对象。本质其实就是基于字节流读取时，去查了指定的码表。

### 1.4、IO流特性

1、先进先出，最先写入输出流的数据最先被输入流读取到。

2、顺序存取，可以一个接一个地往流中写入一串字节，读出时也将按写入顺序读取一串字节，不能随机访问中间的数据。（RandomAccessFile**可以从文件的任意位置进行存取（输入输出）操作**）

3、只读或只写，每个流只能是输入流或输出流的一种，不能同时具备两个功能，输入流只能进行读操作，对输出流只能进行写操作。在一个数据传输通道中，如果既要写入数据，又要读取数据，则要分别提供两个流。

### 1.5、IO流常用到的五类一接口

在整个Java.io包中最重要的就是5个类和一个接口。5个类指的是File、OutputStream、InputStream、Writer、Reader；一个接口指的是Serializable.掌握了这些IO的核心操作那么对于Java中的IO体系也就有了一个初步的认识了。

主要的类如下：

   \1. File（文件特征与管理）：File类是对文件系统中文件以及文件夹进行封装的对象，可以通过对象的思想来操作文件和文件夹。 File类保存文件或目录的各种元数据信息，包括文件名、文件长度、最后修改时间、是否可读、获取当前文件的路径名，判断指定文件是否存在、获得当前目录中的文件列表，创建、删除文件和目录等方法。  

   \2. InputStream（二进制格式操作）：抽象类，基于字节的输入操作，是所有输入流的父类。定义了所有输入流都具有的共同特征。

   \3. OutputStream（二进制格式操作）：抽象类。基于字节的输出操作。是所有输出流的父类。定义了所有输出流都具有的共同特征。

   4.Reader（文件格式操作）：抽象类，基于字符的输入操作。

   \5. Writer（文件格式操作）：抽象类，基于字符的输出操作。

   \6. RandomAccessFile（随机文件操作）：一个独立的类，直接继承至Object.它的功能丰富，可以从文件的任意位置进行存取（输入输出）操作。

![img](https://images2015.cnblogs.com/blog/1186236/201706/1186236-20170628084745102-439177264.png)

### **1.6、Java IO流对象**

 

#### 1.6.1、输入字节流InputStream

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530112251336-478728150.png)

**认识每个类的功能即作用**

　　　　　ByteArrayInputStream：字节数组输入流，该类的功能就是从字节数组(byte[])中进行以字节为单位的读取，也就是将资源文件都以字节的形式存入到该类中的字节数组中去，我们拿也是从这个字节数组中拿

　　　　　PipedInputStream：管道字节输入流，它和PipedOutputStream一起使用，能实现**多线程间的管道通信**

　　　　　FilterInputStream ：装饰者模式中处于装饰者，具体的装饰者都要继承它，所以在该类的子类下都是用来装饰别的流的，也就是处理类。具体装饰者模式在下面会讲解到，到时就明白了

　　　　　**BufferedInputStream**：缓冲流，对处理流进行装饰，增强，内部会有一个缓存区，用来存放字节，每次都是将缓存区存满然后发送，而不是一个字节或两个字节这样发送。效率更高

　　　　  **DataInputStream**：数据输入流，它是用来装饰其它输入流，它“允许应用程序以与机器无关方式从底层输入流中读取基本 Java 数据类型”

　　　　　FileInputSream：文件输入流。它通常用于对文件进行读取操作

　　　　　File：对指定目录的文件进行操作，具体可以查看讲解File的博文。注意，该类虽然是在IO包下，但是并不继承自四大基础类。

 　　　 ObjectInputStream：对象输入流，用来提供对“基本数据或对象”的持久存储。通俗点讲，也就是能直接传输对象（反***\*序列化中使用\****），



#### 1.6.2、输出字节流OutputStream

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121318274-160516931.png)

IO 中输出字节流的继承图可见上图，可以看出：

1. OutputStream 是所有的输出字节流的父类，它是一个抽象类。
2. **ByteArrayOutputStream、FileOutputStream 是两种基本的介质流，它们分别向Byte 数组、和本地文件中写入数据。**PipedOutputStream 是向与其它线程共用的管道中写入数据，
3. **ObjectOutputStream** 和所有FilterOutputStream 的子类都是装饰流(***\*序列化中使用\****)。

![img](https://files.jb51.net/file_images/article/201705/20170501095714.jpg)    

#### 1.6.3、字符输入流Reader

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121521321-799067835.png)

在上面的继承关系图中可以看出：

1. Reader 是所有的输入字符流的父类，它是一个抽象类。
2. **CharReader、StringReader 是两种基本的介质流，它们分别将Char 数组、String中读取数据。**PipedReader 是从与其它线程共用的管道中读取数据。
3. BufferedReader 很明显就是一个装饰器，它和其子类负责装饰其它Reader 对象。
4. FilterReader 是所有自定义具体装饰流的父类，其子类PushbackReader 对Reader 对象进行装饰，会增加一个行号。
5. **InputStreamReader** 是一个连接字节流和字符流的桥梁，它将字节流转变为字符流。FileReader 可以说是一个达到此功能、常用的工具类，在其源代码中明显使用了将FileInputStream 转变为Reader 的方法。我们可以从这个类中得到一定的技巧。Reader 中各个类的用途和使用方法基本和InputStream 中的类使用一致。后面会有Reader 与InputStream 的对应关系。

#### 1.6.4、字符输出流Writer

![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530121746211-57243059.png)

在上面的关系图中可以看出：

1. Writer 是所有的输出字符流的父类，它是一个抽象类。
2. **CharArrayWriter、StringWriter 是两种基本的介质流，它们分别向Char 数组、String 中写入数据。**PipedWriter 是向与其它线程共用的管道中写入数据，
3. BufferedWriter 是一个装饰器为Writer 提供缓冲功能。
4. PrintWriter 和PrintStream 极其类似，功能和使用也非常相似。
5. **OutputStreamWriter** 是OutputStream 到Writer 转换的桥梁，它的子类FileWriter 其实就是一个实现此功能的具体类（具体可以研究一SourceCode）。功能和使用和OutputStream 极其类似，后面会有它们的对应图。

![img](https://files.jb51.net/file_images/article/201705/20170501095735.jpg)

#### 1.6.5、字节流和字符流使用情况：（重要）

字符流和字节流的使用范围：字节流一般用来处理图像，视频，以及PPT，Word类型的文件。字符流一般用于处理纯文本类型的文件，如TXT文件等，字节流可以用来处理纯文本文件，但是字符流不能用于处理图像视频等非文本类型的文件。

#### 1.7、字符流与字节流转换

![img](https://files.jb51.net/file_images/article/201705/20170501095948.jpg)

**转换流的作用，文本文件在硬盘中以字节流的形式存储时，通过InputStreamReader读取后转化为字符流给程序处理，程序处理的字符流通过OutputStreamWriter转换为字节流保存。**

转换流的特点：

1. 其是字符流和字节流之间的桥梁
2. 可对读取到的字节数据经过指定编码转换成字符
3. 可对读取到的字符数据经过指定编码转换成字节

何时使用转换流？

1. 当字节和字符之间有转换动作时；
2. 流操作的数据需要编码或解码时。

具体的对象体现：

1. **InputStreamReader**:*字节到字符的桥梁*
2. **OutputStreamWriter**:*字符到字节的桥梁*

这两个流对象是字符体系中的成员，它们有转换作用，本身又是字符流，所以在构造的时候需要传入字节流对象进来。

 

OutputStreamWriter(OutStreamout):将字节流以字符流输出。

InputStreamReader(InputStream in)：将字节流以字符流输入。

#### 1.8、字节流和字符流的区别（重点）

**字节流和字符流的区别**：(详细可以参见http://blog.csdn.net/qq_25184739/article/details/51203733)  

​     节流没有缓冲区，是直接输出的，而**字符流是输出到缓冲区的**。因此在输出时，字节流不调用colse()方法时，信息已经输出了，而**字符流只有在调用close()方法关闭缓冲区**时，信息才输出。要想字符流在未关闭时输出信息，则需要手动调用flush()方法。

·    读写单位不同：字节流以字节（8bit）为单位，字符流以字符为单位，根据码表映射字符，一次可能读多个字节。

·    处理对象不同：字节流能处理所有类型的数据（如图片、avi等），而字符流只能处理字符类型的数据。

**结论：只要是处理纯文本数据，就优先考虑使用字符流。除此之外都使用字节流。**

#### **1.9、System类对IO的支持** 

## ![img](https://img-blog.csdn.net/20160421010054372?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

 针对一些频繁的设备交互，Java语言系统预定了3个可以直接使用的流对象，分别是：

·    System.in（标准输入），通常代表键盘输入。

·    System.out（标准输出）：通常写往显示器。

·    System.err（标准错误输出）：通常写往显示器。

 标准I/O
   Java程序可通过命令行参数与外界进行简短的信息交换，同时，也规定了与标准输入、输出设备，如键盘、显示器进行信息交换的方式。而通过文件可以与外界进行任意数据形式的信息交换。

#### 2.0、**处理流BufferedReader，BufferedWriter,BufferedInputStream**

BufferedOutputsStream，都要包上一层节点流。也就是说处理流是在节点流的基础之上进行的，带有Buffered的流又称为缓冲流，缓冲流处理文件的输入输出的速度是最快的。所以一般缓冲流的使用比较多。

 

#### 2.1、什么是装饰者模式？

​    推荐一篇博文，http://blog.csdn.net/jason0539/article/details/22713711 就详细说明了什么是装饰者模式？用我自己的话来说，就是往一个添加更多的功能，而我们首先想到的是继承，继承就很好的符合了我们的要求，不管你想加多少层的功能，都可以使用继承一层层的实现，但是这带来了一个问题，一旦我需要改变我的需求，那么我就需要往源码中改东西，再就是在这个继承链中某个类做一些修改，这不符合我们的设计模式思想，所以就有了装饰者模式，装饰者中拥有被装饰者的实例，然后有什么具体的装饰我们都另写一个类来继承该装饰者，当我们需要该装饰时，就new出该类来，然后将其被装饰者当作参数传递进去。

 　　　　　　　　　　　　　　　　　![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530152826571-1924640286.png)

　　光说可能没理解那么清楚，现在来看看一个具体的实例。比如，我们需要制作一份鸡腿堡，流程是怎样的呢？看下图

　　1、先有基本原料，也就是两块面包，这是不管做什么汉堡都需要的，

　　2、做什么汉堡，取决于加什么材料，比如生菜，鸡肉等，所以根据材料来做汉堡，想做什么汉堡就加什么材料

　　3、所有材料加完之后，直接计算价格即可

　　这样使用装饰者模式，是不是比一直使用继承方便的多的多呢？换一种汉堡，也不需要改源码，什么也不需要，希望你能够理解清楚其中的思想。

　　　　　　　　　　　　　　　　　　　　![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530160335977-1889860348.png)

 

　　　　　　3.2、io流中的装饰者模式的运用

　　　　　　　　　　　　画张图，在结合源码和自己写的代码来看。

　　　　　　　　　　　　　　　　　　![img](https://images2015.cnblogs.com/blog/874710/201705/874710-20170530162636930-1288255116.png)

 

　　　处理流就是一个具体的装饰者，而节点流就是被装饰者。

当我们使用继承，导致子类膨胀，我们不想增加很多子类的情况下，将具体功能职责划分，同时继承装饰者超类，动态地给一个对象添加一些额外的职责便实现了我们的装饰者模式。

四、优缺点

　　1、优点：装饰类和被装饰类可以独立发展，不会相互耦合，装饰模式是继承的一个替代模式，装饰模式可以动态扩展一个实现类的功能。

　　2、缺点：多层装饰比较复杂。

五、使用场景： 

　　1、扩展一个类的功能。

　　 2、动态增加功能，动态撤销。

　　实际使用：这里我们说一下，在java中I/O便使用了装饰者模式。

#### 2.2、Scanner类

 Java 5添加了java.util.Scanner类，这是一个用于扫描输入文本的新的实用程序。它是以前的StringTokenizer和Matcher类之间的某种结合。由于任何数据都必须通过同一模式的捕获组检索或通过使用一个索引来检索文本的各个部分。于是可以结合使用正则表达式和从输入流中检索特定类型数据项的方法。这样，除了能使用**正则表达式**之外，Scanner类还可以任意地对**字符串和基本类型**(如int和double)的数据进行分析。借助于Scanner，可以针对任何要处理的文本内容编写自定义的语法分析器。

Scanner套接字节流或字符流：

字节流的套接：在Scanner的构造方法中**[Scanner](https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html#Scanner(java.io.InputStream))**([InputStream](https://docs.oracle.com/javase/7/docs/api/java/io/InputStream.html) source)，InputStream只要经过适当的套接，总能获得你想要的流接口。

字符流的套接：**[Scanner](https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html#Scanner(java.lang.Readable))**([Readable](https://docs.oracle.com/javase/7/docs/api/java/lang/Readable.html) source)，你需要使用Java SE5中新加入的一个接口Readable，该接口表示“具有read()方法的某种东西”，查看Readable接口的API你可以发现你想要的带有Reader的类基本都在其中。

#### 2.3、序列化

将保存在内存中的对象数据转化为二进制数据流进行传输，任何对象都可以序列化

实现方法：实现java.io.Serializable接口

**作用**：把一个Java对象写入到硬盘或者传输到网路上面的其它计算机，这时我们就需要自己去通过java把相应的对象写成转换成字节流。对于这种通用的操作，我们为什么不使用统一的格式呢？没错，这里就出现了java的序列化的概念。在Java的OutputStream类下面的子类ObjectOutput-Stream类就有对应的WriteObject(Object object) 其中要求对应的object实现了java的序列化的接口。

在使用tomcat开发JavaEE相关项目的时候，我们关闭tomcat后，相应的session中的对象就存储在了硬盘上，如果我们想要在tomcat重启的时候能够从tomcat上面读取对应session中的内容，那么保存在session中的内容就必须实现相关的序列化操作，还有jdbc加载驱动用的就是反序列化，将字符串变为对象。。。

```java
//序列化类：java.ioObjectOutputStream
//讲对象变为指定的二进制数据
class Book implements Serializable{
	private String title;
	private double price;
	public Book(String tit,double pri){
		this.title=tit;
		this.price=pri;
	}
	public String toString() {
		return "书名："+this.title+",价格："+this.price;
	}
}
public class Demo10 {
	public static void main(String[] args) throws Exception {
//序列化到指定的文本
		ObjectOutputStream oos=new ObjectOutputStream(new FileOutputStream(new File("e:"+File.separator+"demoA.txt")));
		oos.writeObject(new Book("java开发", 45.2));
		oos.close();
	}
}
```

#### 反序列化

将二进制数据换回原对象

构造：

   ObjectInputStream（InputStream in）

方法:

   Object readObject() 从 ObjectInputStream 读取对象 

```java
class Book implements Serializable{
	private String title;
	private double price;
	public Book(String tit,double pri){
		this.title=tit;
		this.price=pri;
	}
	public String toString() {
		return "书名："+this.title+",价格："+this.price;
	}
}
public class Demo11 {
	public static void main(String[] args) throws FileNotFoundException, IOException, ClassNotFoundException {
		ObjectInputStream ois=new ObjectInputStream(new FileInputStream(new File("e:"+File.separator+"demoA.txt")));
		Object obj=ois.readObject();
		Book book=(Book) obj;
		System.out.println(book);
		ois.close();
	}

}
```

#### transient关键字（一个类某些属性不需要序列化）

以上序列化和反序列化实现了的对象序列化，但是可以发现，操作时是将整个对象的所有属性序列化，那么transient关键字可以将某些内容不需要保存，就可以通过transient关键字来定义

private transient string title；

此时title属性无法被序列化，

#### 2.2、总结

inputStream类的功能不足被Scanner解决了

OutputStream类的功能不足被PrintStream解决了

Reader类功能不足被BufferReader解决了

Writer类的功能不足被PrintWriter解决了

输出数据用printStream，printwriter读取数据用Scanner其次是bufferReader

#### 序列化实例

框架实体类实现了序列化接口（public class UserServiceImpl implements UserService）



客户端访问了某个能开启会话功能的资源， web服务器就会创建一个与该客户端对应的HttpSession对象，每个HttpSession对象都要站用一定的内存空间。如果在某一时间段内访问站点的用户很多，web服务器内存中就会积累大量的HttpSession对象，消耗大量的服务器内存，即使用户已经离开或者关闭了浏览器，web服务器仍要保留与之对应的HttpSession对象，在他们超时之前，一直占用web服务器内存资源。

​    web服务器通常将那些暂时不活动但未超时的HttpSession对象转移到文件系统或数据库中保存，服务器要使用他们时再将他们从文件系统或数据库中装载入内存，这种技术称为Session的持久化。

​     将HttpSession对象保存到文件系统或数据库中，需要采用序列化的方式将HttpSession对象中的每个属性对象保存到文件系统或数据库中；将HttpSession对象从文件系统或数据库中装载如内存时，需要采用反序列化的方式，恢复HttpSession对象中的每个属性对象。所以存储在HttpSession对象中的每个属性对象必须实现Serializable接口。

serialVersionUID 的作用
serialVersionUID 用来表明类的不同版本间的兼容性

   Java的序列化机制是通过在运行时判断类的serialVersionUID来**验证版本一致性**的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID与本地相应实体（类）的serialVersionUID进行比较，如果相同就认为是一致的，可以进行反序列化，否则就会出现序列化版本不一致的异常。

  当实现java.io.Serializable接口的实体（类）没有显式地定义一个名为serialVersionUID，类型为long的变量时，Java序列化机制会根据编译的class自动生成一个serialVersionUID作序列化版本比较用，这种情况下，只有同一次编译生成的class才会生成相同的serialVersionUID 。

   如果我们不希望通过编译来强制划分软件版本，即实现序列化接口的实体能够兼容先前版本，未作更改的类，就需要显式地定义一个名为serialVersionUID，类型为long的变量，不修改这个变量值的序列化实体都可以相互进行串行化和反串行化。

  引起这个疑问，还是从Hibernate使用查询缓存说起；对象实例除了存在于内存，二级缓存还会将对象写进硬盘在需要的时候再读取出来使用，此时就必须提到一个概念：序列化。

  程序在运行时实例化出对象，这些对象存在于内存中，随着程序运行停止而消失，但如果我们想把某些对象（一般都是各不相同的属性）保存下来或者传输给其他进程，在程序终止运行后这些对象仍然存在，可以在程序再次运行时读取这些对象的信息，或者在其他程序中利用这些保存下来的对象信息恢复成实例对象。这种情况下就要用到对象的序列化和反序列化。

 其实很早就知道的，在Java中常见的几个类，如：Interger/String等，都实现了java.io.Serializable接口。这个序列化接口没有任何方法和域，仅用于标识序列化语意；实现 Serializable 接口的类是可序列化的，没有实现此接口的类将不能被序列化和反序列化。序列化类的所有子类本身都是可序列化的，不再需要显式实现 Serializable 接口。只有经过序列化，才能兼容对象在磁盘文本以及在网络中的传输，以及恢复对象的时候反序列化等操作。


### **为什么要序列化**

1. 存储对象在存储介质中，以便在下次使用的时候，可以很快捷的重建一个副本。
2. 便于数据传输，尤其是在远程调用的时候！

### **Serializable接口怎样工作**

Serializable是一个空接口，那怎样工作呢？Serializable仅仅作为一个标识符的作用，通过该接口让JVM识别，并将其进行序列化。在反序列化的过程中则需要使用serialVersionUID来确定由那个类来加载这个对象，所以我们在实现Serializable接口的时候，一般还会要去尽量显示地定义serialVersionUID，如：

```java
private static final long serialVersionUID = 1L; 
```

 如果我们在序列化中没有显示地声明serialVersionUID，则序列化运行时将会根据该类的各个方面计算该类默认的serialVersionUID值。但是，Java官方强烈建议所有要序列化的类都显示地声明serialVersionUID字段，因为如果高度依赖于JVM默认生成serialVersionUID，可能会导致其与编译器的实现细节耦合，这样可能会导致在反序列化的过程中发生意外的InvalidClassException异常。因此，为了保证跨不同Java编译器实现的serialVersionUID值的一致，实现Serializable接口的必须显示地声明serialVersionUID字段。

此外serialVersionUID字段地声明要尽可能使用private关键字修饰，这是因为该字段的声明只适用于声明的类，该字段作为成员变量被子类继承是没有用处的!有个特殊的地方需要注意的是，数组类是不能显示地声明serialVersionUID的，因为它们始终具有默认计算的值，不过数组类反序列化过程中也是放弃了匹配serialVersionUID值的要求。



Java的序列化机制是通过在运行时判断类的serialVersionUID来验证版本一致性的。在进行反序列化时，JVM会把传来的字节流中的serialVersionUID与本地相应实体（类）的serialVersionUID进行比较，如果相同就认为是一致的，可以进行反序列化，否则就会出现序列化版本不一致的异常。

      当实现java.io.Serializable接口的实体（类）没有显式地定义一个名为serialVersionUID，类型为long的变量时，Java序列化机制会根据编译的class自动生成一个serialVersionUID作序列化版本比较用，这种情况下，只有同一次编译生成的class才会生成相同的serialVersionUID 。
    
       如果我们不希望通过编译来强制划分软件版本，即实现序列化接口的实体能够兼容先前版本，未作更改的类，就需要显式地定义一个名为serialVersionUID，类型为long的变量，不修改这个变量值的序列化实体都可以相互进行串行化和反串行化。
    
      引起这个疑问，还是从Hibernate使用查询缓存说起；对象实例除了存在于内存，二级缓存还会将对象写进硬盘在需要的时候再读取出来使用，此时就必须提到一个概念：序列化。
    
      程序在运行时实例化出对象，这些对象存在于内存中，随着程序运行停止而消失，但如果我们想把某些对象（一般都是各不相同的属性）保存下来或者传输给其他进程，在程序终止运行后这些对象仍然存在，可以在程序再次运行时读取这些对象的信息，或者在其他程序中利用这些保存下来的对象信息恢复成实例对象。这种情况下就要用到对象的序列化和反序列化。

 其实很早就知道的，在Java中常见的几个类，如：Interger/String等，都实现了java.io.Serializable接口。这个序列化接口没有任何方法和域，仅用于标识序列化语意；实现 Serializable 接口的类是可序列化的，没有实现此接口的类将不能被序列化和反序列化。序列化类的所有子类本身都是可序列化的，不再需要显式实现 Serializable 接口。只有经过序列化，才能兼容对象在磁盘文本以及在网络中的传输，以及恢复对象的时候反序列化等操作。

问题一：为何要实现序列化？
答：序列化就是对实例对象的状态(State 对象属性而不包括对象方法)进行通用编码（如格式化的字节码）并保存，以保证对象的完整性和可传递性。

简而言之：序列化，就是为了在不同时间或不同平台的JVM之间共享实例对象

```
// 经常使用如下：
public static void main(String[] args) throws Exception {
    File file = new File("user.ser");

ObjectOutputStream oout = new ObjectOutputStream(new FileOutputStream(file));
User user = new User("zhang", 18, Gender.MALE);
oout.writeObject(user);
oout.close();

ObjectInputStream oin = new ObjectInputStream(new FileInputStream(file));
Object newUser = oin.readObject();
oin.close();
System.out.println(newUser);

}
```

  如没有 实现Serializable接口，在序列化时，使用ObjectOutputStream的write（object）方法将对象保存时将会出现异常。其实 java.io.Serializable 只是一个没有属性和方法的空接口。





最后提点注意：
1、在序列化对象时，不仅会序列化当前对象本身，还会对该对象引用的其它对象也进行序列化，如此引用传递序列化。如果一个对象包含的成员变量是容器类等并深层引用，那么序列化过程开销也较大。

2、当字段被声明为 transient 后，默认序列化机制就会忽略该字段。（还有方法就是自定义writeObject方法，见下代码示例）

3、在单例类中添加一个readResolve()方法（直接返回单例对象），以保证在序列化过程仍保持单例特性。

此外补充一下，
 在路径下jdk中还有另外一种形式的对象持久化，即：外部化（Externalization）。

```
public interface Externalizable extends java.io.Serializable {
  void writeExternal(ObjectOutput out) throws IOException;
  void readExternal(ObjectInput in) throws IOException, ClassNotFoundException;
}
```


  外部化和序列化是实现同一目标的两种不同方法。

  通过 Serializable 接口对对象序列化的支持是jdk内支持的 API ，但是java.io.Externalizable的所有实现者必须提供读入和写出的具体实现，怎么实现完全由你自定义。序列化（Serializable ）会自动存储所有必要的信息（如属性以及属性类型等），用以反序列化成原来一样的实例，而外部化（Externalizable）则只保存被存储实例中你需要的信息。

示例代码如下：

```
public class User implements Externalizable {
    private String name;
    transient private Integer age;  // 屏蔽字段
    private Gender gender;

public User() {
    System.out.println("none constructor");
}

public User(String name, Integer age, Gender gender) {
    System.out.println("arg constructor");
    this.name = name;
    this.age = age;
    this.gender = gender;
}

// 实现读写
private void writeObject(ObjectOutputStream out) throws IOException {
    out.defaultWriteObject();
    out.writeInt(age);
    // 屏蔽gender
}
private void readObject(ObjectInputStream in) throws IOException, ClassNotFoundException {
    in.defaultReadObject();
    age = in.readInt();
}

// 具体重写
@Override
public void writeExternal(ObjectOutput out) throws IOException {
    out.writeObject(name);
    out.writeInt(age);
    // 屏蔽gender
}
@Override
public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
    name = (String) in.readObject();
    age = in.readInt();
} 

}
```



### BIO NIO AIO

IO的方式通常分为几种，同步阻塞的BIO、同步非阻塞的NIO、异步非阻塞的AIO。

一、BIO

   在JDK1.4出来之前，我们建立网络连接的时候采用BIO模式，需要先在服务端启动一个ServerSocket，然后在客户端启动Socket来对服务端进行通信，默认情况下服务端需要对每个请求建立一堆线程等待请求，而客户端发送请求后，先咨询服务端是否有线程相应，如果没有则会一直等待或者遭到拒绝请求，如果有的话，客户端会线程会等待请求结束后才继续执行。

二、NIO

  NIO本身是基于事件驱动思想来完成的，其主要想解决的是BIO的大并发问题： 在使用同步I/O的网络应用中，如果要同时处理多个客户端请求，或是在客户端要同时和多个服务器进行通讯，就必须使用多线程来处理。也就是说，将每一个客户端请求分配给一个线程来单独处理。这样做虽然可以达到我们的要求，但同时又会带来另外一个问题。由于每创建一个线程，就要为这个线程分配一定的内存空间（也叫工作存储器），而且操作系统本身也对线程的总数有一定的限制。如果客户端的请求过多，服务端程序可能会因为不堪重负而拒绝客户端的请求，甚至服务器可能会因此而瘫痪。

  **NIO基于Reactor**，当socket有流可读或可写入socket时，操作系统会相应的通知引用程序进行处理，应用再将流读取到缓冲区或写入操作系统。 也就是说，这个时候，已经不是一个连接就要对应一个处理线程了，而是有效的请求，对应一个线程，当连接没有数据时，是没有工作线程来处理的。

  BIO与NIO一个比较重要的不同，是我们使用BIO的时候往往会引入多线程，每个连接一个单独的线程；而NIO则是使用单线程或者只使用少量的多线程，每个连接共用一个线程。

![img](http://images2015.cnblogs.com/blog/37237/201512/37237-20151222220329015-207666376.png)

   NIO的最重要的地方是当一个连接创建后，不需要对应一个线程，这个连接会被注册到多路复用器上面，所以所有的连接只需要一个线程就可以搞定，当这个线程中的多路复用器进行轮询的时候，发现连接上有请求的话，才开启一个线程进行处理，也就是一个请求一个线程模式。

   在NIO的处理方式中，当一个请求来的话，开启线程进行处理，可能会等待后端应用的资源(JDBC连接等)，其实这个线程就被阻塞了，当并发上来的话，还是会有BIO一样的问题。

　　HTTP/1.1出现后，有了Http长连接，这样除了超时和指明特定关闭的http header外，这个链接是一直打开的状态的，这样在NIO处理中可以进一步的进化，在后端资源中可以实现资源池或者队列，当请求来的话，开启的线程把请求和请求数据传送给后端资源池或者队列里面就返回，并且在全局的地方保持住这个现场(哪个连接的哪个请求等)，这样前面的线程还是可以去接受其他的请求，而后端的应用的处理只需要执行队列里面的就可以了，这样请求处理和后端应用是异步的.当后端处理完，到全局地方得到现场，产生响应，这个就实现了异步处理。



三大IO模型
BIO模型
每一个请求开一个线程,缺点:

这种方式势必会造成线程开销
当请求没有结果的时候,会造成阻塞

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200503144953154.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ppc3V1,size_16,color_FFFFFF,t_70)


NIO模型
一个线程处理多个请求,即客户端发送的请求会发送到多路复用器上,多路复用器轮询到连接又I/O请求就进行处理

从上面这幅图可以看出,一个线程维护一个选择器,一个选择器轮询多个请求,只要有请求带着事件到来,就去处理----即netty这个框架是一个事件驱动的框架NIO框架

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200503145457576.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ppc3V1,size_16,color_FFFFFF,t_70)

AIO模型

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200503145936224.png)

NIO三大组件
NIO三大组件的关系:
三大组件:selector,channel,buffer

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200503150434485.png)

一个Select对应一个线程,一个线程对应多个channel

程序切换到那个channel是由事件决定的

Selector会根据不同的事件,在各个通道上切换

Buffer是一个内存块,底层是一个数据

数据的读取写入是通过Buffer.在传统Bio中要么是输入流,要么是输出流,不能是双向,但是NIO的Buffer是可以读也可以写,需要通过flip方法进行切换

缓冲区(Buffer)就是在内存中预留指定大小的存储空间用来对输入/输出(I/O)的数据作临时存储，这部分预留的内存空间就叫做缓冲区：

使用缓冲区有这么两个好处：

1、减少实际的物理读写次数

2、缓冲区在创建时就被分配内存，这块内存区域一直被重用，可以减少动态分配和回收内存的次数

举个简单的例子，比如A地有1w块砖要搬到B地

由于没有工具（缓冲区），我们一次只能搬一本，那么就要搬1w次（实际读写次数）



如果A，B两地距离很远的话（IO性能消耗），那么性能消耗将会很大

但是要是此时我们有辆大卡车（缓冲区），一次可运5000本，那么2次就够了

相比之前，性能肯定是大大提高了。

而且一般在实际过程中，我们一般是先将文件读入内存，再从内存写出到别的地方

这样在输入输出过程中我们都可以用缓存来提升IO性能。

 

所以，buffer在IO中很重要。在旧I/O类库中（相对java.nio包）中的BufferedInputStream、BufferedOutputStream、BufferedReader和BufferedWriter在其实现中都运用了缓冲区。java.nio包公开了Buffer API，使得Java程序可以直接控制和运用缓冲区。在Java NIO中，缓冲区的作用也是用来临时存储数据，可以理解为是I/O操作中数据的中转站。缓冲区直接为通道(Channel)服务，写入数据到通道或从通道读取数据，这样的操利用缓冲区数据来传递就可以达到对数据高效处理的目的。在NIO中主要有八种缓冲区类(其中MappedByteBuffer是专门用于内存映射的一种ByteBuffer)：

 

 

**Fields**

所有缓冲区都有4个属性：capacity、limit、position、mark，并遵循：mark <= position <= limit <= capacity，下表格是对着4个属性的解释：

 

属性 描述

Capacity 容量，即可以容纳的最大数据量；在缓冲区创建时被设定并且不能改变

Limit     表示缓冲区的当前终点，不能对缓冲区超过极限的位置进行读写操作。且极限是可以修改的

Position  位置，下一个要被读或写的元素的索引，每次读写缓冲区数据时都会改变改值，为下次读写作准备

Mark     标记，调用mark()来设置mark=position，再调用reset()可以让position恢复到标记的位置

 

**Methods**

**1****、实例化**

java.nio.Buffer类是一个抽象类，不能被实例化。Buffer类的直接子类，如ByteBuffer等也是抽象类，所以也不能被实例化。

但是ByteBuffer类提供了4个静态工厂方法来获得ByteBuffer的实例：

 

方法 描述

allocate(int capacity)：从堆空间中分配一个容量大小为capacity的byte数组作为缓冲区的byte数据存储器

allocateDirect(int capacity)：是不使用JVM堆栈而是通过操作系统来创建内存块用作缓冲区，它与当前操作系统能够更好的耦合，因此能进一步提高I/O操作速度。但是分配直接缓冲区的系统开销很大，因此只有在缓冲区较大并长期存在，或者需要经常重用时，才使用这种缓冲区

wrap(byte[] array)：这个缓冲区的数据会存放在byte数组中，bytes数组或buff缓冲区任何一方中数据的改动都会影响另一方。其实ByteBuffer底层本来就有一个bytes数组负责来保存buffer缓冲区中的数据，通过allocate方法系统会帮你构造一个byte数组

wrap(byte[] array, int offset, int length) ：在上一个方法的基础上可以指定偏移量和长度，这个offset也就是包装后byteBuffer的position，而length呢就是limit-position的大小，从而我们可以得到limit的位置为length+position(offset)

 

**2****、另外一些常用的方法**

方法 描述

limit(), limit(10)等：其中读取和设置这4个属性的方法的命名和jQuery中的val(),val(10)类似，一个负责get，一个负责set

reset()：把position设置成mark的值，相当于之前做过一个标记，现在要退回到之前标记的地方

clear()：position = 0;limit = capacity;mark = -1; 有点初始化的味道，但是并不影响底层byte数组的内容

flip()：   limit = position;position = 0;mark = -1; 翻转，也就是让flip之后的position到limit这块区域变成之前的0到position这块，翻转就是将一个处于存数据状态的缓冲区变为一个处于准备取数据的状态

rewind()：把position设为0，mark设为-1，不改变limit的值

remaining()：return limit - position;返回limit和position之间相对位置差

hasRemaining()：return position < limit返回是否还有未读内容

compact()：把从position到limit中的内容移到0到limit-position的区域内，position和limit的取值也分别变成limit-position、capacity。如果先将positon设置到limit，再compact，那么相当于clear()

get() ：相对读，从position位置读取一个byte，并将position+1，为下次读写作准备

get(int index)：绝对读，读取byteBuffer底层的bytes中下标为index的byte，不改变position

get(byte[] dst, int offset, int length)：从position位置开始相对读，读length个byte，并写入dst下标从offset到offset+length的区域

put(byte b)：相对写，向position的位置写入一个byte，并将postion+1，为下次读写作准备

put(int index, byte b)：绝对写，向byteBuffer底层的bytes中下标为index的位置插入byte b，不改变position

put(ByteBuffer src)：用相对写，把src中可读的部分（也就是position到limit）写入此byteBuffer

put(byte[] src, int offset, int length)：从src数组中的offset到offset+length区域读取数据并使用相对写写入此byteBuffer

ByteOrder    order()：检索此缓冲区的字节顺序。

ByteBuffer    order(ByteOrder bo)：修改缓冲区的字节顺序。

ByteBuffer putInt(int value)：编写int值的相对put方法（可选操作） 。以当前字节顺序将包含给定int值的四个字节写入当前位置的缓冲区，然后将位置递增四。

byte[] array()：返回支持此缓冲区的字节数组（可选操作） 。对此缓冲区内容的修改将导致返回的数组的内容被修改，反之亦然。在调用此方法之前调用hasArray方法，以确保此缓冲区具有可访问的后台阵列。



channel是双向的

在传统的BIO模型中,如果一个请求没有携带数据或者返回数据,可能会造成线程阻塞,但是在NIO模型中,数据被缓冲在Buffer里,客户端只能从Buffer中读取数据及发送数据,如果缓冲区中没有数据,服务器的Select就不会区处理这个通道,而是处理其他Buffer区中有数据的通道

Nio与Bio的比较

1.BIO以**流**的方式处理数据，而NIO以**块**的方式处理数据，块I/O的效率比流I/O高很多

2.BIO是阻塞的，NIO是非阻塞的

3.BIO基于字节流和字符流进行操作，而NIO基于Channel（通信）和Buffer（缓冲区）进行操作，数据总是**从通道读到缓冲区**中，或者从缓冲区写入到通道中。Selector（选择器）用于监听多个通道的事件（比如：请求连接，数据到达等），因此使用**单个线程**就可以监听多个客户端通道



组件一 Buffer
简单demo

```
 public static void main(String[] args) {
        //创建一个Buffer,可以存放5个Int类型数据
        IntBuffer intBuffer=IntBuffer.allocate(5);
        for(int i=0;i<intBuffer.capacity();i++){
            //放数据
            intBuffer.put(i*2);
        }
        //将buffer转换,读写切换(!!!!!)
        intBuffer.flip();
        while(intBuffer.hasRemaining()){
            System.out.println(intBuffer.get());
        }
    }

```


常用Buffer子类

常用方法
buffer类的常用方法总结

组件二 通道channel
基本介绍

n类似于流,能够同时进行读写操作
可以实现异步读取数据
可以从缓冲区buffer读取数据


案例一:本地文件写数据
其实FileChannel是对输出流的一个包装


代码实列:’

    public static void main(String[] args) throws IOException {
        String str="hello world";
        //创建一个输出流
        FileOutputStream stream=new FileOutputStream("D://Aimg//test/5.txt");
        //这个fileChanel真是类型是FileChannelImpl
        FileChannel channel=stream.getChannel();
        //创建一个缓冲区
        ByteBuffer byteBuffer=ByteBuffer.allocate(1024);
        //放str入byteBuffer
        byteBuffer.put(str.getBytes());
        //读写反装
        byteBuffer.flip();
        //将缓冲区数据写入通道
        channel.write(byteBuffer);
        stream.close();
    
    }


案例二:本地文件读数据

```
public static void main(String[] args) throws IOException {
        //文件
        File file=new File("D://Aimg//test/5.txt");
        FileInputStream inputStream=new FileInputStream(file);
        FileChannel channel=inputStream.getChannel();
        ByteBuffer byteBuffer=ByteBuffer.allocate((int)file.length());
        //将通道数据读入到buffer中,注意,write方法是从缓冲区读取数据到通道
         channel.read(byteBuffer);
        System.out.println(new String(byteBuffer.array()));
    }
```

上述两个案列的示意图:

案例三:一个Buffer完成文件的读写
流程:

```
 public static void main(String[] args) throws IOException {
        //文件
        File file=new File("D://Aimg//test/5.txt");
        FileInputStream inputStream=new FileInputStream(file);
        FileChannel readChannel=inputStream.getChannel();
        FileOutputStream outputStream=new FileOutputStream("D://Aimg//test/6.txt");
        FileChannel writeChannel=outputStream.getChannel();
        ByteBuffer buffer = ByteBuffer.allocate(1024);
        while(true){
        //每次读的时候要记得清空缓存
            buffer.clear();
            int read= readChannel.read(buffer);
            if(read!=-1){
            //读写反装
                buffer.flip();
                writeChannel.write(buffer);
            }else break;
        }
    }

```


案例四:channel的transferFrom拷贝文件

```
 public static void main(String[] args) throws IOException {
        //文件
        File file=new File("D://Aimg//12.jpg");
        FileInputStream inputStream=new FileInputStream(file);
        FileChannel readChannel=inputStream.getChannel();
        FileOutputStream outputStream=new FileOutputStream("D://Aimg//13.jpg");
        FileChannel writeChannel=outputStream.getChannel();
        writeChannel.transferFrom(readChannel,0,readChannel.size());
    }
```


组件三 Selector选择器
常用方法

组件三 Selector选择器
常用方法

一个channel通道对应了一个selectKey,每次有事件发生时,selector会根据获取的selectKeys数组来遍历channel

Selector关系图及解析:


说明:

当客户端连接时,会通过ServerSocketChannel
,得到SocketChannel

将socketChannel注册到Selector上,并且返回一个
selectorKey,该SelectorKey会和Selector关联

selector进行监听select方法,返回有事件发生的通道个数

进一步得到各个SelectKey

再通过SelectKey,反向获取channel

最后通过channel完成对应的事件

NIO快速入门
在学习nio入门前,请先学习前一篇文章,理清nio三大组件的关系

图解关系:

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200503162217881.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3ppc3V1,size_16,color_FFFFFF,t_70)

说明:

当客户端连接时,会通过ServerSocketChannel
,得到SocketChannel

将socketChannel注册到Selector上,并且返回一个
selectorKey,该SelectorKey会和Selector关联

selector进行监听select方法,返回有事件发生的通道个数

进一步得到各个SelectKey

再通过SelectKey,反向获取channel

最后通过channel完成对应的事件

```
服务端:
  public static void main(String[] args) throws IOException {
        //创建serverSocketChannel
        ServerSocketChannel serverSocketChannel = ServerSocketChannel.open();
        //创建selector对象
        Selector selector = Selector.open();
        //绑定端口6666,在服务器端监听
        serverSocketChannel.socket().bind(new InetSocketAddress(6666));
        //设置非阻塞
        serverSocketChannel.configureBlocking(false);
        //把ServerSocketChannel注册到Selector
        serverSocketChannel.register(selector, SelectionKey.OP_ACCEPT);
        //循环等待客户端请求
        while (true) {
            if (selector.select(1000) == 0) {
                System.out.println("服务器等待了1秒,无连接");
                continue;
            }
            //获取selectorKey集合
            Set<SelectionKey> selectionKeys = selector.selectedKeys();
            //遍历集合
            for (SelectionKey key : selectionKeys) {
                //反向获取到channel,根据不同事件做出处理
                if (key.isAcceptable()) {//如果是连接请求
                    //给该客户端生成一个socketChannel
                    SocketChannel channel = serverSocketChannel.accept();
                    //将当前的channel注册到selector上
                    channel.register(selector, SelectionKey.OP_READ, ByteBuffer.allocate(1024));
                }
                if (key.isReadable()) {//读的请求
                    //获取到该channel
                    SocketChannel channel = (SocketChannel) key.channel();
                    //获取buffer
                    ByteBuffer byteBuffer = (ByteBuffer) key.attachment();
                    channel.read(byteBuffer);
                    System.out.println("from 客户端" + new String(byteBuffer.array()));

​            }
​            //最后移出
​            selectionKeys.remove(key);
​        }
​    }
}
```



```
客户端:
  public static void main(String[] args) throws IOException {
        SocketChannel socketChannel=SocketChannel.open();
        //非阻塞
        socketChannel.configureBlocking(false);
        //提供服务端的ip和端口
        InetSocketAddress address=new InetSocketAddress("127.0.0.1",6666);
        //连接服务器
        if(!socketChannel.connect(address)){
            while(!socketChannel.finishConnect()){
                System.out.println("因为连接需要事件,可以做其他的事情");
            }
        }else {
            //连接成功了
            String str="hello world";
            ByteBuffer byteBuffer=ByteBuffer.wrap(str.getBytes());
            //将数据写入channel
            socketChannel.write(byteBuffer);

​    }
}
```



三、AIO

   与NIO不同，当进行读写操作时，只须直接调用API的read或write方法即可。这两种方法均为异步的，对于读操作而言，当有流可读取时，操作系统会将可读的流传入read方法的缓冲区，并通知应用程序；对于写操作而言，当操作系统将write方法传递的流写入完毕时，操作系统主动通知应用程序。 即可以理解为，read/write方法都是异步的，完成后会主动调用回调函数。 在JDK1.7中，这部分内容被称作NIO.2，主要在java.nio.channels包下增加了下面四个异步通道：

- AsynchronousSocketChannel
- AsynchronousServerSocketChannel
- AsynchronousFileChannel
- AsynchronousDatagramChannel

其中的read/write方法，会返回一个带回调函数的对象，当执行完读取/写入操作后，直接调用回调函数。

BIO是一个连接一个线程。

NIO是一个请求一个线程。

AIO是一个有效请求一个线程。

先来个例子理解一下概念，以银行取款为例： 

- 同步 ： 自己亲自出马持银行卡到银行取钱（使用同步IO时，Java自己处理IO读写）；
- 异步 ： 委托一小弟拿银行卡到银行取钱，然后给你（使用异步IO时，Java将IO读写委托给OS处理，需要将数据缓冲区地址和大小传给OS(银行卡和密码)，OS需要支持异步IO操作API）；
- 阻塞 ： ATM排队取款，你只能等待（使用阻塞IO时，Java调用会一直阻塞到读写完成才返回）；
- 非阻塞 ： 柜台取款，取个号，然后坐在椅子上做其它事，等号广播会通知你办理，没到号你就不能去，你可以不断问大堂经理排到了没有，大堂经理如果说还没到你就不能去（使用非阻塞IO时，如果不能读写Java调用会马上返回，当IO事件分发器会通知可读写时再继续进行读写，不断循环直到读写完成）

Java对BIO、NIO、AIO的支持：

- Java BIO ： 同步并阻塞，服务器实现模式为一个连接一个线程，即客户端有连接请求时服务器端就需要启动一个线程进行处理，如果这个连接不做任何事情会造成不必要的线程开销，当然可以通过线程池机制改善。
- Java NIO ： 同步非阻塞，服务器实现模式为一个请求一个线程，即客户端发送的连接请求都会注册到多路复用器上，多路复用器轮询到连接有I/O请求时才启动一个线程进行处理。
- Java AIO(NIO.2) ： 异步非阻塞，服务器实现模式为一个有效请求一个线程，客户端的I/O请求都是由OS先完成了再通知服务器应用去启动线程进行处理，

BIO、NIO、AIO适用场景分析:

- BIO方式适用于连接数目比较小且固定的架构，这种方式对服务器资源要求比较高，并发局限于应用中，JDK1.4以前的唯一选择，但程序直观简单易理解。
- NIO方式适用于连接数目多且连接比较短（轻操作）的架构，比如聊天服务器，并发局限于应用中，编程比较复杂，JDK1.4开始支持。
- AIO方式使用于连接数目多且连接比较长（重操作）的架构，比如相册服务器，充分调用OS参与并发操作，编程比较复杂，JDK7开始支持。

另外，I/O属于底层操作，需要操作系统支持，并发也需要操作系统的支持，所以性能方面不同操作系统差异会比较明显。

在高性能的I/O设计中，有两个比较著名的模式**Reactor**和**Proactor**模式，

其中**Reactor**模式用于**同步I/O**，而**Proactor**运用于**异步I/O**操作。

   在比较这两个模式之前，我们首先的搞明白几个概念，什么是阻塞和非阻塞，什么是同步和异步,同步和异步是针对应用程序和内核的交互而言的，同步指的是用户进程触发IO操作并等待或者轮询的去查看IO操作是否就绪，而异步是指用户进程触发IO操作以后便开始做自己的事情，而当IO操作已经完成的时候会得到IO完成的通知。而阻塞和非阻塞是针对于进程在访问数据的时候，根据IO操作的就绪状态来采取的不同方式，说白了是一种读取或者写入操作函数的实现方式，阻塞方式下读取或者写入函数将一直等待，而非阻塞方式下，读取或者写入函数会立即返回一个状态值。

 一般来说I/O模型可以分为：同步阻塞，同步非阻塞，异步阻塞，异步非阻塞IO

同步阻塞IO：在此种方式下，用户进程在发起一个IO操作以后，必须等待IO操作的完成，只有当真正完成了IO操作以后，用户进程才能运行。JAVA传统的IO模型属于此种方式！

同步非阻塞IO:在此种方式下，用户进程发起一个IO操作以后边可返回做其它事情，但是用户进程需要时不时的询问IO操作是否就绪，这就要求用户进程不停的去询问，从而引入不必要的CPU资源浪费。其中目前JAVA的NIO就属于同步非阻塞IO。

异步阻塞IO：此种方式下是指应用发起一个IO操作以后，不等待内核IO操作的完成，等内核完成IO操作以后会通知应用程序，这其实就是同步和异步最关键的区别，同步必须等待或者主动的去询问IO是否完成，那么为什么说是阻塞的呢？因为此时是通过select系统调用来完成的，而select函数本身的实现方式是阻塞的，而采用select函数有个好处就是它可以同时监听多个文件句柄，从而提高系统的并发性！

 异步非阻塞IO:在此种模式下，用户进程只需要发起一个IO操作然后立即返回，等IO操作真正的完成以后，应用程序会得到IO操作完成的通知，此时用户进程只需要对数据进行处理就好了，不需要进行实际的IO读写操作，因为真正的IO读取或者写入操作已经由内核完成了。目前Java中还没有支持此种IO模型。

#### **Reactor模式**

 在BIO线程模型中，为了解决同步阻塞的问题，采用了多线程的方式处理并发，即经典的connection per thread，每一个连接用一个线程处理。虽然在单个线程内仍然是阻塞的，但在整体上看是可以同时处理多个连接请求的，原理图如下：

![8c9d2203ab7b7a059d241a091f7280fd.png](https://img-blog.csdnimg.cn/img_convert/8c9d2203ab7b7a059d241a091f7280fd.png)

但这种方式的缺点在于资源要求太高，系统中创建线程是需要比较高的系统资源的，如果连接数太多，系统无法承受，而且，线程的反复创建和销毁也需要代价。

为了解决这个问题，出现了Reactor线程模型。简单来说，Reactor线程模型就是多路I/O复用结合线程池的思想。

I/O多路复用：多个连接共用一个阻塞对象(即下图中的ServiceHandler)，应用程序只需要在一个阻塞对象等待，无需阻塞等待所有连接，当某个连接有新的数据可以处理时，操作系统通知应用程序线程从阻塞状态返回，并将数据分发给对应的线程处理
基于线程池复用线程资源：不必再为每个连接创建线程，将连接完成后的业务处理任务交给线程池中的线程处理，处理完成后归还线程，同一个线程可以处理多个连接的业务，达到线程复用

![0bc3701da6ea80285ce9175e1d5f87fa.png](https://img-blog.csdnimg.cn/img_convert/0bc3701da6ea80285ce9175e1d5f87fa.png)




在Reactor线程模型的发展过程中，出现了不同的实现方式，具体有：

单Reactor单线程

单Reactor多线程

主从Reactor多线程

1.**单Reactor单线程模式** (Reactor和handler都在同一个线程中)

方案说明：
Select是IO复用模型介绍的标准网络编程API，可以实现应用程序通过一个阻塞对象监听多路连接请求
Reactor对象通过Select监控客户端请求事件，收到事件后通过Dispatch进行分发
如果是建立连接请求事件，则由Acceptor通过Accept处理连接请求，然后创建一个Handler对象处理连接完成后的后续业务
如果不是建立连接事件，则Reactor会分发调用连接对应的Handler来处理业务
Handler会完成Read->业务处理->Send的完整业务流程

![c2bcdddaedfdcd364a71e1cb8d43eeb8.png](https://img-blog.csdnimg.cn/img_convert/c2bcdddaedfdcd364a71e1cb8d43eeb8.png)



 这种模式的缺点在于：
服务器端用一个线程通过多路复用搞定所有的IO操作，包括连接、读、写等，但是如果客户端连接数较多，将无法支撑，比如处理一个客户端的业务时，别的客户端的业务请求只能阻塞等待
单线程无法发挥多核CPU的性能
2.**单Reactor多线程** 方案说明：
Reactor对象通过select监控客户端请求事件，收到事件后，通过dispatcher进行分发
如果是建立连接的请求，则由Acceptor通过accept处理连接请求，然后创建一个Handler对象处理完成连接后的各种事件
如果不是连接请求，则由Reactor分发调用连接对应的handler进行处理
handler只负责响应事件，不做具体的业务处理，通过read读取数据后，会分发给后面的worker线程池的某个线程处理业务
worker线程池会分发独立的线程完成真正的业务，并将结果返回给handler
handler收到响应的结果后，再通过send将结果返回给client

![03f594066eb6ecffeace5b2e299e16e6.png](https://img-blog.csdnimg.cn/img_convert/03f594066eb6ecffeace5b2e299e16e6.png)


优点：

多线程可以充分利用多核CPU的处理能力

采用线程池复用线程，减少创建和销毁线程带来的性能开销

缺点：

reactor处理所有事件的监听和响应，在单线程运行，高并发场景下容易出现性能瓶颈

多线程数据共享和访问比较复杂

3.主从Reactor多线程

方案说明：

Reactor主线程MainReactor对象通过select监听连接事件，收到事件后，通过Acceptor处理连接事件

当Acceptor处理连接事件后，MainReactor将连接分配给SubReactor

SubReactor将连接加入到连接队列进行监听，并创建handler进行各种事件处理

当有新事件发生时，SubReactor就会调用对应的handler进行处理

handler通过Read读取数据，分发给后面的worker线程处理

worker线程池会分配独立的worker线程进行业务处理，并返回结果

handler收到响应的结果后，再通过send将结果返回给client

MainReactor主线程可以关联多个SubReactor子线程

![cda6b4b4126a944d0e5690b980479b66.png](https://img-blog.csdnimg.cn/img_convert/cda6b4b4126a944d0e5690b980479b66.png)

优点：

主线程与子线程的数据交互简单职责明确，主线程只需要接收新连接，子线程完成后续的业务处理

可以通过扩展多个Reactor子线程的方式来减小单个子线程的压力，提高并发处理能力

Netty就是在主从Reactor多线程模型的基础上进行了一定的改进，同时，Kafka的网络架构设计也采用了这种主从Reactor多线程的模型。



原文链接：https://blog.csdn.net/weixin_39724469/article/details/111295927





#### **Proactor模式**

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191212213841310.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODA1NDA0NQ==,size_16,color_FFFFFF,t_70)

1. Actor模型
传统的并发模型主要由两种实现的形式，一是同一个进程下，多个线程天然的共享内存，由程序对读写做同步控制(有锁或无锁). 二是多个进程通过进程间通讯或者内存映射实现数据的同步.

Actors模型更多的使用消息机制来实现并发，目标是让开发者不再考虑线程这种东西，每个Actor最多同时只能进行一样工作，Actor内部可以有自己的变量和数据.

在Actors模型中，每个Actor都有一个专属的命名”邮箱”, 其他Actor可以随时选择一个Actor通过邮箱收发数据,对于“邮箱”的维护，通常是使用发布订阅的机制实现的，比如我们可以定义发布者是自己，订阅者可以是某个Socket接口，另外的消息总线或者直接是目标Actor.

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222205716395.png)



总结：Actor模型解决了并发问题。

参考文献：
https://cppfans.org/2176.html
https://www.jdon.com/concurrent/actor-csp.html

2. CSP模型
CSP模型中，worker之间不直接彼此联系，而是通过不同channel进行消息发布和侦听。消息的发送者和接收者之间通过Channel松耦合，发送者不知道自己消息被哪个接收者消费了，接收者也不知道是哪个发送者发送的消息。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222210110828.png)




总结：CSP比Actor解耦程度高

个人感觉CSP着这种模型的Channel似乎和Netty的Channel有着相似之处，但是查阅不到相关的资料。欢迎了解这一块同学提出宝贵见解

3. Reactor模型
大概就是连接客户端和处理客户端任务之间有一个select去对接。（具体可以自行了解以下select模型）



![在这里插入图片描述](https://img-blog.csdnimg.cn/2020022221093486.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1Njg4MTQw,size_16,color_FFFFFF,t_70)




参考文献：
https://juejin.im/post/5cc1c3156fb9a0322b5bfe86

4. Proactor模型
也就是我们不必等待I/O数据准备好也就是内核缓存已经读数据到用户空间。这一切都有内核来帮我们搞定，数据准备好了之后就通知Proactor，然后Proactor就调用相应的Handler进行业务处理。相对于Reactor省去了遍历事件通知队列selector 的代价。

个人感觉有点像响应式代替了select的轮询

所以理论上Proactor的效率比Reactor高，但是linux并没有真正的实现Proactor模型，而是epoll模拟出Proactor模型。



![在这里插入图片描述](https://img-blog.csdnimg.cn/20200222211302917.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM1Njg4MTQw,size_16,color_FFFFFF,t_70)

原文链接：https://blog.csdn.net/qq_35688140/article/details/104450370







#### 滑动窗口



## 多线程

​		在一个操作系统中，每个独立执行的程序都可以称为一个**进程**，也就是“正在运行的程序”。在多任务操作系统中，表面上看是支持进程并发执行的，但实际上这些进程并不是同时运行的。在计算机中，所以的应用程序都由cpu执行，对于一个cpu来说，每个时间点只能运行一个程序，也就是只能执行一个进程。操作系统会为每一个进程分配一段优先的cpu使用时间，cpu在这段实践中执行某个检查，然后会在下一段时间切换到另一个进程去执行。由于cpu运行速度很快，能在极端的时间内在不同的进程之间进行切换，所以给人同时执行多个程序的感觉。

#### 多线程的作用

1. **发挥多核CPU的优势**

   多段逻辑同时工作，多线程，可以真正发挥出多核CPU的优势来，达到**充分利用CPU**的目的

2. **防止阻塞**

   单核CPU频繁切换线程，反而会降低程序整体运行的效率。使用多线程防止阻塞。

3. **便于建模**

   把大任务拆分成小任务，把小任务单独建模（程序模型），并通过多线程分别运行这几个任务。

### 线程

​		每一个程序都是一个进程，一个进程中可以有多个执行单元同时运行。这些执行单元可以看做程序执行的一条条线索，被称为线程。操作系统中每一个进程都至少存在一个线程。

​		所谓多线程是只一个进程在执行过长中可以产生多个单线程，这些单线程程序在运行时是相互独立的，它们可以并发执行。实际上也是由CPU轮流执行的。

#### 线程的创建

​	1. 继承java.lang包下的Thread类，覆写read类的run()方法，在run()方法中实现运行在线程上的代码

  		2. 实现java.lang.Runnable接口

##### Thread创建多线程

**单线程例子**

```
public class ThreadOne{
	public static void main(String[] args){
	MyThread myThread=	new Mythread();
	myThread.run();
	while(true){
		System.out.println("Main方法在执行")；
		}
	}
}

class MyThread{
	pubic void run(){
	while(true){
		System.out.println("MyThread类的run()方法在执行")；
		}
	}
}
```

​		因为调用MyThread类的run()方法时，遇到死循环，循环会一直进行，因此，MyThread类的打印语句将永远只想，而main方法中的打印语句永远无法得到执行。

​		**多线程例子**

```
public class ThreadTwo{
	public static void main(String[] args){
	MyThread myThread=	new Mythread();
	myThread.start();
	while(true){
		System.out.println("Main方法在执行")；
		}
	}
}

class MyThread extends Thread{
	pubic void run(){
	while(true){
		System.out.println("MyThread类的run()方法在执行")；
		}
	}
}
```

​		因为MyThread类继承了Thread类，重写Thread类中的run()方法，用start()方法用于启动新线程，两个while循环的打印语句就轮流执行了。

##### Runnable创建多线程

​		为了避免单继承的局限性，Thread类提供了另外一个构造方法Thread(Runnable target)，其中Runnable是一个接口，它只有run()方法。当通过Thread(Runnable target)构造方法创建线程对象时，只需为该方法传递一个实现了Runnable接口的类中的run()方法作为运行代码，而不需要调用Thread中的run()方法。

```
public class ThreadThree{
	public static void main(String[] args){
	MyThread myThread=	new Mythread();//创建MyThread的实例对象
	Thread thread =new Thread(mythread);//创建线程对象
	thread.start();//开启线程，执行run方法
	while(true){
		System.out.println("Main方法在执行")；
		}
	}
}

class MyThread implements Runnable{
	pubic void run(){//线程的代码块，当调用start()方法时，线程从此处开始执行
	while(true){
		System.out.println("MyThread类的run()方法在执行")；
		}
	}
}
```

​		MyThread类继承了Runnable接口，并重写了run()方法，通过Thread类的构造方法将MyThread类的实例对象作为参数传入。实现多线程。

##### 两种方法的对比

场景：

​		一个车站4个窗口发售100张票。4个窗口可理解成四个线程，100个票理解为共享资源。



```
public class ThreadFive{
	public static void main(String[] args){
	TicketWindow task=	new TicketWindow();//创建线程的任务对象
	new Thread(task, "窗口1").start;//创建线程起名为窗口1，开启线程
    new Thread(task, "窗口2").start;//创建线程起名为窗口2，开启线程
    new Thread(task, "窗口3").start;//创建线程起名为窗口3，开启线程
    new Thread(task, "窗口4").start;//创建线程起名为窗口4，开启线程
	}
}

class TicketWindow implements Runnable{
	private int tickets=100;
	pubic void run(){//线程的代码块，当调用start()方法时，线程从此处开始执行
	while(true){
		if(tickets>0){
			Thread th=Thread.currentThread();//获取当前运行run方法的线程
			String th_name=th.getName();/.获取到线程的名称	
            System.out.println(th_name+"正在发售第"+tickets+"张票")；
			}
		}
	}
}
```

​		这里注意点有：

1. TicketWindow task=	new TicketWindow();//创建线程的任务对象

   保证四个线程访问的是同一个tickets变量，避免各发各的，共享100张票。

2. 避免单继承的问题，多实现很好的解决了这个问题

#### 两者优劣

​	肯定是后者好，因为实现接口的方式比继承类的方式更灵活，也能减少程序之间的耦合度，**面向接口编程**也是设计模式6大原则的核心

##### **start()方法和run()方法的区别**

​	只有调用了start()方法，才会表现出多线程的特性，不同线程的run()方法里面的代码交替执行。如果只是调用run()方法，那么代码还是同步执行的，必须等待一个线程的run()方法里面的代码全部执行完毕之后，另外一个线程才可以执行其run()方法里面的代码



#### 第三种：**Callable**

​	Runnable接口中的run()方法的返回值是void，它做的事情只是纯粹地去执行run()方法中的代码而已；Callable接口中的call()方法是有返回值的，是一个泛型，和Future、FutureTask配合可以用来获取异步执行的结果



**FutureTask**

​	FutureTask表示一个异步运算的任务。FutureTask里面可以传入一个Callable的具体实现类，可以对这个异步运算的任务的结果进行等待获取、判断是否已经完成、取消任务等操作。当然，由于FutureTask也是Runnable接口的实现类，所以FutureTask也可以放入线程池中。



#### CyclicBarrier和CountDownLatch区别

CyclicBarrier和CountDownLatch 都位于java.util.concurrent 这个包下

|                                                              |                                                              |
| :----------------------------------------------------------- | ------------------------------------------------------------ |
| CountDownLatch                                               | CyclicBarrier                                                |
| 减计数方式                                                   | 加计数方式                                                   |
| 计算为0时释放所有等待的线程                                  | 计数达到指定值时释放所有等待线程                             |
| 计数为0时，无法重置                                          | 计数达到指定值时，计数置为0重新开始                          |
| 调用countDown()方法计数减一，调用await()方法只进行阻塞，对计数没任何影响 | 调用await()方法计数加1，若加1后的值不等于构造方法的值，则线程阻塞 |
| 不可重复利用                                                 | 可重复利用                                                   |



1）CyclicBarrier的某个线程运行到某个点上之后，该线程即停止运行，直到所有的线程都到达了这个点，所有线程才重新运行；CountDownLatch则不是，某线程运行到某个点上之后，只是给某个数值-1而已，该线程继续运行。

2）CyclicBarrier只能唤起一个任务，CountDownLatch可以唤起多个任务。

3) CyclicBarrier可重用，CountDownLatch不可重用，计数值为0该CountDownLatch就不可再用了



**CountDownLatch**

```
public CountDownLatch(int count) {  };  *//参数count为计数值*
```

```
1. public void await() throws InterruptedException { };   
*//调用await()方法的线程会被挂起，它会等待直到count值为0才继续执行*
2. public boolean await(long timeout, TimeUnit unit) throws InterruptedException { }; 
*//和await()类似，只不过等待一定的时间后count值还没变为0的话就会继续执行*
3. public void countDown() { };  *//将count值减1*
```



CountDownLatch， 一个同步辅助类，在完成一组正在其他线程中执行的操作之前，它允许一个或多个线程一直等待。

下面举个例子说明：



```java
package main.java.CountDownLatch;

import java.util.concurrent.CountDownLatch;

public class countDownlatchTest {
    public static void main(String[] args) throws InterruptedException {
        CountDownLatch countDownLatch = new CountDownLatch(5);
        for(int i=0;i<5;i++){
            new Thread(new readNum(i,countDownLatch)).start();
        }
        countDownLatch.await();
        System.out.println("线程执行结束。。。。");
    }

    static class readNum  implements Runnable{
        private int id;
        private CountDownLatch latch;
        public readNum(int id,CountDownLatch latch){
            this.id = id;
            this.latch = latch;
        }
        @Override
        public void run() {
            synchronized (this){
                System.out.println("id:"+id);
                latch.countDown();
                System.out.println("线程组任务"+id+"结束，其他任务继续");
            }
        }
    }
}
```


输出结果：



```
id:1
线程组任务1结束，其他任务继续
id:0
线程组任务0结束，其他任务继续
id:2
线程组任务2结束，其他任务继续
id:3
线程组任务3结束，其他任务继续
id:4
线程组任务4结束，其他任务继续
线程执行结束。。。。
```



**线程在countDown()之后，会继续执行自己的任务，而CyclicBarrier会在所有线程任务结束之后，才会进行后续任务**

CyclicBarrier提供2个构造器：

```java
public CyclicBarrier(int parties, Runnable barrierAction) {}
public CyclicBarrier(int parties) {}
```

参数parties指让多少个线程或者任务等待至barrier状态；参数barrierAction为当这些线程都达到barrier状态时会执行的内容。

CyclicBarrier中最重要的方法就是await方法

```java
public int await() throws InterruptedException, BrokenBarrierException { };
//挂起当前线程，直至所有线程都到达barrier状态再同时执行后续任务；
public int await(long timeout, TimeUnit unit)throws InterruptedException,BrokenBarrierException,TimeoutException { };
//让这些线程等待至一定的时间，如果还有线程没有到达barrier状态就直接让到达barrier的线程执行后续任务
```



举例说明

```java
package main.java.countOff;

import java.util.concurrent.CyclicBarrier;

public class cyclicBarrierTest {
    public static void main(String[] args) throws InterruptedException {
        CyclicBarrier cyclicBarrier = new CyclicBarrier(5, new Runnable() {
            @Override
            public void run() {
                System.out.println("线程组执行结束");
            }
        });
        for (int i = 0; i < 5; i++) {
            new Thread(new readNum(i,cyclicBarrier)).start();
        }
        //CyclicBarrier 可以重复利用，
        // 这个是CountDownLatch做不到的
//        for (int i = 11; i < 16; i++) {
//            new Thread(new readNum(i,cyclicBarrier)).start();
//        }
    }
    static class readNum  implements Runnable{
        private int id;
        private CyclicBarrier cyc;
        public readNum(int id,CyclicBarrier cyc){
            this.id = id;
            this.cyc = cyc;
        }
        @Override
        public void run() {
            synchronized (this){
                System.out.println("id:"+id);
                try {
                    cyc.await();
                    System.out.println("线程组任务" + id + "结束，其他任务继续");
                } catch (Exception e) {
                    e.printStackTrace();
                }
            }
        }
    }
}
```


输出结果：



```
id:1
id:2
id:4
id:0
id:3
线程组执行结束
线程组任务3结束，其他任务继续
线程组任务1结束，其他任务继续
线程组任务4结束，其他任务继续
线程组任务0结束，其他任务继续
线程组任务2结束，其他任务继续
```

#### **volatile关键字**

1）多线程主要围绕可见性和原子性两个特性而展开，使用volatile关键字修饰的变量，保证了其在多线程之间的可见性，即每次读取到volatile变量，一定是最新的数据。

2）代码底层执行不像我们看到的高级语言----Java程序这么简单，它的执行是**Java代码-->字节码-->根据字节码执行对应的C/C++代码-->C/C++代码被编译成汇编语言-->和硬件电路交互**，现实中，为了获取更好的性能JVM可能会对指令进行重排序，多线程下可能会出现一些意想不到的问题。使用volatile则会对禁止语义重排序，当然这也一定程度上降低了代码执行效率。

一个volatile变量自身具有以下三个特性：

1. 可见性：即当一个线程修改了声明为volatile变量的值，新值对于其他要读该变量的线程来说是立即可见的。而普通变量是不能做到这一点的，普通变量的值在线程间传递需要通过主内存来完成。
2. 有序性：volatile变量的所谓有序性也就是被声明为volatile的变量的临界区代码的执行是有顺序的，即禁止指令重排序。
3. 受限原子性：这里volatile变量的原子性与synchronized的原子性是不同的，synchronized的原子性是指只要声明为synchronized的方法或代码块儿在执行上就是原子操作的。而volatile是不修饰方法或代码块儿的，它用来修饰变量，对于单个volatile变量的读/写操作都具有原子性，但类似于volatile++这种复合操作不具有原子性。所以volatile的原子性是受限制的。并且在多线程环境中，volatile并不能保证原子性

从实践角度而言，volatile的一个重要作用就是和CAS（乐观锁）结合，保证了原子性

##### volatile写-读的内存语义

volatile写的内存语义：当写线程写一个volatile变量时，JMM会把该线程对应的本地内存中的共享变量值刷新到主内存。

volatile读的内存语义：当读线程读一个volatile变量时，JMM会把该线程对应的本地内存置为无效，线程接下来将从主内存读取共享变量。

#### 2.volatile语义实现原理

在介绍volatile语义实现原理之前，我们先来看两个与CPU相关的专业术语：

- 内存屏障（memory barriers）：一组处理器指令，用于实现对内存操作的顺序限制。

- 缓存行（cache line）：CPU高速缓存中可以分配的最小存储单位。处理器填写缓存行时会加载整个缓存行

  volatile可见性的实现就是借助了CPU的lock指令，通过在写volatile的机器指令前加上lock前缀，使写volatile具有以下两个原则：

1. 写volatile时处理器会将缓存写回到主内存。
2. 一个处理器的缓存写回到内存会导致其他处理器的缓存失效。

总结：volatile变量的操作实际上是把锁转移到了硬件层面，手段是：通过汇编的lock指令。

lock指令实现的过程：1，处理器环迅写回内存，2其他处理器缓存无效（缓存一致性协议）。

# [volatile与synchronized的区别](https://www.cnblogs.com/tf-Y/p/5266710.html)

1、锁提供了两种主要特性：*互斥（mutual exclusion）* 和*可见性（visibility）*。

　　互斥即一次只允许一个线程持有某个特定的锁，因此可使用该特性实现对共享数据的协调访问协议，这样，一次就只有一个线程能够使用该共享数据。

　　可见性要更加复杂一些，它必须确保释放锁之前对共享数据做出的更改对于随后获得该锁的另一个线程是可见的 —— 如果没有同步机制提供的这种可见性保证，线程看到的共享     变量可能是修改前的值或不一致的值，这将引发许多严重问题。（竞态条件）

2、在Java中,为了保证多线程读写数据时保证数据的一致性,可以采用两种方式：

　 同步：如用synchronized关键字,或者使用锁对象

　 使用volatile关键字：用一句话概括volatile,它能够使变量在值发生改变时能尽快地让其他线程知道。

3、volatile详解

　当一个变量定义为volatile后，它将具备两种特性：1. 可见性，2. 禁止指令重排序。

  首先，我们要意识到有这样的现象：编译器为了加快程序运行速度，对一些变量的写操作会现在寄存器或CPU缓存上进行，最后写入内存。而在这个过程中，变量的新值对其它线程是不可见的。

  可见性：当对volatile标记的变量进行修改时，会将其它缓存中存储的修改前的变量清除，然后重新读取。这里从哪读尚未明确，一般来说应该是先在进行修改的缓存A中修改为新值，然后通知其它缓存清除掉此变量，当其它缓存B中的线程读取此变量时，会向总线发送消息，这是存储新值的缓存A获取到消息，将新值传给B，最后将新值写入内存。

 

**volatile的作用是被其修饰的变量每次刷新时，都会刷新上述步骤。**

4、volatile与synchronized

  1）volatile本质是告诉JVM当前变量在寄存器中的值是不确定的，需要从主存中读取。synchronized则是锁定当前变量，只有当前线程可以访问该变量，其它线程被阻塞。

  2）volatile仅能使用在变量级别，synchronized则可以使用在变量、方法。

  3）volatile仅能实现变量修改的可见性，而synchronized则可以保证变量修改的可见性和原子性。《Java编程思想》上说，定义long或double时，如果使用volatile关键字(简单的赋值与返回操作)，就会获得原子性。(常规状态下，这两个变量由于其长度，其操作不是原子的)

  4）volatile不会造成线程阻塞，synchronized会造成线程阻塞。

  5）使用volatile而不是synchronized的唯一安全情况是类中只有一个可变的域。

5、当一个域的值依赖于它之前的值时，volatile就无法工作了，如n=n+1,n++等。如果某个域的值受到其他域的值的限制，那么volatile也无法工作，如Range类的lower和upper边界，必须遵循lower<=upper的限制。

6、使用volatile而不是synchronized的唯一安全的情况是类中只有一个可变的域



#### 线程的生命周期及状态转换

![IMG_20201020_170034(1)](F:\自制笔记\图片\IMG_20201020_170034(1).jpg)

##### 1.新建状态（New）

　　创建一个线程对象后，该线程对象就处于新建状态，此时还不能运行，和其他Java对象一样，仅仅有Java虚拟机为其分配了内存，没有表现出任何线程的动态特征。

#####  2.就绪状态（Runnable）

　　当线程对象调用了start()方法后，该线程就进入就绪状态（可运行状态），处于就绪状态的线程位于可运行池中，此时它只是具备了运行的条件，能否获得CPU使用权开始运行，还需要等待系统的调度。

#####  3.运行状态（Running）

　　如果处于就绪状态的线程获得了CPU的使用权，开始执行run()方法中的执行体，则该线程处于运行状态。当一个线程启动后，它不可能一直处于运行状态（除非它的线程执行体足够短，瞬间就结束了），当使用完系统分配时间后，系统就会剥夺该线程占用的CPU资源，让其他线程获得执行机会。只有处于就绪状态的线程才可能转换到运行状态！

#####  4.阻塞状态（Blocked）

　　一个正在执行的线程在某些特殊情况下，如耗时的输入/输出操作时，会放弃CPU的使用权，进入阻塞状态。线程进入阻塞状态后，就不能进入排队队列。只有当引起阻塞的原因被消除后，线程才可以转入就绪状态。

　　线程由运行状态转换成阻塞状态的原因，以及如何从阻塞状态转换成就绪状态：

- 当线程试图获取某个对象的同步锁时，如果该锁被其他线程所持有，则当前线程就会进入阻塞状态，如果想从阻塞状态进入就绪状态必须获取到其他线程所持有的锁。
- 当线程调用了一个阻塞式的IO方法时，该线程就会进入阻塞状态，如果想进入就绪状态就必须要等到这个阻塞的IO方法返回。
- 当线程调用了某个对象的wait()方法时，也会使线程进入阻塞状态，如果想进入就绪状态就需要使用notify()方法唤醒该线程。
- 当线程调用了Thread的sleep(long millis)方法时，也会使线程进入阻塞状态，在这种情况下，只需等到线程睡眠的时间结束，线程就会自动进入就绪状态。
- 当在一个线程中调用了另一个线程的join()方法时，会使当前线程进入阻塞状态，在这种情况下，需要等到新加入的线程运行结束后才会结束阻塞状态，进入就绪状态。

　　线程从阻塞状态只能进入就绪状态，而不能直接进入运行状态，也就是说：结束阻塞的线程需要重新进入可运行池中，等待系统的调度。

##### **5.死亡状态（Terminated）**

　　线程的run()方法正常执行完毕或者抛出一个未捕获的异常(Excption)、错误(Error),线程就进入死亡状态。一旦进入死亡状态，线程就不再拥有运行的资格，也不能再转换到其他状态

#### 线程的调度

​		java虚拟机会按照特定的机制为程序中的每个线程分配CPU使用权，这种机制被称为线程的调度。

​		调度模式：

1. 分时调度

   ​	轮流获取调度使用权和是键盘

2. 抢占式调入

   ​	程序自己控制，随机选择

线程的优先级：

​	优先级越高，获得CPU执行的机会越大，数字越大优先级越高。1——10，10最大

#### 线程休眠

​		进入阻塞状态不会被调用，，使正在执行的线程暂停，将CPU让给别的线程。

使用sleep(long millis)方法可以让正在执行的线程暂停一段时间，进入休眠状态

#### 线程让步

​		正在执行的线程，在某些情况下将CPU资源让给其他线程执行。

可以使用yield()方法来实现，可以让当前进程暂停，但不会阻塞该线程，它只是将线程转化成就绪状态，让系统的调度器重新调度一次。当某个线程调用yield方法后，只有当前优先级相同或者更高的线程才能获得执行机会。

#### 线程插队

​		在某个线程调用其他线程的join()方法时，调用的线程将被阻塞，直到被join方法加入的线程执行完成后他才会继续运行。



### 多线程同步

#### 线程安全问题

​		由多个线程同时处理共享数据导致的。要想解决线程安全问题，必须保证用于处理共享资源的代码在任何时刻只能有一个线程访问。

#### **synchronized关键字**

​		为了实现这种限制，Java中提供了同步机制。当多个线程使用同一个共享资源时，可以将处理共享资源的代码放在一个使用synchronized关键字来修饰的代码块中，这个代码块被称作同步代码块

​		synchronized本质是对对象加锁

synchronized的使用

- 修饰实例方法，对当前实例对象加锁
- 修饰静态方法，多当前类的Class对象加锁
- 修饰代码块，对synchronized括号内的对象加锁

synchronized的锁同步依赖软件层面的JVM，而j.u.c.Lock给出的答案是在硬件层面依赖特殊的CPU指令

反编译结果

1. **monitorenter**：每个**对象**都是一个监视器锁（monitor）。当monitor被占用时就会处于锁定状态，线程执行monitorenter指令时尝试获取monitor的所有权，过程如下：

   > 1. 如果monitor的进入数为0，则该线程进入monitor，然后将进入数设置为1，该线程即为monitor的所有者；
   > 2. 如果线程已经占有该monitor，只是重新进入，则进入monitor的进入数加1；
   > 3. 如果其他线程已经占用了monitor，则该线程进入阻塞状态，直到monitor的进入数为0，再重新尝试获取monitor的所有权；

2. monitorexit：执行monitorexit的线程必须是objectref所对应的monitor的所有者。指令执行时，monitor的进入数减1，如果减1后进入数为0，那线程退出monitor，不再是这个monitor的所有者。其他被这个monitor阻塞的线程可以尝试去获取这个 monitor 的所有权。

   > monitorexit指令出现了两次，第1次为同步正常退出释放锁；第2次为发生异步退出释放锁；

   Synchronized的语义**底层**是通过一个monitor的对象来完成，其实wait/notify等方法也依赖于monitor对象，这就是为什么只有在同步的块或者方法中才能调用wait/notify等方法，否则会抛出java.lang.IllegalMonitorStateException的异常的原因。

   但是`Synchronized`虽然确保了线程的安全，但是在性能上却不是最优的，`Synchronized`关键字会让没有得到锁资源的线程进入`BLOCKED`状态，而后在争夺到锁资源后恢复为`RUNNABLE`状态，这个过程中涉及到操作系统用户模式和内核模式的转换，代价比较高。

```
synchronized(lock){
	****//操作共享资源代码块
}
```

##### 同步方法

​		在方法前面同样可以用synchronized关键词来修饰，被修饰的方法称为同步方法

```
public class ThreadSix{
	public static void main(String[] args){
	TicketWindow task=	new TicketWindow();//创建线程的任务对象
	new Thread(task, "窗口1").start;//创建线程起名为窗口1，开启线程
    new Thread(task, "窗口2").start;//创建线程起名为窗口2，开启线程
    new Thread(task, "窗口3").start;//创建线程起名为窗口3，开启线程
    new Thread(task, "窗口4").start;//创建线程起名为窗口4，开启线程
	}
}

class TicketWindow implements Runnable{
	private int tickets=100;
	pubic void run(){//线程的代码块，当调用start()方法时，线程从此处开始执行
	while(true){
		sendTicket();
		}
	}
	public synchronized void sendTicket(){
	try{
		Thread.sleep(10);//线程休眠10ms
		}catch(InterrutptedException e)｛
			e.printStackTrace();
		｝
		if(tickes>0){
		 System.out.println(Thread.currentThread().getName+"卖票的编号为"+tickets--)；
		}else{
			System.exit(0);
		}
	}
}
```

**JVM对synchronized的锁优化**

Synchronized是通过对象内部的一个叫做监视器锁（monitor）来实现的，监视器锁本质又是依赖于底层的操作系统的Mutex Lock（互斥锁）来实现的。而操作系统实现线程之间的切换需要从用户态转换到核心态，这个成本非常高，状态之间的转换需要相对比较长的时间，这就是为什么Synchronized效率低的原因。因此，这种依赖于操作系统Mutex Lock所实现的锁我们称之为“重量级锁”。

Java SE 1.6为了减少获得锁和释放锁带来的性能消耗，引入了“偏向锁”和“轻量级锁”：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190310225911793.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODQ4MTk2Mw==,size_16,color_FFFFFF,t_70)

锁一共有4种状态，级别从低到高依次是：无锁状态、偏向锁状态、轻量级锁状态和重量级锁状态。锁可以升级但不能降级。

1、偏向锁
偏向锁是JDK1.6中引用的优化，它的目的是消除数据在无竞争情况下的同步原语，进一步提高程序的性能。

偏向锁的获取：

1. 判断是否为可偏向状态
2. 如果为可偏向状态，则判断线程ID是否是当前线程，如果是进入同步块；
3. 如果线程ID并未指向当前线程，利用CAS（乐观锁）操作竞争锁，如果竞争成功，将Mark Word中线程ID更新为当前线程ID，进入同步块
4. 如果竞争失败，等待全局安全点，准备撤销偏向锁，根据线程是否处于活动状态，决定是转换为无锁状态还是升级为轻量级锁。

当锁对象第一次被线程获取的时候，虚拟机会把对象头中的标志位设置为“01”，即偏向模式。同时使用CAS操作把获取到这个锁的线程ID记录在对象的Mark Word中，如果CAS操作成功。持有偏向锁的线程以后每次进入这个锁相关的同步块时，虚拟机都可以不再进行任何同步操作。

偏向锁的释放：
偏向锁使用了遇到竞争才释放锁的机制。偏向锁的撤销需要等待全局安全点，然后它会首先暂停拥有偏向锁的线程，然后判断线程是否还活着，如果线程还活着，则升级为轻量级锁，否则，将锁设置为无锁状态。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311190530462.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODQ4MTk2Mw==,size_16,color_FFFFFF,t_70)

2、轻量级锁
轻量级锁也是在JDK1.6中引入的新型锁机制。它不是用来替换重量级锁的，它的本意是在没有多线程竞争的情况下，减少传统的重量级锁使用操作系统互斥量产生的性能消耗。

加锁过程：
在代码进入同步块的时候，如果此对象没有被锁定（锁标志位为“01”状态），虚拟机首先在当前线程的栈帧中建立一个名为锁记录（Lock Record）的空间，用于存储对象目前Mark Word的拷贝（官方把这份拷贝加了一个Displaced前缀，即Displaced Mark Word）。然后虚拟机使用CAS操作尝试将对象的Mark Word更新为指向锁记录（Lock Record）的指针。如果更新成功，那么这个线程就拥有了该对象的锁，并且对象的Mark Word标志位转变为“00”，即表示此对象处于轻量级锁定状态；如果更新失败，虚拟机首先会检查对象的Mark Word是否指向当前线程的栈帧，如果说明当前线程已经拥有了这个对象的锁，那就可以直接进入同步块中执行，否则说明这个锁对象已经被其他线程占有了。如果有两条以上的线程竞争同一个锁，那轻量级锁不再有效，要膨胀为重量级锁，锁标志变为“10”，Mark Word中存储的就是指向重量级锁的指针，而后面等待的线程也要进入阻塞状态。

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311190732602.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODQ4MTk2Mw==,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190311190736763.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl8zODQ4MTk2Mw==,size_16,color_FFFFFF,t_70)
解锁过程：
如果对象的Mark Word仍然指向线程的锁记录，那就用CAS操作将对象当前的Mark Word与线程栈帧中的Displaced Mark Word交换回来，如果替换成功，整个同步过程就完成了。如果替换失败，说明有其他线程尝试过获取该锁，那就要在释放锁的同时，唤醒被挂起的线程。

如果没有竞争，轻量级锁使用CAS操作避免了使用互斥量的开销，但如果存在竞争，除了互斥量的开销外，还额外发生了CAS操作，因此在有竞争的情况下，轻量级锁比传统重量级锁开销更大。

3、重量级锁
Synchronized的重量级锁是通过对象内部的一个叫做监视器锁（monitor）来实现的，监视器锁本质又是依赖于底层的操作系统的Mutex Lock（互斥锁）来实现的。而操作系统实现线程之间的切换需要从用户态转换到核心态，这个成本非常高，状态之间的转换需要相对比较长的时间，这就是为什么Synchronized效率低的原因。

4、自旋锁
互斥同步对性能影响最大的是阻塞的实现，挂起线程和恢复线程的操作都需要转入到内核态中完成，这些操作给系统的并发性能带来很大的压力。
于是在阻塞之前，我们让线程执行一个忙循环（自旋），看看持有锁的线程是否释放锁，如果很快释放锁，则没有必要进行阻塞。

5、锁消除
锁消除是指虚拟机即时编译器（JIT）在运行时，对一些代码上要求同步，但是检测到不可能发生数据竞争的锁进行消除。

6、锁粗化
如果虚拟机检测到有这样一串零碎的操作都对同一个对象加锁，将会把加锁同步的范围扩展（粗化）到整个操作序列的外部

我们以 Hotspot 虚拟机为例，Hopspot 对象头主要包括两部分数据：Mark Word(标记字段) 和 Klass Pointer(类型指针)。

Mark Word：默认存储对象的HashCode，分代年龄和锁标志位信息。这些信息都是与对象自身定义无关的数据，所以Mark Word被设计成一个非固定的数据结构以便在极小的空间内存存储尽量多的数据。它会根据对象的状态复用自己的存储空间，也就是说在运行期间Mark Word里存储的数据会随着锁标志位的变化而变化。

Klass Point：对象指向它的类元数据的指针，虚拟机通过这个指针来确定这个对象是哪个类的实例。



##### 死锁问题

​		两个线程都需要对方所占用的锁，但是都无法释放自己拥有的锁，于是这两个线程都处于挂起状态，从而造成了死锁。

解决方法：

1. 调整申请锁的范围
2. 调整申请锁的顺序

**避免死锁的发生**

​		很多时候实际锁的交叉可能涉及很多个，要想很好的避免只能人工仔细检查，一旦我们在一个同步方法中，或者说在一个锁的保护的范围中，调用了其它对象的方法时，就要十分的小心：

1. 如果其它对象的这个方法会消耗比较长的时间，那么就会导致锁被我们持有了很长的时间；
2. 如果其它对象的这个方法是一个同步方法，那么就要注意避免发生死锁的可能性了

总之是尽量避免在一个同步方法中调用其它对象的延时方法和同步方法。



#### **线程安全**

**如果你的代码在多线程下执行和在单线程下执行永远都能获得一样的结果，那么你的代码就是线程安全的**

线程安全在三个方面体现：

- 原子性：提供互斥访问，同一时刻只能有一个线程对数据进行操作，（atomic,synchronized）；
- 可见性：一个线程对主内存的修改可以及时地被其他线程看到，（synchronized,volatile）；
- 有序性：一个线程观察其他线程中的指令执行顺序，由于指令重排序，该观察结果一般杂乱无序，（happens-before原则）

**1）不可变**

​	像String、Integer、Long这些，都是final类型的类，任何一个线程都改变不了它们的值，要改变除非新创建一个，因此这些不可变对象不需要任何同步手段就可以直接在多线程环境下使用

**2）绝对线程安全**

​	不管运行时环境如何，调用者都不需要额外的同步措施。要做到这一点通常需要付出许多额外的代价，Java中标注自己是线程安全的类，实际上绝大多数都不是线程安全的，不过绝对线程安全的类，Java中也有，比方说CopyOnWriteArrayList、CopyOnWriteArraySet

**3）相对线程安全**

​	相对线程安全也就是我们通常意义上所说的线程安全，像Vector这种，add、remove方法都是原子操作，不会被打断，但也仅限于此，如果有个线程在遍历某个Vector、有个线程同时在add这个Vector，99%的情况下都会出现ConcurrentModificationException，也就是**fail-fast机制**。

**4）线程非安全**

这个就没什么好说的了，ArrayList、LinkedList、HashMap等都是线程非安全的类



**一个线程如果出现了运行时异常**

如果这个异常没有被捕获的话，这个线程就停止执行了。

另外重要的一点是：**如果这个线程持有某个某个对象的监视器，那么这个对象监视器会被立即释放**



**两个线程之间共享数据**

​	通过在线程之间**共享对象**就可以了，然后通过wait/notify/notifyAll、await/signal/signalAll进行唤起和等待，比方说阻塞队列BlockingQueue就是为线程之间共享数据而设计的



**sleep方法和wait方法的区别**

​	sleep方法和wait方法都可以用来放弃CPU一定的时间，不同点在于如果线程持有某个对象的监视器，sleep方法**不会**放弃这个对象的监视器，wait方法会放弃这个对象的监视器



**ThreadLocal有什么用**

​	ThreadLocal就是一种以**空间换时间**的做法，在每个Thread里面维护了一个以开地址法实现的ThreadLocal.ThreadLocalMap，把数据进行隔离，数据不共享，自然就没有线程安全方面的问题了



**为什么wait()方法和notify()/notifyAll()方法要在同步块中被调用**

​	是JDK强制的，wait()方法和notify()/notifyAll()方法在调用前都必须先获得对象的锁



> **什么是线程池？**



很简单，简单看名字就知道是装有线程的池子，我们可以把要执行的多线程交给线程池来处理，和连接池的概念一样，通过维护一定数量的线程池来达到多个线程的复用。



> **线程池的好处**



我们知道不用线程池的话，每个线程都要通过new Thread(xxRunnable).start()的方式来创建并运行一个线程，线程少的话这不会是问题，而真实环境可能会开启多个线程让系统和程序达到最佳效率，当线程数达到一定数量就会耗尽系统的CPU和内存资源，也会造成GC频繁收集和停顿，因为每次创建和销毁一个线程都是要消耗系统资源的，如果为每个任务都创建线程这无疑是一个很大的性能瓶颈。所以，线程池中的线程复用极大节省了系统资源，当线程一段时间不再有任务处理时它也会自动销毁，而不会长驻内存。



> **线程池核心类**



在java.util.concurrent包中我们能找到线程池的定义，其中ThreadPoolExecutor是我们线程池核心类，首先看看线程池类的主要参数有哪些。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXT2ibtLtqKVfibytiaLDz9eHO0dvdHdRcGtOSHmmQShwHibD8udASLLhNvg/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

- corePoolSize：线程池的核心大小，也可以理解为最小的线程池大小。
- maximumPoolSize：最大线程池大小。
- keepAliveTime：空余线程存活时间，指的是超过corePoolSize的空余线程达到多长时间才进行销毁。
- unit：销毁时间单位。
- workQueue：存储等待执行线程的工作队列。
- threadFactory：创建线程的工厂，一般用默认即可。
- handler：拒绝策略，当工作队列、线程池全已满时如何拒绝新任务，默认抛出异常。



> **线程池工作流程**



1、如果线程池中的线程小于corePoolSize时就会创建新线程直接执行任务。

2、如果线程池中的线程大于corePoolSize时就会暂时把任务存储到工作队列workQueue中等待执行。

3、如果工作队列workQueue也满时：当线程数小于最大线程池数maximumPoolSize时就会创建新线程来处理，而线程数大于等于最大线程池数maximumPoolSize时就会执行拒绝策略。



> **线程池分类**



Executors是jdk里面提供的创建线程池的工厂类，它默认提供了4种常用的线程池应用，而不必我们去重复构造。



- newFixedThreadPool

  

  

  固定线程池，核心线程数和最大线程数固定相等，而空闲存活时间为0毫秒，说明此参数也无意义，工作队列为最大为Integer.MAX_VALUE大小的阻塞队列。当执行任务时，如果线程都很忙，就会丢到工作队列等有空闲线程时再执行，队列满就执行默认的拒绝策略。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXSFvp35yg7UT5iavgNJPfMoXD57FeyAwZn5z16kOsNSazzJnC67dyjpA/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- newCachedThreadPool

​    

​    带缓冲线程池，从构造看核心线程数为0，最大线程数为Integer最大值大小，超过0个的空闲线程在60秒后销毁，SynchronousQueue这是一个直接提交的队列，意味着每个新任务都会有线程来执行，如果线程池有可用线程则执行任务，没有的话就创建一个来执行，线程池中的线程数不确定，一般建议执行速度较快较小的线程，不然这个最大线程池边界过大容易造成内存溢出。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cX8M0mYRVWlvfWIXJCw2gEiasDmMywKBicMQxoibcmVBs35sNP1eXUzm0PQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- newSingleThreadExecutor

​    

​    单线程线程池，核心线程数和最大线程数均为1，空闲线程存活0毫秒同样无意思，意味着每次只执行一个线程，多余的先存储到工作队列，一个一个执行，保证了线程的顺序执行。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXParcIicWAj8Xvcg0RXAzGoiaUEm2mGg4zcpzIrOP0llMG5E6cuKKEv6A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- newScheduledThreadPool

  

  调度线程池，即按一定的周期执行任务，即定时任务，对ThreadPoolExecutor进行了包装而已。

  

![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXycqZicU8BMRHoibcNT7ElxNoa9GhkUosDB8J07icTdDVWAQicrbdjIqYaw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



> **拒绝策略**



- AbortPolicy



   简单粗暴，直接抛出拒绝异常，这也是默认的拒绝策略。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXamDh2oyIzRAicSd0VCvVWwrj4aDbcYCjiaP5MsUsSlMRcaLF8xL4bogw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cX50lqnO7yWXcMiaMLNrWhuE1d8ZDroiaYk5epzQgDm7bo88AHu2d8cptw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- CallerRunsPolicy

  

​    

​    如果线程池未关闭，则会在调用者线程中直接执行新任务，这会导致主线程提交线程性能变慢。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXTAt8uM7tkiatibJIq6bfg5icsSbItxeJBhPww2Tg51icKGOiaImzVNlOP6g/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- DiscardPolicy



​    从方法看没做任务操作，即表示不处理新任务，即丢弃。



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXH427zh2sdpoFmcCog2HVjhqIQHEn3BqtgGcOs4jfkFCib8MAFj67K7A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



- DiscardOldestPolicy



​    抛弃最老的任务，就是从队列取出最老的任务然后放入新的任务进行执行。    



![图片](http://mmbiz.qpic.cn/mmbiz_png/TNUwKhV0JpRoocouwYsS3lwwSpCzq8cXOxU1W74OzqYFn925mxd3TL5aqIKwGiccx17WeeQhF8fnRic9bQWUr1Hw/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)



> **如何提交线程**



如可以先随便定义一个固定大小的线程池

ExecutorService es = Executors.newFixedThreadPool(3);



提交一个线程

es.submit(xxRunnble);

es.execute(xxRunnble);



submit和execute分别有什么区别呢？

execute没有返回值，如果不需要知道线程的结果就使用execute方法，性能会好很多。

submit返回一个Future对象，如果想知道线程结果就使用submit提交，而且它能在主线程中通过Future的get方法捕获线程中的异常。



> **如何关闭线程池**



es.shutdown(); 

不再接受新的任务，之前提交的任务等执行结束再关闭线程池。



es.shutdownNow();

不再接受新的任务，试图停止池中的任务再关闭线程池，返回所有未处理的线程list列表。



**为什么要使用线程池**

​	避免频繁地创建和销毁线程，达到线程对象的重用。另外，使用线程池还可以根据项目灵活地控制并发的数目。点击[这里](https://mp.weixin.qq.com/s?__biz=MzI3ODcxMzQzMw==&mid=2247483824&idx=1&sn=7e34a3944a93d649d78d618cf04e0619&scene=21#wechat_redirect)学习线程池详解。



**怎么检测一个线程是否持有对象监视器**

​	Thread类提供了一个holdsLock(Object obj)方法，当且仅当对象obj的监视器被某条线程持有的时候才会返回true，注意这是一个static方法，这意味着**"某条线程"指的是当前线程**



**synchronized和ReentrantLock的区别**

​	synchronized是和if、else、for、while一样的关键字，ReentrantLock是类，这是二者的本质区别。既然ReentrantLock是类，那么它就提供了比synchronized更多更灵活的特性，可以被继承、可以有方法、可以有各种各样的类变量，ReentrantLock比synchronized的扩展性体现在几点上：

（1）ReentrantLock可以对获取锁的等待时间进行设置，这样就避免了死锁

（2）ReentrantLock可以获取各种锁的信息

（3）ReentrantLock可以灵活地实现多路通知

另外，二者的锁机制其实也是不一样的。ReentrantLock底层调用的是Unsafe的park方法加锁，synchronized操作的应该是对象头中mark word



**ConcurrentHashMap的并发度是什么**

​	ConcurrentHashMap的并发度就是segment的大小，默认为16，这意味着最多同时可以有16条线程操作ConcurrentHashMap，这也是ConcurrentHashMap对Hashtable的最大优势，任何情况下，Hashtable能同时有两条线程获取Hashtable中的数据



**Linux环境下如何查找哪个线程使用CPU最长**

（1）获取项目的pid，jps或者ps -ef | grep java，这个前面有讲过

（2）top -H -p pid，顺序不能改变



**Java编程写一个会导致死锁的程序**

1）两个线程里面分别持有两个Object对象：lock1和lock2。这两个lock作为同步代码块的锁；

2）线程1的run()方法中同步代码块先获取lock1的对象锁，Thread.sleep(xxx)，时间不需要太多，50毫秒差不多了，然后接着获取lock2的对象锁。这么做主要是为了防止线程1启动一下子就连续获得了lock1和lock2两个对象的对象锁

3）线程2的run)(方法中同步代码块先获取lock2的对象锁，接着获取lock1的对象锁，当然这时lock1的对象锁已经被线程1锁持有，线程2肯定是要等待线程1释放lock1的对象锁的

这样，线程1"睡觉"睡完，线程2已经获取了lock2的对象锁了，线程1此时尝试获取lock2的对象锁，便被阻塞，此时一个死锁就形成了



**唤醒一个阻塞的线程**

​	如果线程是因为调用了wait()、sleep()或者join()方法而导致的阻塞，可以中断线程，并且通过抛出InterruptedException来唤醒它；

如果线程遇到了IO阻塞，无能为力，因为IO是操作系统实现的，Java代码并没有办法直接接触到操作系统



**不可变对象对多线程有什么帮助**

不可变对象保证了对象的内存可见性，对不可变对象的读取不需要进行额外的同步手段，提升了代码执行效率。



**什么是多线程的上下文切换**

CPU控制权由一个已经正在运行的线程切换到另外一个就绪并等待获取CPU执行权的线程的过程



**提交任务时，线程池队列已满**

1）如果使用的是无界队列LinkedBlockingQueue，也就是无界队列的话，没关系，继续添加任务到阻塞队列中等待执行，因为LinkedBlockingQueue可以近乎认为是一个无穷大的队列，可以无限存放任务

2）如果使用的是有界队列比如ArrayBlockingQueue，任务首先会被添加到ArrayBlockingQueue中，

ArrayBlockingQueue满了，会根据maximumPoolSize的值增加线程数量，

如果增加了线程数量还是处理不过来，ArrayBlockingQueue继续满，那么则会使用拒绝策略RejectedExecutionHandler处理满了的任务，默认是AbortPolicy



**Java中用到的线程调度算法**

​	抢占式。一个线程用完CPU之后，操作系统会根据线程优先级、线程饥饿情况等数据算出一个总的优先级并分配下一个时间片给某个线程执行。	



**Thread.sleep(0)的作用**

​	很多synchronized里面的代码只是一些很简单的代码，执行时间非常快，此时等待的线程都加锁可能是一种不太值得的操作，因为线程阻塞涉及到用户态和内核态切换的问题。既然synchronized里面的代码执行得非常快，不妨让等待锁的线程不要被阻塞，而是在synchronized的边界做忙循环，这就是自旋。如果做了多次忙循环发现还没有获得锁，再阻塞，这样可能是一种更好的策略。



**守护线程**

守护线程（即daemon thread），是个服务线程，准确地来说就是服务其他的线程。



**notify()和 notifyAll()**

- 如果线程调用了对象的 wait()方法，那么线程便会处于该对象的等待池中，等待池中的线程不会去竞争该对象的锁。
- 当有线程调用了对象的 notifyAll()方法（唤醒所有 wait 线程）或 notify()方法（只随机唤醒一个 wait 线程），被唤醒的的线程便会进入该对象的锁池中，锁池中的线程会去竞争该对象锁。也就是说，调用了notify后只要一个线程会由等待池进入锁池，而notifyAll会将该对象等待池内的所有线程移动到锁池中，等待锁竞争。
- 优先级高的线程竞争到对象锁的概率大，假若某线程没有竞争到该对象锁，它还会留在锁池中，唯有线程再次调用 wait()方法，它才会重新回到等待池中。而竞争到对象锁的线程则继续往下执行，直到执行完了 synchronized 代码块，它会释放掉该对象锁，这时锁池中的线程会继续竞争该对象锁。















