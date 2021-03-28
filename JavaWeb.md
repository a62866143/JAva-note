# JavaWeb

## 测试

### 黑盒测试

​	不需要写代码，给输入值，看程序能否输出期望的值

### 白盒测试

​	需要写代码，关注程序具体的运行流程。

### Junit（白盒）：

1. 定义一个测试类（测试用例）
2. 定义测试方法：可独立运行
3. 给方法加@Test注解
4. 
5. 导入juint环境

判定结果：

红色：失败

绿色：成功

一般会使用断言操作来处理结果

```
Assert.assertEquals(3,result)
//第一个参数 预期的值	//第二个参数 实际的值
//比较两值是否相同
```

在测试中会产生很多相同的步骤，可以提取出来减少资源的消耗

@Before：初始化方法，用于资源申请，所有测试方法在执行之前都会先执行该方法

@After：释放资源方法，用于资源释放，所有测试方法在执行之后都会执行该方法



## Java虚拟机模型（JVM）

<img src="https://img-blog.csdn.net/20170513134212845?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvTFpONTE=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center" alt="img" style="zoom:150%;" />



1 Class Loader（类加载器）就是将Class文件加载到内存，再说的详细一点就是，把描述类的数据从Class文件加载到内存，并对数据进行校验、转换解析和初始化，最终形成可以被虚拟机直接使用的Java类型，这就是类加载器的作用。

2 Run Data Area（运行时数据区） 就是我们常说的JVM管理的内存了，也是我们这里主要讨论的部分。运行数据区是整个JVM的重点。我们所有写的程序都被加载到这里，之后才开始运行。这部分也是我们这里将要讨论的重点。

3 Execution engine（执行引擎） 是Java虚拟机最核心的组成部分之一。执行引擎用于执行指令，不同的java虚拟机内部实现中，执行引擎在执行Java代码的时候可能有解释执行（解释器执行）和编译执行（通过即时编译器产生本地代码执行，例如BEA JRockit），也有可能两者兼备。任何JVM specification实现(JDK)的核心都是Execution engine，不同的JDK例如Sun 的JDK 和IBM的JDK好坏主要就取决于他们各自实现的Execution engine的好坏。

4 Native interface（本机接口） 与native libraries交互，是其它编程语言交互的接口。当调用native方法的时候，就进入了一个全新的并且不再受虚拟机限制的世界，所以也很容易出现JVM无法控制的native heap OutOfMemory。

<img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly91c2VyLWdvbGQtY2RuLnhpdHUuaW8vMjAxOS83LzIyLzE2YzFhNDI2ZWQ5YWI0OGI_aW1hZ2VWaWV3Mi8wL3cvMTI4MC9oLzk2MC9mb3JtYXQvd2VicC9pZ25vcmUtZXJyb3IvMQ?x-oss-process=image/format,png" alt="img" style="zoom: 80%;" />



程序计数器：当前线程所执行的字节码的行号指示器，用于记录正在执行的虚拟机字节指令地址，线程私有。

Java虚拟栈：存放基本数据类型、对象的引用、方法出口等，线程私有。

Native方法栈：和虚拟栈相似，只不过它服务于Native方法，线程私有。

Java堆：java内存最大的一块，所有对象实例、数组都存放在java堆，GC回收的地方，线程共享。

方法区：存放已被加载的类信息、常量、静态变量、即时编译器编译后的代码数据等。（即永久带），回收目标主要是常量池的回收和类型的卸载，各线程共享



| 数据                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| Program Counter Register | 程序计数器，线程私有、指向下一条要执行的指令                 |
| Java Stack               | Java虚拟机栈，线程私有，生命周期与线程相同。描述的是Java方法执行的内存模型：每个方法被执行的时候都会同时创建一个栈帧（Stack Frame）用于存储局部变量表、操作栈、动态链接、方法出口 |
| Native Method Stack      | 为虚拟机使用到的Native 方法服务                              |
| Heap、（java堆）         | 堆内存，线程共享，由于现在收集器基本采用的分代收集算法，所以Java堆中还可以细分：新生代和老生代；更细致一点的有Eden空间、From Survivor空间、To Survivor空间等。所有的对象实例以及数组都要在堆上分配，是垃圾收集器管理的主要区域 |
| Method Area              | 方法区，别名叫做非堆(Non-Heap)，线程共享的内存区域。目的是与Java堆区分开来，存储类信息、常量、静态变量、即时编译器编译后的代码。 方法区存放的信息包括： **A 类的基本信息：** 1.每个类的全限定名 2.每个类的直接超类的全限定名(可约束类型转换) 3.该类是类还是接口 4.该类型的访问修饰符 5.直接超接口的全限定名的有序列表 **B 已装载类的详细信息** 1.运行时常量池：在方法区中，每个类型都对应一个常量池，存放该类型所用到的所有常量，常量池中存储了诸如文字字符串、final变量值、类名和方法名常量。它们以数组形式通过索引被访 问，是外部调用与类联系及类型对象化的桥梁。（存的可能是个普通的字符串，然后经过常量池解析，则变成指向某个类的引用） 2.字段信息：字段信息存放类中声明的每一个字段的信息，包括字段的名、类型、修饰符。字段名称指的是类或接口的实例变量或类变量，字段的描述符是一个指示字段的类型的字符串，如private A a=null;则a为字段名，A为描述符，private为修饰符。 3.方法信息：类中声明的每一个方法的信息，包括方法名、返回值类型、参数类型、修饰符、异常、方法的字节码。(在编译的时候，就已经将方法的局部变量、操作数栈大小等确定并存放在字节码中，在装载的时候，随着类一起装入方法区。) 4.静态变量：就是类变量，类的所有实例都共享，我们只需知道，在方法区有个静态区，静态区专门存放静态变量和静态块。 5.到类classloader的引用：到该类的类装载器的引用。 6.到类class 的引用：jvm为每个加载的类型(译者：包括类和接口)都创建一个java.lang.Class的实例。而jvm必须以某种方式把Class的这个实例和存储在方法区中的类型数据联系起来。 |



JVM内存模型中包括：

- 程序计数器(PC)
- java虚拟机栈
- 本地方法栈
- java堆
- 方法区

##### 程序计数器(PC)

> 程序计数器是一块很小的内存空间，用于记录下一条要运行的指令。每个线程都需要一个程序计数器，各个线程之中的计数器相互独立，是线程中私有的内存空间

##### java虚拟机栈

> java虚拟机栈也是线程私有的内存空间，它和java线程同一时间创建，保存了局部变量、部分结果，并参与方法的调用和返回

##### 本地方法栈

> 本地方法栈和java虚拟机栈的功能相似，java虚拟机栈用于管理**Java函数**的调用，而本地方法栈用于管理本地方法的调用，但不是由Java实现的，而是由C实现的

##### java堆（堆内存）

> 为所有创建的对象和数组分配**内存空间**,被JVM中所有的线程共享

堆内存版本区别：

1.7版本中的永久区替换成了1.8的Metaspace（元数据空间）进行了替换

需要特别说明的是：Metaspace所占用的内存空间不是在虚拟机内部，而是在本地内存空间中，这也是与1.7的永 久代大的区别所在。

什么要废弃1.7中的永久区？

现实使用中，由于永久代内存经常不够用或发生内存泄露，爆出异常java.lang.OutOfMemoryError: PermGen。
基于此，将永久区废弃，而改用元空间，改为了使用本地内存空间

##### 方法区

> 也被称为永久区，与堆空间相似，被JVM中所有的线程共享。方法区主要保存的信息是类的元数据，方法区中最为重要的是类的类型信息、常量池、域信息、方法信息，**其中运行时常量池就在方法区**，对永久区的GC回收，一是GC对永久区常量池的回收;二是永久区对元数据的回收



**JVM内存为什么要分成新生代，老年代，持久代。新生代中为什么要分为Eden和Survivor**

**思路：** 先讲一下JAVA堆，新生代的划分，再谈谈它们之间的转化，相互之间一些参数的配置（如： –XX:NewRatio，–XX:SurvivorRatio等），再解释为什么要这样划分，最好加一点自己的理解

1）共享内存区划分

