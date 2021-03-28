## **Spring是什么?**

Spring是一个轻量级的IoC和AOP容器框架。是为Java应用程序提供基础性服务的一套框架，目的是用于简化企业应用程序的开发，它使得开发者只需要关心业务需求。主要包括以下七个模块：

- Spring Context：提供框架式的Bean访问方式，以及企业级功能（JNDI、定时任务等）；
- Spring Core：核心类库，所有功能都依赖于该类库，提供IOC和DI服务；
- Spring AOP：AOP服务；
- Spring Web：提供了基本的面向Web的综合特性，提供对常见框架如Struts2的支持，Spring能够管理这些框架，将Spring的资源注入给框架，也能在这些框架的前后插入拦截器；
- Spring MVC：提供面向Web应用的Model-View-Controller，即MVC实现。
- Spring DAO：对JDBC的抽象封装，简化了数据访问异常的处理，并能统一管理JDBC事务；
- Spring ORM：对现有的ORM框架的支持；



![img](https://img2018.cnblogs.com/blog/842514/201906/842514-20190611160935478-279758854.png)

Spring Core：基础，可以说Spring其他所有的功能都依赖于该类库。主要提供IOC和DI功能。

Spring Aspects：该模块为与AspectJ的集成提供支持。

Spring AOP：提供面向方面的编程实现。

Spring JDBC：Java数据库连接。

Spring JMS：Java消息服务。

Spring ORM：用于支持Hibernate等ORM工具。

Spring Web：为创建Web应用程序提供支持。

Spring Test：提供了对JUnit和TestNG测试的支持



**Spring 的优点？**

（1）spring属于低侵入式设计，代码的污染极低；

（2）spring的DI机制将对象之间的依赖关系交由框架处理，减低组件的耦合性；

（3）Spring提供了AOP技术，支持将一些通用任务，如安全、事务、日志、权限等进行集中式管理，从而提供更好的复用。

（4）spring对于主流的应用框架提供了集成支持。



**Spring的IoC理解：**

（1）IOC就是控制反转，指创建对象的控制权转移给Spring框架进行管理，并由Spring根据配置文件去创建实例和管理各个实例之间的依赖关系，对象与对象之间**松散耦合**，也利于**功能的复用**。DI依赖注入，和控制反转是同一个概念的不同角度的描述，即 应用程序在运行时依赖IoC容器来动态注入对象需要的外部依赖。**高内聚低耦合**

（2）最直观的表达就是，以前创建对象的主动权和时机都是由自己把控的，IOC让对象的创建不用去new了，可以由spring自动生产，使用java的反射机制，根据配置文件在运行时动态的去创建对象以及管理对象，并调用对象的方法的。

（3）Spring的IOC有三种注入方式 ：构造器注入、setter方法注入、根据注解注入



**Spring的AOP理解：**

OOP面向对象，允许开发者定义纵向的关系，但并不适用于定义横向的关系，会导致大量代码的重复，而不利于各个模块的重用。

AOP，一般称为面向切面，作为面向对象的一种补充，用于将那些与业务无关，但却对多个对象产生影响的公共行为和逻辑，抽取并封装为一个可重用的模块，这个模块被命名为“切面”（Aspect），减少系统中的重复代码，**降低了模块间的耦合度**，提高系统的可维护性。可用于权限认证、日志、事务处理。

AOP实现的关键在于 代理模式，AOP代理主要分为**静态代理**和**动态代理**。静态代理的代表为AspectJ；动态代理则以Spring AOP为代表。

（1）AspectJ是静态代理，也称为**编译时增强**，AOP框架会在编译阶段生成AOP代理类，并将AspectJ(切面)织入到Java字节码中，运行的时候就是增强之后的AOP对象。

（2）Spring AOP使用的动态代理，所谓的动态代理就是说AOP框架不会去修改字节码，而是每次运行时在内存中临时为方法生成一个AOP对象，这个AOP对象包含了目标对象的全部方法，并且在特定的切点做了增强处理，并回调原对象的方法。

Spring AOP中的动态代理主要有两种方式，JDK动态代理和CGLIB动态代理：

​    ① JDK动态代理只提供接口的代理，不支持类的代理，要求被代理类实现接口。JDK动态代理的核心是InvocationHandler接口和Proxy类，在获取代理对象时，使用Proxy类来动态创建目标类的代理类（即最终真正的代理类，这个类继承自Proxy并实现了我们定义的接口），当代理对象调用真实对象的方法时， InvocationHandler 通过invoke()方法反射来调用目标类中的代码，动态地将横切逻辑和业务编织在一起；

>  InvocationHandler 的 invoke(Object proxy,Method method,Object[] args)：proxy是最终生成的代理对象; method 是被代理目标实例的某个具体方法; args 是被代理目标实例某个方法的具体入参, 在方法反射调用时使用。

​    ② 如果被代理类没有实现接口，那么Spring AOP会选择使用CGLIB来动态代理目标类。CGLIB（Code Generation Library），是一个代码生成的类库，可以在运行时动态的生成指定类的一个子类对象，并覆盖其中特定方法并添加增强代码，从而实现AOP。CGLIB是通过继承的方式做的动态代理，因此如果某个类被标记为final，那么它是无法使用CGLIB做动态代理的。

（3）静态代理与动态代理区别在于生成AOP代理对象的时机不同，相对来说AspectJ的静态代理方式具有更好的性能，但是AspectJ需要特定的编译器进行处理，而Spring AOP则无需特定的编译器处理。

> IoC让相互协作的组件保持松散的耦合，而AOP编程允许你把遍布于应用各层的功能分离出来形成可重用的功能组件。



### 初始化过程，源码解析

![img](https://images2015.cnblogs.com/blog/801753/201702/801753-20170201125310058-568989522.png)

**applicationContext会自动注册beanPostProcess等信息 而beanFactory需要手动注册addBeanPostProcess\***

**第一步：通过配置文件/注解等方法读取信息**

**![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151051934-1309704238.png)**

 **第二步：进入到方法里发现做了如下三个步骤**

**![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151125251-1598251088.png)**

**1：资源匹配 **

**2：读取配置文件，获取到environment对象（加载系统属性值以及系统环境信息），并且解析配置文件（整个变量值替换） **

**3 ：整个spring初始化核心（代码分析如下）**

 ![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151312939-840437147.png)

每个方法所做的功能如图所示，invokeBeanFactoryPostProcessors方法里加载了所有的beanDefinition信息到beanDefinitionMap里

**我理解是调用了invokeBeanDefinitionRegistryPostProcessors后置处理器，之后invokeBeanDefinitionRegistryPostProcessors把所有的标注了不同注解类型的类注册进来，（比如@Bean @Import等），但是不确定**

**继续来分析Spring容器核心创建方法`refresh（）`的最后一步`finishBeanFactoryInitialization(beanFactory)，`**

我们进入此方法：

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151520777-1623133242.png) 这个方法里的东西呢我们只需关注最后一行即可，也就是`beanFactory.preInstantiateSingletons();`

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151625499-1916166568.png)

getMergedLocalBeanDefinition方法。**Bean定义公共的抽象类是AbstractBeanDefinition，普通的Bean在Spring加载Bean定义的时候，实例化出来的是GenericBeanDefinition，而Spring上下文包括实例化所有Bean用的AbstractBeanDefinition是RootBeanDefinition，这时候就使用getMergedLocalBeanDefinition方法做了一次转化，将非RootBeanDefinition转换为RootBeanDefinition以供后续操作**。

在上图我们同样可以看到，开头通过beanName获取bean实例，如果获取到的实例不满足条件，就会调用核心代码`getBean(beanName)`，**这个方法也是Spring最核心的方法之一。我们把这个核心方法分为几部分来剖析：**

**第一部分**

**![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630151953669-725341152.png)**

 **第二部分：**

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630152432351-802622272.png)

 （我理解和jvm的双亲委派是同一个意思，先从父类找）

**` 第三部分`**

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630153213971-581493840.png)

 **第四部分：**

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630153312883-398351826.png)

**第五部分：**

接着看createBean方法

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630153548324-1909065043.png)

 上图代码是判断该bean的class是否存在，也就是该bean是可以通过class创建的 

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630153655820-2095028376.png)

 准备方法重写

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630153816302-416896534.png)

这边有个return，也就是说这边有可能提前返回bean，看注释：Give BeanPostProcessors a chance to return a proxy instead of the target bean instance.我们以前在beanPostProcessor时说过，**beanPostProcessor是可以临时修改bean的，它的优先级高于正常实例化bean的（也就是后续实例化该bean的过程）**，如果beanPostProcessor能返回，则直接返回了

**最后调用了doGreateBean方法**

**doGreateBean方法里去执行真正的实例化动作**

**一般是先从工厂中删除一遍，确保单例对象不会被重复创建，在通过反射去实例化对象**