- 共享内存区 = 持久带 + 堆
- 持久带 = 方法区 + 其他
- Java堆 = 老年代 + 新生代
- 新生代 = Eden + S0 + S1

2）一些参数的配置

- 默认的，新生代 ( Young ) 与老年代 ( Old ) 的比例的值为 1:2 ，可以通过参数 –XX:NewRatio 配置。
- 默认的，Edem : from : to = 8 : 1 : 1 ( 可以通过参数 –XX:SurvivorRatio 来设定)
- Survivor区中的对象被复制次数为15(对应虚拟机参数 -XX:+MaxTenuringThreshold)

3)为什么要分为Eden和Survivor?为什么要设置两个Survivor区？

- 如果没有Survivor，Eden区每进行一次Minor GC，存活的对象就会被送到老年代。老年代很快被填满，触发Major GC.老年代的内存空间远大于新生代，进行一次Full GC消耗的时间比Minor GC长得多,所以需要分为Eden和Survivor。
- Survivor的存在意义，就是**减少被送到老年代的对象，进而减少Full GC的发生**，Survivor的预筛选保证，只有经历16次Minor GC还能在新生代中存活的对象，才会被送到老年代。
- 设置两个Survivor区最大的好处就是解决了碎片化，刚刚新建的对象在Eden中，经历一次Minor GC，Eden中的存活对象就会被移动到第一块survivor space S0，Eden被清空；等Eden区再满了，就再触发一次Minor GC，Eden和S0中的存活对象又会被复制送入第二块survivor space S1（这个过程非常重要，因为这种复制算法**保证了S1中来自S0和Eden两部分的存活对象占用连续的内存空间**，避免了碎片化的发生）



**JVM中一次完整的GC流程是怎样的，对象如何晋升到老年代**

**思路：** 先描述一下Java堆内存划分，再解释Minor GC，Major GC，full GC，描述它们之间转化流程。

**我的答案：**

- Java堆 = 老年代 + 新生代
- 新生代 = Eden + S0 + S1
- 当 Eden 区的空间满了， Java虚拟机会触发一次 Minor GC，以收集新生代的垃圾，存活下来的对象，则会转移到 Survivor区。
- **大对象**（需要大量连续内存空间的Java对象，如那种很长的字符串）**直接进入老年态**；
- 如果对象在Eden出生，并经过第一次Minor GC后仍然存活，并且被Survivor容纳的话，年龄设为1，每熬过一次Minor GC，年龄+1，**若年龄超过一定限制（15），则被晋升到老年态**。即**长期存活的对象进入老年态**。
- 老年代满了而**无法容纳更多的对象**，Minor GC 之后通常就会进行Full GC，Full GC 清理整个内存堆 – **包括年轻代和年老代**。
- Major GC **发生在老年代的GC**，**清理老年区**，经常会伴随至少一次Minor GC，**比Minor GC慢10倍以上**。

老年代与新生代不同，老年代对象存活的时间比较长、比较稳定，因此采用标记(Mark)算法来进行回收，所谓标记就是扫描出存活的对象，然后再进行回收未被标记的对象，回收后对用空出的空间要么进行合并、要么标记出来便于下次进行分配，总之目的就是要减少内存碎片带来的效率损耗



GC判断对象是否"存活"或"死去"（GC回收的对象）：

1.引用计数器算法

给对象中添加一个引用计数器，每当有一个地方引用它时，计数器的值加1；当引用失效时，计数器的值减；当该对象的计数器的值为0时，标志该对象失效。

2.跟搜索算法

基本思路：通过一系列的名为“GCRoots”的对象作为起始点，从这些节点开始向下搜索，搜索过的路径称为引用链，当一个对象到GCRoots没有任何引用链相连（用图论的话来说就是从GC Roots到这个对象不可达）时，则证明对象是不可用的。







**你知道哪几种垃圾收集器，各自的优缺点，重点讲下cms和G1，包括原理，流程，优缺点**

**思路：** 一定要记住典型的垃圾收集器，尤其cms和G1，它们的原理与区别，涉及的垃圾回收算法。

1）几种垃圾收集器：

- **Serial收集器：** 新生代，单线程的收集器，收集垃圾时，必须stop the world，使用**复制算法**。
- **ParNew收集器：** Serial收集器的多线程版本，也需要stop the world，**复制算法**。
- **Parallel Scavenge收集器：** 新生代收集器，复制算法的收集器，并发的多线程收集器，目标是达到一个可控的吞吐量。如果虚拟机总共运行100分钟，其中垃圾花掉1分钟，吞吐量就是99%。
- **Serial Old收集器：** 是Serial收集器的老年代版本，单线程收集器，使用**标记整理算法**。
- **Parallel Old收集器：** 是Parallel Scavenge收集器的老年代版本，使用多线程，**标记-整理算法**。
- **CMS(Concurrent Mark Sweep) 收集器：** 是一种以获得最短回收停顿时间为目标的收集器，**老年代的收集器**标记清除算法**，运作过程：**初始**标记，**并发**标记，**重新标记**，**并发清除，收集结束会产生大量空间碎片。
- **G1收集器：** **标记整理算法**实现，**运作流程主要包括以下：初始标记，并发标记，最终标记，筛选标记**。不会产生空间碎片，可以精确地控制停顿。

2）CMS收集器和G1收集器的区别：

- CMS收集器是**老年代**的收集器，**可以配合**新生代的Serial和ParNew收集器一起使用；
- G1收集器收集范围是**老年代和新生代**，**不需要结合其他**收集器使用；
- CMS收集器**以最小的停顿时间**为**目标**的收集器；
- G1收集器**可预测**垃圾回收的**停顿时间**
- CMS收集器是使用“标记-清除”算法进行的垃圾回收，**容易产生内存碎片**
- G1收集器使用的是“标记-整理”算法，进行了**空间整合**，降低了内存空间碎片。



### JVM类加载过程

1.概述

从类的生命周期而言，一个类包括如下阶段：

![img](https://img-blog.csdnimg.cn/2019062014564165.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3poYW9jdWl0,size_16,color_FFFFFF,t_70)

​    

​    加载、验证、准备、初始化和卸载这5个阶段的顺序是确定的，类的加载过程必须按照这种顺序进行，而解析阶段则不一定，它在某些情况下可能在初始化阶段后在开始，因为java支持运行时绑定。

2. 类加载时机

加载（loading）阶段，java虚拟机规范中没有进行约束，但初始化阶段，java虚拟机严格规定了有且只有如下5种情况必须立即进行初始化（初始化前，必须经过加载、验证、准备阶段）：

（1）使用new实例化对象时，读取和设置类的静态变量、静态非字面值常量（静态字面值常量除外）时，调用静态方法时。

（2）对内进行反射调用时。

（3）当初始化一个类时，如果父类没有进行初始化，需要先初始化父类。

（4）启动程序所使用的main方法所在类

（5）当使用1.7的动态语音支持时。

如上5种场景又被称为主动引用，除此之外的引用称为被动引用，被动引用有如下3种常见情况

通过子类引用父类的静态字段，只会触发父类的初始化，而不会触发子类的初始化。
定义对象数组和集合，不会触发该类的初始化
类A引用类B的static final常量不会导致类B初始化（注意静态常量必须是字面值常量，否则还是会触发B的初始化）

```
public class TestClass {
    public static void main(String[] args) {
        System.out.println(ClassInit.str);
        System.out.println(ClassInit.id);
    }
}
class ClassInit{
    public static final long id=IdGenerator.getIdWorker().nextId();//需要初始化ClassInit类
    public static final String str="abc";//字面值常量
    static{
        System.out.println("ClassInit init");
    }
}
```

通过类名获取Class对象，不会触发类的初始化。如System.out.println(Person.class);
通过Class.forName加载指定类时，如果指定参数initialize为false时，也不会触发类初始化。
通过ClassLoader默认的loadClass方法，也不会触发初始化动作
    注意：被动引用不会导致类初始化，但不代表类不会经历加载、验证、准备阶段。

通过类名获取Class对象，不会触发类的初始化。如System.out.println(Person.class);
通过Class.forName加载指定类时，如果指定参数initialize为false时，也不会触发类初始化。
通过ClassLoader默认的loadClass方法，也不会触发初始化动作
    注意：被动引用不会导致类初始化，但不代表类不会经历加载、验证、准备阶段。

    3. 类加载方式
    
    这里的类加载不是指类加载阶段，而是指整个类加载过程，即类加载阶段到初始化完成。

   （1）隐式加载

创建类对象
使用类的静态域
创建子类对象
使用子类的静态域
在JVM启动时，BootStrapLoader会加载一些JVM自身运行所需的class
在JVM启动时，ExtClassLoader会加载指定目录下一些特殊的class
在JVM启动时，AppClassLoader会加载classpath路径下的class，以及main函数所在的类的class文件
    （2）显式加载

ClassLoader.loadClass(className)，只加载和连接、不会进行初始化
Class.forName(String name, boolean initialize,ClassLoader loader); 使用loader进行加载和连接，根据参数initialize决定是否初始化。
2. 加载阶段
    加载是类加载过程中的一个阶段，不要将这2个概念混淆了。

    在加载阶段，虚拟机需要完成以下3件事情：

通过一个类的全限定名来获取定义此类的二进制字节流
将这个字节流所代表的静态存储结构转化为方法区的运行时数据结构。
在内存中生成一个代表这个类的java.lang.Class对象，作为方法区这个类的各种数据的访问入口。
    加载.class文件的方式

从本地系统中直接加载
通过网络下载.class文件
从zip，jar等归档文件中加载.class文件
从专有数据库中提取.class文件
将Java源文件动态编译为.class文件    
    相对于类生命周期的其他阶段而言，加载阶段（准确地说，是加载阶段获取类的二进制字节流的动作）是可控性最强的阶段，因为开发人员既可以使用系统提供的类加载器来完成加载，也可以自定义自己的类加载器来完成加载。

3. 连接阶段
    3.1 验证：确保被加载的类的正确性

    确保Class文件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机自身的安全。

文件格式验证：验证字节流是否符合Class文件格式的规范，如：是否以模数0xCAFEBABE开头、主次版本号是否在当前虚拟机处理范围内等等。
元数据验证：对字节码描述的信息进行语义分析，以保证其描述的信息符合Java语言规范的要求；如：这个类是否有父类，是否实现了父类的抽象方法，是否重写了父类的final方法，是否继承了被final修饰的类等等。
字节码验证：通过数据流和控制流分析，确定程序语义是合法的、符合逻辑的，如：操作数栈的数据类型与指令代码序列能配合工作，保证方法中的类型转换有效等等。
符号引用验证：确保解析动作能正确执行；如：通过符合引用能找到对应的类和方法，符号引用中类、属性、方法的访问性是否能被当前类访问等等。
    验证阶段是非常重要的，但不是必须的。可以采用-Xverify:none参数来关闭大部分的类验证措施。

  3.2 准备：为类的静态变量分配内存，并将其赋默认值

    为类变量分配内存并设置类变量初始值，这些内存都将在方法区中分配。对于该阶段有以下几点需要注意：

只对static修饰的静态变量进行内存分配、赋默认值（如0、0L、null、false等）。
对final的静态字面值常量直接赋初值（赋初值不是赋默认值，如果不是字面值静态常量，那么会和静态变量一样赋默认值）。
  3.3 解析：将常量池中的符号引用替换为直接引用（内存地址）的过程

    符号引用就是一组符号来描述目标，可以是任何字面量。属于编译原理方面的概念如：包括类和接口的全限定名、字段的名称和描述符、方法的名称和描述符。
    
    直接引用就是直接指向目标的指针、相对偏移量或一个间接定位到目标的句柄。如指向方法区某个类的一个指针。
    
    假设：一个类有一个静态变量，该静态变量是一个自定义的类型，那么经过解析后，该静态变量将是一个指针，指向该类在方法区的内存地址。 具体见后续文章。

4. 初始化：为类的静态变量赋初值
    赋初值两种方式：

定义静态变量时指定初始值。如 private static String x="123";
在静态代码块里为静态变量赋值。如 static{ x="123"; } 
    注意：只有对类的主动使用才会导致类的初始化。

5. clinit 与 init
    在编译生成class文件时，编译器会产生两个方法加于class文件中，一个是类的初始化方法clinit, 另一个是实例的初始化方法init。

  5.1 clinit 

clinit指的是类构造器，主要作用是在类加载过程中的初始化阶段进行执行，执行内容包括静态变量初始化和静态块的执行。

注意事项：

1. 如果类中没有静态变量或静态代码块，那么clinit方法将不会被生成。

2. 在执行clinit方法时，必须先执行父类的clinit方法。

3. clinit方法只执行一次。

3. static变量的赋值操作和静态代码块的合并顺序由源文件中出现的顺序决定。如下代码所示：

```
public class TestClass {
    public static void main(String[] args) {
        ClassInit init=ClassInit.newInstance();

        System.out.println(init.x);
        System.out.println(init.y);
    }

}

class ClassInit{
    private static ClassInit init=new ClassInit();
    public static int x;
    public static int y=0;
    static{
        x=10;
        y=10;
    }
    private ClassInit(){
        x++;
        y++;
    }
    public static ClassInit newInstance(){
        return init;
    }
}
//在类加载到连接完成阶段，ClassInit类在内存中的状态为：init=null,x=0,y=0
//初始化阶段时，需要执行clinit方法，该方法类似如下伪代码：
clinit(){
	//init=new ClassInit();调用构造方法
    x++;//x=1 因为此时x的值为连接的准备阶段赋的默认值0，然后++变成1
    y++;//y=1 因为此时y的值为连接的准备阶段赋的默认值0，然后++变成1
    //x=0;//为什么这里没有执行x=0，因为程序没有给x赋初值，因此在初始化阶段时，不会执行赋初值操作
    y=0;//因为类变量y在定义时，指定了初值，尽管初值为0，因此在初始化阶段的时候，需要执行赋初值操作
    x++;//第一个静态块的自增操作，结果为x=2;
    y++;//第一个静态块的自增操作，结果为y=1;
}
//所以最终结果为x=2,y=1
//如果private static ClassInit init=new ClassInit(); 代码在public static int y=0;后面，那么clinit方法的伪代码如下：
clinit(){
    //x=0;//这里虽然没有执行，但此时x的值为连接的准备阶段赋的默认值0
    y=0;//因为类变量y在定义时，指定了初值，尽管初值为0，因此在初始化阶段的时候，需要执行赋初值操作
	//init=new ClassInit();调用构造方法
    x++;//x=1 因为此时x的值为连接的准备阶段赋的默认值0，然后++变成1
    y++;//y=1 因为此时y的值为初始化阶段赋的初值，只是这个初值刚好等于默认值0而已，然后++变成1
    x++;//第一个静态块的自增操作，结果为x=2;
    y++;//第一个静态块的自增操作，结果为y=2;
}
//最终结果为x=2,y=2
```


​    5.2 init

init指的是实例构造器，主要作用是在类实例化过程中执行，执行内容包括成员变量初始化和代码块的执行。

注意事项：

1. 如果类中没有成员变量和代码块，那么clinit方法将不会被生成。

2. 在执行init方法时，必须先执行父类的init方法。

3. init方法每实例化一次就会执行一次。

3. init方法先为实例变量分配内存空间，再执行赋默认值，然后根据源码中的顺序执行赋初值或代码块。如下代码所示：

```
public class TestClass {
    public static void main(String[] args) {
        ClassInit init=new ClassInit();
    }
}

class ClassInit{
    public int x;
    public int y=111;
    public ClassInit(){
        x=1;
        y=1;
    }
    {
        x=2;
        y=2;
    }
    {
        x=3;
        y=3;
    }
}
//实例化步骤为：先为属性分配空间，再执行赋默认值，然后按照顺序执行代码块或赋初始值，最后执行构造方法
//根据上述代码，init方法的伪代码如下：
init(){
	x=0;//赋默认值
    y=0;//赋默认值
    y=111;//赋初值
    x=2;//从上到下执行第一个代码块
    y=2;//从上到下执行第一个代码块
    x=3;//从上到下执行第二个代码块
    y=3;//从上到下执行第二个代码块
    //ClassInit();执行构造方法
    x=1;//最后执行构造方法
    y=1;//最后执行构造方法
}
//如果上述代码的成员变量x,y的定义在类最后时，那么init方法的伪代码如下：
init(){
	x=0;//赋默认值
    y=0;//赋默认值
    x=2;//从上到下执行第一个代码块
    y=2;//从上到下执行第一个代码块
    x=3;//从上到下执行第二个代码块
    y=3;//从上到下执行第二个代码块
    y=111;//赋初值
    //ClassInit();执行构造方法
    x=1;//最后执行构造方法
    y=1;//最后执行构造方法
}
```


6. 卸载阶段
   

执行了System.exit()方法
    
程序正常执行结束
    
程序在执行过程中遇到了异常或错误而异常终止
    
由于操作系统出现错误而导致Java虚拟机进程终止




## **JVM内存调优**

![img](https://pic2.zhimg.com/80/v2-c256a1d88bd0a626a4583778d2c13bc9_720w.jpg)



**对JVM内存的系统级的调优主要的目的是减少GC的频率和Full GC的次数。**

**1.Full GC**

会对整个堆进行整理，包括Young、Tenured和Perm。Full GC因为需要对整个堆进行回收，所以比较慢，因此应该**尽可能减少**Full GC的次数。

**2.导致Full GC的原因**

**1)\*年老代（Tenured）被写满\***

调优时尽量让对象在新生代GC时被回收、让对象在新生代多存活一段时间和不要创建过大的对象及数组避免直接在旧生代创建对象 。

**2)持久代Pemanet Generation空间不足**