![img](https://img2020.cnblogs.com/blog/2040701/202006/2040701-20200630154724880-34219432.png)





详细源码码解析https://www.cnblogs.com/xrq730/p/6361578.html











**Spring AOP里面的几个名词的概念：**

（1）连接点（Join point）：指程序运行过程中所执行的方法。在Spring AOP中，一个连接点总代表一个方法的执行。 

（2）切面（Aspect）：被抽取出来的公共模块，可以用来会横切多个对象。Aspect切面可以看成 Pointcut切点 和 Advice通知 的结合，一个切面可以由多个切点和通知组成。

> 在Spring AOP中，切面可以在类上使用 @AspectJ 注解来实现。

（3）切点（Pointcut）：切点用于定义 要对哪些Join point进行拦截。

> 切点分为execution方式和annotation方式。execution方式可以用路径表达式指定对哪些方法拦截，比如指定拦截add*、search*。annotation方式可以指定被哪些注解修饰的代码进行拦截。

（4）通知（Advice）：指要在连接点（Join Point）上执行的动作，即增强的逻辑，比如权限校验和、日志记录等。通知有各种类型，包括Around、Before、After、After returning、After throwing。

（5）目标对象（Target）：包含连接点的对象，也称作被通知（Advice）的对象。 由于Spring AOP是通过动态代理实现的，所以这个对象永远是一个代理对象。

（6）织入（Weaving）：通过动态代理，在目标对象（Target）的方法（即连接点Join point）中执行增强逻辑（Advice）的过程。

（7）引入（Introduction）：添加额外的方法或者字段到被通知的类。Spring允许引入新的接口（以及对应的实现）到任何被代理的对象。例如，你可以使用一个引入来使bean实现 IsModified 接口，以便简化缓存机制。

几个概念的关系图可以参考下图：

![img](https://img-blog.csdnimg.cn/2020120700443256.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E3NDUyMzM3MDA=,size_16,color_FFFFFF,t_70)

网上有张非常形象的图，描述了各个概念所处的场景和作用，贴在这里供大家理解：

![img](https://img-blog.csdnimg.cn/20201207001947787.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E3NDUyMzM3MDA=,size_16,color_FFFFFF,t_70)





**Spring通知（Advice）有哪些类型？**

（1）前置通知（Before Advice）：在连接点（Join point）之前执行的通知。

（2）后置通知（After Advice）：当连接点退出的时候执行的通知（不论是正常返回还是异常退出）。 

（3）环绕通知（Around Advice）：包围一个连接点的通知，这是最强大的一种通知类型。 环绕通知可以在方法调用前后完成自定义的行为。它也可以选择是否继续执行连接点或直接返回它们自己的返回值或抛出异常来结束执行。

（4）返回后通知（AfterReturning Advice）：在连接点正常完成后执行的通知（如果连接点抛出异常，则不执行）

（5）抛出异常后通知（AfterThrowing advice）：在方法抛出异常退出时执行的通知

![img](https://img-blog.csdnimg.cn/20201207005911882.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2E3NDUyMzM3MDA=,size_16,color_FFFFFF,t_70)

> 同一个Aspect，不同advice的执行顺序：
>
> （1）没有异常情况下的执行顺序：
>
> - around before advice
> - before advice
> - target method 执行
> - around after advice
> - after advice
> - afterReturning
>
> （2）有异常情况下的执行顺序：
>
> - around before advice
> - before advice
> - target method 执行
> - around after advice
> - after advice
> - afterThrowing
> - java.lang.RuntimeException: 异常发生



**BeanFactory和ApplicationContext有什么区别？**

​    BeanFactory和ApplicationContext是Spring的两大核心接口，都可以当做Spring的容器。

（1）BeanFactory是Spring里面最底层的接口，是IoC的核心，定义了IoC的基本功能，包含了各种Bean的定义、加载、实例化，依赖注入和生命周期管理。ApplicationContext接口作为BeanFactory的子类，除了提供BeanFactory所具有的功能外，还提供了更完整的框架功能：

- 继承MessageSource，因此支持国际化。
- 资源文件访问，如URL和文件（ResourceLoader）。
- 载入多个（有继承关系）上下文（即同时加载多个配置文件） ，使得每一个上下文都专注于一个特定的层次，比如应用的web层。
- 提供在监听器中注册bean的事件。

（2）①BeanFactroy采用的是延迟加载形式来注入Bean的，只有在使用到某个Bean时(调用getBean())，才对该Bean进行加载实例化。这样，我们就不能提前发现一些存在的Spring的配置问题。如果Bean的某一个属性没有注入，BeanFacotry加载后，直至第一次使用调用getBean方法才会抛出异常。

​    ②ApplicationContext，它是在容器启动时，一次性创建了所有的Bean。这样，在容器启动时，我们就可以发现Spring中存在的配置错误，这样有利于检查所依赖属性是否注入。 

​    ③ApplicationContext启动后预载入所有的单实例Bean，所以在运行的时候速度比较快，因为它们已经创建好了。相对于BeanFactory，ApplicationContext 唯一的不足是占用内存空间，当应用程序配置Bean较多时，程序启动较慢。

（3）BeanFactory和ApplicationContext都支持BeanPostProcessor、BeanFactoryPostProcessor的使用，但两者之间的区别是：BeanFactory需要手动注册，而ApplicationContext则是自动注册。

（4）BeanFactory通常以编程的方式被创建，ApplicationContext还能以声明的方式创建，如使用ContextLoader。



**Spring Bean的生命周期？**

简单来说，Spring Bean的生命周期只有四个阶段：实例化 Instantiation --> 属性赋值 Populate --> 初始化 Initialization --> 销毁 Destruction

但具体来说，Spring Bean的生命周期包含下图的流程：

![img](https://img-blog.csdnimg.cn/img_convert/84341632e9df3625a91c3e2a1437ee65.png)

（1）实例化Bean：

对于BeanFactory容器，当客户向容器请求一个尚未初始化的bean时，或初始化bean的时候需要注入另一个尚未初始化的依赖时，容器就会调用createBean进行实例化。

对于ApplicationContext容器，当容器启动结束后，通过获取BeanDefinition对象中的信息，实例化所有的bean。

（2）设置对象属性（依赖注入）：实例化后的对象被封装在BeanWrapper对象中，紧接着，Spring根据BeanDefinition中的信息 以及 通过BeanWrapper提供的设置属性的接口完成属性设置与依赖注入。

（3）处理Aware接口：Spring会检测该对象是否实现了xxxAware接口，通过Aware类型的接口，可以让我们拿到Spring容器的一些资源：

- ①如果这个Bean实现了BeanNameAware接口，会调用它实现的setBeanName(String beanId)方法，传入Bean的名字；
- ②如果这个Bean实现了BeanClassLoaderAware接口，调用setBeanClassLoader()方法，传入ClassLoader对象的实例。
- ②如果这个Bean实现了BeanFactoryAware接口，会调用它实现的setBeanFactory()方法，传递的是Spring工厂自身。
- ③如果这个Bean实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文；

（4）BeanPostProcessor前置处理：如果想对Bean进行一些自定义的前置处理，那么可以让Bean实现了BeanPostProcessor接口，那将会调用postProcessBeforeInitialization(Object obj, String s)方法。

（5）InitializingBean：如果Bean实现了InitializingBean接口，执行afeterPropertiesSet()方法。

（6）init-method：如果Bean在Spring配置文件中配置了 init-method 属性，则会自动调用其配置的初始化方法。

（7）BeanPostProcessor后置处理：如果这个Bean实现了BeanPostProcessor接口，将会调用postProcessAfterInitialization(Object obj, String s)方法；由于这个方法是在Bean初始化结束时调用的，所以可以被应用于内存或缓存技术；

> 以上几个步骤完成后，Bean就已经被正确创建了，之后就可以使用这个Bean了。

（8）DisposableBean：当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用其实现的destroy()方法；

（9）destroy-method：最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法。



**将一个类声明为Spring的bean的注解有哪些？**

我们一般使用@Autowired注解去自动装配bean。而想要把一个类标识为可以用@Autowired注解自动装配的bean，可以采用以下的注解实现：

1.@Component注解。通用的注解，可标注任意类为Spring组件。如果一个Bean不知道属于哪一个层，可以使用@Component注解标注。

2.@Repository注解。对应持久层，即Dao层，主要用于数据库相关操作。

3.@Service注解。对应服务层，即Service层，主要涉及一些复杂的逻辑，需要用到Dao层（注入）。

4.@Controller注解。对应Spring MVC的控制层，即Controller层，主要用于接受用户请求并调用Service层的方法返回数据给前端页面。



**Spring中bean的作用域：**

（1）singleton：默认作用域，单例bean，每个容器中只有一个bean的实例。

（2）prototype：为每一个bean请求创建一个实例。

（3）request：为每一个request请求创建一个实例，在请求完成以后，bean会失效并被垃圾回收器回收。

（4）session：与request范围类似，同一个session会话共享一个实例，不同会话使用不同的实例。

（5）global-session：全局作用域，所有会话共享一个实例。如果想要声明让所有会话共享的存储变量的话，那么这全局变量需要存储在global-session中。



**Spring框架中的Bean是线程安全的么？如果线程不安全，那么如何处理？**

Spring容器本身并没有提供Bean的线程安全策略，因此可以说Spring容器中的Bean本身不具备线程安全的特性，但是具体情况还是要结合Bean的作用域来讨论。

（1）对于prototype作用域的Bean，每次都创建一个新对象，也就是线程之间不存在Bean共享，因此不会有线程安全问题。

（2）对于singleton作用域的Bean，所有的线程都共享一个单例实例的Bean，因此是存在线程安全问题的。但是如果单例Bean是一个无状态Bean，也就是线程中的操作不会对Bean的成员执行查询以外的操作，那么这个单例Bean是线程安全的。比如Controller类、Service类和Dao等，这些Bean大多是无状态的，只关注于方法本身。

> 有状态Bean(Stateful Bean) ：就是有实例变量的对象，可以保存数据，是非线程安全的。
>
> 无状态Bean(Stateless Bean)：就是没有实例变量的对象，不能保存数据，是不变类，是线程安全的。

对于有状态的bean（比如Model和View），就需要自行保证线程安全，最浅显的解决办法就是将有状态的bean的作用域由“singleton”改为“prototype”。

也可以采用ThreadLocal解决线程安全问题，为每个线程提供一个独立的变量副本，不同线程只操作自己线程的副本变量。

> ThreadLocal和线程同步机制都是为了解决多线程中相同变量的访问冲突问题。同步机制采用了“时间换空间”的方式，仅提供一份变量，不同的线程在访问前需要获取锁，没获得锁的线程则需要排队。而ThreadLocal采用了“空间换时间”的方式。ThreadLocal会为每一个线程提供一个独立的变量副本，从而隔离了多个线程对数据的访问冲突。因为每一个线程都拥有自己的变量副本，从而也就没有必要对该变量进行同步了。



#### **Spring基于xml注入bean的几种方式：**

- set()方法注入；
- 构造器注入：①通过index设置参数的位置；②通过type设置参数类型；
- 静态工厂注入；
- 实例工厂；



**Spring的自动装配：**

在spring中，使用autowire来配置自动装载模式，对象无需自己查找或创建与其关联的其他对象，由容器负责把需要相互协作的对象引用赋予各个对象。

（1）在Spring框架xml配置中共有5种自动装配：

- no：默认的方式是不进行自动装配的，通过手工设置ref属性来进行装配bean。
- byName：通过bean的名称进行自动装配，如果一个bean的 property 与另一bean 的name 相同，就进行自动装配。 
- byType：通过参数的数据类型进行自动装配。
- constructor：利用构造函数进行装配，并且构造函数的参数通过byType进行装配。
- autodetect：自动探测，如果有构造方法，通过 construct的方式自动装配，否则使用 byType的方式自动装配。

（2）基于注解的自动装配方式：

使用@Autowired、@Resource注解来自动装配指定的bean。在使用@Autowired注解之前需要在Spring配置文件进行配置，<context:annotation-config />。在启动spring IoC时，容器自动装载了一个AutowiredAnnotationBeanPostProcessor后置处理器，当容器扫描到@Autowied、@Resource或@Inject时，就会在IoC容器自动查找需要的bean，并装配给该对象的属性。在使用@Autowired时，首先在容器中查询对应类型的bean：

如果查询结果刚好为一个，就将该bean装配给@Autowired指定的数据；

如果查询的结果不止一个，那么@Autowired会根据名称来查找；

如果上述查找的结果为空，那么会抛出异常。解决方法时，使用required=false。

> @Autowired可用于：构造函数、成员变量、Setter方法
>
> 注：@Autowired和@Resource之间的区别：
>
> (1) @Autowired默认是按照类型装配注入的，默认情况下它要求依赖对象必须存在（可以设置它required属性为false）。
>
> (2) @Resource默认是按照名称来装配注入的，只有当找不到与名称匹配的bean才会按照类型来装配注入。



#### **Spring 框架中都用到了哪些设计模式**

（1）工厂模式：Spring使用工厂模式，通过BeanFactory和ApplicationContext来创建对象

（2）单例模式：Bean默认为单例模式

（3）策略模式：例如Resource的实现类，针对不同的资源文件，实现了不同方式的资源获取策略

（4）代理模式：Spring的AOP功能用到了JDK的动态代理和CGLIB字节码生成技术

（5）模板方法：可以将相同部分的代码放在父类中，而将不同的代码放入不同的子类中，用来解决代码重复的问题。比如RestTemplate, JmsTemplate, JpaTemplate

（6）适配器模式：Spring AOP的增强或通知（Advice）使用到了适配器模式，Spring MVC中也是用到了适配器模式适配Controller

（7）观察者模式：Spring事件驱动模型就是观察者模式的一个经典应用。

（8）桥接模式：可以根据客户的需求能够动态切换不同的数据源。比如我们的项目需要连接多个数据库，客户在每次访问中根据需要会去访问不同的数据库



**Spring框架中有哪些不同类型的事件？**

Spring 提供了以下5种标准的事件：

（1）上下文更新事件（ContextRefreshedEvent）：在调用ConfigurableApplicationContext 接口中的refresh()方法时被触发。

（2）上下文开始事件（ContextStartedEvent）：当容器调用ConfigurableApplicationContext的Start()方法开始/重新开始容器时触发该事件。

（3）上下文停止事件（ContextStoppedEvent）：当容器调用ConfigurableApplicationContext的Stop()方法停止容器时触发该事件。

（4）上下文关闭事件（ContextClosedEvent）：当ApplicationContext被关闭时触发该事件。容器被关闭时，其管理的所有单例Bean都被销毁。

（5）请求处理事件（RequestHandledEvent）：在Web应用中，当一个http请求（request）结束触发该事件。

如果一个bean实现了ApplicationListener接口，当一个ApplicationEvent 被发布以后，bean会自动被通知

#### springmvc常用注解标签详解

1、@Controller
在SpringMVC 中，控制器Controller 负责处理由DispatcherServlet 分发的请求，它把用户请求的数据经过业务处理层处理之后封装成一个Model ，然后再把该Model 返回给对应的View 进行展示。在SpringMVC 中提供了一个非常简便的定义Controller 的方法，你无需继承特定的类或实现特定的接口，只需使用@Controller 标记一个类是Controller ，然后使用@RequestMapping 和@RequestParam 等一些注解用以定义URL 请求和Controller 方法之间的映射，这样的Controller 就能被外界访问到。此外Controller 不会直接依赖于HttpServletRequest 和HttpServletResponse 等HttpServlet 对象，它们可以通过Controller 的方法参数灵活的获取到。
@Controller 用于标记在一个类上，使用它标记的类就是一个SpringMVC Controller 对象。分发处理器将会扫描使用了该注解的类的方法，并检测该方法是否使用了@RequestMapping 注解。@Controller 只是定义了一个控制器类，而使用@RequestMapping 注解的方法才是真正处理请求的处理器。单单使用@Controller 标记在一个类上还不能真正意义上的说它就是SpringMVC 的一个控制器类，因为这个时候Spring 还不认识它。那么要如何做Spring 才能认识它呢？这个时候就需要我们把这个控制器类交给Spring 来管理。有两种方式：
（1）在SpringMVC 的配置文件中定义MyController 的bean 对象。
（2）在SpringMVC 的配置文件中告诉Spring 该到哪里去找标记为@Controller 的Controller 控制器。
2、@RequestMapping
RequestMapping是一个用来处理请求地址映射的注解，可用于类或方法上。用于类上，表示类中的所有响应请求的方法都是以该地址作为父路径。
3、@Resource和@Autowired
@Resource和@Autowired都是做bean的注入时使用，其实@Resource并不是Spring的注解，它的包是javax.annotation.Resource，需要导入，但是Spring支持该注解的注入。
4、@ModelAttribute和 @SessionAttributes
代表的是：该Controller的所有方法在调用前，先执行此@ModelAttribute方法，可用于注解和方法参数中，可以把这个@ModelAttribute特性，应用在BaseController当中，所有的Controller继承BaseController，即可实现在调用Controller时，先执行@ModelAttribute方法。
@SessionAttributes即将值放到session作用域中，写在class上面。
具体示例参见下面：使用 @ModelAttribute 和 @SessionAttributes 传递和保存数据
5、@PathVariable
用于将请求URL中的模板变量映射到功能处理方法的参数上，即取出uri模板中的变量作为参数。
6、@requestParam
@requestParam主要用于在SpringMVC后台控制层获取参数，类似一种是request.getParameter("name")，它有三个常用参数：defaultValue = "0", required = false, value = "isApp"；defaultValue 表示设置默认值，required 铜过boolean设置是否是必须要传入的参数，value 值表示接受的传入的参数类型。
7、@ResponseBody
作用： 该注解用于将Controller的方法返回的对象，通过适当的HttpMessageConverter转换为指定格式后，写入到Response对象的body数据区。
使用时机：返回的数据不是html标签的页面，而是其他某种格式的数据时（如json、xml等）使用；
8、@Component
相当于通用的注解，当不知道一些类归到哪个层时使用，但是不建议。
9、@Repository
用于注解dao层，在daoImpl类上面注解。

### Spring事务

Spring事务本质是对数据库事务的支持，如果数据库不支持事务（例如MySQL的MyISAM引擎不支持事务），则Spring事务也不会生效。

Spring的事务传播
事务传播行为是指一个事务方法A被另一个事务方法B调用时，这个事务A应该如何处理。事务A应该在事务B中运行还是另起一个事务，这个有事务A的传播行为决定。

事务传播属性定义TransactionDefinition

```
int PROPAGATION_REQUIRED = 0;
int PROPAGATION_SUPPORTS = 1;
int PROPAGATION_MANDATORY = 2;
int PROPAGATION_REQUIRES_NEW = 3;
int PROPAGATION_NOT_SUPPORTED = 4;
int PROPAGATION_NEVER = 5;
int PROPAGATION_NESTED = 6;
 
```

常量名称	常量解释

PROPAGATION_REQUIRED	

支持当前事务，如果当前没有事务，就新建一个事务。这是Spring 默认的事务的传播。

PROPAGATION_SUPPORTS	

支持当前事务，如果当前没有事务，就以非事务方式执行。

PROPAGATION_MANDATORY	

支持当前事务，如果当前没有事务，就抛出异常。

PROPAGATION_REQUIRES_NEW	

新建事务，如果当前存在事务，把当前事务挂起。新建的事务将和被挂起的事务没有任何关系，是两个独立的事务，外层事务失败回滚之后， 不能回滚内层事务执行的结果，内层事务失败抛出异常，外层事务捕获， 也可以不处理回滚操作。 使用JtaTransactionManager作为事务管理器

PROPAGATION_NOT_SUPPORTED	

以非事务方式执行操作，如果当前存在事务，就把当前事务挂起。使用JtaTransactionManager作为事务管理器
PROPAGATION_NEVER	以非事务方式执行，如果当前存在事务，则抛出异常。
PROPAGATION_NESTED	如果一个活动的事务存在，则运行在一个嵌套的事务中。如果没有活动事务，则按REQUIRED属性执行。它使用了一个单独的事务，这个事务拥有多个可以回滚的保存点。内部事务的回滚不会对外部事务造成影响。它只对DataSourceTransactionManager事务管理器起效。

PROPAGATION_REQUIRED
如果存在一个事务，则支持当前事务，如果没有事务则开启事务。


如下例子，单独调用methodB时，当前上下文没有事务，所以会开启一个新的事务。

调用methodA方法时，因为当前上下文不存在事务，所以会开启一个新的事务。当执行到methodB时，methodB发现当前上下文有事务，因此就加入到当前事务A中来。

```
@Transactional(propagation = Propagation.REQUIRED)
public void methodA() {
    methodB();
    // do something
}

@Transactional(propagation = Propagation.REQUIRED)
public void methodB() {
    // do something
}
```

PROPAGATION_SUPPORTS
如果存在一个事务，支持当前事务。如果没有事务，则非事务的执行.


单独的调用methodB时，methodB方法是非事务的执行的。当调用methdA时,methodB则加入了methodA的事务中,事务地执行。

```
@Transactional(propagation = Propagation.REQUIRED)
public void methodA() {
    methodB();
    // do something
}

// 事务属性为SUPPORTS
@Transactional(propagation = Propagation.SUPPORTS)
public void methodB() {
    // do something
}
```


PROPAGATION_MANDATORY
如果已经存在一个事务，支持当前事务。如果没有一个活动的事务，则抛出异常。

PROPAGATION_MANDATORY
如果已经存在一个事务，支持当前事务。如果没有一个活动的事务，则抛出异常。


当单独调用methodB时，因为当前没有一个活动的事务，则会抛出异常throw new IllegalTransactionStateException(“Transaction propagation ‘mandatory’ but no existing transaction found”)

当调用methodA时，methodB则加入到methodA的事务中，以事务方式执行。

```
@Transactional(propagation = Propagation.REQUIRED)
public void methodA() {
    methodB();
    // do something
}

@Transactional(propagation = Propagation.MANDATORY)
public void methodB() {
    // do something
}
```

PROPAGATION_REQUIRES_NEW
使用PROPAGATION_REQUIRES_NEW,需要使用 JtaTransactionManager作为事务管理器。
它会开启一个新的事务。如果一个事务已经存在，则先将这个存在的事务挂起。


从下面代码可以看出，事务B与事务A是两个独立的事务，互不相干。事务B是否成功并不依赖于 事务A。如果methodA方法在调用methodB方法后的doSomeThingB方法失败了，而methodB方法所做的结果依然被提交。而除了 methodB之外的其它代码导致的结果却被回滚了

```
@Transactional(propagation = Propagation.REQUIRED)
public void methodA() {
    doSomeThingA();
    methodB();
    doSomeThingB();
    // do something else
}

@Transactional(propagation = Propagation.REQUIRES_NEW)
public void methodB() {
    // do something
}
```


当调用methodA()，相当于

当调用methodA()，相当于

```
public static void main(){
    TransactionManager tm = null;
    try{
        //获得一个JTA事务管理器
        tm = getTransactionManager();
        tm.begin();//开启一个新的事务
        Transaction ts1 = tm.getTransaction();
        doSomeThing();
        tm.suspend();//挂起当前事务
        try{
            tm.begin();//重新开启第二个事务
            Transaction ts2 = tm.getTransaction();
            methodB();
            ts2.commit();//提交第二个事务
        } Catch(RunTimeException ex) {
            ts2.rollback();//回滚第二个事务
        } finally {
            //释放资源
        }
        //methodB执行完后，恢复第一个事务
        tm.resume(ts1);
        doSomeThingB();
        ts1.commit();//提交第一个事务
    } catch(RunTimeException ex) {
        ts1.rollback();//回滚第一个事务
    } finally {
        //释放资源
    }
}
```


PROPAGATION_NOT_SUPPORTED
总是非事务地执行，并挂起任何存在的事务。

PROPAGATION_NOT_SUPPORTED
总是非事务地执行，并挂起任何存在的事务。

使用PROPAGATION_NOT_SUPPORTED,也需要使用JtaTransactionManager作为事务管理器。



PROPAGATION_NEVER
总是非事务地执行，如果存在一个活动事务，则抛出异常。

PROPAGATION_NESTED
如果一个活动的事务存在，则运行在一个嵌套的事务中。

如果没有活动事务,则按TransactionDefinition.PROPAGATION_REQUIRED 属性执行。

这是一个嵌套事务,使用JDBC3.0驱动时,仅仅支持DataSourceTransactionManager作为事务管理器。 需要JDBC 驱动的java.sql.Savepoint类。使用PROPAGATION_NESTED，还需要把PlatformTransactionManager的nestedTransactionAllowed属性设为true(属性值默认为false)。



```
@Transactional(propagation = Propagation.REQUIRED)
methodA(){
    doSomeThingA();
    methodB();
    doSomeThingB();
}

@Transactional(propagation = Propagation.NEWSTED)
methodB(){
    // do something
}
```

单独调用methodB方法，则按REQUIRED属性执行。如果调用methodA方法，则相当于：

```
main(){
    Connection con = null;
    Savepoint savepoint = null;
    try{
        con = getConnection();
        con.setAutoCommit(false);
        doSomeThingA();
        savepoint = con2.setSavepoint();
        try{
            methodB();
        } catch(RuntimeException ex) {
            con.rollback(savepoint);
        } finally {
            //释放资源
        }
        doSomeThingB();
        con.commit();
    } catch(RuntimeException ex) {
        con.rollback();
    } finally {
        //释放资源
    }
}
```


当methodB方法调用之前，调用setSavepoint方法，保存当前的状态到savepoint。如果methodB方法调用失败，则恢复到之前保存的状态。

当methodB方法调用之前，调用setSavepoint方法，保存当前的状态到savepoint。如果methodB方法调用失败，则恢复到之前保存的状态。

需要注意的是，这时的事务并没有进行提交，如果后续的代码(doSomeThingB()方法)调用失败，则回滚包括methodB方法的所有操作。嵌套事务一个非常重要的概念就是内层事务依赖于外层事务。外层事务失败时，会回滚内层事务所做的动作。而内层事务操作失败并不会引起外层事务的回滚。



#### Spring事务配置方式

Spring配置文件中关于事务配置总是由三个组成部分，分别是DataSource、TransactionManager和代理机制这三部分，无论哪种配置方式，一般变化的只是代理机制这部分。

DataSource、TransactionManager这两部分只是会根据数据访问方式有所变化，比如使用Hibernate进行数据访问时，DataSource实际为SessionFactory，TransactionManager的实现为HibernateTransactionManager。

具体如下图：

![img](https://img-blog.csdn.net/20131212094707828?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvaGptNDcwMjE5Mg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)




 根据代理机制的不同，总结了五种Spring事务的配置方式，配置文件如下：

第一种方式：每个Bean都有一个代理

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:aop="http://www.springframework.org/schema/aop"
    xsi:schemaLocation="http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context-2.5.xsd
           http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.5.xsd">

<bean id="sessionFactory"  
        class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">  
    <property name="configLocation" value="classpath:hibernate.cfg.xml" />  
    <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
</bean>  

<!-- 定义事务管理器（声明式的事务） -->  
<bean id="transactionManager"
    class="org.springframework.orm.hibernate3.HibernateTransactionManager">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

<!-- 配置DAO -->
<bean id="userDaoTarget" class="com.bluesky.spring.dao.UserDaoImpl">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

<bean id="userDao"  
    class="org.springframework.transaction.interceptor.TransactionProxyFactoryBean">  
       <!-- 配置事务管理器 -->  
       <property name="transactionManager" ref="transactionManager" />     
    <property name="target" ref="userDaoTarget" />  
     <property name="proxyInterfaces" value="com.bluesky.spring.dao.GeneratorDao" />
    <!-- 配置事务属性 -->  
    <property name="transactionAttributes">  
        <props>  
            <prop key="*">PROPAGATION_REQUIRED</prop>
        </props>  
    </property>  
</bean>  

</beans>
```

第二种方式：所有Bean共享一个代理基类

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:aop="http://www.springframework.org/schema/aop"
    xsi:schemaLocation="http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context-2.5.xsd
           http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.5.xsd">

<bean id="sessionFactory"  
        class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">  
    <property name="configLocation" value="classpath:hibernate.cfg.xml" />  
    <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
</bean>  

<!-- 定义事务管理器（声明式的事务） -->  
<bean id="transactionManager"
    class="org.springframework.orm.hibernate3.HibernateTransactionManager">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

<bean id="transactionBase"  
        class="org.springframework.transaction.interceptor.TransactionProxyFactoryBean"  
        lazy-init="true" abstract="true">  
    <!-- 配置事务管理器 -->  
    <property name="transactionManager" ref="transactionManager" />  
    <!-- 配置事务属性 -->  
    <property name="transactionAttributes">  
        <props>  
            <prop key="*">PROPAGATION_REQUIRED</prop>  
        </props>  
    </property>  
</bean>    

<!-- 配置DAO -->
<bean id="userDaoTarget" class="com.bluesky.spring.dao.UserDaoImpl">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

<bean id="userDao" parent="transactionBase" >  
    <property name="target" ref="userDaoTarget" />   
</bean>

</beans>
```

第三种方式：使用拦截器



```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:aop="http://www.springframework.org/schema/aop"
    xsi:schemaLocation="http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context-2.5.xsd
           http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.5.xsd">

<bean id="sessionFactory"  
        class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">  
    <property name="configLocation" value="classpath:hibernate.cfg.xml" />  
    <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
</bean>  

<!-- 定义事务管理器（声明式的事务） -->  
<bean id="transactionManager"
    class="org.springframework.orm.hibernate3.HibernateTransactionManager">
    <property name="sessionFactory" ref="sessionFactory" />
</bean> 

<bean id="transactionInterceptor"  
    class="org.springframework.transaction.interceptor.TransactionInterceptor">  
    <property name="transactionManager" ref="transactionManager" />  
    <!-- 配置事务属性 -->  
    <property name="transactionAttributes">  
        <props>  
            <prop key="*">PROPAGATION_REQUIRED</prop>  
        </props>  
    </property>  
</bean>

<bean class="org.springframework.aop.framework.autoproxy.BeanNameAutoProxyCreator">  
    <property name="beanNames">  
        <list>  
            <value>*Dao</value>
        </list>  
    </property>  
    <property name="interceptorNames">  
        <list>  
            <value>transactionInterceptor</value>  
        </list>  
    </property>  
</bean>  

<!-- 配置DAO -->
<bean id="userDao" class="com.bluesky.spring.dao.UserDaoImpl">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

</beans>


```

第四种方式：使用tx标签配置的拦截器



```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:aop="http://www.springframework.org/schema/aop"
    xmlns:tx="http://www.springframework.org/schema/tx"
    xsi:schemaLocation="http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context-2.5.xsd
           http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.5.xsd
           http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-2.5.xsd">

<context:annotation-config />
<context:component-scan base-package="com.bluesky" />

<bean id="sessionFactory"  
        class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">  
    <property name="configLocation" value="classpath:hibernate.cfg.xml" />  
    <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
</bean>  

<!-- 定义事务管理器（声明式的事务） -->  
<bean id="transactionManager"
    class="org.springframework.orm.hibernate3.HibernateTransactionManager">
    <property name="sessionFactory" ref="sessionFactory" />
</bean>

<tx:advice id="txAdvice" transaction-manager="transactionManager">
    <tx:attributes>
        <tx:method name="*" propagation="REQUIRED" />
    </tx:attributes>
</tx:advice>

<aop:config>
    <aop:pointcut id="interceptorPointCuts"
        expression="execution(* com.bluesky.spring.dao.*.*(..))" />
    <aop:advisor advice-ref="txAdvice"
        pointcut-ref="interceptorPointCuts" />        
</aop:config>      

</beans>
```



第五种方式：全注解

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xmlns:aop="http://www.springframework.org/schema/aop"
    xmlns:tx="http://www.springframework.org/schema/tx"
    xsi:schemaLocation="http://www.springframework.org/schema/beans 
           http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
           http://www.springframework.org/schema/context
           http://www.springframework.org/schema/context/spring-context-2.5.xsd
           http://www.springframework.org/schema/aop http://www.springframework.org/schema/aop/spring-aop-2.5.xsd
           http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-2.5.xsd">
```



    <context:annotation-config />
    <context:component-scan base-package="com.bluesky" />
     
    <tx:annotation-driven transaction-manager="transactionManager"/>
     
    <bean id="sessionFactory"  
            class="org.springframework.orm.hibernate3.LocalSessionFactoryBean">  
        <property name="configLocation" value="classpath:hibernate.cfg.xml" />  
        <property name="configurationClass" value="org.hibernate.cfg.AnnotationConfiguration" />
    </bean>  
     
    <!-- 定义事务管理器（声明式的事务） -->  
    <bean id="transactionManager"
        class="org.springframework.orm.hibernate3.HibernateTransactionManager">
        <property name="sessionFactory" ref="sessionFactory" />
    </bean>

</beans>

此时在DAO上需加上@Transactional注解，如下：



```
package com.bluesky.spring.dao;

import java.util.List;

import org.hibernate.SessionFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.orm.hibernate3.support.HibernateDaoSupport;
import org.springframework.stereotype.Component;

import com.bluesky.spring.domain.User;

@Transactional
@Component("userDao")
public class UserDaoImpl extends HibernateDaoSupport implements UserDao {

public List<User> listUsers() {
    return this.getSession().createQuery("from User").list();
}


​     
}
```

Spring声明式事务让我们从复杂的事务处理中得到解脱。使得我们再也无需要去处理获得连接、关闭连接、事务提交和回滚等这些操作。再也无需要我们在与事务相关的方法中处理大量的try…catch…finally代码。 
我们在使用Spring声明式事务时，有一个非常重要的概念就是事务属性。事务属性通常由事务的传播行为，事务的隔离级别，事务的超时值和事务只读标志组成。我们在进行事务划分时，需要进行事务定义，也就是配置事务的属性。 
Spring在TransactionDefinition接口中定义这些属性,以供PlatfromTransactionManager使用, PlatfromTransactionManager是spring事务管理的核心接口。 



1. ```
   1.	TransactionDefinition  
   2.	public interface TransactionDefinition {  
   3.	int getPropagationBehavior();  
   4.	int getIsolationLevel();  
   5.	int getTimeout();  
   6.	boolean isReadOnly();  
   7.	}  
   ```

   

getTimeout()方法，它返回事务必须在多少秒内完成。 
isReadOnly(),事务是否只读，事务管理器能够根据这个返回值进行优化，确保事务是只读的。 
getIsolationLevel()方法返回事务的隔离级别，事务管理器根据它来控制另外一个事务可以看到本事务内的哪些数据。 

在TransactionDefinition接口中定义了五个不同的事务隔离级别 
ISOLATION_DEFAULT 这是一个PlatfromTransactionManager默认的隔离级别，使用数据库默认的事务隔离级别.另外四个与JDBC的隔离级别相对应 
ISOLATION_READ_UNCOMMITTED 这是事务最低的隔离级别，它充许别外一个事务可以看到这个事务未提交的数据。这种隔离级别会产生脏读，不可重复读和幻像读。 
  例如: 
  Mary的原工资为1000,财务人员将Mary的工资改为了8000，但未提交事务 

Java代码  

1. ```
   1. Connection con1 = getConnection();  
   
   2. con.setAutoCommit(false);  
   
   3. update employee set salary = 8000 where empId ="Mary";  
   ```

   


与此同时，Mary正在读取自己的工资 

Java代码  

1. ```
   1. Connection con2 = getConnection();  
   
   2. select  salary from employee where empId ="Mary";  
   
   3. con2.commit();  
   
   
   ```

   

Mary发现自己的工资变为了8000，欢天喜地！ 
而财务发现操作有误，而回滚了事务,Mary的工资又变为了1000 

Java代码  

1. ```
   1. //con1  
   
   2. con1.rollback();  
   ```

   


像这样,Mary记取的工资数8000是一个脏数据。 

ISOLATION_READ_COMMITTED  保证一个事务修改的数据提交后才能被另外一个事务读取。另外一个事务不能读取该事务未提交的数据。这种事务隔离级别可以避免脏读出现，但是可能会出现不可重复读和幻像读。 

ISOLATION_REPEATABLE_READ  这种事务隔离级别可以防止脏读，不可重复读。但是可能出现幻像读。它除了保证一个事务不能读取另一个事务未提交的数据外，还保证了避免下面的情况产生(不可重复读)。 

在事务1中，Mary 读取了自己的工资为1000,操作并没有完成 

Java代码  

1. ```
   1. con1 = getConnection();  
   
   2. select salary from employee empId ="Mary";  
   ```

   



在事务2中，这时财务人员修改了Mary的工资为2000,并提交了事务. 

Java代码  

1. ```
   1. con2 = getConnection();  
   
   2. update employee set salary = 2000;  
   
   3. con2.commit();  
   ```

   



在事务1中，Mary 再次读取自己的工资时，工资变为了2000 

Java代码  

1. ```
   1. //con1  
   
   2. select salary from employee empId ="Mary";  
   ```

   



在一个事务中前后两次读取的结果并不致，导致了不可重复读。 
使用ISOLATION_REPEATABLE_READ可以避免这种情况发生。 

ISOLATION_SERIALIZABLE 这是花费最高代价但是最可靠的事务隔离级别。事务被处理为顺序执行。除了防止脏读，不可重复读外，还避免了幻像读。 

目前工资为1000的员工有10人。 
事务1,读取所有工资为1000的员工。 

Java代码  

1. ```
   1. con1 = getConnection();  
   
   2. Select * from employee where salary =1000;  
   ```

   

共读取10条记录 

这时另一个事务向employee表插入了一条员工记录，工资也为1000 

Java代码  

1. ```
   1. con2 = getConnection();  
   
   2. Insert into employee(empId,salary) values("Lili",1000);  
   
   3. con2.commit();  
   ```

   



事务1再次读取所有工资为1000的员工 

Java代码  

1. ```
   1. //con1  
   
   2. select * from employee where salary =1000;  
   ```

   



共读取到了11条记录，这就产生了幻像读。 
ISOLATION_SERIALIZABLE能避免这样的情况发生。但是这样也耗费了最大的资源。 

getPropagationBehavior()返回事务的传播行为，由是否有一个活动的事务来决定一个事务调用。 

在TransactionDefinition接口中定义了七个事务传播行为。 

PROPAGATION_REQUIRED 如果存在一个事务，则支持当前事务。如果没有事务则开启一个新的事务。 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED  
   
   2. methodA{  
   
   3. ……  
   
   4. methodB();  
   
   5. ……  
   
   6. }  
   
   7. 
   
   8. //事务属性 PROPAGATION_REQUIRED  
   
   9. methodB{  
   
   10. ……  
   
   11.}  
   ```

   


使用spring声明式事务，spring使用AOP来支持声明式事务，会根据事务属性，自动在方法调用之前决定是否开启一个事务，并在方法执行之后决定事务提交或回滚事务。 

单独调用methodB方法 

Java代码  

1. ```
   1. main{  
   
   2. metodB();  
   
   3. } 
   ```

    


相当于 

Java代码  

1. ```
   1. Main{  
   
   2. Connection con=null;  
   
   3. 
   
   4. rry{  
   
   5. con = getConnection();  
   
   6. con.setAutoCommit(false);  
   
   7. //方法调用  
   
   8. methodB();  
   
   9. //提交事务  
   
   10.con.commit();  
   
   11.}  
   
   12.Catch(RuntimeException ex){  
   
   13.  //回滚事务  
   
   14.  con.rollback();    
   
   15.}  
   
   16.finally{  
   
   17.  //释放资源  
   
   18.  closeCon();  
   
   19.}  
   
   20.}  
   ```

   


Spring保证在methodB方法中所有的调用都获得到一个相同的连接。在调用methodB时，没有一个存在的事务，所以获得一个新的连接，开启了一个新的事务。 

单独调用MethodA时，在MethodA内又会调用MethodB. 

执行效果相当于 

Java代码  

1. ```
   1. main{  
   
   2. Connection con = null;  
   
   3. try{  
   
   4. con = getConnection();  
   
   5. methodA();  
   
   6. con.commit();  
   
   7. }  
   
   8. cathc(RuntimeException ex){  
   
   9. con.rollback();  
   
   10.}  
   
   11.finally{  
   
   12.  closeCon();  
   
   13.}   
   
   14.}  
   ```

   


调用MethodA时，环境中没有事务，所以开启一个新的事务. 
当在MethodA中调用MethodB时，环境中已经有了一个事务，所以methodB就加入当前事务。 

PROPAGATION_SUPPORTS 如果存在一个事务，支持当前事务。如果没有事务，则非事务的执行。但是对于事务同步的事务管理器，PROPAGATION_SUPPORTS与不使用事务有少许不同。 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. methodB();  
   
   4. }  
   
   5. 
   
   6. //事务属性 PROPAGATION_SUPPORTS   
   
   7. methodB(){  
   
   8. ……  
   
   9. }  
   
   
   单纯的调
   ```

   用methodB时，methodB方法是非事务的执行的。 
   当调用methdA时,methodB则加入了methodA的事务中,事务地执行。 

PROPAGATION_MANDATORY 如果已经存在一个事务，支持当前事务。如果没有一个活动的事务，则抛出异常。 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. methodB();  
   
   4. }  
   
   5. 
   
   6. //事务属性 PROPAGATION_MANDATORY   
   
   7. methodB(){  
   
   8. ……  
   
   9. }  
   ```

   


当单独调用methodB时，因为当前没有一个活动的事务，则会抛出异常 
throw new IllegalTransactionStateException("Transactionpropagation 'mandatory' but no existing transaction found"); 

当调用methodA时，methodB则加入到methodA的事务中，事务地执行。 

PROPAGATION_REQUIRES_NEW 总是开启一个新的事务。如果一个事务已经存在，则将这个存在的事务挂起。 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. doSomeThingA();  
   
   4. methodB();  
   
   5. doSomeThingB();  
   
   6. }  
   
   7. 
   
   8. //事务属性 PROPAGATION_REQUIRES_NEW   
   
   9. methodB(){  
   
   10. ……  
   
   11.}  
   ```

   


当单独调用methodB时，相当于把methodb声明为REQUIRED。开启一个新的事务，事务地执行。 

当调用methodA时 

Java代码  

1. ```
   1. main(){  
   
   2. methodA();  
   
   3. }  
   ```

   

情况有些大不一样.相当于下面的效果。 

Java代码  

1. ```
   1. main(){  
   
   2. TransactionManager tm = null;  
   
   3. try{  
   
   4. //获得一个JTA事务管理器  
   
   5. tm = getTransactionManager();  
   
   6. tm.begin();//开启一个新的事务  
   
   7. Transaction ts1 = tm.getTransaction();  
   
   8. doSomeThing();  
   
   9. tm.suspend();//挂起当前事务  
   
   10. try{  
   
   11. tm.begin();//重新开启第二个事务  
   
   12. Transaction ts2 = tm.getTransaction();  
   
   13. methodB();  
   
   14. ts2.commit();//提交第二个事务  
   
   15. 
   
   16. }  
   
   17. Catch(RunTimeException ex){  
   
   18. ts2.rollback();//回滚第二个事务  
   
   19. }  
   
   20. finally{  
   
   21. //释放资源  
   
   22. }  
   
   23. //methodB执行完后，复恢第一个事务  
   
   24. tm.resume(ts1);  
   
   25.doSomeThingB();  
   
   26.   ts1.commit();//提交第一个事务  
   
   27.}  
   
   28.catch(RunTimeException ex){  
   
   29.  ts1.rollback();//回滚第一个事务  
   
   30.}  
   
   31.finally{  
   
   32.  //释放资源  
   
   33.}  
   
   34.}  
   ```

   


在这里，我把ts1称为外层事务，ts2称为内层事务。从上面的代码可以看出，ts2与ts1是两个独立的事务，互不相干。Ts2是否成功并不依赖于ts1。如果methodA方法在调用methodB方法后的doSomeThingB方法失败了，而methodB方法所做的结果依然被提交。而除了methodB之外的其它代码导致的结果却被回滚了。 
使用PROPAGATION_REQUIRES_NEW,需要使用JtaTransactionManager作为事务管理器。 

PROPAGATION_NOT_SUPPORTED  总是非事务地执行，并挂起任何存在的事务。 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. doSomeThingA();  
   
   4. methodB();  
   
   5. doSomeThingB();  
   
   6. }  
   
   7. 
   
   8. //事务属性 PROPAGATION_NOT_SUPPORTED   
   
   9. methodB(){  
   
   10. ……  
   
   11.}  
   ```

   


当单独调用methodB时，不启用任何事务机制，非事务地执行。 
当调用methodA时，相当于下面的效果 

Java代码  

1. ```
   1. main(){  
   
   2. TransactionManager tm = null;  
   
   3. try{  
   
   4. //获得一个JTA事务管理器  
   
   5. tm = getTransactionManager();  
   
   6. tm.begin();//开启一个新的事务  
   
   7. Transaction ts1 = tm.getTransaction();  
   
   8. doSomeThing();  
   
   9. tm.suspend();//挂起当前事务  
   
   10. methodB();  
   
   11. //methodB执行完后，复恢第一个事务  
   
   12. tm.resume(ts1);  
   
   13.doSomeThingB();  
   
   14.   ts1.commit();//提交第一个事务  
   
   15.}  
   
   16.catch(RunTimeException ex){  
   
   17.  ts1.rollback();//回滚第一个事务  
   
   18.}  
   
   19.finally{  
   
   20.  //释放资源  
   
   21.}  
   
   22.}  
   ```

   

使用PROPAGATION_NOT_SUPPORTED,也需要使用JtaTransactionManager作为事务管理器。 

PROPAGATION_NEVER 总是非事务地执行，如果存在一个活动事务，则抛出异常 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. doSomeThingA();  
   
   4. methodB();  
   
   5. doSomeThingB();  
   
   6. }  
   
   7. 
   
   8. //事务属性 PROPAGATION_NEVER   
   
   9. methodB(){  
   
   10. ……  
   
   11.}  
   ```

   

单独调用methodB，则非事务的执行。 
调用methodA则会抛出异常 
throw new IllegalTransactionStateException( 
"Transaction propagation 'never' butexisting transaction found"); 


PROPAGATION_NESTED如果一个活动的事务存在，则运行在一个嵌套的事务中. 如果没有活动事务, 则按TransactionDefinition.PROPAGATION_REQUIRED 属性执行 

这是一个嵌套事务,使用JDBC 3.0驱动时,仅仅支持DataSourceTransactionManager作为事务管理器。需要JDBC 驱动的java.sql.Savepoint类。有一些JTA的事务管理器实现可能也提供了同样的功能。 

使用PROPAGATION_NESTED，还需要把PlatformTransactionManager的nestedTransactionAllowed属性设为true; 
而nestedTransactionAllowed属性值默认为false; 

Java代码  

1. ```
   1. //事务属性 PROPAGATION_REQUIRED   
   
   2. methodA(){  
   
   3. doSomeThingA();  
   
   4. methodB();  
   
   5. doSomeThingB();  
   
   6. }  
   
   7. 
   
   8. //事务属性 PROPAGATION_NESTED  
   
   9. methodB(){  
   
   10. ……  
   
   11.}  
   
   
   如果
   ```

   单独调用methodB方法，则按REQUIRED属性执行。 

如果调用methodA方法，相当于下面的效果 

Java代码  

1. ```
   1. main(){  
   
   2. Connection con = null;  
   
   3. Savepoint savepoint = null;  
   
   4. try{  
   
   5. con = getConnection();  
   
   6. con.setAutoCommit(false);  
   
   7. doSomeThingA();  
   
   8. savepoint = con2.setSavepoint();  
   
   9. try  
   
   10. methodB();  
   
   11. }catch(RuntimeException ex){  
   
   12. con.rollback(savepoint);  
   
   13. }  
   
   14. finally{  
   
   15. //释放资源  
   
   16. }  
   
   17. 
   
   18. doSomeThingB();  
   
   19. con.commit();  
   
   20.}  
   
   21.catch(RuntimeException ex){  
   
   22.  con.rollback();  
   
   23.}  
   
   24.finally{  
   
   25.  //释放资源  
   
   26.}  
   
   27.}  
   ```

   

当methodB方法调用之前，调用setSavepoint方法，保存当前的状态到savepoint。如果methodB方法调用失败，则恢复到之前保存的状态。但是需要注意的是，这时的事务并没有进行提交，如果后续的代码(doSomeThingB()方法)调用失败，则回滚包括methodB方法的所有操作。 

嵌套事务一个非常重要的概念就是内层事务依赖于外层事务。外层事务失败时，会回滚内层事务所做的动作。而内层事务操作失败并不会引起外层事务的回滚。 

PROPAGATION_NESTED与PROPAGATION_REQUIRES_NEW的区别:它们非常类似,都像一个嵌套事务，如果不存在一个活动的事务，都会开启一个新的事务。使用PROPAGATION_REQUIRES_NEW时，内层事务与外层事务就像两个独立的事务一样，一旦内层事务进行了提交后，外层事务不能对其进行回滚。两个事务互不影响。两个事务不是一个真正的嵌套事务。同时它需要JTA事务管理器的支持。 
使用PROPAGATION_NESTED时，外层事务的回滚可以引起内层事务的回滚。而内层事务的异常并不会导致外层事务的回滚，它是一个真正的嵌套事务。DataSourceTransactionManager使用savepoint支持PROPAGATION_NESTED时，需要JDBC 3.0以上驱动及1.4以上的JDK版本支持。其它的JTA TrasactionManager实现可能有不同的支持方式。 

PROPAGATION_REQUIRED应该是我们首先的事务传播行为。它能够满足我们大多数的事务需求。 

```
@Transactional(propagation = Propagation.REQUIRED, rollbackFor = { AppBizExeA.class } , noRollbackFor = { AppBizExeB.class })  
    public void method1() throws Exception {  
        System.out.println("method1 start");  
        TPerson per = new TPerson();  
        per.setAge("24");  
        per.setId(123);  
        per.setName("xj");  
        personDao.add(per);  
        throw new NullPointerException();  
    }  
```





    @Transactional(propagation = Propagation.NESTED, rollbackFor = { AppBizExeA.class })  
    public void method2() throws Exception {  
        System.out.println("method2 start");  
        TPerson per = new TPerson();  
        per.setAge("24");  
        per.setId(1234);  
        per.setName("xj");  
        personDao.add(per);  
        System.out.println("method2 end");  
      
    }  

Java代码  

1. ```
   1. public static void main(String[] args) throws Exception {  
   
   2. 
   
   3. ApplicationContext context = new ClassPathXmlApplicationContext(new String[] { "classpath:com/benx/benx.xml" });  
   
   4. PersonService service = (PersonService) context.getBean("personService");  
   
   5. service.method1();  
   
   6. 
   
   7. }  
   ```

   

 

 

 

今天只谈传播行为为REQUIRED的，其他先不谈，因为使用比较少，而且支持也不够好

 

1、执行service.method1()，不管method里面是否嵌套了method2或其他，事务都是以method1开始和结尾，且事务配置同样以method1为准，忽略其他REQUIRED行为的配置，比如异常机制，以method1为准，忽略method2的异常配置

 

2、Transactional的异常控制，默认是Check Exception 不回滚，unCheck Exception回滚

 

3、如果配置了rollbackFor 和 noRollbackFor 且两个都是用同样的异常，那么遇到该异常，还是回滚

 

4、rollbackFor 和noRollbackFor 配置也许不会含盖所有异常，对于遗漏的按照Check Exception 不回滚，unCheck Exception回滚

 


 @Transactional只能被应用到public方法上, 对于其它非public的方法,如果标记了@Transactional也不会报错,但方法没有事务功能.

Spring使用声明式事务处理，默认情况下，如果被注解的数据库操作方法中发生了unchecked异常，所有的数据库操作将rollback；如果发生的异常是checked异常，默认情况下数据库操作还是会提交的。
这种默认的行为是可以改变的。


使用@Transactional注解的noRollbackFor和rollbackFor属性

如：@Transactional(rollbackFor=Exception.class)可以使checked异常发生时，数据库操作也rollback、@Transactional(noRollbackFor=RuntimeException.class)可以使unchecked异常发生时也提交数据库操作。

也可以使用noRollbackForClassName、rollbackForClassName属性来指定一个异常类名的String数组来改变默认的行为。



读取数据库中的数据时是不需要事务管理的，这种情况下可以使用事务的传播行为来告诉Spring不需要开启事务，
如：@Transactional(propagation =Propagation.NOT_SUPPORTED)。

##### 事务的传播行为有：

1.           REQUIRED：表示业务方法需要在一个事务中处理，如果业务方法执行时已经在一个事务中，则加入该事务，否则重新开启一个事务。这也是默认的事务传播行为；

2.           NOT_SUPPORTED：声明业务方法不需要事务，如果业务方法执行时已经在一个事务中，则事务被挂起，等方法执行完毕后，事务恢复进行；

3.           REQUIRES_NEW：表明业务方法需要在一个单独的事务中进行，如果业务方法进行时已经在一个事务中，则这个事务被挂起，并重新开启一个事务来执行这个业务方法，业务方法执行完毕后，原来的事务恢复进行；

4.           MANDATORY：该属性指定业务方法只能在一个已经存在的事务中进行，业务方法不能发起自己的事务；如果业务方法没有在一个既有的事务中进行，容器将抛出异常；

5.           SUPPORTS：该属性指定，如果业务方法在一个既有的事务中进行，则加入该事务；否则，业务方法将在一个没有事务的环境下进行；

6.           NEVER：指定业务方法不可以在事务中进行，如果业务方法执行时已经在一个事务中，容器将抛出异常；

7.           NESTED：该属性指定，如果业务方法在一个既有的事务中执行，则该业务方法将在一个嵌套的事务中进行；否则，按照REQUEIRED来对待。它使用一个单独的事务，这个事务可以有多个rollback点，内部事务的rollback对外部事务没有影响，但外部事务的rollback会导致内部事务的rollback。这个行为只对DataSourceTransactionManager有效。

 

事务的隔离级别

  使用@Transactional的Isolation属性可以指定事务的隔离级别。但事务的隔离级别是由底层的数据库实现的，并不是由Spring来实现。

1.       READ_UNCOMMITTED：会出现脏读、不可重复读和幻读问题；

2.       READ_COMMITTED：会出现不可重复读和幻读问题；

3.       REPEATABLE_READ：会出现幻读问题；

4.       SERIALIZABLE：串行化，不会出现上面的问题。

  一般的数据库默认提供的是READ_COMMITTED隔离级别，如sqlserver2000；Mysql默认提供的是REPEATABLE_READ。

@Transactional  的所有可选属性如下:
属性     类型     默认值     说明
propagation                            Propagation枚举    REQUIRED     事务传播属性 
isolation                                   isolation枚举            DEFAULT     事务隔离级别
readOnly                                  boolean                    false     是否只读
timeout                                      int                            -1     超时(秒)
rollbackFor                              Class[]  {}                 需要回滚的异常类
rollbackForClassName          String[]  {}                 需要回滚的异常类名
noRollbackFor                        Class[]  {}                 不需要回滚的异常类
noRollbackForClassName     String[]  {}                 不需要回滚的异常类名



```
//事务传播属性
    @Transactional(propagation=Propagation.REQUIRED) //如果有事务,那么加入事务,没有的话新建一个(不写的情况下)
    @Transactional(propagation=Propagation.NOT_SUPPORTED) //容器不为这个方法开启事务
    @Transactional(propagation=Propagation.REQUIRES_NEW) //不管是否存在事务,都创建一个新的事务,原来的挂起,新的执行完毕,继续执行老的事务
    @Transactional(propagation=Propagation.MANDATORY) //必须在一个已有的事务中执行,否则抛出异常
    @Transactional(propagation=Propagation.NEVER) //必须在一个没有的事务中执行,否则抛出异常(与Propagation.MANDATORY相反)
    @Transactional(propagation=Propagation.SUPPORTS) //如果其他bean调用这个方法,在其他bean中声明事务,那就用事务.如果其他bean没有声明事务,那就不用事务.
    
```




    @Transactional(propagation=Propagation.NESTED) 
    @Transactional (propagation =Propagation.REQUIRED,readOnly=true) //readOnly=true只读,不能更新,删除 
    @Transactional (propagation =Propagation.REQUIRED,timeout=30)//设置超时时间 
    @Transactional (propagation =Propagation.REQUIRED,isolation=Isolation.DEFAULT)//设置数据库隔离级别

```
用 spring 事务管理器,由spring来负责数据库的打开,提交,回滚.
默认遇到运行期例外(throw new RuntimeException("注释");)会回滚，即遇到不受检查（unchecked）的例外时回滚；
而遇到需要捕获的例外(throw new Exception("注释");)不会回滚,即遇到受检查的例外（就是非运行时抛出的异常，编译器会检查到的异常叫受检查例外或说受检查异常）时，需我们指定方式来让事务回滚 ,如下:
@Transactional(rollbackFor=Exception.class) //指定回滚,遇到异常Exception时回滚
    public void methodName() {
       throw new Exception("注释");
       

}

@Transactional(noRollbackFor=Exception.class)//指定不回滚,遇到运行期例外(throw newRuntimeException("注释");)会回滚
    public ItimDaoImpl getItemDaoImpl() {
        throw new RuntimeException("注释");
    } 
```


















#### Spring事务的隔离级别

```
事务隔离级别定义TransactionDefinition

int ISOLATION_DEFAULT = -1;
int ISOLATION_READ_UNCOMMITTED = 1;
int ISOLATION_READ_COMMITTED = 2;
int ISOLATION_REPEATABLE_READ = 4;
int ISOLATION_SERIALIZABLE = 8;
```

隔离级别	解释
ISOLATION_DEFAULT	这是个 PlatfromTransactionManager 默认的隔离级别， 使用数据库默认的事务隔离级别。另外四个与 JDBC 的 隔离级别相对应。
ISOLATION_READ_UNCOMMITTED	这是事务最低的隔离级别，它允许另外一个事务可以看 到这个事务未提交的数据。这种隔离级别会产生脏读， 不可重复读和幻像读。
ISOLATION_READ_COMMITTED	保证一个事务修改的数据提交后才能被另外一个事务读 取。另外一个事务不能读取该事务未提交的数据。 ISOLATION_REPEATABLE_READ
ISOLATION_SERIALIZABLE	这是花费最高代价但是最可靠的事务隔离级别。事务被 处理为顺序执行。

#### **Spring事务基本配置样例**

```
<aop:aspectj-autoproxy proxy-target-class="true"/>
	
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
	<property name="dataSource" ref="dataSource"/>
</bean>

<tx:advice id="transactionAdvice" transaction-manager="transactionManager">
	<tx:attributes>
		<tx:method name="add*" propagation="REQUIRED" rollback-for="Exception,RuntimeException,SQLException"/>
		<tx:method name="remove*" propagation="REQUIRED" rollback-for="Exception,RuntimeException,SQLException"/>
		<tx:method name="edit*" propagation="REQUIRED" rollback-for="Exception,RuntimeException,SQLException"/>
		<tx:method name="login" propagation="NOT_SUPPORTED"/>
		<tx:method name="query*" read-only="true"/>
	</tx:attributes>
</tx:advice>

<aop:config>
	<aop:advisor advice-ref="transactionAdvice" pointcut-ref="transactionPointcut"/>
    <aop:aspect ref="dataSource">
        <aop:pointcut id="transactionPointcut" expression="execution(public * com.gupaoedu..*.service..*Service.*(..))" />
    </aop:aspect>
</aop:config
```

#### spring事务失效场景

 `@Transactional` 

1. 数据库引擎是否支持事务（Mysql 的 MyIsam引擎不支持事务）；

2. 注解所在的类是否被加载为 Bean（是否被spring 管理）；未注释
3. 注解所在的方法是否为 public 修饰的；
4. 是否存在自身调用的问题；
5. 所用数据源是否加载了事务管理器；
6. @Transactional的扩展配置propagation是否正确
   

##### 自身调用问题

来看两个示例：

//示例1

@Service
public class OrderServiceImpl implements OrderService {

    public void update(Order order) {
        updateOrder(order);
    }
     
    @Transactional
    public void updateOrder(Order order) {
        // update order
    }

}
//示例2

@Service
public class OrderServiceImpl implements OrderService {

    @Transactional
    public void update(Order order) {
        updateOrder(order);
    }
     
    @Transactional(propagation = Propagation.REQUIRES_NEW)
    public void updateOrder(Order order) {
        // update order
    }

}
示例1 中，update方法上面没有加 @Transactional 注解，调用有 @Transactional 注解的 updateOrder 方法，updateOrder 方法上的事务管用吗？

示例2 中，update方法上面没有加 @Transactional 注解，调用有 @Transactional 注解的 updateOrder 方法，updateOrder 方法上的事务管用吗？

这两个例子的答案是：都不管用！

因为它们发生了自身调用，就调该类自己的方法，而没有经过 Spring 的代理类，默认只有在外部调用事务才会生效，这也是老生常谈的经典问题了。

这个的解决方案之一就是在的类中注入自己，用注入的对象再调用另外一个方法，这个不太优雅，另外一个可行的方案可以参考《Spring 如何在一个事务中开启另一个事务？》这篇文章。


##### 数据源没有配置事务管理器

如下代码所示，当前数据源若没有配置事务管理器，那也是白搭！

@Bean
public PlatformTransactionManager transactionManager(DataSource dataSource) {
    return new DataSourceTransactionManager(dataSource);
}
@Transactional的扩展配置不支持事务


Propagation.NOT_SUPPORTED： 表示不以事务运行，当前若存在事务则挂起。这表示不支持以事务的方式运行，所以即使事务生效也是白搭！

@Service
public class OrderServiceImpl implements OrderService {

    @Transactional
    public void update(Order order) {
        updateOrder(order);
    }
     
    @Transactional(propagation = Propagation.NOT_SUPPORTED)
    public void updateOrder(Order order) {
        // update order
    }

}
异常被吃了
这个也是出现比较多的场景：把异常吃了，然后又不抛出来，事务也不会回滚！

@Service
public class OrderServiceImpl implements OrderService {

    @Transactional
    public void updateOrder(Order order) {
        try {
            // update order
        } catch {
     
        }
    }

}
异常类型错误
接上面的例子，再抛出一个异常

@Service
public class OrderServiceImpl implements OrderService {

    @Transactional
    public void updateOrder(Order order) {
        try {
            // update order
        } catch {
            throw new Exception("更新错误");
        }
    }

}
这样事务也是不生效的，因为默认回滚的是：RuntimeException，如果你想触发其他异常的回滚，需要在注解上配置一下，如：

@Transactional(rollbackFor = Exception.class)
这个配置仅限于 Throwable 异常类及其子类。



# controller、service、dao调用关系

初做java项目前，了解一下各package下类的调用关系还是很有必要的

![img](https://img-blog.csdnimg.cn/20200721091036679.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMDI2NjY5,size_16,color_FFFFFF,t_70)

1：controller是为前端提供的访问入口，不用关心具体的业务逻辑。具体的业务逻辑放在了serviceImpl里，controller只需调用它封装好的方法即可。你可能会问：直接@Resource一个serviceImpl类不行吗，为什么要加个service。当然可以这么做，但用接口可以重写方法，更利于扩展。一般要求要有service的，咱不是要面向接口的编程嘛，最好还是加上吧。

2：service提供业务逻辑要用到的方法，serviceImpl提供方法的具体实现，@Service的a和controller里@Resource下的a要保持一致，否则controller找不到a。出现下面的标志说明没写错，其他类间的调用也会有类似的标志，可以通过这个提示更快的排错

![img](https://img-blog.csdnimg.cn/20200721090024788.png)



![img](https://img-blog.csdnimg.cn/20200721090124388.png)

3：dao为serviceImpl提供操作数据的方法，但方法的具体实现(也就是SQL语句)放在了mapper下的xml文件里，serviceImpl除了复杂它们间的逻辑关系，还可以对目标数据进行一些操作，比如不用从前端获取的数据可以在serviceImpl里赋值，调试后端代码时可以在这里给假数据，测方法有没有问题。同样，serviceImpl下的b和dao中的b也要保持一致，否则会找不到类。

4：mapper相当于dao的实现类，它下面是xml格式文件，xml里是SQL语句。示例：

![img](https://img-blog.csdnimg.cn/20200721091819642.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMDI2NjY5,size_16,color_FFFFFF,t_70)

![img](https://img-blog.csdnimg.cn/20200721091732152.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMDI2NjY5,size_16,color_FFFFFF,t_70)



写的方式和用到的注解不只这一种方式。

# PO BO VO DTO POJO DAO DO 在java中的概念

PO DTO VO BO 都叫POJO，就是个简单的java对象； 

DAO 是进行数据库增删改查的类。 

BO 业务对象，封装对象、复杂对象 ，里面可能包含多个类； 

DTO 传输对象，前端调用时传输 ； 

VO 表现对象，前端界面展示。 

po 持久化对象，它跟持久层（通常是关系型数据库）的数据结构形成一一对应的映射关系

PO：persistent object 持久对象

1 ．有时也被称为Data对象，对应数据库中的entity，可以简单认为一个PO对应数据库中的一条记录。

2 ．在hibernate持久化框架中与insert/delet操作密切相关。

3 ．PO中不应该包含任何对数据库的操作。

------

POJO ：plain ordinary java object 无规则简单java对象

一个中间对象，可以转化为PO、DTO、VO。

1 ．POJO持久化之后==〉PO

（在运行期，由Hibernate中的cglib动态把POJO转换为PO，PO相对于POJO会增加一些用来管理数据库entity状态的属性和方法。PO对于programmer来说完全透明，由于是运行期生成PO，所以可以支持增量编译，增量调试。）

2 ．POJO传输过程中==〉DTO

3 ．POJO用作表示层==〉VO

PO 和VO都应该属于它。

------

BO：business object 业务对象

业务对象主要作用是把业务逻辑封装为一个对象。这个对象可以包括一个或多个其它的对象。

比如一个简历，有教育经历、工作经历、社会关系等等。我们可以把教育经历对应一个PO，工作经历对应一个PO，社会关系对应一个PO。

建立一个对应简历的BO对象处理简历，每个BO包含这些PO。

这样处理业务逻辑时，我们就可以针对BO去处理。

封装业务逻辑为一个对象（可以包括多个PO，通常需要将BO转化成PO，才能进行数据的持久化，反之，从DB中得到的PO，需要转化成BO才能在业务层使用）。

关于BO主要有三种概念

1 、只包含业务对象的属性；

2 、只包含业务方法；

3 、两者都包含。

在实际使用中，认为哪一种概念正确并不重要，关键是实际应用中适合自己项目的需要。

------

VO：value object 值对象 / view object 表现层对象

1 ．主要对应页面显示（web页面/swt、swing界面）的数据对象。

2 ．可以和表对应，也可以不，这根据业务的需要。

------

DTO（TO）：Data Transfer Object 数据传输对象

1 ．用在需要跨进程或远程传输时，它不应该包含业务逻辑。

2 ．比如一张表有100个字段，那么对应的PO就有100个属性（大多数情况下，DTO内的数据来自多个表）。但view层只需显示10个字段，没有必要把整个PO对象传递到client，这时我们就可以用只有这10个属性的DTO来传输数据到client，这样也不会暴露server端表结构。到达客户端以后，如果用这个对象来对应界面显示，那此时它的身份就转为VO。

------

DAO：data access object数据访问对象

1 ．主要用来封装对DB的访问（CRUD操作）。

2 ．通过接收Business层的数据，把POJO持久化为PO。

简易的关系图：

![这里写图片描述](https://img-blog.csdn.net/20180717104224284?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTE4NzA1NDc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)