增大Perm Gen空间，避免太多静态对象 ， 控制好新生代和旧生代的比例

**3)System.gc()被显示调用**

垃圾回收不要手动触发，尽量依靠JVM自身的机制

**在对JVM调优的过程中，很大一部分工作就是对于FullGC的调节，下面详细介绍对应JVM调优的方法和步骤。**



## **二、JVM性能调优方法和步骤** 

![img](https://pic1.zhimg.com/80/v2-5e1966122f124e4034a4c4f281cf7458_720w.jpg)



**1.监控GC的状态**

使用各种JVM工具，查看当前日志，分析当前JVM参数设置，并且分析当前堆内存快照和gc日志，根据实际的各区域内存划分和GC执行时间，觉得是否进行优化。

**举一个例子： 系统崩溃前的一些现象：**

- 每次垃圾回收的时间越来越长，由之前的10ms延长到50ms左右，FullGC的时间也有之前的0.5s延长到4、5s
- FullGC的次数越来越多，最频繁时隔不到1分钟就进行一次FullGC
- 年老代的内存越来越大并且每次FullGC后年老代没有内存被释放

之后系统会无法响应新的请求，逐渐到达OutOfMemoryError的临界值，这个时候就需要分析JVM内存快照dump。

**2.生成堆的dump文件**

通过JMX的MBean生成当前的Heap信息，大小为一个3G（整个堆的大小）的hprof文件，如果没有启动JMX可以通过Java的jmap命令来生成该文件。

**3.分析dump文件**

打开这个3G的堆信息文件，显然一般的Window系统没有这么大的内存，必须借助高配置的Linux，几种工具打开该文件：

- Visual VM
- IBM HeapAnalyzer
- JDK 自带的Hprof工具
- **Mat(Eclipse专门的静态内存分析工具)推荐使用**

备注：文件太大，建议使用Eclipse专门的静态内存分析工具Mat打开分析。

**4.分析结果，判断是否需要优化**

如果各项参数设置合理，系统没有超时日志出现，GC频率不高，GC耗时不高，那么没有必要进行GC优化，如果GC时间超过1-3秒，或者频繁GC，则必须优化。

**注：如果满足下面的指标，则一般不需要进行GC：**

- Minor GC执行时间不到50ms；
- Minor GC执行不频繁，约10秒一次；
- Full GC执行时间不到1s；
- Full GC执行频率不算频繁，不低于10分钟1次；

**5.调整GC类型和内存分配**

如果内存分配过大或过小，或者采用的GC收集器比较慢，则应该优先调整这些参数，并且先找1台或几台机器进行beta，然后比较优化过的机器和没有优化的机器的性能对比，并有针对性的做出最后选择。

**6.不断的分析和调整**

通过不断的试验和试错，分析并找到最合适的参数，如果找到了最合适的参数，则将这些**参数应用到所有服务器。**



![img](https://pic3.zhimg.com/80/v2-1acebd36d4d6777d87e594c1572c11ba_720w.jpg)


cms参数优化步流程





## JVM调优参数参考 

1.针对JVM堆的设置，一般可以通过-Xms -Xmx限定其最小、最大值，**为了防止垃圾收集器在最小、最大之间收缩堆而产生额外的时间，通常把最大、最小设置为相同的值;**

**2.年轻代和年老代将根据默认的比例（1：2）分配堆内存**， 可以通过调整二者之间的比率NewRadio来调整二者之间的大小，也可以针对回收代。

比如年轻代，通过 -XX:newSize -XX:MaxNewSize来设置其绝对大小。同样，为了防止年轻代的堆收缩，我们通常会把-XX:newSize -XX:MaxNewSize设置为同样大小。

3.年轻代和年老代设置多大才算合理

**1）更大的年轻代必然导致更小的年老代，大的年轻代会延长普通GC的周期，但会增加每次GC的时间；小的年老代会导致更频繁的Full GC**

**2）更小的年轻代必然导致更大年老代，小的年轻代会导致普通GC很频繁，但每次的GC时间会更短；大的年老代会减少Full GC的频率**

如何选择应该依赖应用程序**对象生命周期的分布情况**： 如果应用存在大量的临时对象，应该选择更大的年轻代；如果存在相对较多的持久对象，年老代应该适当增大。但很多应用都没有这样明显的特性。

**在抉择时应该根 据以下两点：**

（1）本着Full GC尽量少的原则，让年老代尽量缓存常用对象，JVM的默认比例1：2也是这个道理 。

（2）通过观察应用一段时间，看其他在峰值时年老代会占多少内存，在不影响Full GC的前提下，根据实际情况加大年轻代，比如可以把比例控制在1：1。但应该给年老代至少预留1/3的增长空间。

**4.在配置较好的机器上（比如多核、大内存），可以为年老代选择并行收集算法**： **-XX:+UseParallelOldGC** **。**

**5.线程堆栈的设置**：每个线程默认会开启1M的堆栈，用于存放栈帧、调用参数、局部变量等，对大多数应用而言这个默认值太了，一般256K就足用。

理论上，在内存不变的情况下，减少每个线程的堆栈，可以产生更多的线程，但这实际上还受限于操作系统。



**Java内存模型的相关知识了解多少，比如重排序，内存屏障，happen-before，主内存，工作内存**

<img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly91c2VyLWdvbGQtY2RuLnhpdHUuaW8vMjAxOS83LzIzLzE2YzFjMTk4MmUzNjA5YjE_aW1hZ2VWaWV3Mi8wL3cvMTI4MC9oLzk2MC9mb3JtYXQvd2VicC9pZ25vcmUtZXJyb3IvMQ?x-oss-process=image/format,png" alt="img" style="zoom:67%;" />

Java内存模型规定了所有的**变量都存储在主内存**中，每条**线程还有自己的工作内存**，线程的工作内存中保存了该线程中是用到的变量的主内存副本拷贝，**线程对变量的所有操作都必须在工作内存中**进行，**而不能直接读写主内存**。不同的线程之间也**无法直接访问对方工作内存中的变量**，线程间变量的传递均需要自己的工作内存和主存之间进行数据同步进行



3）内存屏障

**内存屏障**，也叫内存栅栏，是一种CPU指令，用于控制特定条件下的重排序和内存可见性问题。

- **LoadLoad屏障**：对于这样的语句Load1; LoadLoad; Load2，在Load2及后续读取操作要读取的数据被访问前，保证Load1要读取的数据被读取完毕。
- **StoreStore屏障**：对于这样的语句Store1; StoreStore; Store2，在Store2及后续写入操作执行前，保证Store1的写入操作对其它处理器可见。
- **LoadStore屏障**：对于这样的语句Load1; LoadStore; Store2，在Store2及后续写入操作被刷出前，保证Load1要读取的数据被读取完毕。
- **StoreLoad屏障**：对于这样的语句Store1; StoreLoad; Load2，在Load2及后续所有读取操作执行前，保证Store1的写入对所有处理器可见。它的开销是四种屏障中最大的。 在大多数处理器的实现中，这个屏障是个万能屏障，兼具其它三种内存屏障的功能。

4）happen-before原则

- **单线程happen-before原则**：在同一个线程中，书写在前面的操作happen-before后面的操作。 锁的happen-before原则：同一个锁的unlock操作happen-before此锁的lock操作。
- **volatile的happen-before原则**：对一个volatile变量的写操作happen-before对此变量的任意操作(当然也包括写操作了)。
- **happen-before的传递性原则**：如果A操作 happen-before B操作，B操作happen-before C操作，那么A操作happen-before C操作。
- **线程启动的happen-before原则**：同一个线程的start方法happen-before此线程的其它方法。
- **线程中断的happen-before原则** ：对线程interrupt方法的调用happen-before被中断线程的检测到中断发送的代码。
- **线程终结的happen-before原则：** 线程中的所有操作都happen-before线程的终止检测。
- **对象创建的happen-before原则：** 一个对象的初始化完成先于他的finalize方法调用。



### 四大引用

#### 强引用

强引用就是我们平时使用的对象方式，也是使用最多的一种方式，请记住不管内存紧张也罢，不足也罢，**gc永不回收强引用的对象**， 即使jvm 出现(内存溢出错误)OutOfMemoryError，使程序停止，也不会回收对象来提高内存代码

```
Object object=new Object();
```



```
public class StrongReferenceDemo {
public static void main(String[] args) {
Integer data = new Integer(4);
String str = "123";Student student = new Student();
//以上三个对象都是强引用对象，指我们平时使用的对象方式
	}
}
class Student {

}
```

#### 软引用

对象具备软引用，请记住，**只要内存足够，我们不对对象回收，但是当内存不足， gc对软引用对象进行回收** 可以看出软引用对内存很敏感，可用来高速缓存，同时它可以结合队列使用，如果软引用被gc回收，jvm就会把软引用加入到队列中。



```
Object object=new Object();
SoftReference<String> soft = new SoftReference<String>(object);
Object result=softReference.get();
```

代码

```
public class Demo {
public static void main(String[] args) {
String ss = "hello";
//这时"hello"有一个强引用， 还有一个软引用
//泛型指的是软引用指向的类型
//软引用是内存不足时，对象被回收
SoftReference<String> soft = new SoftReference<String>(ss);
//获取软引用的对象
String content = soft.get(); 
System.out.println(content);ss = null; 
//强引用没有了，这时只有软引用指向"hello"System.gc(); 
//强制回收System.gc();
System.gc();content = soft.get();
//看看有没有被回收
	}
}
```

#### 弱引用

**gc内存是发现弱引用，就会立刻回收弱引用对象**，但是我们知道gc是一个优先级很低的线程，所以不一定立刻发现并回收弱引用对象，但记住，只要被gc发现弱引用，不管内存够不够，直接回收，同时，弱引用，也可以结合队列使用，当被回收，就进去于之关联的队列中

```
Object object=new Object();
WeakReference<String> weakReference = new WeakReference<String>(object);
Object result=weakReference.get();
```

代码

```
public class WeakReference {
public static void main(String[] args) { 
String ss = "hello";
ReferenceQueue<String> queue = new ReferenceQueue<>(); 

java.lang.ref.WeakReference<String> weak = newjava.lang.ref.WeakReference<String>(ss,queue); 
System.out.println("现在的引用 " + weak.get()); ss = null;System.gc();
//gcReference<? extends String> poll = queue.poll();
//如果null，说明被回收了if(poll != null) {String content = poll.get(); System.out.println(content);}
//看看有没有被回收
	}
}
```

#### 虚引用

虚引用和前面的软引用、弱引用不同，**它并不影响对象的生命周期**。在java中用java.lang.ref.PhantomReference类表示。如果一个对象与虚引用关联，则跟没有引用与之关联一样，**在任何时候都可能被垃圾回收器回收**。

要注意的是，虚引用必须和引用队列关联使用，当垃圾回收器准备回收一个对象 时，如果发现它还有虚引用，就会把这个虚引用加入到与之 关联的引用队列中。程序可以通过判断引用队列中是否已经加入了虚引用，来了解被引用的对象是否将要被垃圾回 收。如果程序发现某个虚引用已经被加入到引用队列，那么就可以在所引用的对象的内存被回收之前采取必要的行动。

```
Object object=new Object();
ReferenceQueue queue = new ReferenceQueue();
PhantomReference pr = new PhantomReference(object, queue);
```



```
import java.lang.ref.PhantomReference; 
import java.lang.ref.ReferenceQueue; 
public class Main {

public static void main(String[] args) {

ReferenceQueue<String> queue = new ReferenceQueue<String>(); 
PhantomReference<String> pr = new PhantomReference<String>(new String("hello"), queue);

System.out.println(pr.get());

	}

}
```



### 简单说说你了解的类加载器，可以打破双亲委派么，怎么打破。

**思路：** 先说明一下什么是类加载器，可以给面试官画个图，再说一下类加载器存在的意义，说一下双亲委派模型，最后阐述怎么打破双亲委派模型。

**我的答案：**

1) 什么是类加载器？

**类加载器** 就是根据指定全限定名称将class文件加载到JVM内存，转为Class对象。

> - 启动类加载器（Bootstrap ClassLoader）：由C++语言实现（针对HotSpot）,负责将存放在<JAVA_HOME>\lib目录或-Xbootclasspath参数指定的路径中的类库加载到内存中。
> - 其他类加载器：由Java语言实现，继承自抽象类ClassLoader。如：
>
> > - 扩展类加载器（Extension ClassLoader）：负责加载<JAVA_HOME>\lib\ext目录或java.ext.dirs系统变量指定的路径中的所有类库。
> > - 应用程序类加载器（Application ClassLoader）。负责加载用户类路径（classpath）上的指定类库，我们可以直接使用这个类加载器。一般情况，如果我们没有自定义类加载器默认就是用这个加载器。

2）双亲委派模型

**双亲委派模型工作过程是：**

> 如果一个类加载器收到类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器完成。每个类加载器都是如此，只有当父加载器在自己的搜索范围内找不到指定的类时（即ClassNotFoundException），子加载器才会尝试自己去加载。

双亲委派模型图：

<img src="https://imgconvert.csdnimg.cn/aHR0cHM6Ly91c2VyLWdvbGQtY2RuLnhpdHUuaW8vMjAxOS83LzIzLzE2YzFjNTRjZjRhZDg4NmI_aW1hZ2VWaWV3Mi8wL3cvMTI4MC9oLzk2MC9mb3JtYXQvd2VicC9pZ25vcmUtZXJyb3IvMQ?x-oss-process=image/format,png" alt="img" style="zoom:80%;" />

 

3）为什么需要双亲委派模型？

在这里，先想一下，如果没有双亲委派，那么用户是不是可以**自己定义一个java.lang.Object的同名类**，**java.lang.String的同名类**，并把它放到ClassPath中,那么**类之间的比较结果及类的唯一性将无法保证**，因此，为什么需要双亲委派模型？**防止内存中出现多份同样的字节码**

4）怎么打破双亲委派模型？

打破双亲委派机制则不仅**要继承ClassLoader**类，还要**重写loadClass和findClass**方法。



### JVM参数

1）堆栈配置相关

```java
java -Xmx3550m -Xms3550m -Xmn2g -Xss128k 



-XX:MaxPermSize=16m -XX:NewRatio=4 -XX:SurvivorRatio=4 -XX:MaxTenuringThreshold=0
```

**-Xmx3550m：** 最大堆大小为3550m。

**-Xms3550m：** 设置初始堆大小为3550m。

**-Xmn2g：** 设置年轻代大小为2g。

**-Xss128k：** 每个线程的堆栈大小为128k。

**-XX:MaxPermSize：** 设置持久代大小为16m

**-XX:NewRatio=4:** 设置年轻代（包括Eden和两个Survivor区）与年老代的比值（除去持久代）。

**-XX:SurvivorRatio=4：** 设置年轻代中Eden区与Survivor区的大小比值。设置为4，则两个Survivor区与一个Eden区的比值为2:4，一个Survivor区占整个年轻代的1/6

**-XX:MaxTenuringThreshold=0：** 设置垃圾最大年龄。如果设置为0的话，则年轻代对象不经过Survivor区，直接进入年老代。

2）垃圾收集器相关

```java
-XX:+UseParallelGC
-XX:ParallelGCThreads=20
-XX:+UseConcMarkSweepGC 
-XX:CMSFullGCsBeforeCompaction=5
-XX:+UseCMSCompactAtFullCollection：
```

**-XX:+UseParallelGC：** 选择垃圾收集器为并行收集器。

**-XX:ParallelGCThreads=20：** 配置并行收集器的线程数

**-XX:+UseConcMarkSweepGC：** 设置年老代为并发收集。

**-XX:CMSFullGCsBeforeCompaction**：由于并发收集器不对内存空间进行压缩、整理，所以运行一段时间以后会产生“碎片”，使得运行效率降低。此值设置运行多少次GC以后对内存空间进行压缩、整理。

**-XX:+UseCMSCompactAtFullCollection：** 打开对年老代的压缩。可能会影响性能，但是可以消除碎片

3）辅助信息相关

```java
-XX:+PrintGC
-XX:+PrintGCDetails
```

**-XX:+PrintGC 输出形式:**

[GC 118250K->113543K(130112K), 0.0094143 secs] [Full GC 121376K->10414K(130112K), 0.0650971 secs]

**-XX:+PrintGCDetails 输出形式:**

[GC [DefNew: 8614K->781K(9088K), 0.0123035 secs] 118250K->113543K(130112K), 0.0124633 secs] [GC [DefNew: 8614K->8614K(9088K), 0.0000665 secs][Tenured: 112761K->10414K(121024K), 0.0433488 secs] 121376K->10414K(130112K), 0.0436268 secs



### 怎么打出线程栈信息。

**思路：** 可以说一下jps，top ，jstack这几个命令，再配合一次排查线上问题进行解答。

**我的答案：**

- 输入jps，获得进程号。
- top -Hp pid 获取本进程中所有线程的CPU耗时性能
- jstack pid命令查看当前java进程的堆栈状态
- 或者 jstack -l > /tmp/output.txt 把堆栈信息打到一个txt文件。
- 可以使用fastthread 堆栈定位，[fastthread.io/](https://link.juejin.im/?target=http%3A%2F%2Ffastthread.io%2F)



### 强引用、软引用、弱引用、虚引用的区别？

**思路：** 先说一下四种引用的定义，可以结合代码讲一下，也可以扩展谈到ThreadLocalMap里弱引用用处。

**我的答案：**

1）强引用

我们平时new了一个对象就是强引用，例如 Object obj = new Object();即使在内存不足的情况下，JVM宁愿抛出OutOfMemory错误也不会回收这种对象。

2）软引用

如果一个对象只具有软引用，则内存空间足够，垃圾回收器就不会回收它；如果内存空间不足了，就会回收这些对象的内存。

```java
SoftReference<String> softRef=new SoftReference<String>(str);     // 软引用
```

**用处：** 软引用在实际中有重要的应用，例如浏览器的后退按钮。按后退时，这个后退时显示的网页内容是重新进行请求还是从缓存中取出呢？这就要看具体的实现策略了。

（1）如果一个网页在浏览结束时就进行内容的回收，则按后退查看前面浏览过的页面时，需要重新构建

（2）如果将浏览过的网页存储到内存中会造成内存的大量浪费，甚至会造成内存溢出

如下代码：

```java
Browser prev = new Browser();               // 获取页面进行浏览



SoftReference sr = new SoftReference(prev); // 浏览完毕后置为软引用        



if(sr.get()!=null){ 



    rev = (Browser) sr.get();           // 还没有被回收器回收，直接获取



}else{



    prev = new Browser();               // 由于内存吃紧，所以对软引用的对象回收了



    sr = new SoftReference(prev);       // 重新构建



}
```

3）弱引用

具有弱引用的对象拥有更短暂的生命周期。在垃圾回收器线程扫描它所管辖的内存区域的过程中，一旦发现了只具有弱引用的对象，不管当前内存空间足够与否，都会回收它的内存。

```java
String str=new String("abc");    
WeakReference<String> abcWeakRef = new WeakReference<String>(str);
str=null;
等价于
str = null;
System.gc();
```

4）虚引用

如果一个对象仅持有虚引用，那么它就和没有任何引用一样，在任何时候都可能被垃圾回收器回收。虚引用主要用来跟踪对象被垃圾回收器回收的活动。



## Java内存模型（JMM）

​		我们常说的JVM内存模式指的是JVM的内存分区；而Java内存模式是一种虚拟机规范

​		Java 内存模型（JMM）是一种抽象的概念，并不真实存在，它描述了一组规则或规范，通过这组规范定义了程序中各个变量（包括实例字段、静态字段和构成数组对象的元素）的访问方式。试图屏蔽各种硬件和操作系统的内存访问差异，以实现让 Java 程序在各种平台下都能达到一致的内存访问效果。

​		JMM描述的是一组规则，围绕原子性、有序性和可见性展开

​		JMM是什么？JMM的主要目的是定义程序中各种变量的访问规则，变量包含实例字段和静态字段，但是不包括局部变量和方法参数。也就是说管理的是线程共享的，线程私有的是不需要管理的。众所周知现代计算机都包含多处理器，多个处理器之间共享主内存，极大的提高了计算机的运行效率。为了提升性能会在每个处理器上增加一个小容量cache（高速缓存，容量小但是速度快）加快读写，但是这样导致了缓存的一致性问题，为了解决缓存一致性问题又引入了了一系列的cache一致性协议（MSI,MESI,MOSI,Synapse，firefly等），用来保证CPU本地缓存和主内存数据的一致性



## 什么是JMM

　　JMM即为JAVA 内存模型（java memory model）。因为在不同的硬件生产商和不同的操作系统下，**内存的访问逻辑**有一定的差异，结果就是当你的代码在某个系统环境下运行良好，并且线程安全，但是换了个系统就出现各种问题。**Java内存模型，就是为了屏蔽系统和硬件的差异，让一套代码在不同平台下能到达相同的访问结果。**JMM从java 5开始的JSR-133发布后，已经成熟和完善起来。

## 　　内存划分

　　JMM规定了内存主要划分为主内存和工作内存两种。此处的主内存和工作内存跟JVM内存划分（堆、栈、方法区）是在不同的层次上进行的，如果非要对应起来，主内存对应的是**Java堆中的对象实例部分**，工作内存对应的是**栈中的部分区域**，从更底层的来说，主内存对应的是**硬件的物理内存**，工作内存对应的是**寄存器和高速缓存**。

![img](https://images2018.cnblogs.com/blog/1102674/201808/1102674-20180815143324915-2024156794.png)

　　JVM在设计时候考虑到，如果JAVA线程每次读取和写入变量都直接操作主内存，对性能影响比较大，所以每条线程拥有各自的工作内存，工作内存中的变量是主内存中的一份拷贝，线程对变量的读取和写入，直接在工作内存中操作，而不能直接去操作主内存中的变量。但是这样就会出现一个问题，当一个线程修改了自己工作内存中变量，对其他线程是不可见的，会导致线程不安全的问题。因为JMM制定了一套标准来保证开发者在编写多线程程序的时候，能够控制什么时候内存会被同步给其他线程。

## 　　内存交互操作

 　内存交互操作有8种，虚拟机实现必须保证每一个操作都是原子的，不可在分的（对于double和long类型的变量来说，load、store、read和write操作在某些平台上允许例外）

- - lock   （锁定）：作用于主内存的变量，把一个变量标识为线程独占状态
  - unlock （解锁）：作用于主内存的变量，它把一个处于锁定状态的变量释放出来，释放后的变量才可以被其他线程锁定
  - read  （读取）：作用于主内存变量，它把一个变量的值从主内存传输到线程的工作内存中，以便随后的load动作使用
  - load   （载入）：作用于工作内存的变量，它把read操作从主存中变量放入工作内存中
  - use   （使用）：作用于工作内存中的变量，它把工作内存中的变量传输给执行引擎，每当虚拟机遇到一个需要使用到变量的值，就会使用到这个指令
  - assign （赋值）：作用于工作内存中的变量，它把一个从执行引擎中接受到的值放入工作内存的变量副本中
  - store  （存储）：作用于主内存中的变量，它把一个从工作内存中一个变量的值传送到主内存中，以便后续的write使用
  - write 　（写入）：作用于主内存中的变量，它把store操作从工作内存中得到的变量的值放入主内存的变量中

　　JMM对这八种指令的使用，制定了如下规则：

- - 不允许read和load、store和write操作之一单独出现。即使用了read必须load，使用了store必须write
  - 不允许线程丢弃他最近的assign操作，即工作变量的数据改变了之后，必须告知主存
  - 不允许一个线程将没有assign的数据从工作内存同步回主内存
  - 一个新的变量必须在主内存中诞生，不允许工作内存直接使用一个未被初始化的变量。就是怼变量实施use、store操作之前，必须经过assign和load操作
  - 一个变量同一时间只有一个线程能对其进行lock。多次lock后，必须执行相同次数的unlock才能解锁
  - 如果对一个变量进行lock操作，会清空所有工作内存中此变量的值，在执行引擎使用这个变量前，必须重新load或assign操作初始化变量的值
  - 如果一个变量没有被lock，就不能对其进行unlock操作。也不能unlock一个被其他线程锁住的变量
  - 对一个变量进行unlock操作之前，必须把此变量同步回主内存

　　JMM对这八种操作规则和对[volatile的一些特殊规则](https://www.cnblogs.com/null-qige/p/8569131.html)就能确定哪里操作是线程安全，哪些操作是线程不安全的了。但是这些规则实在复杂，很难在实践中直接分析。所以一般我们也不会通过上述规则进行分析。更多的时候，使用java的happen-before规则来进行分析。

## 　　模型特征

　　**原子性：**例如上面八项操作，在操作系统里面是不可分割的单元。被synchronized关键字或其他锁包裹起来的操作也可以认为是原子的。从一个线程观察另外一个线程的时候，看到的都是一个个原子性的操作。

```
1         synchronized (this) {
2             a=1;
3             b=2;
4         }
```

　　例如一个线程观察另外一个线程执行上面的代码，只能看到a、b都被赋值成功结果，或者a、b都尚未被赋值的结果。

　　**可见性：**每个工作线程都有自己的工作内存，所以当某个线程修改完某个变量之后，在其他的线程中，未必能观察到该变量已经被修改。volatile关键字要求被修改之后的变量要求立即更新到主内存，每次使用前从主内存处进行读取。因此volatile可以保证可见性。除了volatile以外，synchronized和final也能实现可见性。synchronized保证unlock之前必须先把变量刷新回主内存。final修饰的字段在构造器中一旦完成初始化，并且构造器没有this逸出，那么其他线程就能看到final字段的值。

　　**有序性：**java的有序性跟线程相关。如果在线程内部观察，会发现当前线程的一切操作都是有序的。如果在线程的外部来观察的话，会发现线程的所有操作都是无序的。因为JMM的工作内存和主内存之间存在延迟，而且java会对一些指令进行重新排序。volatile和synchronized可以保证程序的有序性，很多程序员只理解这两个关键字的执行互斥，而没有很好的理解到volatile和synchronized也能保证指令不进行重排序。



### 并发编程三要素

1. **原子性:** 一个不可再被分割的颗粒。原子性指的是一个或多个操作要么全部执行成功要么全部执行失败。
2. **有序性:** 程序执行的顺序按照代码的先后顺序执行。（处理器可能会对指令进行重排序）
3. **可见性:** 一个县城对共享变量的修改,另一个线程能够立刻看到



## 　　Volatile内存语义

　　　[volatile的一些特殊规则](https://www.cnblogs.com/null-qige/p/8569131.html)

## 　　Final域的内存语义

　　被final修饰的变量，相比普通变量，内存语义有一些不同。具体如下：

- - JMM禁止把Final域的写重排序到构造器的外部。
  - 在一个线程中，初次读该对象和读该对象下的Final域，JMM禁止处理器重新排序这两个操作。

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

```
 1 public class FinalConstructor {
 2 
 3     final int a;
 4 
 5     int b;
 6 
 7     static FinalConstructor finalConstructor;
 8 
 9     public FinalConstructor() {
10         a = 1;
11         b = 2;
12     }
13 
14     public static void write() {
15         finalConstructor = new FinalConstructor();
16     }
17 
18     public static void read() {
19         FinalConstructor constructor = finalConstructor;
20         int A = constructor.a;
21         int B = constructor.b;
22     }
23 }
```

[![复制代码](https://common.cnblogs.com/images/copycode.gif)](javascript:void(0);)

　　假设现在有线程A执行FinalConstructor.write()方法，线程B执行FinalConstructor.read()方法。

　　对应上述的Final的第一条规则，因为JMM禁止把Final域的写重排序到构造器的外部，而对普通变量没有这种限制，所以变量A=1，而变量B可能会等于2（构造完成），也有可能等于0（第11行代码被重排序到构造器的外部）。

 　对应上述的Final的第二条规则，如果constructor的引用不为null，A必然为1，要么constructor为null，抛出空指针异常。保证读final域之前，一定会先读该对象的引用。但是普通对象就没有这种规则。

　　（上述的Final规则反复测试，遗憾的是我并没有能模拟出来普通变量不能正常构造的结果）

## 　　Happen-Before（先行发生规则）

　　在常规的开发中，如果我们通过上述规则来分析一个并发程序是否安全，估计脑壳会很疼。因为更多时候，我们是分析一个并发程序是否安全，其实都依赖Happen-Before原则进行分析。Happen-Before被翻译成先行发生原则，意思就是当A操作先行发生于B操作，则在发生B操作的时候，操作A产生的影响能被B观察到，“影响”包括修改了内存中的共享变量的值、发送了消息、调用了方法等。

　　Happen-Before的规则有以下几条

- - 程序次序规则（Program Order Rule）：在一个线程内，程序的执行规则跟程序的书写规则是一致的，从上往下执行。
  - 管程锁定规则（Monitor Lock Rule）：一个Unlock的操作肯定先于下一次Lock的操作。这里必须是同一个锁。同理我们可以认为在synchronized同步同一个锁的时候，锁内先行执行的代码，对后续同步该锁的线程来说是完全可见的。
  - volatile变量规则（volatile Variable Rule）：对同一个volatile的变量，先行发生的写操作，肯定早于后续发生的读操作
  - 线程启动规则（Thread Start Rule）：Thread对象的start()方法先行发生于此线程的每一个动作
  - 线程中止规则（Thread Termination Rule）：Thread对象的中止检测（如：Thread.join()，Thread.isAlive()等）操作，必行晚于线程中所有操作
  - 线程中断规则（Thread Interruption Rule）：对线程的interruption（）调用，先于被调用的线程检测中断事件(Thread.interrupted())的发生
  - 对象中止规则（Finalizer Rule）：一个对象的初始化方法先于一个方法执行Finalizer()方法
  - 传递性（Transitivity）：如果操作A先于操作B、操作B先于操作C,则操作A先于操作C











































































## 反射（框架设计的灵魂）

框架：半成品，可以在框架的基础上进行软件开发，简化代码

反射：将类的各个组成部分封装成其他对象，这就是反射机制

​		好处：

​	1.可以在程序运行过程中，操作这些对象

​	2. 可以解耦，提高程序的可扩展性



#### 获取Class对象的方式：

1. Class.forName("全类名")：讲字节码文件加载进内存，返回Class对象

   //多用于配置文件，将类名定义在配置文件中，读取文件，加载类

2. 类名.class：通过类名的属性class获取

   //多用于参数的传递

3. 对象.getClass(): getClass()方法在object类中定义

   //多用于对象的获取字节码的方式

**结论：**

​		同一个字节码文件（*.class）在一次程序运行过程中，**只会被加载一次**，无论通过哪一种方式获取的class对象都是同一个



![img](https://img-blog.csdnimg.cn/20190810110241602.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTE0NDI3MjY=,size_16,color_FFFFFF,t_70)

第一个阶段（源代码阶段）：

先从**java文件**按成员变量，构造方法，成员方法通过**javac编译**成**class文件**。如上图Person.java-->Person.class

第二个阶段（Class类对象阶段）：

通过**类加载器**把class文件中的成员变量，构造方法，成员方法加载到**内存**中。

第三个阶段（Runtime运行时阶段）：

该阶段就可以创建对象和调用对象里的方法了

### 获取字节码Class对象的三种方法

#### class对象功能：

##### 	获取功能

  1. 获取成员变量们

     ```
     Field[] getFields()  	获取所有被public修饰的成员变量
     Field getField(String name)	获取指定名称被public修饰的成员变量
     
     Field[] getDeclaredFields()	
     Field getDeclaredField(String name)
     ```

     ​	

  2. 获取构造方法们

     ```
     Constructor<?>[]	getConstructors()
     Constructor<T>[]	getConstructor(类<?>...	paramterTypes)
     
     Constructor<T>[]	getDeclaredConstructor(类<?>...	paramterTypes)
     Constructor<?>[]	getDeclaredConstructors()
     ```

     

  3. 获取成员方法们

     ```
     Method[]	getMethods()
     Method	getMethod(String name,类<?>... paramterTypes)
     
     Method[]	getDeclaredMethods()
     Method	getDeclaredMethod(String name,类<?>... paramterTypes)
     ```

     

  4. 获取类名

     ```
     String getName()
     ```



##### Field：成员变量

1. 设置值

   ```
   void set(Object obj, Object value)
   ```

   

2. 获取值

   ```
   get(object obj)
   ```




3. 忽略访问权限修饰符

```
setAccessible(true)//设置为true为忽略
```



##### Constructor：构造方法

​	创建对象：

```
* T newInstance(object... initargs)
```

	* 如果使用空参数构造方法创建对象，操作可以简化Class对象的newInstance方法



##### Method：方法对象

​	执行方法：

```
* Object invoke(Object obj,Object... args)
```

* String getName:获取方法名





```
//0.获取Person的Class成员变量
Class personClass =Person.class;
//1.获取成员变量们
//1.Field[] getFields()  获取所有public修饰的成员变量
Field[] fields=personClass.getFields();
for(Field field:field){
	System.out.println(field);
}
System.out.println("---------------------");
Field a=personClass.getField("a");
//获取成员变量a的值
Person p=new Person();
Object value=a.get(p);
System.out.println(value)
a.set(p,“张三”);
System.out.println(p);

```



```
//1.Filed[] personClass.getFields() 获取所有public修饰的成员变量
Filed[] fileds=personClass.getFields();
for (Filed field : fields){
	System.out.println(field);
}
System.out.println("---------------------");
Field a= personClass.getField("a");
//获取成员变量a的值
Person p= new Person();
Object value= a.get(p);
System.out.println(value);
//设置a的值
a.set(p,"张三")
System.out.println(p);
System.out.println("---------------------");
//Filed[] personclass.getDeclarFields() 获取所有的成员变量，无视修饰符
Filed[] declareFields= personclass.getDeclarFields();
for (Filed declareField : declarefields){
	System.out.println(declareField);
}
Field a= personClass.getField("d");
//忽略访问权限修饰符的安全检查
d.setAccessible(true);//暴力反射
Object value2= a.get(p);
System.out.println(value2);
```

**//在反射面前不存在什么公有私有，无视一切**



```
//0.获取Person的Class成员变量
Class personClass =Person.class;
Constructor constructor=personClass.getConstructor(String.class ,int.class);
//创建对象
Object person= constructor.newInstance("张三"，23)
//空参构造
Constructor constructor1=personClass.getConstructor();
Object person1= constructor.newInstance();
System.out.println(person1);
//优化版
Object o= personClass.newInstance();
System.out.println(o);
```



```
//0.获取Person的Class成员变量
Class personClass =Person.class;
//获取指定名称的方法
Mtehod eat_method= personClass.getMethod("eat");//无参构造方法，只需传方法名
Person p= new Person();
//执行方法
eat_method.invoke(p);
//下面为有参例子
Mtehod eat_method2= personClass.getMethod("eat"，String.class);//有参构造方法，还需传参数类型及个数
//执行方法
eat_method.invoke(p，“饭”);
System.out.println("---------------------");
//获取所有public修饰的方法
Method[] methods= personClass.getMethods();
for (Method method : methods){
	System.out.println(method);
}//打印出来的不止有本身定义的方法，还有Object的公共方法
```



### 简易框架

#### 需求：

​		在不改变该类的任何代码的前提下，可以帮我们创建任何类的对象，并且执行其中任意方法

​				**实现**

​			1. 配置文件

   				2. 反射

**步骤**

1. 将需要创建的对线的全类名和需要执行的方法定义在配置文件中

2. 在程序中加载读取配置文件

3. 使用反射技术来加载类文件来加载进内存

4. 创建对象

5. 执行方法



获取Class对象的方式：

1. Class.forName("全类名")：讲字节码文件加载进内存，返回Class对象
2. 类名.class：通过类名的属性class获取
3. 对象.getClass(): getClass()方法在object类中定义



```
public static void main(String[] args) throws Exception{
	1.Class cls1=Class.forName("cn.itcast.domain.Person");
	//此处若出现ClassNotFoundException说明从包名到类名一定有位置拼写出错了
	System.out.println(cls1);
	//2.类名.class
	Class cls2= Person.class;
	System.out.println(cls2);
	//3.对象.getClass()
	Person p =new Person();
	Class cls2= p.getName;
	System.out.println(cls3);
	//比较三个对象是否相同
	//结论为相同
}
```



## 注解：

​		概念：说明程序的，给计算机看

​		注解：用文字描述程序，给程序员看的

#### 定义：

​		JDK1.5之后的新特性

​		说明程序的

​		使用注解：@注解名称

#### 作用分类：

	1. 编写文档：通过代码里标识的元数据生成文档【生成文档：doc文档】
 	2. 代码分析： 通过代码里标识的元数据对代码进行分析【使用反射】
 	3. 编译检查：通过代码里表示的元数据让编译器能够实现基本的编译检查【Override】



##### JDK中预定义的一些注解

**1.@Override**

​		检测被该注解标注的方法是否继承自父类（接口）的

**2.@Deprecated**

​		该注解标注的内容已过时，可以有更好的选择，不过目前这个也能用

**3.@SuppressWarnings**

​		压制规定范围内的警告



##### 自定义注解

​		**格式：**

​		元注解

​		public @interface 注解名称｛｝

​		**本质：**

​		public interface 类名 extends java.lang.annoation.Annotation{}

​		**注解本质上就是一个接口，该接口默认继承.Annotation接口**

​		**属性：**

​		接口中的抽象方法

​		**要求：**

		1. 属性的返回值类型的取值范围

基本数据类型

String

美剧

注解

以上类型的数组

2. 定义属性后，使用时赋值

   如果定义属性时用default关键字给属性默认值初始化值，则使用注解时，可以不进行属性的赋值

   如果只有一个属性需要赋值，并且属性的名称是value，则可以省略，直接写值

   数组赋值时，值使用｛｝包裹。且如果数组中只有一个值，｛｝可以省略

**元注解：**

​		用于描述注解的注解

​	@Target:描述注解能够作用的位置

​			TYPE：可以作用于类上

​			METHOD：可以作用于方法上

​			FIELD：可以作用于成员变量上

​	@Retention:描述注解被保留的阶段

​			@Retention（RetentionPolicy.RUNTIME）:当前被描述的注解会保留到class字节码文件中，并被JVM读取到

​	@Documented:描述注解是否被抽取到API文档中

 	@Inhertited:描述注解是否被子类继承

##### 在程序中使用（解析）注解

​	获取注解中定义的属性值 

	1. 获取注解定义的位置的对象 （Class，Method，Field）
 	2. 获取指定的注解
 	3. 调用注解中的抽象方法获取配置的属性值





