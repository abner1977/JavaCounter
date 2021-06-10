# 复习杂记

## 	一、基础

1、面向过程，是分析解决问题的步骤，每个步骤挨个实现。性能高于面向对象。比如单片机、嵌入式开发
2、面向对象，描述的是事务在解决问题中的行为。属于行为的抽象。具有封装、继承、多态的特性。
3、byte 1  short 2  long 4   int 8  float 4  double  8  char   2 
4、装箱是自动将基本数据类型转换为包装器类型，拆箱相反。
5、重载是同一个类中多态的表现，方法名一致，参数不一致，返回值可相同，可不同。
6、重写发生在父子类中，方法名一致，参数一致，返回一致，方法修饰符的权限需要大于父类public>protected>default>private
异常方面不要抛出新的异常，就是异常也需要在父类的范围下。
7、 == 比较内存地址， equals 比较值大小。
8、HashCode 是为了提高集合中查找元素的效率。  （equals 对于数据量大的性能有影响。） hashcode返回的是对象内存地址换算的
值，这样集合新增元素是，会根据hashcode直接找到存放位置，如果没有直接存放，如果有就equals，减少equals次数，提升效率。
9、String 是只读字符串，一经定义，不可改动，对String的操作都会生成新的String对象。
10、对字符串频繁操作，使用StringBuffer（线程安全，加了同步锁）和StringBuilder 都继承AbstractStringBuilder。
11、ArrayList (底层是数组)和LinkList（底层是双向链表） 基于List 实现。 有序，可重复。 

12、HashMap(父类是 AbstractMap) 和 HashTable (父类是Dictionary)，同时都实现了map、Cloneable（可复制）、Serializable（可序列化） 三个接口
13、对外提供的接口，HashTable 多了elments（）和contains()  ；elments() 方法继承自Dictionnary。elements() 方法用于返回此Hashtable中的 value的枚举。contains()方法判断该Hashtable是否包含传入的value。
14、HashTable key value不支持null  HashMap key 可以为null 唯一 ，可以value多个null
15、HashTable 线程安全，HashMap 线程不安全,效率高。 多线程可以采用ConcurrentHashMap
16、初始容量大小和扩容不一样以及计算hash方法不通。

17、强 - 软 -  弱  - 虚  引用。对象本身的引用。  强 OOM不会回收   / 软 内存不足时， jvm优先回收早期创建的对象   /  弱 jvm发现即处理  / 虚 回收之前放在ReferenceQueue引用队列中，其他引用时回收之后放，并且创建虚引用，必须带有ReferenceQueue。 
18、java创建对象  new / 反射/  clone /序列化

19、hash冲突 
拉链法:每个哈希表节点都有一个next指针,多个哈希表节点可以用next指针构成一个单向链表，被 分配到同一个索引上的多个节点可以用这个单向链表进行存储. 
开放定址法:一旦发生了冲突,就去寻找下一个空的散列地址,只要散列表足够大,空的散列地址总能找 到,并将记录存入 
再哈希:又叫双哈希法,有多个不同的Hash函数.当发生冲突时,使用第二个,第三个….等哈希函数计算 地址,直到无冲突.
20、浅拷贝仅仅复制所考虑的对象,而不复制它所引用的对象 / 深拷贝把要复制的对象所引用的对象都 复制了一遍. 

21、被ﬁnal修饰的类不可以被继承 / 被ﬁnal修饰的方法不可以被重写  / 被ﬁnal修饰的变量不可以被改，如果修饰引用,那么表示引用不可变,引用指向的内容可变. 
22、 被ﬁnal修饰的常量,在编译阶段会存入常量池

23、static 修饰 静态变量 和静态方法  、 静态块 、 静态内部类、 静态导入 import static ，不需要使用类名 直接使用资源名。
24、+= 操作符会进行隐式自动类型转换,此处a+=b隐式的将加操作的结果类型强制转换为持有结果的类型。
25、 运行时异常 ClassCastException（类转换异常） /  IndexOutOfBoundsException（数组越界）
NullPointerException（空指针异常） /  ArrayStoreException（数据存储异常，操作数组是类型不一致） / BuﬀerOverﬂowException 
26、被检查异常    CloneNotSupportedException / IOException /  FileNotFoundException / SQLException
27、错误  OutOfMemoryError
28、线程，是同类的多个线程共享同一块内存空间和一组系统资源，称为轻量级进程。
29、程序是含有指令和数据的文件，被存储在磁盘或其他的数据存储设备中，也就是说程序是静态的代码。
30、进程是程序的一次执行过程，是系统运行程序的基本单位。线程和进程大的不同在于基本上各进程是独立的，而各线程则不一定。，进程属于操作系统的范畴。
31、不想进行序列化的变量，使用 transient 关键字修饰。 。transient 只能修饰变量，不能修饰类和方法
32、反射  Class.forName(“类的路径”)； /  类名.class  / 对象名.getClass()  / 基本类型的包装类，可以调用包装类的Type属性来获得该包装类的Class对象 

## 二、spring

### ***1、IOC***

控制反转也叫依赖注入。工厂模式 ，对象交给容器管理，只需在spring配置文件总配置相应的bean，以及设置相关的属性，让 spring容器来生成类的实例对象以及管理对象。
（在spring容器启动的时候，spring会把你在配置文件 中配置的bean都初始化好，然后在你需要调用的时候，就把它已经初始化好的那些bean分配给你需要 调用这些bean的类（假设这个类名是A），分配的方法就是调用A的setter方法来注入，而不需要你在 A里面new这些bean了。 ）

### ***2、AOP***

**面向切面编程。（Aspect-Oriented Programming） ，处理的是公共行为**。包括动态代理，截取消息然后处理，取代原有对象的执行/ 静态织入，引入特定的语法创建“方面”，从而使得编 译器可以在编译期间织入有关“方面”的代码.

1. @Async注解的方法， 只有外部类调用才有效果
2. @Cache注解的方法， 只有外部类调用才有效果 ...` `**几乎所有spring特性必须要从外部调用才可以生效。自己调用自己类方法无效的。**  **通过this来调用是走的类自身的函数调用，而没有经过代理类，所以代理类的相关前置、后置等方法是不生效的。**`!!!!!!!!

#### **pointCut使用**

##### wildcards通配符

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221160058455.png" alt="image-20201221160058455" style="zoom:50%;" />

##### operators运算符

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221160139160.png" alt="image-20201221160139160" style="zoom:50%;" />

##### designators标识符

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221160241656.png" alt="image-20201221160241656" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221160419326.png" alt="image-20201221160419326" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221160830636.png" alt="image-20201221160830636" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221161331344.png" alt="image-20201221161331344" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221161638036.png" alt="image-20201221161638036" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162052475.png" alt="image-20201221162052475" style="zoom:50%;" />

#### advice使用

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162754684.png" alt="image-20201221162754684" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162826045.png" alt="image-20201221162826045" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162837078.png" alt="image-20201221162837078" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162847268.png" alt="image-20201221162847268" style="zoom:50%;" />



<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221162911164.png" alt="image-20201221162911164" style="zoom:50%;" />

#### 实现原理

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221163907361.png" alt="image-20201221163907361" style="zoom:50%;" />

#### 使用场景

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221173007668.png" alt="image-20201221173007668" style="zoom:50%;" />









### ***3、@Autowired 和 @Resource***

org.springframework.beans.factory.annotation.Autowired;只按照byType注入 ，可以写在字段和setter方法
（如果我们想使用按照名称（byName）来装配，可以结 合@Qualiﬁer注解一起使用。 
 @Autowired   
 @Qualifier("userDao")    
 private UserDao userDao
）
**@Resource**默认按照ByName自动注入 导入包javax.annotation.Resource ， 有name 和type 注入方式。
(最好是将@Resource放在setter方法上，因为这样更符合面向对象的思想，通过set、get去操作属 性，而不是直接去操作属性。)

### ***4、Bean实例化方式***

####  常规方式

构造器（配置元信息：xml、java注解和Java API）

静态工厂方法(配置元信息：xml和java api)

Bean工厂方法(配置元信息：xml和java api)

FactoryBean （配置元信息：xml、java注解和Java API）

#### 特殊方式

通过ServiceLoaderFactoryBean（配置元信息：xml、java注解和Java API）

通过AutowireCapableBeanFactory#Object createBean(Class<?> var1, int var2, boolean var3) throws BeansException;

通过BeanDefinitionRegistry#void registerBeanDefinition(String var1, BeanDefinition var2) throws BeanDefinitionStoreException;



5、Spring是一个轻量级的IoC和AOP容器框架。：基于XML的 配置、基于注解的配置、基于Java的配置。  主要模块
Spring Core：核心类库，提供IOC服务；
Spring Context：提供框架式的Bean访问方式，以及企业级功能（JNDI、定时任务等）； 
Spring AOP：AOP服务；
Spring DAO：对JDBC的抽象，简化了数据访问异常的处理；
 Spring ORM：对现有的ORM框架的支持；
 Spring Web：提供了基本的面向Web的综合特性，例如多方文件上传；
Spring MVC：提供面向Web应用的Model-View-Controller实现。 

### ***5、springmvc 流程***

![5bcab258-e372-424f-9139-e0f2795127cf](D:\dailySoftWare\typora\md\img\5bcab258-e372-424f-9139-e0f2795127cf.png)

1、 用户发送请求至前端控制器DispatcherServlet。
2、 DispatcherServlet收到请求调用HandlerMapping处理器映射器。
3、 处理器映射器找到具体的处理器(可以根据xml配置、注解进行查找)，生成处理器对象及处理器拦截 器(如果有则生成)一并返回给DispatcherServlet。 4、 DispatcherServlet调用HandlerAdapter处理器适配器。
5、 HandlerAdapter经过适配调用具体的处理器(Controller，也叫后端控制器)。 
6、 Controller执行完成返回ModelAndView。 
7、 HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet。
8、 DispatcherServlet将ModelAndView传给ViewReslover视图解析器。 
9、 ViewReslover解析后返回具体View。
10、DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。 公众号：Java专栏
11、 DispatcherServlet响应用户。 

### ***6、动态代理和静态代理***

1. 动态代理
   
   JDK只提供接口的代理，不支持类的代理。核心**InvocationHandler**接口和Proxy类， InvocationHandler 通过invoke()方法反射来调用目标类中的代码，动态地将横切逻辑和业务编织在一 起；接着，Proxy利用 InvocationHandler动态创建一个符合某一接口的的实例,  生成目标类的代理对 象。
   如果代理类没有实现 InvocationHandler 接口，那么Spring AOP会选择使用CGLIB来动态代理目 标类。
   
   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221165449015.png" alt="image-20201221165449015" style="zoom:50%;" />
   
   **其实就是动态的对目标类的方法进行增强，动态的生成了多个增强方法，而不需要像静态代理一般写多个方法。**
   
   
   
   CGLIB（Code Generation Library），是一个代码生成的类库，可以在运行时动态的生成指定类 的一个子类对象，并覆盖其中特定方法并添加增强代码，从而实现AOP。CGLIB是通过继承的方式做的动态代 理，因此如果某个类被标记为final，那么它是无法使用CGLIB做动态代理的。
   
   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221170304506.png" alt="image-20201221170304506" style="zoom:50%;" />![image-20201221170344008](C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221170344008.png)
   
   ![image-20201221170344008](C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221170344008.png)
   
   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221170823072.png" alt="image-20201221170823072" style="zoom:50%;" />
   
   
   
2. AspectJ是静态代理的增强，所谓静态代理，就是AOP框架会在编译阶段生成AOP代理类，因此也 称为编译时增强，他会在编译阶段将AspectJ(切面)织入到Java字节码中，运行的时候就是增强之后的 AOP对象。 （*<u>如果目标类的方法很多，静态代理需要对多个方法进行增强，而增强的方法一致，容易产生冗余代码。</u>*）

3. Spring AOP使用的动态代理，所谓的动态代理就是说AOP框架不会去修改字节码，而是**每次运行 时在内存中临时为方法生成一个AOP对象，这个AOP对象包含了目标对象的全部方法，并且在特定的切 点做了增强处理，并回调原对象的方法**。

   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221170936966.png" alt="image-20201221170936966" style="zoom:50%;" />

   ```java
   public class DefaultAopProxyFactory implements AopProxyFactory, Serializable {
       public DefaultAopProxyFactory() {
       }
   
       public AopProxy createAopProxy(AdvisedSupport config) throws AopConfigException {
           if (!config.isOptimize() && !config.isProxyTargetClass() && !this.hasNoUserSuppliedProxyInterfaces(config)) {
               return new JdkDynamicAopProxy(config);
           } else {
               Class<?> targetClass = config.getTargetClass();
               if (targetClass == null) {
                   throw new AopConfigException("TargetSource cannot determine target class: Either an interface or a target is required for proxy creation.");
               } else {
                   return (AopProxy)(!targetClass.isInterface() && !Proxy.isProxyClass(targetClass) ? new ObjenesisCglibAopProxy(config) : new JdkDynamicAopProxy(config));
               }
           }
       }
   
       private boolean hasNoUserSuppliedProxyInterfaces(AdvisedSupport config) {
           Class<?>[] ifcs = config.getProxiedInterfaces();
           return ifcs.length == 0 || ifcs.length == 1 && SpringProxy.class.isAssignableFrom(ifcs[0]);
       }
   }
   ```

   

   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221171159196.png" alt="image-20201221171159196" style="zoom:50%;" />

   

   <img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201221171429328.png" alt="image-20201221171429328" style="zoom:50%;" />

   

   

   

   

### ***7、bean 生命周期***

![16bc9fe0f8b19240 (1)](D:\dailySoftWare\typora\md\img\16bc9fe0f8b19240 (1).jpg)

**1、 实例化bean** 
对于BeanFactory容器，当客户向容器请求一个尚未初始化的bean时，或初始化bean的时候需要注入 另一个尚未初始化的依赖时，容器就会调用createBean进行实例化。对于ApplicationContext容器，当 容器启动结束后，通过获取BeanDeﬁnition对象中的信息，实例化所有的bean。 
**2、设置对象属性（依赖注入）**：
实例化后的对象被封装在BeanWrapper对象中，紧接着，Spring根据BeanDeﬁnition中的信息 以及 通 过BeanWrapper提供的设置属性的接口完成依赖注入。
**3、处理Aware接口**： 接着，Spring会检测该对象是否实现了xxxAware接口，并将相关的xxxAware实例注入给Bean：
①如果这个Bean已经实现了BeanNameAware接口，会调用它实现的setBeanName(String beanId)方 法，此处传递的就是Spring配置文件中Bean的id值； 
②如果这个Bean已经实现了BeanFactoryAware接口，会调用它实现的setBeanFactory()方法，传递的 是Spring工厂自身。 
③如果这个Bean已经实现了ApplicationContextAware接口，会调用 setApplicationContext(ApplicationContext)方法，传入Spring上下文；
**4、BeanPostProcessor**： 如果想对Bean进行一些自定义的处理，那么可以让Bean实现了BeanPostProcessor接口，那将会调用 postProcessBeforeInitialization(Object obj, String s)方法。

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201228172453.png" alt="TIM截图20201228172453" style="zoom:50%;" />

ApplicationContextAwareProcessor#invokeAwareInterfaces 实现

```java
public interface BeanPostProcessor {
    @Nullable
    default Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
        return bean;
    }
    @Nullable
    default Object postProcessAfterInitialization(Object bean, String beanName) throws BeansException {
        return bean;
    }
}
```

```java

class ApplicationContextAwareProcessor implements BeanPostProcessor {
    private final ConfigurableApplicationContext applicationContext;
    private final StringValueResolver embeddedValueResolver;


    @Nullable
    public Object postProcessBeforeInitialization(Object bean, String beanName) throws BeansException {
        AccessControlContext acc = null;
        if (System.getSecurityManager() != null && (bean instanceof EnvironmentAware || bean instanceof EmbeddedValueResolverAware || bean instanceof ResourceLoaderAware || bean instanceof ApplicationEventPublisherAware || bean instanceof MessageSourceAware || bean instanceof ApplicationContextAware)) {
            acc = this.applicationContext.getBeanFactory().getAccessControlContext();
        }

        if (acc != null) {
            AccessController.doPrivileged(() -> {
                this.invokeAwareInterfaces(bean);
                return null;
            }, acc);
        } else {
            this.invokeAwareInterfaces(bean);
        }

        return bean;
    }

    private void invokeAwareInterfaces(Object bean) {
        if (bean instanceof Aware) {
            if (bean instanceof EnvironmentAware) {
                ((EnvironmentAware)bean).setEnvironment(this.applicationContext.getEnvironment());
            }

            if (bean instanceof EmbeddedValueResolverAware) {
                ((EmbeddedValueResolverAware)bean).setEmbeddedValueResolver(this.embeddedValueResolver);
            }

            if (bean instanceof ResourceLoaderAware) {
                ((ResourceLoaderAware)bean).setResourceLoader(this.applicationContext);
            }

            if (bean instanceof ApplicationEventPublisherAware) {
                ((ApplicationEventPublisherAware)bean).setApplicationEventPublisher(this.applicationContext);
            }

            if (bean instanceof MessageSourceAware) {
                ((MessageSourceAware)bean).setMessageSource(this.applicationContext);
            }

            if (bean instanceof ApplicationContextAware) {
                ((ApplicationContextAware)bean).setApplicationContext(this.applicationContext);
            }
        }

    }

    public Object postProcessAfterInitialization(Object bean, String beanName) {
        return bean;
    }
}

```



5、InitializingBean 与 init-method**： 如果Bean在Spring配置文件中配置了 init-method 属性，则会自动调用其配置的初始化方法。 
**6、如果这个Bean实现了BeanPostProcessor接口**，将会调用postProcessAfterInitialization(Object obj, String s)方法；由于这个方法是在Bean初始化结束时调用的，所以可以被应用于内存或缓存技术；
以上几个步骤完成后，Bean就已经被正确创建了，之后就可以使用这个Bean了。 
**7、DisposableBean：**
当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean这个接口，会调用其实现的 destroy()方法； 
**8、destroy-method：**
如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法

### ***8、bean作用域***

（1）singleton：默认，每个容器中只有一个bean的实例，单例的模式由BeanFactory自身来维护。 
（2）prototype：为每一个bean请求提供一个实例。
（3）request：为每一个网络请求创建一个实例，在请求完成以后，bean会失效并被垃圾回收器回 收。
（4）session：与request范围类似，确保每个session中有一个bean的实例，在session过期后，bean 会随之失效。
（5）global-session：全局作用域，global-session和Portlet应用相关。当你的应用部署在Portlet容器 中工作时，它包含很多portlet。如果你想要声明让所有的portlet共用全局的存储变量的话，那么这全局 变量需要存储在global-session中。全局作用域与Servlet中的session作用域效果相同。

**Prototype 适合有状态的 Bean，而 Singleton 则更适合无状态的情况**

<u>singleton Bean 是否在应用中唯一？</u>

**否，仅在spring IOC容器 （BeanFactory）中 是单例对象。**  应用可能存在多个应用上下文（层次性上下文）

<u>静态字段在jvm是否唯一？</u>

**否，在classLoader中是唯一的。**张三的classloader和李四的classloader可能维护不同的静态变量，在同一个类中。



### **9、 **依赖注入方式

#### **xml注入方式**

（1）Set方法注入； （2）构造器注入：①通过index设置参数的位置；②通过type设置参数类型； （3）静态工厂注入；
（4）实例工厂

#### **依赖注入方式**

构造器注入（少依赖 强制依赖） /  setter注入（多依赖  非强制依赖） / 字段注入 （开发便利） / 方法注入（做声明 比如@Bean） / 接口回调注入 (生命周期回调 比如setApplicationContext setBeanFactory回调)

**构造器和setter注入都可以使用，如果必须依赖推荐构造物器注入，如果可选依赖，用setter**



**依赖注入和依赖查找来源**

来源不同，**依赖查找的来源仅限于Spring BeanDefinition （有完整的生命周期管理）以及单例对象（java api 调用registry 生存的方法）， 而依赖注入的来源还包括Resolvable Dependency（ConfigurableListableBeanFactory#registerResolvableDependency实现）以及@value所标注的外部化配置。**



<img src="D:\dailySoftWare\typora\md\img\TIM截图20201228170242.png" alt="TIM截图20201228170242" style="zoom:50%;" />

```java
    public void freezeConfiguration() {
        this.configurationFrozen = true;
        this.frozenBeanDefinitionNames = StringUtils.toStringArray(this.beanDefinitionNames);
    }
// BeanDefinition 默认实现DefaultListableBeanFactory 进行了冻结注册的操作，而单例实现类DefaultSingletonBeanRegistry 则是DefaultListableBeanFactory的父类 ，换言之 子类的状态无法控制父类的行为。所以是无限制的。
```



### ***10、spring设计模式例子***

（1）工厂模式：BeanFactory就是简单工厂模式的体现，用来创建对象的实例； 
（2）单例模式：Bean默认为单例模式。
（3）代理模式：Spring的AOP功能用到了JDK的动态代理和CGLIB字节码生成技术； 
（4）模板方法：用来解决代码重复的问题。比如. RestTemplate, JmsTemplate, JpaTemplate。
（5）观察者模式：定义对象键一种一对多的依赖关系，当一个对象的状态发生改变时，所有依赖于它 的对象都会得到通知被制动更新，如Spring中listener的实现--ApplicationListener。 

### 11、重点类、接口描述

#### BeanFactory

BeanFactory是提供了IOC容器最基本的形式，给**具体的IOC容器的实现提供了规范**

```java
//
// Source code recreated from a .class file by IntelliJ IDEA
// (powered by Fernflower decompiler)
//

package org.springframework.beans.factory;

import org.springframework.beans.BeansException;
import org.springframework.core.ResolvableType;

public interface BeanFactory {
    String FACTORY_BEAN_PREFIX = "&";

    Object getBean(String var1) throws BeansException;

    <T> T getBean(String var1, Class<T> var2) throws BeansException;

    <T> T getBean(Class<T> var1) throws BeansException;

    Object getBean(String var1, Object... var2) throws BeansException;

    <T> T getBean(Class<T> var1, Object... var2) throws BeansException;

    boolean containsBean(String var1);

    boolean isSingleton(String var1) throws NoSuchBeanDefinitionException;

    boolean isPrototype(String var1) throws NoSuchBeanDefinitionException;

    boolean isTypeMatch(String var1, ResolvableType var2) throws NoSuchBeanDefinitionException;

    boolean isTypeMatch(String var1, Class<?> var2) throws NoSuchBeanDefinitionException;

    Class<?> getType(String var1) throws NoSuchBeanDefinitionException;

    String[] getAliases(String var1);
}

```

**BeanFactory.getBean 是线程安全的。默认实现DefaultListableBeanFactory 中，对应BeanDefinition的获取加了synchronized互斥锁**。

```java
   synchronized(this.beanDefinitionMap) {
                    this.beanDefinitionMap.put(beanName, beanDefinition);
                    List<String> updatedDefinitions = new ArrayList(this.beanDefinitionNames.size() + 1);
                    updatedDefinitions.addAll(this.beanDefinitionNames);
                    updatedDefinitions.add(beanName);
                    this.beanDefinitionNames = updatedDefinitions;
                    this.removeManualSingletonName(beanName);
                }
```



#### FactoryBean

FactoryBean可以**说为IOC容器中Bean的实现提供了更加灵活的方式，**FactoryBean在IOC容器的基础上给Bean的实现加上了一个简单工厂模式和装饰模式，我们可以在getObject()方法中灵活配置。

```java
//
// Source code recreated from a .class file by IntelliJ IDEA
// (powered by Fernflower decompiler)
//

package org.springframework.beans.factory;

public interface FactoryBean<T> {
    T getObject() throws Exception;

    Class<?> getObjectType();

    boolean isSingleton();
}
```

```java
public class FactoryBeanPojo implements FactoryBean{
	private String type;
    // 重写getObject 简单工厂模式  对于bean的实现  增加了更加灵活的方式
	@Override
	public Object getObject() throws Exception {
		if("student".equals(type)){
			return new Student();			
		}else{
			return new School();
		}
    }
		
```

#### ApplicationContext

ApplicationContext是**具备应用特性的BeanFactory的超集**。

#### BeanDefinition

是spring Framework **定义Bean的配置元信息接口**，包含

Bean的类名

Bean的行为配置元素，如作用域、自动绑定的模式、生命周期回调等

其他Bean的引用，又称合作者或者依赖

配置设置，比如Bean属性Properties



<img src="D:\dailySoftWare\typora\md\img\微信图片_202012281547513.png" alt="微信图片_202012281547513" style="zoom:50%;" />

<u>BeanDefinition 通过BeanDefinitionBuilder 或者 AbstractBeanDefinition以及派生类 创建</u>

##### BeanDefinition注册

###### xml配置元信息 

```xml
<bean name ="" />
```

###### java注解配置

@Bean @Component @Import

###### Java api配置元信息

命名方式 BeanDefinitionRegistry#void registerBeanDefinition(String var1, BeanDefinition var2) throws BeanDefinitionStoreException

非命名方式 

BeanDefinitionReaderUtils#registerWithGeneratedName

```java
  public static String registerWithGeneratedName(AbstractBeanDefinition definition, BeanDefinitionRegistry registry) throws BeanDefinitionStoreException {
        String generatedName = generateBeanName(definition, registry, false);
        registry.registerBeanDefinition(generatedName, definition);
        return generatedName;
    }
```

AnnotatedBeanDefinitionReader#register

```java
  public void register(Class<?>... annotatedClasses) {
        Class[] var2 = annotatedClasses;
        int var3 = annotatedClasses.length;

        for(int var4 = 0; var4 < var3; ++var4) {
            Class<?> annotatedClass = var2[var4];
            this.registerBean(annotatedClass);
        }

    }
```



### 12、循环依赖

#### 分类

##### 构造器注入循环依赖

```java
@Service
public class A {
    public A(B b) {
    }
}
@Service
public class B {
    public B(A a) {
    }
}
```

Spring解决循环依赖依靠的是Bean的“中间态”这个概念，而这个中间态指的是**`已经实例化`**，但还没初始化的状态。而构造器是完成实例化的东东，所以构造器的循环依赖无法解决~~~

##### singleton模式field属性注入循环依赖

```java
@Service
public class A {
    @Autowired
    private B b;
}
 
@Service
public class B {
    @Autowired
    private A a;
}
```

启动成功

##### prototype模式field属性注入循环依赖

````java
@Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
@Service
public class A {
    @Autowired
    private B b;
}
 
@Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
@Service
public class B {
    @Autowired
    private A a;
}
````

**需要注意的是**本例中**启动时是不会报错的**（因为非单例Bean**`默认`**不会初始化，而是使用时才会初始化），所以很简单咱们只需要手动**`getBean()`**或者在一个单例Bean内**`@Autowired`**一下它即可

```java

// 在单例Bean内注入
    @Autowired
    private A a;
```

不能解决

#### 原理分析

1、对Bean的创建最为核心三个方法解释如下：

- createBeanInstance：例化，其实也就是调用对象的构造方法实例化对象
- populateBean：填充属性，这一步主要是对bean的依赖属性进行注入(@Autowired)   循环依赖主要发生在**第二步**
- initializeBean：回到一些形如initMethod、InitializingBean等方法

2、spring使用`三级缓存`处理

DefaultSingletonBeanRegistry 中

- singletonObjects：用于存放完全初始化好的 bean，从该缓存中取出的 bean 可以直接使用
- earlySingletonObjects：提前曝光的单例对象的cache，存放原始的 bean 对象（尚未填充属性），用于解决循环依赖
- singletonFactories：单例对象工厂的cache，存放 bean 工厂对象，用于解决循环依赖



<img src="D:\dailySoftWare\typora\md\img\2019061918335746.png" alt="2019061918335746" style="zoom:80%;" />

### 13、事务传播机制

#### PROPAGATION_REQUIRED

**若当前存在事务，则加入该事务，若不存在事务，则新建一个事务。**

**出现异常，都未进行捕获，同时回滚。**这点也有区别，PAOPAGATION_REQUIRE_NEW中functionOne出异常是不影响functionTwo正常提交的，但是functionTwo异常是整体回滚。

functionOne捕获funtionTwo的异常，则回滚。事务冲突。 **这点和PAOPAGATION_REQUIRE_NEW不一致，PAOPAGATION_REQUIRE_NEWfunctionOne是可以提交的，不是同一个事务。**

若functionTwo方法抛出异常，functionTwo方法内部捕获，functionOne、functionTwo都不会回滚。

A、B可操作同一条记录，因为处于同一个事务中

```java
 @Transactional(propagation = Propagation.REQUIRED,rollbackFor = Exception.class)
    @Override
    public void functionOne(){
        AttendanceRecord attendanceRecord=new AttendanceRecord();
        attendanceRecord.setUserName("test");
        saveAttendanceRecord(attendanceRecord);
        try {
        leaveRecordService.functionTwo();  // functionOne 进行异常捕捉,functionTwo抛出异常。 事务回滚。
            // Participating transaction failed - marking existing transaction as rollback-only 
        }catch (Exception e){
            log.error(e.getMessage());
        }

    }
```

```java
 @Override
    @Transactional(propagation = Propagation.REQUIRED,rollbackFor = Exception.class)
    public void functionTwo() {
        this.baseMapper.deleteById(749);
        throw new RuntimeException();
    }
```

#### PAOPAGATION_REQUIRE_NEW

若当前没有事务，则新建一个事务。若当前存在事务，则新建一个事务，**新老事务相互独立**。外部事务抛出异常回滚不会影响内部事务的正常提交。

**functionTwo抛出异常，functionOne捕获异常，functionTwo回滚，functionOne正常提交。**

functionTwo方法抛出异常，functionTwo方法内部捕获，functionTwo和functionOne都不会回滚。

**若functionOne方法抛出异常，不会影响functionTwo正常执行**。

**若functionTwo方法抛出异常，functionOne、functionTwo方法都没有处理，则functionOne、functionTwo都会回滚。**

A、B不可操作同一条记录，因为处于不同事务中，会产生死锁。

```java
    @Transactional(propagation = Propagation.REQUIRED,rollbackFor = Exception.class)
    @Override
    public void functionOne(){
        AttendanceRecord attendanceRecord=new AttendanceRecord();
        attendanceRecord.setUserName("test");
        saveAttendanceRecord(attendanceRecord);
        try {
        leaveRecordService.functionTwo();  // 
        }catch (Exception e){
            log.error(e.getMessage());
        }

    }
```

```java
@Override
    @Transactional(propagation = Propagation.REQUIRES_NEW,rollbackFor = Exception.class)
    public void functionTwo() {
        this.baseMapper.deleteById(749);
        throw new RuntimeException();
    }
```

#### PROPAGATION_NESTED

如果当前存在事务，则嵌套在当前事务中执行。如果当前没有事务，则新建一个事务，类似于REQUIRE_NEW

若functionTwo方法抛出异常，functionOne方法进行捕获，functionTwo方法回滚，functionOne方法正常执行。 **这点等同于REQUIRE_NEW**

若functionTwo或者functionOne抛出异常，不做任何处理的话，functionOne、functionTwo都要回滚。**这点等同于REQUIRED**

functionTwo、functionOne可操作同一条记录，因为处于同一个事务中。**这点等同于REQUIRED**

```java
  @Override
    @Transactional(propagation = Propagation.NESTED,rollbackFor = Exception.class)
    public void functionTwo() {
        this.baseMapper.deleteById(749);
//        throw new RuntimeException();
    }
```

#### PROPAGATION_SUPPORTS

支持当前事务，若当前不存在事务，以非事务的方式执行。

functionOne捕获funtionTwo的异常，则回滚。事务冲突。 这点和REQUIRED一致。

**出现异常，都未进行捕获，同时回滚。 这点和REQUIRED一致。**



```java
 @Override
    @Transactional(propagation = Propagation.SUPPORTS,rollbackFor = Exception.class)
    public void functionTwo() {
        this.baseMapper.deleteById(749);
        throw new RuntimeException();
    }
```

#### PROPAGATION_NOT_SUPPORTED

以**非事务的方式执行**，若当前存在事务，则把当前事务挂起。（事务在我functionTwo上不适用）

A、B不可操作同一条记录，因为A是事务执行，B在A尚未提交前再操作同一条记录，会产生死锁。

functionTwo 或者functionOne抛出异常，functionTwo都能正常提交，functionOne会回滚。**因为functionTwo非事务。**

```java
 @Override
    @Transactional(propagation = Propagation.NOT_SUPPORTED,rollbackFor = Exception.class)
    public void functionTwo() {
        this.baseMapper.deleteById(749);
        throw new RuntimeException();

    }
```

#### PROPAGATION_MANDATORY

强制事务执行，若当前不存在事务，则抛出异常(functionOne不存在事务，functionTwo强制事务)

functionOne捕获funtionTwo的异常，则回滚。事务冲突。 **这点和REQUIRED一致。**

任意出现异常，都未捕获，回滚。

```java
 No existing transaction found for transaction marked with propagation 'mandatory
```

#### PROPAGATION_NEVER

以非事务的方式执行，如果当前存在事务，则抛出异常。

### 14、Bean初始化及销毁

<img src="D:\dailySoftWare\typora\md\img\微信图片_2020122815475111.png" alt="微信图片_2020122815475111" style="zoom:50%;" />

执行顺序 @PostConstruct 先执行 然后 afterPropertiesSet 最后自定义初始化方法



**延迟初始化**

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201228162905.png" alt="TIM截图20201228162905" style="zoom:50%;" />

**销毁**

<img src="D:\dailySoftWare\typora\md\img\微信图片_2020122815475113.png" alt="微信图片_2020122815475113" style="zoom:50%;" />

**Bean GC**

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201228163029.png" alt="TIM截图20201228163029" style="zoom:50%;" />

### 15、spring5.x特性

基于 Java8，运行时兼容 JDK9
Spring5 已经移除 Log4jConfigListener，官方建议使用 Log4j2，Spring5 框架整合 Log4j2
新功能（Webflux） 响应式编程出现的框架。 Webflux 是一种**异步非阻塞**的框架，异步非阻塞的框架在 **Servlet3.1 以后才支持，核心是基于 Reactor 的相关 API 实现**
**Lambda 表达式注册 bean**
JUnit 5 全面接纳了 Java 8 流和 lambda 表达式

### 16、java常用注解汇总

[java常用注解汇总](https://blog.csdn.net/weixin_53601359/article/details/114378460)

### 17、统一异常处理

[异常处理demo](https://juejin.cn/post/6943570205758980126?utm_source=gold_browser_extension)





## 三、springcloud

### ***1、Eureka***

保证了AP(可用性（**A**vailability）\分区容错性（**P**artition tolerance）),无法保证C一致性（**C**onsistency）

1、Eureka Server 启动成功，等待服务端注册。在启动过程中如果配置了集群，集群之间定时通过 Replicate（复制） 同步注册表，每个 Eureka Server 都存在独立完整的服务注册表信息

2、Eureka Client 启动时根据配置的 Eureka Server 地址去注册中心注册服务

3、Eureka Client 会每 30s 向 Eureka Server 发送一次心跳请求，证明客户端服务正常

4、当 Eureka Server 90s 内没有收到 Eureka Client 的心跳，注册中心则认为该节点失效，会注销该实例

5、单位时间内 Eureka Server 统计到有大量的 Eureka Client 没有上送心跳，则认为可能为网络异常，进入自我保护机制，不再剔除没有发送心跳的客户端

6、当 Eureka Client 心跳请求恢复正常之后，Eureka Server 自动退出自我保护模式

7、Eureka Client 定时全量或者增量从注册中心获取服务注册表，并且将获取到的信息缓存到本地

8、服务调用时，Eureka Client 会先从本地缓存找寻调取的服务。如果获取不到，先从注册中心刷新注册表，再同步到本地缓存

9、Eureka Client 获取到目标服务器信息，发起服务调用

10、Eureka Client 程序关闭时向 Eureka Server 发送取消请求，Eureka Server 将实例从注册表中删除

### ***2、Feign***

是一个声明式的伪Http客户端.使用Feign，只需要创建一个接口并注解。它具有可插拔的注解特性，可使用Feign 注解和JAX-RS注解。Feign支持可插拔的编码器和解码器。Feign默认集成了Ribbon，并和Eureka结合，默认实现了负载均衡的效果。  @FeignClient    动态代理实现。

基于 Feign 的动态代理机制，根据注解和选择的机器，拼接请求 URL 地址，发起请求。

<u>Feign的动态代理会根据你在接口上的 @RequestMapping 等注解，来动态构造出你要请求的服务的地址。</u>

支持服务降级（配置fallbackfactory类）和异常过滤（过滤器是对异常信息的再封装，把 feign 的异常信息封装成我们系统的通用异常对象）

### ***3、ribbon***

是一个负载均衡客户端  @LoadBalanced 默认Round Robin 轮询算法

### **4、*Zuul***

的主要功能是路由转发和过滤器  zuul默认和Ribbon结合实现了负载均衡的功能， 类似于nginx转发。 @EnableZuulProxy  /  服务过滤功能

<u>统一的降级、限流、认证授权、安全</u>

**路由的转发**

**过滤访问**

**安全访问**

**熔断**

|              | gateway                                                      | zuul                                                         |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 基本介绍     | Spring Cloud Gateway是Spring官方基于Spring 5.0，Spring Boot 2.0和Project Reactor等技术开发的网关，Spring Cloud Gateway旨在为微服务架构提供一种简单而有效的统一的API路由管理方式。Spring Cloud Gateway作为Spring Cloud生态系中的网关，目标是替代Netflix ZUUL，其不仅提供统一的路由方式，并且基于Filter链的方式提供了网关基本的功能，例如：**安全，监控/埋点，和限流等。** | Zuul1 是基于 Servlet 框架构建，如图所示，采用的是阻塞和多线程方式，即一个线程处理一次连接请求，这种方式在内部延迟严重、设备故障较多情况下会引起存活的连接增多和线程增加的情况发生 |
| 性能         | WebFlux 模块的名称是 spring-webflux，名称中的 Flux 来源于 Reactor 中的类 Flux。Spring webflux 有一个全新的非堵塞的函数式 Reactive Web 框架，可以用来构建异步的、非堵塞的、事件驱动的服务，在伸缩性方面表现非常好。使用非阻塞API。 Websockets得到支持，并且由于它与Spring紧密集成，所以将会是一个更好的 开发 体验。 | 本文的Zuul，指的是Zuul 1.x，是一个基于阻塞io的API Gateway。Zuul已经发布了Zuul 2.x，基于Netty，也是非阻塞的，支持长连接，但Spring Cloud暂时还没有整合计划。 |
| 源码维护组织 | `pring-cloud-Gateway`是spring旗下`spring-cloud`的一个子项目。还有一种说法是因为`zuul2`连续跳票和`zuul1`的性能表现不是很理想，所以催生了spring孵化`Gateway`项目。 | `zuul`则是`netflix`公司的项目，只是spring将`zuul`集成在spring-cloud中使用而已。关键目前spring不打算集成zuul2.x。 |
| 版本         | springboot2.0                                                | springboot1.x                                                |





### **5、*断路器*Hystrix**

#### 工作流程

1. 构造一个 HystrixCommand或HystrixObservableCommand对象，用于封装请求，并在构造方法配置请求被执行需要的参数；

2. 执行命令，Hystrix提供了4种执行命令的方法，后面详述；

3. 判断是否使用缓存响应请求，若启用了缓存，且缓存可用，直接使用缓存响应请求。Hystrix支持请求缓存，但需要用户自定义启动；

4. 判断熔断器是否打开，如果打开，跳到第8步；

5. 判断线程池/队列/信号量是否已满，已满则跳到第8步；

6. **执行HystrixObservableCommand.construct()或HystrixCommand.run()**，如果执行失败或者超时，跳到第8步；否则，跳到第9步；

7. 统计熔断器监控指标；

8. 走Fallback备用逻辑

9. 返回请求响应

   

#### 执行命令方法

以上 执行方法部分 Hystrix提供了4种执行命令的方法，**execute()和queue() 适用于HystrixCommand对象**，而**observe()和toObservable()适用于HystrixObservableCommand对象。**

**execute()**

以**同步堵塞方式执行run()，只支持接收一个值对象**。hystrix会从线程池中取一个线程来执行run()，并等待返回值。

**queue()**

以**异步非阻塞方式执行run()，只支持接收一个值对象**。调用queue()就直接返回一个Future对象。可通过 Future.get()拿到run()的返回结果，但Future.get()是阻塞执行的。若执行成功，Future.get()返回单个返回值。当执行失败时，如果没有重写fallback，Future.get()抛出异常。

**observe()**

**事件注册前执行run()/construct()，支持接收多个值对象**，取决于发射源。调用observe()会返回一个hot Observable，也就是说，调用observe()自动触发执行run()/construct()，**无论是否存在订阅者**。

如果继承的是HystrixCommand，hystrix会从线程池中取一个线程以非阻塞方式执行run()；如果继承的是HystrixObservableCommand，将以调用线程阻塞执行construct()。

observe()使用方法：

1. 调用observe()会返回一个Observable对象
2. 调用这个Observable对象的subscribe()方法完成事件注册，从而获取结果

**toObservable()**

**事件注册后执行run()/construct()，支持接收多个值对象**，取决于发射源。调用toObservable()会返回一个cold Observable，也就是说，调用toObservable()不会立即触发执行run()/construct()，**必须有订阅者订阅Observable时才会执行**。

如果继承的是HystrixCommand，hystrix会从线程池中取一个线程以非阻塞方式执行run()，调用线程不必等待run()；如果继承的是HystrixObservableCommand，将以调用线程堵塞执行construct()，调用线程需等待construct()执行完才能继续往下走。

toObservable()使用方法：

1. 调用observe()会返回一个Observable对象
2. 调用这个Observable对象的subscribe()方法完成事件注册，从而获取结果

需注意的是，**HystrixCommand也支持toObservable()和observe()，但是即使将HystrixCommand转换成Observable，它也只能发射一个值对象。只有HystrixObservableCommand才支持发射多个值对象。**

- execute()实际是调用了queue().get()
- queue()实际调用了toObservable().toBlocking().toFuture()
- observe()实际调用toObservable()获得一个cold Observable，再创建一个ReplaySubject对象订阅Observable，将源Observable转化为hot Observable。因此调用observe()会自动触发执行run()/construct()。

**Hystrix总是以Observable的形式作为响应返回，不同执行命令的方法只是进行了相应的转换。**

（隔离 -》 熔断-》降级）

@HystrixCommand 作用:服务发生错误，回调方法。

@EnableHystrix 启动断路器

#### **隔离**

<u>不同的服务，**默认使用不同的线程池 来进行隔离**，避免服务雪崩</u> 

**信号量隔离**是采用一个全局变量来控制并发量，一个请求过来全局变量加 1，单加到跟配置 中的大小相等是就不再接受用户请求了。

**Hystrix默认使用线程池做线程隔离**，使用信号量隔离需要显示地将属性execution.isolation.strategy设置为ExecutionIsolationStrategy.SEMAPHORE，同时配置信号量个数，默认为10。客户端需向依赖服务发起请求时，首先要获取一个信号量才能真正发起调用，由于信号量的数量有限，当并发请求量超过信号量个数时，后续的请求都会直接拒绝，进入fallback流程。

**信号量隔离主要是通过控制并发请求量，防止请求线程大面积阻塞，从而达到限流和防止雪崩的目的。**

|              | 线程池隔离                                                   | 信号量隔离                                                   |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 线程         | 与调用线程非相同线程                                         | 与调用线程相同（jetty线程）                                  |
| 开销         | 排队、调度、上下文开销等                                     | 无线程切换，开销低                                           |
| 异步         | 可以是异步，也可以是同步。看调用的方法                       | 同步调用，不支持异步                                         |
| 并发支持     | 支持（最大线程池大小hystrix.threadpool.default.maximumSize） | 支持（最大信号量上限maxConcurrentRequests）                  |
| 是否超时     | 支持，可直接返回                                             | 不支持，如果阻塞，只能通过调用协议（如：socket超时才能返回） |
| 是否支持熔断 | 支持，当线程池到达maxSize后，再请求会触发fallback接口进行熔断 | 支持，当信号量达到maxConcurrentRequests后。再请求会触发fallback |
| 隔离原理     | 每个服务单独用线程池                                         | 通过信号量的计数器                                           |
| 资源开销     | 大，大量线程的上下文切换，容易造成机器负载高                 | 小，只是个计数器                                             |



#### **降级**

服务降级是对服务调用过程的出现的异常的友好封装，当出现异常时，我们不希 望直接把异常原样返回，所以当出现异常时我们需要对异常信息进行包装，抛一 个友好的信息给前端。

指定降级方法 **定义降级方法fallbackmethod**，降级方法的返回值和业务方法的方法值要一样

##### 降级逻辑场景：

- 执行construct()或run()抛出异常
- 熔断器打开导致命令短路
- 命令的线程池和队列或信号量的容量超额，命令被拒绝
- 命令执行超时

##### 降级回退方式

建议重写getFallBack或resumeWithFallback提供自己的备用逻辑，但不建议在回退逻辑中执行任何可能失败的操作。

###### **Fail Fast 快速失败**

快速失败是最普通的命令执行方法，命令没有重写降级逻辑。 如果命令执行发生任何类型的故障，它将直接抛出异常。

###### **Fail Silent 无声失败**

指在降级方法中通过**返回null，空Map，空List或其他类似的响应**来完成。

```java
@Override
protected Integer getFallback() {
   return null;
}
@Override
protected List<Integer> getFallback() {
   return Collections.emptyList();
}
@Override
protected Observable<Integer> resumeWithFallback() {
   return Observable.empty();
}
```

###### **Fallback: Static**

指在降级方法中**返回静态默认值**。 这不会导致服务以“无声失败”的方式被删除，而是导致默认行为发生。如：应用根据命令执行返回true / false执行相应逻辑，但命令执行失败，则默认为true

```java
@Override
protected Boolean getFallback() {
    return true;
}
@Override
protected Observable<Boolean> resumeWithFallback() {
    return Observable.just( true );
}
```

###### **Fallback: Stubbed（多梗株的 多个字段）**

当命令返回一个包含多个字段的复合对象时，适合以Stubbed 的方式回退。

```java
@Override
protected MissionInfo getFallback() {
   return new MissionInfo("missionName","error");
}
```

###### **Fallback: Cache via Network**

如果调用依赖服务失败，可以从缓存服务（如redis）中查询旧数据版本。由于又会发起远程调用，所以建议重新封装一个Command，使用不同的ThreadPoolKey，与主线程池进行隔离。

```java

@Override
protected Integer getFallback() {
   return new RedisServiceCommand(redisService).execute();
}
```

###### **Primary + Secondary with Fallback**

有时系统具有两种行为- 主要和次要，或主要和故障转移。**主要和次要逻辑涉及到不同的网络调用和业务逻辑，所以需要将主次逻辑封装在不同的Command中，使用线程池进行隔离**。为了实现主从逻辑切换，可以将主次command封装在外观HystrixCommand的run方法中，并结合配置中心设置的开关切换主从逻辑。由于主次逻辑都是经过线程池隔离的HystrixCommand，因此外观HystrixCommand可以使用信号量隔离，而没有必要使用线程池隔离引入不必要的开销。原理图如下

<img src="D:\dailySoftWare\typora\md\img\181402_RQHc_2663573.png" alt="181402_RQHc_2663573" style="zoom:50%;" />

```java
public class CommandFacadeWithPrimarySecondary extends HystrixCommand<String> {
 
    private final static DynamicBooleanProperty usePrimary = DynamicPropertyFactory.getInstance().getBooleanProperty("primarySecondary.usePrimary", true);
 
    private final int id;
 
    public CommandFacadeWithPrimarySecondary(int id) {
        super(Setter
                .withGroupKey(HystrixCommandGroupKey.Factory.asKey("SystemX"))
                .andCommandKey(HystrixCommandKey.Factory.asKey("PrimarySecondaryCommand"))
                .andCommandPropertiesDefaults(
                        // 由于主次command已经使用线程池隔离，Facade Command使用信号量隔离即可
                        HystrixCommandProperties.Setter()
                                .withExecutionIsolationStrategy(ExecutionIsolationStrategy.SEMAPHORE)));
        this.id = id;
    }
 
    @Override
    protected String run() {
        if (usePrimary.get()) {
            return new PrimaryCommand(id).execute();
        } else {
            return new SecondaryCommand(id).execute();
        }
    }
 
    @Override
    protected String getFallback() {
        return "static-fallback-" + id;
    }
 
    @Override
    protected String getCacheKey() {
        return String.valueOf(id);
    }
 
    private static class PrimaryCommand extends HystrixCommand<String> {
 
        private final int id;
 
        private PrimaryCommand(int id) {
            super(Setter
                    .withGroupKey(HystrixCommandGroupKey.Factory.asKey("SystemX"))
                    .andCommandKey(HystrixCommandKey.Factory.asKey("PrimaryCommand"))
                    .andThreadPoolKey(HystrixThreadPoolKey.Factory.asKey("PrimaryCommand"))
                    .andCommandPropertiesDefaults(                          HystrixCommandProperties.Setter().withExecutionTimeoutInMilliseconds(600)));
            this.id = id;
        }
 
        @Override
        protected String run() {
            return "responseFromPrimary-" + id;
        }
 
    }
 
    private static class SecondaryCommand extends HystrixCommand<String> {
 
        private final int id;
 
        private SecondaryCommand(int id) {
            super(Setter
                    .withGroupKey(HystrixCommandGroupKey.Factory.asKey("SystemX"))
                    .andCommandKey(HystrixCommandKey.Factory.asKey("SecondaryCommand"))
                    .andThreadPoolKey(HystrixThreadPoolKey.Factory.asKey("SecondaryCommand"))
                    .andCommandPropertiesDefaults(  HystrixCommandProperties.Setter().withExecutionTimeoutInMilliseconds(100)));
            this.id = id;
        }
 
        @Override
        protected String run() {
            return "responseFromSecondary-" + id;
        }
 
    }
 
    public static class UnitTest {
 
        @Test
        public void testPrimary() {
            HystrixRequestContext context = HystrixRequestContext.initializeContext();
            try {
                ConfigurationManager.getConfigInstance().setProperty("primarySecondary.usePrimary", true);
                assertEquals("responseFromPrimary-20", new CommandFacadeWithPrimarySecondary(20).execute());
            } finally {
                context.shutdown();
                ConfigurationManager.getConfigInstance().clear();
            }
        }
 
        @Test
        public void testSecondary() {
            HystrixRequestContext context = HystrixRequestContext.initializeContext();
            try {
                ConfigurationManager.getConfigInstance().setProperty("primarySecondary.usePrimary", false);
                assertEquals("responseFromSecondary-20", new CommandFacadeWithPrimarySecondary(20).execute());
            } finally {
                context.shutdown();
                ConfigurationManager.getConfigInstance().clear();
            }
        }
    }
}
```



**hystrix数据监控**

Hystrix 进行服务熔断时会对调用结果进行统计，比如超时数、bad 请求数、降 级数、异常数等等都会有统计，那么统计的数据就需要有一个界面来展示， hystrix-dashboard 就是这么一个展示 hystrix 统计结果的服务。

#### **熔断**

##### **熔断发生的三个必要条件：** 

1、**有一个统计的时间周期**，滚动窗口 相应的配置属性 metrics.rollingStats.timeInMilliseconds 默认 10000 毫秒 

2、**请求次数必须达到一定数量** 相应的配置属性 circuitBreaker.requestVolumeThreshold 默认 20 次 

3、**失败率达到默认失败率** 相应的配置属性 circuitBreaker.errorThresholdPercentage 默认 50% 

上述 3 个条件缺一不可，必须全部满足才能开启 hystrix 的熔断功能。

##### **熔断器的三个状态**： 

1、关闭状态 关闭状态时用户请求是可以到达服务提供方的 

2、开启状态 开启状态时用户请求是不能到达服务提供方的，直接会走降级方法 

3、半开状态 当 hystrix 熔断器开启时，过一段时间后，熔断器就会由开启状态变成半开状态。 

**半开状态的熔断器是可以接受用户请求并把请求传递给服务提供方的**，这时候如果远程调用 返回成功，那么熔断器就会有半开状态变成关闭状态，反之，如果调用失败，熔断器就会有 半开状态变成开启状态。 <u>Hystrix 功能建议在并发比较高的方法上使用，并不是所有方法都得使用的。</u>

##### **熔断器工作的详细过程如下：**

**第一步**，调用**allowRequest()判断是否允许将请求提交到线程池**

1. 如果熔断器强制打开，circuitBreaker.forceOpen为true，不允许放行，返回。
2. 如果熔断器强制关闭，circuitBreaker.forceClosed为true，允许放行。此外不必关注熔断器实际状态，也就是说熔断器仍然会维护统计数据和开关状态，只是不生效而已。

**第二步**，调用**isOpen()判断熔断器开关是否打开**

1. 如果熔断器开关打开，进入第三步，否则继续；
2. 如果一个周期内总的请求数小于circuitBreaker.requestVolumeThreshold的值，允许请求放行，否则继续；
3. 如果一个周期内错误率小于circuitBreaker.errorThresholdPercentage的值，允许请求放行。否则，打开熔断器开关，进入第三步。

**第三步**，调用**allowSingleTest()判断是否允许单个请求通行**，**检查依赖服务是否恢复**

1. 如果熔断器打开，且距离熔断器打开的时间或上一次试探请求放行的时间超过circuitBreaker.sleepWindowInMilliseconds的值时，熔断器器进入半开状态，允许放行一个试探请求；否则，不允许放行。

### **6、*spring* cloud config**

配置中心

### **7、*Spring* Cloud Bus**

 我们通过向服务实例请求Spring Cloud Bus的`/bus/refresh`接口，从而触发总线上其他服务实例的`/refresh`

刷新微服务中某个具体实例的配置

1、提交配置触发post请求给server端的bus/refresh接口

2、server端接收到请求并发送给Spring Cloud Bus总线

3、Spring Cloud bus接到消息并通知给其它连接到总线的客户端

4、其它客户端接收到通知，请求Server端获取最新配置

5、全部客户端均获取到最新的配置

**Spring Cloud Bus**对这种场景也有很好的支持：`/bus/refresh`接口还提供了`destination`参数，用来定位具体要刷新的应用程序。比如，我们可以请求`/bus/refresh?destination=服务名字:9000`，此时总线上的各应用实例会根据`destination`属性的值来判断是否为自己的实例名，

若符合才进行配置刷新，若不符合就忽略该消息。

`　　destination`参数除了可以定位具体的实例之外，还可以用来定位具体的服务。定位服务的原理是通过使用Spring的PathMatecher（路径匹配）来实现，比如：`/bus/refresh?destination=customers:**`，该请求会触发`customers`服务的所有实例进行刷新。

## 四、springboot

**Spring Boot 的最大的优势是“约定优于配置“**

Spring Boot 的目标是简化 Spring 应用和服务的创建、开发与部署，简化了配置文件，使用嵌入式 Web 服务器，含有诸多开箱即用的微服务功能，可以和 Spring Cloud 联合部署。Spring Boot 的核心思想是约定大于配置，应用只需要很少的配置即可，简化了应用开发模式

### **1、*启动流程*：**

1. Spring Boot 在启动时会去依赖的 Starter 包中寻找 resources/META-INF/spring.factories 文件，然后根据文件中配置的 Jar 包去扫描项目所依赖的 Jar 包。
2. 根据 spring.factories 配置加载 AutoConfigure 类
3. 根据 @Conditional 注解的条件，进行自动配置并将 Bean 注入 Spring Context

就是 Spring Boot 在启动的时候，按照约定去读取 Spring Boot Starter 的配置信息，再根据配置信息对资源进行初始化，并注入到 Spring 容器中。这样 Spring Boot 启动完毕后，就已经准备好了一切资源，使用过程中直接注入对应 Bean 资源即可

### **2、*自动装配原理***

通过@@SpringbootApplication注解实现，由@SpringbootConfiguration @ComponentScan @EnableAutoConfiguration  实现

 @EnableAutoConfiguration 是实现自动配置的入口，该注解又通过 @Import 注解导入了AutoConfigurationImportSelector，在该类中加载 META-INF/spring.factories 的配置信息。然后筛选出以 EnableAutoConfiguration 为 key 的数据，加载到 IOC 容器中，实现自动配置功能！

### 3、Undertow,Tomcat和Jetty服务器之间的区别

Undertow 是红帽公司开发的一款**基于 NIO 的高性能 Web 嵌入式服务器**

它由两个核心 Jar 包组成，加载一个 Web 应用可以小于 10MB 内存

**Servlet3.1 支持**：它提供了对 Servlet3.1 的支持

**WebSocket 支持**：对 Web Socket 完全支持，用以满足 Web 应用巨大数量的客户端

**嵌套性**：它不需要容器，只需通过 API 即可快速搭建 Web 服务器

jetty 和undertow都是基于NIO实现。

**高并发情况下，undertow高于tomcat 和jetty**

springboot可以pom配置exclusion排除默认tomcat，来引用undertow。

```xml
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-starter-tomcat</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
<!--替换内置默认容器-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-undertow</artifactId>
            <version>1.5.10.RELEASE</version>
        </dependency>
```

### 4、任务

#### 异步任务

@EnableAysnc、@Aysnc

#### 定时任务

@EnableScheduling、@Scheduled

#### 邮件任务

```xml
<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-mail</artifactId>
		</dependency>
```

```properties
spring.mail.username=534096094@qq.com
spring.mail.password=gtstkoszjelabijb
spring.mail.host=smtp.qq.com
spring.mail.properties.mail.smtp.ssl.enable=true
```

```java
@Autowired
	JavaMailSenderImpl mailSender;

	@Test
	public void contextLoads() {
		SimpleMailMessage message = new SimpleMailMessage();
		//邮件设置
		message.setSubject("通知-今晚开会");
		message.setText("今晚7:30开会");

		message.setTo("17512080612@163.com");
		message.setFrom("534096094@qq.com");

		mailSender.send(message);
	}

	@Test
	public void test02() throws  Exception{
		//1、创建一个复杂的消息邮件
		MimeMessage mimeMessage = mailSender.createMimeMessage();
		MimeMessageHelper helper = new MimeMessageHelper(mimeMessage, true);

		//邮件设置
		helper.setSubject("通知-今晚开会");
		helper.setText("<b style='color:red'>今天 7:30 开会</b>",true);

		helper.setTo("17512080612@163.com");
		helper.setFrom("534096094@qq.com");

		//上传文件
		helper.addAttachment("1.jpg",new File("C:\\Users\\lfy\\Pictures\\Saved Pictures\\1.jpg"));
		helper.addAttachment("2.jpg",new File("C:\\Users\\lfy\\Pictures\\Saved Pictures\\2.jpg"));

		mailSender.send(mimeMessage);

	}
```

### security

WebSecurityConfigurerAdapter：自定义Security策略

AuthenticationManagerBuilder：自定义认证策略

@EnableWebSecurity：开启WebSecurity模式

#### 使用

```java
/**
 * 1、引入SpringSecurity；
 * 2、编写SpringSecurity的配置类；
 * 		@EnableWebSecurity   extends WebSecurityConfigurerAdapter
 * 3、控制请求的访问权限：
 * 		configure(HttpSecurity http) {
 * 		 	http.authorizeRequests().antMatchers("/").permitAll()
 * 		 		.antMatchers("/level1/**").hasRole("VIP1")
 * 		}
 * 4、定义认证规则：
 * 		configure(AuthenticationManagerBuilder auth){
 * 		 	auth.inMemoryAuthentication()
 * 		 		.withUser("zhangsan").password("123456").roles("VIP1","VIP2")
 * 		}
 * 5、开启自动配置的登陆功能：
 * 		configure(HttpSecurity http){
 * 		 	http.formLogin();
 * 		}
 * 6、注销：http.logout();
 * 7、记住我：Remeberme()；
 */
```

```java
package com.atguigu.security.config;

import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@EnableWebSecurity
public class MySecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        //super.configure(http);
        //定制请求的授权规则
        http.authorizeRequests().antMatchers("/").permitAll()
                .antMatchers("/level1/**").hasRole("VIP1")
                .antMatchers("/level2/**").hasRole("VIP2")
                .antMatchers("/level3/**").hasRole("VIP3");

        //开启自动配置的登陆功能，效果，如果没有登陆，没有权限就会来到登陆页面
        http.formLogin().usernameParameter("user").passwordParameter("pwd")
                .loginPage("/userlogin");
        //1、/login来到登陆页
        //2、重定向到/login?error表示登陆失败
        //3、更多详细规定
        //4、默认post形式的 /login代表处理登陆
        //5、一但定制loginPage；那么 loginPage的post请求就是登陆


        //开启自动配置的注销功能。
        http.logout().logoutSuccessUrl("/");//注销成功以后来到首页
        //1、访问 /logout 表示用户注销，清空session
        //2、注销成功会返回 /login?logout 页面；

        //开启记住我功能
        http.rememberMe().rememberMeParameter("remeber");
        //登陆成功以后，将cookie发给浏览器保存，以后访问页面带上这个cookie，只要通过检查就可以免登录
        //点击注销会删除cookie

    }

    //定义认证规则
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        //super.configure(auth);
        auth.inMemoryAuthentication()
                .withUser("zhangsan").password("123456").roles("VIP1","VIP2")
                .and()
                .withUser("lisi").password("123456").roles("VIP2","VIP3")
                .and()
                .withUser("wangwu").password("123456").roles("VIP1","VIP3");

    }
}

```

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org"
	  xmlns:sec="http://www.thymeleaf.org/thymeleaf-extras-springsecurity4">  <!--使用thymeleaf 安全引用 -->
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
<h1 align="center">欢迎光临武林秘籍管理系统</h1>
<div sec:authorize="!isAuthenticated()">  <!--是否授权 -->
	<h2 align="center">游客您好，如果想查看武林秘籍 <a th:href="@{/userlogin}">请登录</a></h2>
</div>
<div sec:authorize="isAuthenticated()">
	<h2><span sec:authentication="name"></span>，您好,您的角色有：
		<span sec:authentication="principal.authorities"></span></h2>
	<form th:action="@{/logout}" method="post">
		<input type="submit" value="注销"/>
	</form>
</div>

<hr>

<div sec:authorize="hasRole('VIP1')">    <!--是否有角色 -->
	<h3>普通武功秘籍</h3>
	<ul>
		<li><a th:href="@{/level1/1}">罗汉拳</a></li>
		<li><a th:href="@{/level1/2}">武当长拳</a></li>
		<li><a th:href="@{/level1/3}">全真剑法</a></li>
	</ul>

</div>
```



## 五、dubbo

### 1、***定义***

Duubbo是一个RPC远程调用框架， 分布式服务治理框架

### *2、Dubbo**服务治理***

服务与服务之间会有很多个Url、依赖关系、负载均衡、容错、自动注册服务。

### 3、***协议***

默认用的dubbo协议、Http、RMI、Hessian

[协议选用参考](https://www.cnblogs.com/barrywxx/p/8589374.html)

thrift原生协议性能表现卓越，是dubbo原生性能的6倍

```properties
dubbo 协议
连接个数：单连接 
连接方式：长连接 
传输协议：TCP 
传输方式：NIO异步传输 
序列化：Hessian二进制序列化 
适用范围：传入传出参数数据包较小（建议小于100K），消费者比提供者个数多，单一消费者无法压满提供者，尽量不要用dubbo协议传输大文件或超大字符串。 
适用场景：常规远程服务方法调用

1、dubbo默认采用dubbo协议，dubbo协议采用单一长连接和NIO异步通讯，适合于小数据量大并发的服务调用，以及服务消费者机器数远大于服务提供者机器数的情况 
2、他不适合传送大数据量的服务，比如传文件，传视频等，除非请求量很低。 
配置如下：
```

```yaml
Hessian
连接个数：多连接 
连接方式：短连接 
传输协议：HTTP 
传输方式：同步传输 
序列化：表单序列化 
适用范围：传入传出参数数据包大小混合，提供者比消费者个数多，可用浏览器查看，可用表单或URL传入参数，暂不支持传文件。 
适用场景：页面传输，文件传输，或与原生hessian服务互操作。

1、Hessian协议用于集成Hessian的服务，Hessian底层采用Http通讯，采用Servlet暴露服务，Dubbo缺省内嵌Jetty作为服务器实现。 
2、Hessian是Caucho开源的一个RPC框架：http://hessian.caucho.com，其通讯效率高于WebService和Java自带的序列化。
```

**RPC请求的效率是HTTP请求的1.6倍左右，性能明显比HTTP请求要高很多，因为HTTP协议包含大量的请求头、响应头信息**

### ***4、负载均衡策略***

随机负载均衡 randomLoadBalance  获取权重和，进行随机，找到第一个大于随机数的权重提供者。权重一致则以个数进行随机获取提供者。

轮询负债均衡：RoundRobinLoadBalance:依次从最大权重的invoker开始选择，然后将选中的项放到最后，轮流选中。使用一个 ConcurrentHashMap 来保存每个url的权重信息，且维护其活跃性

最少活跃调用数：leastActiveLoadBalance：最少活跃调用数，相同活跃数的随机。如果权重不相同且权重大于0则按总权重数随机，确定随机值落在哪个片断上（第一个相减为负的值）

一致性负载均衡：ConsistentHashLoadBalance：取第多少个参数，参与hashCode的计算，然后按照一致性hash算法，定位invoker. 它使用一个 TreeMap 来保存一致性哈希虚拟节点，hashCode->invoker形式存储，使用 **ceilingEntry(hash)** 的方式获取最近的虚拟节点（天然的一致性hash应用

### 5、容错策略

[dubbo熔断、限流、降级的分析理解](https://blog.csdn.net/world_snow/article/details/79080314)

***\*Failover Cluster\**** 失败自动切换，当出现失败，重试其它服务器。通常用于读操作，但重试会带来更长延迟。可通过 retries="2" 来设置重试次数(不含第一次)。

***\*Failfast Cluster\****快速失败，只发起一次调用，失败立即报错。通常用于非幂等性的写操作，比如新增记录。

***\*Failsafe Cluster\**** 失败安全，出现异常时，直接忽略。通常用于写入审计日志等操作。

***\*Failback Cluster\**** 失败自动恢复，后台记录失败请求，定时重发。通常用于消息通知操作。

***\*Forking Cluster\**** 并行调用多个服务器，只要一个成功即返回。通常用于实时性要求较高的读操作，但需要浪费更多服务资源。可通过 forks="2" 来设置最大并行数。

***\*Broadcast Cluster\**** 广播调用所有提供者，逐个调用，任意一台报错则报错 [2]。通常用于通知所有提供者更新缓存或日志等本地资源信息。



### ***5、Dubbo架构流程***

![984f85ba-d0bf-4c37-8933-25340d7ca5ed](D:\dailySoftWare\typora\md\img\984f85ba-d0bf-4c37-8933-25340d7ca5ed.png)

分为四大模块

生产者、消费者、注册中心、监控中心

生产者：提供服务

消费者: 调用服务

注册中心:注册信息(redis、zk)

监控中心:调用次数、关系依赖等。

首先生产者将服务注册到注册中心（zk），使用zk持久节点进行存储，消费订阅zk节点，一旦有节点变更，zk通过事件通知传递给消费者，消费可以调用生产者服务。

服务与服务之间进行调用，都会在监控中心中，存储一个记录。

### ***6、Dubbox与Dubbo区别***

Dubox使用http协议+rest风格传入json或者xml格式进行远程调用。

Dubbo使用Dubbo协议。

### ***7、RPC远程调用框架***

SpringCloud、dubbo、Dubbox、thint、Hessian…

Rpc其实就是远程调用，服务与服务之间相互进行通讯。

目前主流 用http+json

### ***8、SpringCloud与Dubbo区别***

相同点:

**dubbo****与****springcloud****都可以实现****RPC****远程调用。**

**dubbo****与****springcloud****都可以使用分布式、微服务场景下。**

区别:

dubbo有比较强的背景,在国内有一定影响力。

dubbo使用zk或redis作为作为注册中心

springcloud使用eureka作为注册中心

dubbo支持多种协议，默认使用dubbo协议。

Springcloud只能支持http协议。

Springcloud是一套完整的微服务解决方案。

Dubbo目前已经停止更新,SpringCloud更新速度快。

### 9、RPC

RPC（**Remote Procedure Call）— 远程过程调用**，是一个**计算机通信协议**。该协议允许运行于一台计算机的程序调用另一台计算机的子程序，而程序员无需额外地为这个交互作用编程

两个或多个应用程序都分布在不同的服务器上，它们之间的调用都像是本地方法调用一样(如图)

<img src="D:\dailySoftWare\typora\md\img\TIM截图20210308165451.png" alt="TIM截图20210308165451" style="zoom:50%;" />

1)**服务消费方(client)以本地调用方式调用服务**
2)client stub 接收到调用后负责将方法、参数等封装成能够进行网络传输的消息体
3)client stub 将消息进行编码并发送到服务端
4)server stub 收到消息后进行解码
5)server stub 根据解码结果调用本地的服务
6)本地服务执行并将结果返回给 server stub
7)server stub 将返回导入结果进行编码并发送至消费方
8)client stub 接收到消息并进行解码
9)服务消费方(client)得到结果

### 10、SPI机制

#### JAVA SPI

##### 描述

SPI，全名：Service Provider Interface

<u>**接口服务提供方**</u>，是JDK内置的一种**动态服务发现**机制。它的主要实现是"**基于接口的编程＋策略模式＋配置文件"**组合实现的动态加载机制。

为某个接口寻找服务实现的机制。有点类似IOC的思想，**就是将装配的控制权移到程序之外**。所以SPI的核心思想就是**解耦**。

##### 使用场景

- **JDBC数据库驱动实现**

  JDBC4.0以前， 开发人员还需要基于Class.forName("xxx")的方式来装载驱动；JDBC4.0也是基于Java SPI机制来发现驱动服务，可以通过**META-INF/services/java.sql.Driver文件里指定实现类的方式来暴露驱动提供者.**

- **common-logging 日志实现统一接口**

  Apache最早提供的日志的门面接口。只有接口，没有实现。具体方案由各提供商实现，发现日志提供商是通过扫描 META-INF/services/org.apache.commons.logging.LogFactory配置文件，通过读取该文件的内容找到日志提供商的实现类。只要我们的日志实现里包含了这个文件，并在文件里制定 LogFactory工厂接口的实现类即可。 

- **Dubbo 框架很多组件使用到SPI机制**

  Dubbo框架中大量使用了SPI技术，不过它对Java提供的原生SPI做了封装，例如：Dubbo中发布不同协议的Protocol接口

##### 使用规范

遵循"约定优于配置"原则，要使用Java SPI，需要遵循如下约定：

     1.当服务提供者提供了接口的一种具体实现后，在resources/META-INF/services目录下创建一个以"接口全限定名"为命名的文件，内容为实现类的全限定名；
    
     2.主程序通过java.util.ServiceLoder动态装载实现模块，它通过扫描META-INF/services目录下的配置文件找到实现类的全限定名，把类加载到JVM；
    
     3.如果SPI的实现类为Jar包，则需要放在主程序的ClassPath路径中
    
     4.接口的具体实现类，必须有一个无参构造方法
##### ServiceLoader

SPI机制，主要用到ServiceLoader这个类，ServiceLoader通过读取resources/META-INF/services/com.xxx.xxx.xxxService文件下的xxxService的spi实现类，通过反射获取对应类实例，并调用对应方法。

#### Dubbo SPI

##### 描述

**Dubbo框架就是通过 Dubbo SPI 机制，从而实现 Dubbo 自定义协议、Dubbo 自定义路由......等很多模块的自定义**。

##### 和java spi 比较

Dubbo SPI

    ①配置文件存放路径不同：META-INF/dubbo/、META-INF/dubbo/internal/、META-INF/services/(3种)
    
    ②配置文件中内容不同：KV键值对形式（key=value形式）
    
    ③增加了Spring IOC 和 AOP 的支持

Java SPI

    ①配置文件存放路径不同：META-INF/services/(1种)
    
    ②配置文件中内容不同：接口实现类的全限定名
##### 扩展

 由于文件中内容的不同，也就直接导致了Dubbo中无法直接使用JDK中提供的ServiceLoader类，来动态装载实现模块 。与之对应，Dubbo中提供了**ExtensionLoader**类。ExtensionLoader是扩展点载入器，用于载入Dubbo中的各种可配置组件，比如：动态代理方式（ProxyFactory）、负载均衡策略（LoadBalance）、RCP协议（Protocol）、拦截器（Filter）、容器类型（Container）、集群方式（Cluster）和注册中心类型（RegistryFactory）等。

**Dubbo直接通过服务接口（上面提到的ProxyFactory、LoadBalance、Protocol、Filter等）和配置的K从ExtensionLoader拿到服务提供的实现类**

##### SPI实例

[参考Dubbo spi protocol 协议](https://blog.csdn.net/lzb348110175/article/details/98484451)

## 六、分布式锁



### *1、**数据库实现分布式锁***。

参考连接：https://honeypps.com/architect/distribute-lock-based-on-database/

**方式1：**建立一个锁表，添加唯一性约束。当想获得锁的时候，插入数据，释放锁的时候，删除数据。

多个请求的话，只有一个成功，其他都会插入失败。

**<u>优缺点：</u>**

1. 这种锁没有失效时间，一旦释放锁的操作失败就会导致锁记录一直在数据库中，其它线程无法获得锁。这个缺陷也很好解决，比如可以做一个定时任务去定时清理。
2. 这种锁的可靠性依赖于数据库。建议设置备库，避免单点，进一步提高可靠性。
3. 这种锁是非阻塞的，因为插入数据失败之后会直接报错，想要获得锁就需要再次操作。如果需要阻塞式的，可以弄个for循环、while循环之类的，直至INSERT成功再返回。
4. 这种锁也是非可重入的，因为同一个线程在没有释放锁之前无法再次获得锁，因为数据库中已经存在同一份记录了。想要实现可重入锁，可以在数据库中添加一些字段，比如获得锁的主机信息、线程信息等，那么在再次获得锁的时候可以先查询数据，如果当前的主机信息和线程信息等能被查到的话，可以直接把锁分配给它。

**2、乐观锁**

version 版本概念，更新的时候，获取开始查询的version，判断是否一致，一致则更新。

作用于同一行数据记录上，这就导致一个明显的缺点，在一些特殊场景，如大促、秒杀等活动开展的时候，大量的请求同时请求同一条记录的行锁，会对数据库产生很大的写压力。乐观锁比较适合并发量不高，并且写操作不频繁的场景。

**3、悲观锁**

查询语句后面增加FOR UPDATE，数据库会在查询过程中给数据库表增加悲观锁，也称排他锁。

悲观锁中，每一次行数据的访问都是独占的，只有当正在访问该行数据的请求事务提交以后，其他请求才能依次访问该数据，否则将阻塞等待锁的获取。

悲观锁可以严格保证数据访问的安全。但是缺点也明显，即每次请求都会额外产生加锁的开销且未获取到锁的请求将会阻塞等待锁的获取，在高并发环境下，容易造成大量请求阻塞，影响系统可用性。另外，悲观锁使用不当还可能产生死锁的情况。

### ***2、redis实现***

[具体实现以及原理分析]: https://www.jianshu.com/p/47fd7f86c848

#### 1、简单分布式锁（不具备重入性）

##### 加锁

SET lock_key random_value NX PX 5000

`random_value` 是客户端生成的唯一的字符串。
`NX` 代表只在键不存在时，才对键进行设置操作。
`PX 5000` 设置键的过期时间为5000毫秒。

##### 解锁

为了保证解锁操作的原子性，我们用LUA脚本完成这一操作。先判断当前锁的字符串是否与传入的值相等，是的话就删除Key，解锁成功。

```kotlin
if redis.call('get',KEYS[1]) == ARGV[1] then 
   return redis.call('del',KEYS[1]) 
else
   return 0 
end
```

##### 实现

###### 1、引入依赖

```xml
<dependency>
    <groupId>redis.clients</groupId>
    <artifactId>jedis</artifactId>
    <version>3.0.1</version>
</dependency>
```

###### 2、具体逻辑

```java
@Service
public class RedisLock {
    Logger logger = LoggerFactory.getLogger(this.getClass());
    private String lock_key = "redis_lock"; //锁键
    protected long internalLockLeaseTime = 30000;//锁过期时间
    private long timeout = 999999; //获取锁的超时时间
 
    //SET命令的参数 
    SetParams params = SetParams.setParams().nx().px(internalLockLeaseTime);
    @Autowired
    JedisPool jedisPool;
    
    /**
     * 加锁
     * @param id
     * @return
     */
    public boolean lock(String id){
        Jedis jedis = jedisPool.getResource();
        Long start = System.currentTimeMillis();
        try{
            for(;;){
                //SET命令返回OK ，则证明获取锁成功
                String lock = jedis.set(lock_key, id, params);
                if("OK".equals(lock)){
                    return true;
                }
                //否则循环等待，在timeout时间内仍未获取到锁，则获取失败
                long l = System.currentTimeMillis() - start;
                if (l>=timeout) {
                    return false;
                }
                try {
                    Thread.sleep(100);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }finally {
            jedis.close();
        }
    }
}
```

```java
    /**
     * 解锁
     * @param id
     * @return
     */
    public boolean unlock(String id){
        Jedis jedis = jedisPool.getResource();
        String script =
                "if redis.call('get',KEYS[1]) == ARGV[1] then" +
                        "   return redis.call('del',KEYS[1]) " +
                        "else" +
                        "   return 0 " +
                        "end";
        try {
            Object result = jedis.eval(script, Collections.singletonList(lock_key), 
                                    Collections.singletonList(id));
            if("1".equals(result.toString())){
                return true;
            }
            return false;
        }finally {
            jedis.close();
        }
    }
```

#### 2、redisson实现

[Redisson](https://redisson.org/)是架设在[Redis](http://redis.cn/)基础上的一个Java驻内存数据网格（In-Memory Data Grid），具有分布式特性的常用工具类。

##### 实现

###### 引入依赖，直接调用lock 和unlock方法

```java
public static void main(String[] args) {

    Config config = new Config();
    config.useSingleServer().setAddress("redis://127.0.0.1:6379");
    config.useSingleServer().setPassword("redis1234");  
    final RedissonClient client = Redisson.create(config);  
    RLock lock = client.getLock("lock1");
    try{
        lock.lock();
    }finally{
        lock.unlock();
    }
}
```

###### 加锁底层实现逻辑

tryAcquire 有两种处理方式，一种是带有过期时间的锁，一种是不带过期时间的锁。

```java
private <T> RFuture<Long> tryAcquireAsync(long leaseTime, TimeUnit unit, final long threadId) {

    //如果带有过期时间，则按照普通方式获取锁
    if (leaseTime != -1) {
        return tryLockInnerAsync(leaseTime, unit, threadId, RedisCommands.EVAL_LONG);
    }
    
    //先按照30秒的过期时间来执行获取锁的方法
    RFuture<Long> ttlRemainingFuture = tryLockInnerAsync(
        commandExecutor.getConnectionManager().getCfg().getLockWatchdogTimeout(),
        TimeUnit.MILLISECONDS, threadId, RedisCommands.EVAL_LONG);
        
    //如果还持有这个锁，则开启定时任务不断刷新该锁的过期时间
    ttlRemainingFuture.addListener(new FutureListener<Long>() {
        @Override
        public void operationComplete(Future<Long> future) throws Exception {
            if (!future.isSuccess()) {
                return;
            }

            Long ttlRemaining = future.getNow();
            // lock acquired
            if (ttlRemaining == null) {
                scheduleExpirationRenewal(threadId);
            }
        }
    });
    return ttlRemainingFuture;
}
```

```java
<T> RFuture<T> tryLockInnerAsync(long leaseTime, TimeUnit unit,     
                            long threadId, RedisStrictCommand<T> command) {

        //过期时间
        internalLockLeaseTime = unit.toMillis(leaseTime);

        return commandExecutor.evalWriteAsync(getName(), LongCodec.INSTANCE, command,
                  //如果锁不存在，则通过hset设置它的值，并设置过期时间
                  "if (redis.call('exists', KEYS[1]) == 0) then " +
                      "redis.call('hset', KEYS[1], ARGV[2], 1); " +
                      "redis.call('pexpire', KEYS[1], ARGV[1]); " +
                      "return nil; " +
                  "end; " +
                  //如果锁已存在，并且锁的是当前线程，则通过hincrby给数值递增1
                  "if (redis.call('hexists', KEYS[1], ARGV[2]) == 1) then " +
                      "redis.call('hincrby', KEYS[1], ARGV[2], 1); " +
                      "redis.call('pexpire', KEYS[1], ARGV[1]); " +
                      "return nil; " +
                  "end; " +
                  //如果锁已存在，但并非本线程，则返回过期时间ttl
                  "return redis.call('pttl', KEYS[1]);",
        Collections.<Object>singletonList(getName()), 
                internalLockLeaseTime, getLockName(threadId));
    }
```

###### 结论

**通过exists判断，如果锁不存在，则设置值和过期时间，加锁成功**

**通过hexists判断，如果锁已存在，并且锁的是当前线程，则证明是重入锁，加锁成功**

**如果锁已存在，但锁的不是当前线程，则证明有其他线程持有锁。返回当前锁的过期时间，加锁失败**

加锁之后redis内存中数据结构如下：

```shell
127.0.0.1:6379> hgetall lock1
1) "b5ae0be4-5623-45a5-8faa-ab7eb167ce87:1"
2) "1"
```

###### 解锁底层逻辑

```java
public RFuture<Void> unlockAsync(final long threadId) {
    final RPromise<Void> result = new RedissonPromise<Void>();
    
    //解锁方法
    RFuture<Boolean> future = unlockInnerAsync(threadId);

    future.addListener(new FutureListener<Boolean>() {
        @Override
        public void operationComplete(Future<Boolean> future) throws Exception {
            if (!future.isSuccess()) {
                cancelExpirationRenewal(threadId);
                result.tryFailure(future.cause());
                return;
            }
            //获取返回值
            Boolean opStatus = future.getNow();
            //如果返回空，则证明解锁的线程和当前锁不是同一个线程，抛出异常
            if (opStatus == null) {
                IllegalMonitorStateException cause = 
                    new IllegalMonitorStateException("
                        attempt to unlock lock, not locked by current thread by node id: "
                        + id + " thread-id: " + threadId);
                result.tryFailure(cause);
                return;
            }
            //解锁成功，取消刷新过期时间的那个定时任务
            if (opStatus) {
                cancelExpirationRenewal(null);
            }
            result.trySuccess(null);
        }
    });

    return result;
}
```

```java
protected RFuture<Boolean> unlockInnerAsync(long threadId) {
    return commandExecutor.evalWriteAsync(getName(), LongCodec.INSTANCE, EVAL,
    
            //如果锁已经不存在， 发布锁释放的消息
            "if (redis.call('exists', KEYS[1]) == 0) then " +
                "redis.call('publish', KEYS[2], ARGV[1]); " +
                "return 1; " +
            "end;" +
            //如果释放锁的线程和已存在锁的线程不是同一个线程，返回null
            "if (redis.call('hexists', KEYS[1], ARGV[3]) == 0) then " +
                "return nil;" +
            "end; " +
            //通过hincrby递减1的方式，释放一次锁
            //若剩余次数大于0 ，则刷新过期时间
            "local counter = redis.call('hincrby', KEYS[1], ARGV[3], -1); " +
            "if (counter > 0) then " +
                "redis.call('pexpire', KEYS[1], ARGV[2]); " +
                "return 0; " +
            //否则证明锁已经释放，删除key并发布锁释放的消息
            "else " +
                "redis.call('del', KEYS[1]); " +
                "redis.call('publish', KEYS[2], ARGV[1]); " +
                "return 1; "+
            "end; " +
            "return nil;",
    Arrays.<Object>asList(getName(), getChannelName()), 
        LockPubSub.unlockMessage, internalLockLeaseTime, getLockName(threadId));

}
```

**如果锁已经不存在，通过publish发布锁释放的消息，解锁成功**

**如果解锁的线程和当前锁的线程不是同一个，解锁失败，抛出异常**

**通过hincrby递减1，先释放一次锁。若剩余次数还大于0，则证明当前锁是重入锁，刷新过期时间；若剩余次数小于0，删除key并发布锁释放的消息，解锁成功**





### ***3、zookeeper实现***

临时节点+事件通知 实现（这里针对大量请求来竞争锁是不利的，比如产品促销，很多人就买不到。应该是取最小临时节点来作为锁，其他未获取锁的也只会监听比自身大的临时节点。）

```java
package com.abner.test;

import org.I0Itec.zkclient.ZkClient;

public  abstract  class ZookeeperAbstractLock implements  Lock {

    // zk连接地址
    private static final String CONNECTSTRING = "127.0.0.1:2181";
    // 创建zk连接
    protected ZkClient zkClient = new ZkClient(CONNECTSTRING);
    protected static final String PATH = "/lock";

    public void getLock() {
        if (tryLock()) {
            System.out.println("##获取lock锁的资源####");
        } else {
            // 等待
            waitLock();
            // 重新获取锁资源
            getLock();
        }

    }

    // 获取锁资源
    abstract boolean tryLock();

    // 等待
    abstract void waitLock();

    public void unLock() {
        if (zkClient != null) {
            zkClient.close();
            System.out.println("释放锁资源...");
        }
    }

}

```

```java
package com.abner.test;

import org.I0Itec.zkclient.IZkDataListener;

import java.util.concurrent.CountDownLatch;

public class ZookeeperDistrbuteLock  extends ZookeeperAbstractLock  {
    private CountDownLatch countDownLatch = null;
    @Override
    boolean tryLock() {
        try {
            zkClient.createEphemeral(PATH);
            return true;
        } catch (Exception e) {
            return false;
        }

    }

    @Override
    void waitLock() {
        IZkDataListener iZkDataListener=new IZkDataListener() {
            public void handleDataChange(String s, Object o) throws Exception {
                // 唤醒被等待的线程
                if (countDownLatch != null) {
                    countDownLatch.countDown();
                }

            }
            public void handleDataDeleted(String s) throws Exception {

            }
        };
        // 注册事件
        zkClient.subscribeDataChanges(PATH, iZkDataListener);
        if (zkClient.exists(PATH)) {
            countDownLatch = new CountDownLatch(1);
            try {
                countDownLatch.await();
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        // 删除监听
        zkClient.unsubscribeDataChanges(PATH, iZkDataListener);


    }
}

```

```java
package com.abner.test;

public class OrderService implements Runnable {
    private OrderNumGenerator orderNumGenerator = new OrderNumGenerator();
    private Lock lock = new ZookeeperDistrbuteLock();
    public void run() {
        getNumber();
    }
    public void getNumber() {
        try {
            lock.getLock();
            String number = orderNumGenerator.getNumber();
            System.out.println(Thread.currentThread().getName() + ",生成订单ID:" + number);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            lock.unLock();
        }
    }
    public static void main(String[] args) {
        System.out.println("####生成唯一订单号###");
        for (int i = 0; i < 100; i++) {
            new Thread( new OrderService()).start();
        }
    }
}

```



## 七、分布式事务

### ***1、两阶段提交/XA方案  Two Phase Commit*** 

 XA 协 议。这个协议是 X/Open 国际联盟基于二阶段提交协议提出的，也叫作 X/Open Distributed Transaction Processing（DTP）模型

XA中大致分为两部分：事务管理器和本地资源管理器。其中本地资源管理器往往由数据库实现，事务管理器作为全局的调度者，负责各个本地资源的提交和回滚。

2PC，将事务的提交过程分为：

准备阶段和提交阶段。

事务的发起者称协调者，事务的执行者称参与者。

**阶段1：准备阶段**

1、协调者（**事务管理器（TM）**）向所有参与者（**多个资源管理器（RM）**）发送事务内容，询问是否可以提交事务，并等待所有参与者答复。

2、<u>**各参与者执行事务操作，但不提交事务**</u>。

3、如参与者执行成功，给协调者反馈YES，即可以提交；如执行失败，给协调者反馈NO，即不可提交。

**阶段2：提交阶段**

此阶段分两种情况：所有参与者均反馈YES、或任何一个参与者反馈NO。

所有参与者均反馈YES时，即提交事务。

任何一个参与者反馈NO时，即中断事务。

**优点：** 

尽量保证了数据的强一致，实现成本较低，在各大主流数据库都有自己实现，对于 MySQL 是从 5.5 开始支持。 

**缺点：**

单点问题：事务管理器在整个流程中扮演的角色很关键，如果其宕机，比如在第一阶段已经完成，在第二阶段正准备提交 的时候事务管理器宕机，资源管理器就会一直阻塞，导致数据库无法使用。

同步阻塞：在准备就绪之后，资源管理器中的资源一直处于阻塞，直到提交完成，释放资源。

数据不一致：两阶段提交协议虽然为分布式数据强一致性所设计，但仍然存在数据不一致性的可能。 比如在第二阶段中，假设协调者发出了事务 Commit 的通知，但是因为网络问题该通知仅被一部分参与者所收到并执行 了 Commit 操作，其余的参与者则因为没有收到通知一直处于阻塞状态，这时候就产生了数据的不一致性。

### ***2、三阶段提交协议--- 3PC（对2pc优化）***

3PC，三阶段提交协议，是2PC的改进版本，

即将事务的提交过程分为**CanCommit、PreCommit、do Commit**三个阶段来进行处理。

**阶段1：CanCommit**

1、协调者向参与者发出CanCommit请求，询问是否可以提交事务，并等待所有参与者答复。

2、参与者收到CanCommit请求后，如果认为可以执行事务操作，则反馈YES，否则反馈NO。

<u>（这一阶段主要是确定分布式事务的参与者是否具备了完成 commit 的条件，并不会执行事务操作）</u>

**阶段2：PreCommit**　

1、所有参与者均反馈YES，即执行事务预提交。

2、任何一个参与者反馈NO，或者等待超时后协调者尚无法收到所有参与者的反馈，即中断事务。

**（发送预提交请求**：协调者向所有参与者节点发出 preCommit 的请求，并进入 prepared 状态。

**事务预提交：**参与者受到 preCommit 请求后，会执行事务操作，对应 2PC 中的 “执行事务”，也会 Undo 和 Redo 信息记录到事务日 志中。

 各参与者向协调者反馈事务执行的结果：如果参与者成功执行了事务，就反馈 Ack 响应，同时等待指令：提交（commit） 或终止（abor）。 

中断事务也分为 2 个步骤：

**发送中断请求**：协调者向所有参与者节点发出 abort 请求 。

**中断事务：**参与者如果收到 abort 请求或者超时了，都会中断事务。）

**阶段3：do Commit**　　

1、所有参与者均反馈Ack响应，即执行真正的事务提交。

2、任何一个参与者反馈NO，或者等待超时后协调者尚无法收到所有参与者的反馈，即中断事务。

<u>协调者中断事务流程</u>

1、协调者向所有的参与者节点发送 abort 请求。

2、参与者接收到 abort 请求后，会利用其在二阶段记录的 undo 信息来执行事务回滚操作，并在完成回滚之后释放整个事务执行 期间占用的资源。

3、参与者在完成事务回滚之后，想协调者发送 Ack 消息。

4、协调者接收到所有的 Ack 消息后，中断事务。

### *3、TCC*

其<u>将整个业务逻辑的每个分支显式的分成了 Try、Confirm、Cancel 三个操作</u>

1）Try阶段：这个阶段说的是对各个服务的资源做检测以及对资源进行锁定或者预留

2）Confirm阶段：这个阶段说的是在各个服务中执行实际的操作

3）Cancel阶段：如果任何一个服务的业务方法执行出错，那么这里就需要进行补偿，就是执行已经执行成功的业务逻辑的回滚操作

<u>TCC 属于应用层的一种**补偿方式**，所以需要程序员在实现的时候多写很多补偿的代码，而且补偿的时候也有可能失败，在一些场景中，一些 业务流程可能用 TCC 不太好定义及处理</u>**（2PC通常都是在跨库的DB层面，而TCC则在应用层面处理，需要通过业务逻辑来实现）**

为了实现一致 性，**确认操作和补偿操作必须是等幂的，因为这 2 个操作可能会失败重试。**

### **4、*本地消息表***

1）A系统在自己本地一个事务里操作同时，插入一条数据到消息表

2）启动独立的线程，定时对消息日志表中的消息进行扫描并发送至消息中间件，在消息中间件反馈发送成功后删除该消息日志，否则等待定时任务下一周期重试。

3）B系统接收到消息之后，**业务处理完成后向MQ发送ack（即消息确认）**，此时说明消费者正常消费消息完成，MQ将不再向消费者推送消息，否则消费者会不断重试向消费者来发送消息。

<u>最大的问题就在于严重依赖于数据库的消息表来管理事务</u>

### 5、***可靠消息最终一致性方案***

**1、Producer 发送事务消息**

　　Producer （MQ发送方）发送事务消息至MQ Server，MQ Server将消息状态标记为**Prepared（预备状态**），注意此时这条消息消费者（MQ订阅方）是无法消费到的。本例中，Producer 发送 ”增加积分消息“ 到MQ Server。

**2、MQ Server回应消息发送成功**

　　MQ Server接收到Producer 发送给的消息则回应发送成功表示MQ已接收到消息。

**3、Producer 执行本地事务**

　　Producer 端执行业务代码逻辑，通过本地数据库事务控制。本例中，Producer 执行添加用户操作。

**4、消息投递**

　　若Producer 本地事务执行成功则自动向MQServer发送commit消息，MQ Server接收到commit消息后将”增加积分消息“ 状态标记为可消费，此时MQ订阅方（积分服务）即正常消费消息；

　　若Producer 本地事务执行失败则自动向MQServer发送rollback消息，MQ Server接收到rollback消息后 将删除”增加积分消息“ 。

MQ订阅方（积分服务）消费消息，消费成功则向MQ回应ack，否则将重复接收消息。这里ack默认自动回应，即程序执行正常则自动回应ack。

**5、事务回查**

　　如果执行Producer端本地事务过程中，执行端挂掉，或者超时，MQ Server将会不停的询问同组的其他 Producer 来获取事务执行状态，这个过程叫事务回查。MQ Server会根据事务回查结果来决定是否投递消息。

　　以上主干流程已由RocketMQ实现，对用户侧来说，用户需要分别实现本地事务执行以及本地事务回查方法，因此只需关注本地事务的执行状态即可。

典型的场景：注册送积分，登陆送优惠券等

### ***6、最大努力通知方案***

- <u>**可靠消息一致性关注的是交易过程的事务一致，以异步的方式完成交易**</u>
- <u>**最大努力通知关注的是交易后的通知事务，即将交易结果可靠的通知出去**</u>

![v2-96fa90cbb1457ffb3e68ed8e1759a60e_r](D:\dailySoftWare\typora\md\img\v2-96fa90cbb1457ffb3e68ed8e1759a60e_r.jpg)

- 利用MQ的ack机制由MQ向接收通知方发送消息通知，发起方将普通消息发送到MQ
- 接收通知监听MQ，接收消息，业务处理完成回应ACK
- 接收通知方如果没有回应ACK则MQ会重复通知，按照时间间隔的方式，逐步拉大通知间隔
- 此方案适用于内部微服务之间的通知，不适应与通知外部平台

方案二：增加一个**通知服务区进行通知，**提供外部第三方时适用



![v2-d2f6b33f12d2648ba2524cdfb740c5e7_720w](D:\dailySoftWare\typora\md\img\v2-d2f6b33f12d2648ba2524cdfb740c5e7_720w.jpg)

1. 方案1中接收通知方与MQ接口，即接收通知方案监听 MQ，此方案主要应用与内部应用之间的通知。
2. 方案2中由通知程序与MQ接口，**通知程序监听MQ**，收到MQ的消息后由通知程序**通过互联网接口协议调用接收 通知**方。此方案主要应用于外部应用之间的通知，例如**支付宝、微信的支付结果通知。**

### 7、方案比较

- 2PC 最大的一个诟病是一个**阻塞协议**。RM在执行分支事务后需要等待TM的决定，此时服务会阻塞锁定资源。由于其阻塞机制和最差时间复杂度高，因此，这种设计**不能适应随着事务涉及的服务数量增加而扩展的需要**，很难用于并发较高以及子事务生命周期较长的分布式服务中

- 如果拿TCC事务的处理流程与2PC两阶段提交做比较，**2PC通常都是在跨库的DB层面，而TCC则在应用层面处理**，需要通过业务逻辑来实现。这种分布式事务的优势在于，可以让应用自定义数据操作的粒度，使得降低锁冲突，提高吞吐量成为可能。而不足之处在于对应用的侵入性非常强，业务逻辑的每个分支都需要实现三个操作。此外，其实现难度也比较大，需要按照网络状态，系统故障等不同失败原因实现不同的策略。

- 可靠消息最终一致性事务**适合执行周期长且实时性要求不高的场景**。引入消息机制后，同步的事务操作变为基于消息执行的异步操作，避免了分布式事务中的同步阻塞操作的影响，并实现了两个服务的解耦，<u>典型的场景：注册送积分，登陆送优惠券等</u>

- 最大努力通知是分布式事务中要求最低的一种，**适用于一些最终一致性时间敏感度低的业务**，允许发起通知方业务处理失败，在接收通知方收到通知后积极进行失败处理，无论发起通知方如何处理结果都不会影响到接收通知方的后续处理，发起通知方需提供查询执行情况接口，用于接收通知方校对结果，典型的应用场景：**银行通知，支付结果通知等。**

- ![v2-c8cf9cd5a4c6c0f87cbe6faf4704feba_r](D:\dailySoftWare\typora\md\img\v2-c8cf9cd5a4c6c0f87cbe6faf4704feba_r.png)

  **最大努力通知与可靠消息一致性有什么不同**

  1、解决方案思想不同

  可靠消息一致性，发起通知方需要保证将消息发出去，并且将消息发到接收通知方，**消息的可靠性关键由发起通知 方来保证**。

  最大努力通知，发起通知方尽最大的努力将业务处理结果通知为接收通知方，但是可能消息接收不到，**此时需要接 收通知方主动调用发起通知方的接口查询业务处理结果，通知的可靠性关键在接收通知方**

  2、两者的业务应用场景不同

  可靠消息一致性关注的是交易过程的事务一致，以异步的方式完成交易。

  **最大努力通知关注的是交易后的通知事务，即将交易结果可靠的通知出去。**

  3、技术解决方向不同

  可靠消息一致性要解决消息从发出到接收的一致性，即消息发出并且被接收到。

  最大努力通知无法保证消息从发出到接收的一致性，只提供消息接收的可靠性机制。可靠机制是，最大努力的将消 息通知给接收方，当消息无法被接收方接收时，由接收方主动查询消息（业务处理结果）。
  
  

### 8、LCN、TCC、TXC事务模式

#### 1、LCN

##### 1、介绍

- 锁定事务单元（lock）
- 确认事务模块状态(confirm)
- 通知事务(notify)

避免区分LCN模式，特此将LCN分布式事务改名为TX-LCN分布式事务框架。

TX-LCN定位于一款**事务协调性框架**，框架其本身并不操作事务，而是基于对事务的协调从而达到事务一致性的效果

##### 2、事务控制原理

TX-LCN由两大模块组成, **TxClient、TxManager**，TxClient作为模块的依赖框架，提供TX-LCN的标准支持，TxManager作为分布式事务的控制方。事务发起方或者参与反都由TxClient端来控制。

**核心步骤：**

创建事务组：是指在**事务发起方开始执行业务代码之前先调用TxManager创建事务组对象，然后拿到事务标示GroupId的过程。**
加入事务组：添加事务组是指**参与方在执行完业务方法以后**，**将该模块的事务信息通知给TxManage**r的操作。
通知事务组：是指在发起方执行完业务代码以后，将**发起方执行结果状态通知给TxManager,TxManager将根据事务最终状态和事务组的信息来通知相应的参与模块提交或回滚事务，并返回结果给事务发起方。**

<img src="D:\dailySoftWare\typora\md\img\20191104085954936.png" alt="20191104085954936" style="zoom:50%;" />

##### 3、事务模式

**原理介绍:**
 LCN模式是通过**代理Connection的方式实现对本地事务的操作**，然后在由TxManager统一协调控制事务。当本地事务提交回滚或者关闭连接时将会执行假操作，该代理的连接将由LCN连接池管理。
**特点:**
该模式对代码的**嵌入性为低**。
该模式仅限于本地存在连接对象且可通过连接对象控制事务的模块。
该模式下的事务提交与回滚是由本地事务方控制，对于数据一致性上有较高的保障。
该模式缺陷在于代理的连接需要**随事务发起方一共释放连接，增加了连接占用的时间**。

#### 2、TXC

原理介绍：
TXC模式命名来源于淘宝，实现原理是在执行SQL之前，先查询SQL的影响数据，然后保存执行的SQL信息和创建锁。当需要回滚的时候就采用这些记录数据回滚数据库，目前锁实现依赖redis分布式锁控制。
特点:
该模式同样对代码的侵入性低。
该模式仅限于对支持SQL方式的模块支持。
该模式由于每次执行SQL之前需要先查询影响数据，因此相比LCN模式消耗资源与时间要多。
该模式不会占用数据库的连接资源。

### 9、JTA

#### 1、介绍

java平台上事务规范JTA（**Java Transaction API**）也定义了对XA事务的支持

JTA 中，基于XA架构上建模，事务管理器抽象为javax.transaction.TransactionManager接口，并通过底层事务服务（即JTS）实现

JTA仅仅定义了接口，具体的实现则是由供应商(如J2EE厂商)负责提供

目前JTA的实现主要由以下几种：

1.J2EE容器所提供的JTA实现(JBoss)
 2.独立的JTA实现:如JOTM，**Atomikos**.这些实现可以应用在那些不使用J2EE应用服务器的环境里用以提供分布事事务保证。如Tomcat,Jetty以及普通的java应用。

#### 2、

## 八、并发编程

### ***1、进程***

系统正在运行的应用程序。

### ***2、线程***

进程的一条执行路径、指令的集合。轻量级进程。

### *3、多线程*

提高程序效率。

### 4、***应用场景***

多线程下载、批量发送短息。

### 5、***线程实现方式***

**继承Thread/** 

**实现Runnable接口 /**

**线程池创建线程**（源码来看，通过DefaultThreadFactory创建线程，设置名字优先级之类，最终还是new Thread()实现）

**callable创建 有返回值  实现callable接口，传入线程池中执行**

```java
public class ThreadCallableDemo implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return new Random().nextInt();
    }

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        ExecutorService executorService =   Executors.newFixedThreadPool(10);
        Future<Integer> result = executorService.submit(new ThreadCallableDemo());
        System.out.println(result.get());
    }
}
```

**定时器Timer，**源码还是通过继承Thread的TimerThread实现。

匿名内部类

**<u>【其实本质上都是构造一个Thread类来执行Run方法】</u>**

比较：实现Runnable优于继承。

<u>与Thread类解耦，Thread负责线程的启动和属性设置等，权责分明。</u>

<u>实现Runnable可以传入线程池执行，不用每次新建、销毁线程，降低性能消耗。</u>

<u>java不支持双继承，继承不利于代码扩展。</u>

**Callable 和 Runnable 的不同之处**

方法名，Callable 规定的执行方法是 call()，而 Runnable 规定的执行方法是 run()；
**返回值**，Callable 的任务执行后有返回值，而 Runnable 的任务执行后是没有返回值的；
抛出异常，**call() 方法可抛出异常，而 run() 方法是不能抛出受检查异常的；**
**和 Callable 配合的有一个 Future 类，**通过 Future 可以了解任务执行情况，或者取消任务的执行，还可获取任务执行的结果，这些功能都是 Runnable 做不到的，Callable 的功能要比 Runnable 强大。

**Future**

Future 的作用
Future 最主要的作用是，比如当做一定运算的时候，运算过程可能比较耗时，有时会去查数据库，或是繁重的计算，比如压缩、加密等，在这种情况下，如果我们一直在原地等待方法返回，显然是不明智的，整体程序的运行效率会大大降低。我们可以把运算的过程放到子线程去执行，再通过 Future 去控制子线程执行的计算过程，最后获取到计算结果。这样一来就可以把整个程序的运行效率提高，是一种异步的思想。

Callable 和 Future 的关系
接下来我们介绍下 Callable 和 Future 的关系，前面讲过，Callable 接口相比于 Runnable 的一大优势是可以有返回结果，那这个返回结果怎么获取呢？就可以用 Future 类的 get 方法来获取 。因此，**Future 相当于一个存储器，它存储了 Callable 的 call 方法的任务结果。**除此之外，我们还可以通过 **Future 的 isDone 方法来判断任务是否已经执行完毕了，还可以通过 cancel 方法取消这个任务，或限时获取任务的结果等**，总之 Future 的功能比较丰富。有了这样一个从宏观上的概念之后，我们就来具体看一下 Future 类的主要方法。

Future 的方法和用法
首先看一下 Future 接口的代码，一共有 5 个方法，代码如下所示：

复制代码
public interface Future<V> {

```java
boolean cancel(boolean mayInterruptIfRunning);

boolean isCancelled();

boolean isDone();

V get() throws InterruptedException, ExecutionException;

V get(long timeout, TimeUnit unit)
    throws InterruptedException, ExecutionException, TimeoutExceptio
```
}
其中，第 5 个方法是对第 4 个方法的重载，方法名一样，但是参数不一样。

get() 方法：获取结果
get 方法最主要的作用就是获取任务执行的结果，该方法在执行时的行为取决于 Callable 任务的状态，可能会发生以下 5 种情况。

（1）最常见的就是当执行 get 的时候，任务已经执行完毕了，可以立刻返回，获取到任务执行的结果。

（2）任务还没有结果，这是有可能的，比如我们往线程池中放一个任务，线程池中可能积压了很多任务，还没轮到我去执行的时候，就去 get 了，在这种情况下，相当于任务还没开始；还有一种情况是任务正在执行中，但是执行过程比较长，所以我去 get 的时候，它依然在执行的过程中。无论是任务还没开始或在进行中，我们去调用 get 的时候，都会把当前的线程阻塞，直到任务完成再把结果返回回来。

（3）任务执行过程中抛出异常，一旦这样，我们再去调用 get 的时候，就会抛出 ExecutionException 异常，不管我们执行 call 方法时里面抛出的异常类型是什么，在执行 get 方法时所获得的异常都是 ExecutionException。

（4）任务被取消了，如果任务被取消，我们用 get 方法去获取结果时则会抛出 CancellationException。

（5）任务超时，我们知道 get 方法有一个重载方法，那就是带延迟参数的，调用了这个带延迟参数的 get 方法之后，如果 call 方法在规定时间内正常顺利完成了任务，那么 get 会正常返回；但是如果到达了指定时间依然没有完成任务，get 方法则会抛出 TimeoutException，代表超时了。

### 6、***线程***api

| start()                          |                      启动线程                      |
| -------------------------------- | :------------------------------------------------: |
| currentThread()                  |                  获取当前线程对象                  |
| getID()                          |     获取当前线程ID   Thread-编号 该编号从0开始     |
| getName()                        |                  获取当前线程名称                  |
| sleep(long mill)                 |                      休眠线程                      |
| Stop（）                         |                     停止线程,                      |
| **常用线程构造函数**             |                                                    |
| Thread（String name）            | 分配一个新的 Thread对象，具有指定的 name正如其名。 |
| Thread（Runable r）              |              分配一个新的 Thread对象               |
| Thread（）                       |              分配一个新的 Thread 对象              |
| Thread（Runable r, String name） |              分配一个新的 Thread对象               |

### 7、***守护线程***

**主线程和守护线程一起销毁。**setDaemon(true)

**非守护线程和主线程无关系。**

### ***8、多线程运行状态***

*新建-》就绪-》运行-》阻塞-》死亡*

​                                                           运行-》 休眠-》就绪-》运行

### *9、synchronized和线程方法说明*

**阻塞分为Blocked 被阻塞（未获取到synchronize 的 Monitor锁）/ **

**Waiting 等待 （等待某个条件,比如Join执行完毕） /** Object.wait()  Thread.join() LockSupport.park()

**TimeWaiting 计时等待**

**join()**:把指定的线程加入到当前线程,让其他线程变为等待。

**线程安全(数据同步)**:synchronized （自动挡） / lock（手动挡）    保证多个线程之间共享同个全局变量或静态变量，保证数据的一致性、原子性。

同步代码块/ 同步函数（方法）/静态同步函数

**synchronized 修饰方法使用锁是当前this锁。**

**synchronized 修饰静态方法使用锁是当前类的字节码文件**

### 10、***死锁***

同步中嵌套同步,导致锁无法释放。死锁就是两个或多个线程（或进程）**被无限期地阻塞，相互等待对方手中资源**的一种状态。

```java
/**

 * 描述：     必定死锁的情况

 */

public class MustDeadLock implements Runnable {
    public int flag;
    static Object o1 = new Object();
    static Object o2 = new Object();
    public void run() {
        System.out.println("线程"+Thread.currentThread().getName() + "的flag为" + flag);
        if (flag == 1) {
            synchronized (o1) {
                try {
                    Thread.sleep(500);
                } catch (Exception e) {
                    e.printStackTrace();
                }
                synchronized (o2) {
                    System.out.println("线程1获得了两把锁");
                }
            }
        }
        if (flag == 2) {
            synchronized (o2) {
                try {
                    Thread.sleep(500);
                } catch (Exception e) {
                    e.printStackTrace();
                }
                synchronized (o1) {
                    System.out.println("线程2获得了两把锁");
                }
            }
        }
    }

    public static void main(String[] argv) {
        MustDeadLock r1 = new MustDeadLock();
        MustDeadLock r2 = new MustDeadLock();
        r1.flag = 1;
        r2.flag = 2;
        Thread t1 = new Thread(r1, "t1");
        Thread t2 = new Thread(r2, "t2");
        t1.start();
        t2.start();

    }

}
//当第 1 个线程运行的时候，它会发现自己的 flag 是 1 ，所以它会尝试先获得 o1 这把锁，然后休眠 500 毫秒。

//在线程 1 启动并休眠的期间，线程 2 同样会启动起来。由于线程 2 的 flag 是 2，所以它会进入到下面 的 if (flag == 2) 对应的代码块中，然后线程 2 首先会去获取 o2 这把锁。也就是说在线程 1 启动并获取到 o1 这把锁之后进行休眠的期间，线程 2 获取到了 o2 这把锁，然后线程 2 也开始 500 毫秒的休眠。

//当线程 1 的 500 毫秒休眠时间结束后，它将尝试去获取 o2 这把锁，此时 o2 这个锁正被线程 2 持有，所以线程 1 无法获取到的 o2。

//紧接着线程 2 也会苏醒过来，它将尝试获取 o1 这把锁，此时 o1 已被线程 1 持有。
//线程 1 卡在获取 o2 这把锁的位置，而线程 2 卡在获取 o1 这把锁的位置，

```

**条件**

- 第 1 个叫**互斥条件**，它的意思是每个资源每次只能被一个线程（或进程，下同）使用，为什么资源不能同时被多个线程或进程使用呢？这是因为如果每个人都可以拿到想要的资源，那就不需要等待，所以是不可能发生死锁的。

- 第 2 个是**请求与保持条件**，它是指当一个线程因请求资源而阻塞时，则需对已获得的资源保持不放。如果在请求资源时阻塞了，并且会自动释放手中资源（例如锁）的话，那别人自然就能拿到我刚才释放的资源，也就不会形成死锁。

- 第 3 个是**不剥夺条件**，它是指线程已获得的资源，在未使用完之前，不会被强行剥夺。比如我们在上一课时中介绍的数据库的例子，它就有可能去强行剥夺某一个事务所持有的资源，这样就不会发生死锁了。所以要想发生死锁，必须满足不剥夺条件，也就是说当现在的线程获得了某一个资源后，别人就不能来剥夺这个资源，这才有可能形成死锁。

- 第 4 个是**循环等待条件**，只有若干线程之间形成一种头尾相接的循环等待资源关系时，才有可能形成死锁，比如在两个线程之间，这种“循环等待”就意味着它们互相持有对方所需的资源、互相等待；而在三个或更多线程中，则需要形成环路，例如依次请求下一个线程已持有的资源等

  

**死锁定位**

${JAVA_HOME}/bin/jps

```shell
56402 MustDeadLock
56403 Launcher
56474 Jps
55051 KotlinCompileDaemon
```

可以看到第一行是 MustDeadLock 这类的 pid 56402；然后我们继续执行下一个命令， ${JAVA_HOME}/bin/jstack 56402 

```powershell
Found one Java-level deadlock:
=============================
"t2":
  waiting to lock monitor 0x00007fa06c004a18 (object 0x000000076adabaf0, a java.lang.Object),
  which is held by "t1"
"t1":
  waiting to lock monitor 0x00007fa06c007358 (object 0x000000076adabb00, a java.lang.Object),
  which is held by "t2"
Java stack information for the threads listed above:
===================================================
"t2":
	at lesson67.MustDeadLock.run(MustDeadLock.java:31)
	- waiting to lock <0x000000076adabaf0> (a java.lang.Object)
	- locked <0x000000076adabb00> (a java.lang.Object)
	at java.lang.Thread.run(Thread.java:748)
"t1":
	at lesson67.MustDeadLock.run(MustDeadLock.java:19)
	- waiting to lock <0x000000076adabb00> (a java.lang.Object)
	- locked <0x000000076adabaf0> (a java.lang.Object)
	at java.lang.Thread.run(Thread.java:748)
Found 1 deadlock
```

在这里它首先会打印“Found one Java-level deadlock”，表明“找到了一个死锁”，然后是更详细的信息，从中间这部分的信息中可以看出，t2 线程想要去获取这个尾号为 af0 的锁对象，但是它被 t1 线程持有，同时 t2 持有尾号为 b00 的锁对象；相反，t1 想要获取尾号为 b00 的锁对象，但是它被 t2 线程持有，同时 t1 持有的却是尾号为 af0 的锁对象，这就形成了一个依赖环路，发生了死锁。最后它还打印出了“Found 1 deadlock.”



**ThreadMXBean定位**

```java
Thread.sleep(1000);
        ThreadMXBean threadMXBean = ManagementFactory.getThreadMXBean();
        long[] deadlockedThreads = threadMXBean.findDeadlockedThreads();
        if (deadlockedThreads != null && deadlockedThreads.length > 0) {
            for (int i = 0; i < deadlockedThreads.length; i++) {
                ThreadInfo threadInfo = threadMXBean.getThreadInfo(deadlockedThreads[i]);
                System.out.println("线程id为"+threadInfo.getThreadId()+",线程名为" + threadInfo.getThreadName()+"的线程已经发生死锁，需要的锁正被线程"+threadInfo.getLockOwnerName()+"持有。");
            }
        }
```

在 main 函数中，在启动 t1 和 t2 之后的代码，是我们本次新加入的代码，我们用 Thread.sleep(1000) 来确保已经形成死锁，然后利用 ThreadMXBean 来检查死锁。

通过 ThreadMXBean 的 findDeadlockedThreads 方法，可以获取到一个 deadlockedThreads 的数组，然后进行判断，当这个数组不为空且长度大于 0 的时候，我们逐个打印出对应的线程信息。比如我们打印出了**线程 id，也打印出了线程名，同时打印出了它所需要的那把锁正被哪个线程所持有**，



### 11、***线程三大特性***

原子性/可见性/有序性

### 12、***java***内存模型JMM

也叫共享内存模型，定义了主内存和线程之间的关系。线程之间的共享变量存在主内存中，每个线程有各自的本地的私有的内存，本地内存中

存放共享变量的副本。

JMM通过控制主内存与每个线程的本地内存之间的交互，来为java程序员提供内存可见性保证。当多个线程同时访问一个数据的时候，可能本地内存没有及时刷新到主内存，所以就会发生线程安全问题



### 12、**volatile**

:保证变量在多线程之间可见。强制线程每次读取该变量的时候都去主内存中取值。 **非原子性。**

i++实际为load、Increment、store、Memory Barriers 四个操作。

内存屏障是线程安全的,但是内存屏障之前的指令并不是.在某一时刻线程1将i的值load取出来，放置到cpu缓存中，然后再将此值放置到寄存器A中，然后A中的值自增1（寄存器A中保存的是中间值，没有直接修改i，因此其他线程并不会获取到这个自增1的值）。如果在此时线程2也执行同样的操作，获取值i==10,自增1变为11，然后马上刷入主内存。此时由于线程2修改了i的值，实时的线程1中的i==10的值缓存失效，重新从主内存中读取，变为11。接下来线程1恢复。将自增过后的A寄存器值11赋值给cpu缓存i。这样就出现了线程安全问题。



线程1从主内存中拿了一个值为1的数据到自己的工作空间里面进行加1的操作，值变为2，写回主内存，然后*<u>**还没有来得及通知其他线程，线程1就被线程2抢占了，CPU分配，线程1被挂起，线程2还是拿着原来主内存中的数据值为1进行加1**</u>*，值变成2，写回主内存，将主内存值为2的替换成2，这时线程1的通知到了，线程2重新去主内存拿值为2的数据

**适用场合：**

布尔标记位：如果某个共享变量自始至终只是被各个线程所赋值或读取，而没有其他的操作（比如读取并在此基础上进行修改这样的复合操作）的话，那么我们就可以使用 volatile 来代替 synchronized 或者代替原子类，因为赋值操作自身是具有原子性的，volatile 同时又保证了可见性，这就足以保证线程安全了。

作为触发器：

**作用：**

第一层的作用是保证可见性。

第二层的作用就是禁止重排序



**AtomicInteger：**原子操作的Integer类，保证了线程安全。

volatile轻量级，只能修饰变量。synchronized重量级，还可修饰方法

volatile只能保证数据的可见性，不能用来同步，因为多个线程并发访问volatile修饰的变量不会阻塞。

synchronized不仅保证可见性，而且还保证原子性，因为，只有获得了锁的线程才能进入临界区，从而保证临界区中的所有语句都全部执行。多个线程争抢synchronized锁对象时，会出现阻塞。

使用volatile并不能保证线程安全性。而synchronized则可实现线程的安全性。

**线程间对于共享变量的可见性问题，并不是直接由多核引起的，而是由我们刚才讲到的这些 L3 缓存、L2 缓存、L1 缓存，也就是多级缓存引起的**

![Cgq2xl54fTKALhevAAB_l3axT_o532](D:\dailySoftWare\typora\md\img\Cgq2xl54fTKALhevAAB_l3axT_o532.png)

*假设 core 1 修改了变量 a 的值，并写入到了 core 1 的 L1 缓存里，但是还没来得及继续往下同步，由于 core 1 有它自己的的 L1 缓存，core 4 是无法直接读取 core 1 的 L1 缓存的值的，那么此时对于 core 4 而言，变量 a 的值就不是 core 1 修改后的最新的值，core 4 读取到的值可能是一个过期的值，从而引起多线程时可见性问题的发生。*

**主内存和工作内存的关系**

![Ciqah154fUGAS19LAAGap07f1AU762](D:\dailySoftWare\typora\md\img\Ciqah154fUGAS19LAAGap07f1AU762.png)

（1）所有的变量都存储在主内存中，同时每个线程拥有自己独立的工作内存，而工作内存中的变量的内容是主内存中该变量的拷贝；

（2）线程不能直接读 / 写主内存中的变量，但可以操作自己工作内存中的变量，然后再同步到主内存中，这样，其他线程就可以看到本次修改；

（3） 主内存是由多个线程所共享的，但线程间不共享各自的工作内存，如果线程间需要通信，则必须借助主内存中转来完成。

**happens-before**

第一个操作和第二个操作之间满足 happens-before 关系，那么我们就说第一个操作对于第二个操作一定是可见的，也就是第二个操作在执行时就一定能保证看见第一个操作执行的结果。

### 13、*多线程通讯*

多个线程操作同一个资源，动作不通。比如读、取

**wait() / notify()  / notifyAll() :**三个方法最终调用的都是jvm级的native方法。

wait ：持有该对象控制权的线程将控制权交出去，处于等待状态

notify:通知正在等待该对象控制权的线程可以继续运行。

notifyAll:通知所有等待这个对象控制权的线程继续运行

**wait和sleep方法**：wait属于object ，sleep属于thread  / sleep只是程序暂停，仍然是锁的控制者，wait 交出控制权 / sleep必须定义时间，wait则是永久等待/

**<u>wait必须定义在synchronized保护的代码中</u>**（不加锁的话，否正容易永远等待）

**lock**:（手动控制）

```java
Lock lock  = new ReentrantLock();
lock.lock();
try{
//可能会出现线程安全的操作
}finally{
//一定在finally中释放锁
//也不能把获取锁在try中进行，因为有可能在获取锁的时候抛出异常
  lock.ublock();
}

```

**condition**:作用和Object.wait  Object.notify 相似

```java
Condition condition = lock.newCondition();
res. condition.await();  //  类似wait
res. Condition. Signal()  // 类似notify

```

### 14、***停止线程***

1、使用退出线程标识 比如false （valatile修饰变量）退出。部分场景适用。

<u>阻塞队列BlockingQueue 存满，消费者开始消费。在某些业务下，消费者不想消费了，但是队列还是满的，执行put方法会阻塞，进入循环体条件判断标识是否停止。</u>

 2、 stop 强行停止，不建议，数据错乱，过时。supend()和resume()结合也不行，容易造成死锁

影响程序 

**3、使用Interrupt 中断**

### 15、***ThreadLocal***

为每个使用该变量的线程维护一个对立的变量副本。  **实现原理：通过map集合Map.put(“当前线程”,值)；**

- void     set(Object value)设置当前线程的线程局部变量的值。

- public     Object get()该方法返回当前线程所对应的线程局部变量。

- public     void remove()将当前线程局部变量的值删除，目的是为了减少内存的占用，该方法是JDK     5.0新增的方法。需要指出的是，当线程结束后，对应该线程的局部变量将自动被垃圾回收，所以显式调用该方法清除线程的局部变量并不是必须的操作，但它可以加快内存回收的速度。

- protected     Object initialValue()返回该线程局部变量的初始值，该方法是一个protected的方法，显然是为了让子类覆盖而设计的。这个方法是一个延迟调用方法，在线程第1次调用get()或set(Object)时才执行，并且仅执行1次。ThreadLocal中的缺省实现直接返回一个null。

  **应用场景**

  场景1，ThreadLocal 用作**保存每个线程独享的对象，为每个线程都创建一个副本，每个线程都只能修改自己所拥有的副本, 而不会影响其他线程的副本**，这样就让原本在并发情况下，线程不安全的情况变成了线程安全的情况。

  场景2，ThreadLocal 用作每个线程内需要独立保存信息的场景，**供其他方法更方便得获取该信息，**每个线程获取到的信息都可能是不一样的，前面执行的方法设置了信息后，后续方法可以通过 ThreadLocal 直接获取到，避免了传参。

  **Thread、 ThreadLocal 及 ThreadLocalMap 三者之间的关系**

  <u>一个 Thread 里面只有一个ThreadLocalMap</u> ，而在一个 ThreadLocalMap， key 就是 ThreadLocal 的引用。 <u>里面却可以有很多的 ThreadLocal</u>，每一个 ThreadLocal 都对应一个 value。因为一个 Thread 是可以调用多个 ThreadLocal 的，所以 Thread 内部就采用了 ThreadLocalMap 这样 Map 的数据结构来存放 ThreadLocal 和 value。

  **为什么要remove**

  它都会扫描 key 为 null 的 Entry，如果发现某个 Entry 的 key 为 null，则代表它所对应的 value 也没有作用了，所以它就会把对应的 value 置为 null，这样，value 对象就可以被正常回收了。

  但是假设 ThreadLocal 已经不被使用了，那么实际上 set、remove、rehash 方法也不会被调用，与此同时，如果这个线程又一直存活、不终止的话，那么刚才的那个调用链就一直存在，也就**导致了 value 的内存泄漏。**
  调用 ThreadLocal 的 remove 方法。**调用这个方法就可以删除对应的 value 对象，可以避免内存泄漏。**

```java
class Res {
	// 生成序列号共享变量
	public static Integer count = 0;
	public static ThreadLocal<Integer> threadLocal = new ThreadLocal<Integer>() {
		protected Integer initialValue() {

			return 0;
		};

	};

	public Integer getNum() {
		int count = threadLocal.get() + 1;
		threadLocal.set(count);
		return count;
	}
}

```

### ***16、实现生产-消费者模式***

 blockingQueue（阻塞队列）  condition 实现  wait/notify实现

### ***17、多线程问题***

运行结果错误（全局变量的操作）

发布和初始化导致的线程安全问题（线程初始化集合数据，没初始化结束，就调用取值）

活跃性问题（死锁、活锁(线程一直忙碌，得不到结果。不停重试)、饥饿（获取不到cpu资源【优先级设置问题10大，1小】或者一直获取不到锁））

**哪些场景需要额外注意呢**

访问共享变量活或资源 /   依赖时许的操作  /  不同数据之间存在绑定关系（IP和端口号绑定） /  对方没有声明自己是 线程安全的 （ArrayList）

**多线程带来的性能问题**（比如服务器响应慢、吞吐量低、内存占用过多）

<u>线程调度和线程协作导致性能问题</u>

**调度开销：**上下问切换 （cpu对各个线程分配时间片，调度执行时会保存当前线程状态，查找下一个即将恢复执行的线程。如果切换频繁，影响性能。） /缓存失效（为了加速程序运行，可能会添加缓存，但是上下文切换之后，缓存可能失效，需要重新刷新缓存。）

**协作开销**（对于共享数据来说，为了保证线程安全，会禁止编译器和CPU进行重排序优化，也会同步刷新数据到主内存，然后有主内存刷新到工作内存）

### ***18、并发包***

##### Vector 和ArrayList

底层都是数组，Vector 线程jie安全，通过synchronized 实现。

##### HashTable 和HashMap

[HashMap在jdk1.7和1.8种的实现](https://yuanrengu.com/2020/ba184259.html)

[HashMap，HashTable,ConcurrentHashMap区别](https://www.cnblogs.com/heyonggang/p/9112731.html)

HashMap不允许重复键，可以包含重复值。HashMap允许null key和null value，而hashtable不允许。HashTable线程安全。

**Collections.synchronizedMap();**将线程不安全集合变为线程安全集合。

- 1.7中采用数组+链表，1.8采用的是数组+链表/红黑树，即在1.8中链表长度超过一定长度后就改成红黑树存储。
- 1.7扩容时需要重新计算哈希值和索引位置，1.8并不重新计算哈希值，巧妙地采用和扩容后容量进行&操作来计算新的索引位置。
- jdk1.8不会出现环形链表，但是在多线程环境下，会发生数据覆盖的情况，如果没有hash碰撞的时候，它会直接插入元素。如果线程A和线程B同时进行put操作，刚好这两条不同的数据hash值一样。

**为什么说HashMap是线程不安全的？**

在接近临界点时，若此时两个或者多个线程进行put操作，都会进行**resize（扩容）和reHash（为key重新计算所在位置）**，而reHash在并发的情况下可能会形成`链表环`

总结来说就是在多线程环境下，使用HashMap进行put操作会引起死循环，导致CPU利用率接近100%，所以在并发情况下不能使用HashMap。为什么在并发执行put操作会引起死循环？是因为**多线程会导致HashMap的Entry链表形成环形数据结构，一旦形成环形数据结构，Entry的next节点永远不为空，就会产生死循环获取Entry。****jdk1.7的情况下，并发扩容时容易形成链表环**，此情况在1.8时就好太多太多了。因为在1.8中当链表长度大于阈值（默认长度为8）时，链表会被改成树形（红黑树）结构。

 <u>*在1.7中采用表头插入法，在扩容时会改变链表中元素原本的顺序，以至于在并发场景下导致链表成环的问题；在1.8中采用尾部插入法，在扩容时会保持链表元素原本的顺序，就不会出现链表成环的问题了*</u>

**红黑树**

因为**对于搜索，插入，删除操作多的情况**下，使用红黑树的效率要高一些。因为红黑树是一种特殊的**二叉查找树**，二叉查找树**所有节点的左子树都小于该节点，所有节点的右子树都大于该节点，就可以通过大小比较关系来进行快速的检索**。在红黑树上插入或者删除一个节点之后，红黑树就发生了变化，但它不再是一颗红黑树时，**可以通过左旋和右旋，保证每次插入最多只需要三次旋转就能达到平衡，**因为红黑树强制约束了**从根到叶子的最长的路径不多于最短的路径的两倍长**，插入、删除和查找某个值的最坏情况时间都要求与树的高度成比例，这个在高度上的理论上限允许红黑树在最坏情况下都是高效的。





##### **CopyOnWrite**

当容器需要被修改的时候，不直接修改当前容器，而是先将当前容器进行 Copy，复制出一个新的容器，然后修改新的容器，完成修改之后，再将原容器的引用指向新的容器。这样就完成了整个修改过程。

迭代期间允许修改集合内容.因为迭代器使用的依然是旧数组，只不过迭代的内容可能已经过时了.

**缺点**
这些缺点不仅是针对 CopyOnWriteArrayList，其实同样也适用于其他的 CopyOnWrite 容器：

<u>内存占用问题</u>
因为 CopyOnWrite 的写时复制机制，所以在进行写操作的时候，内存里会同时驻扎两个对象的内存，这一点会占用额外的内存空间。

<u>在元素较多或者复杂的情况下，复制的开销很大</u>
复制过程不仅会占用双倍内存，还需要消耗 CPU 等资源，会降低整体性能。

<u>数据一致性问题</u>
由于 CopyOnWrite 容器的修改是先修改副本，所以这次修改对于其他线程来说，并不是实时能看到的，只有在修改完之后才能体现出来。如果你希望写入的的数据马上能被其他线程看到，CopyOnWrite 容器是不适用的。

------

##### **ConcurrenHashMap**: 

JDK1.7ConcurrentHashMap内部使用段(Segment)来表示这些不同的部分，每一个分段上都用lock锁进行保护,锁的粒度更细。

把一个整体分成了16个段(Segment.也就是最高支持16个线程的并发修改操作）。

JDK1.8Node数组+链表+红黑树的数据结构来实现，并发控制使用Synchronized和CAS来操作，

ConcurrentHashMap是使用**了锁分段技术来保证线程安全的**。

**比较**

**并发度**
Java 7 中，每个 Segment 独立加锁，最大并发个数就是 Segment 的个数，默认是 16。

但是到了 Java 8 中，锁粒度更细，理想情况下 table 数组元素的个数（也就是数组长度）就是其支持并发的最大个数，并发度比之前有提高。

**保证并发安全的原理**
Java 7 采用 Segment 分段锁来保证安全，而 Segment 是继承自 ReentrantLock。

Java 8 中放弃了 Segment 的设计，采用 Node + CAS + synchronized 保证线程安全。

**遇到 Hash 碰撞**
Java 7 在 Hash 冲突时，会使用拉链法，也就是链表的形式。

Java 8 先使用拉链法，在链表长度超过一定阈值时，将链表转换为红黑树，来提高查找效率。

**定位数组索引**

根据Key的hash值和当前数组长度求模  hash值 &（数组长度-1）= 下标

**查询时间复杂度**
Java 7 遍历链表的时间复杂度是 O(n)，n 为链表长度。

Java 8 如果变成遍历红黑树，那么时间复杂度降低为 O(log(n))，n 为树的节点个数。

```java
final V putVal(K key, V value, boolean onlyIfAbsent) {
    if (key == null || value == null) {
        throw new NullPointerException();
    }
    //计算 hash 值
    int hash = spread(key.hashCode());
    int binCount = 0;
    for (Node<K, V>[] tab = table; ; ) {
        Node<K, V> f;
        int n, i, fh;
        //如果数组是空的，就进行初始化
        if (tab == null || (n = tab.length) == 0) {
            tab = initTable();
        }
        // 找该 hash 值对应的数组下标
        else if ((f = tabAt(tab, i = (n - 1) & hash)) == null) {
            //如果该位置是空的，就用 CAS 的方式放入新值
            if (casTabAt(tab, i, null,
                    new Node<K, V>(hash, key, value, null))) {
                break;
            }
        }
        //hash值等于 MOVED 代表在扩容
        else if ((fh = f.hash) == MOVED) {
            tab = helpTransfer(tab, f);
        }
        //槽点上是有值的情况
        else {
            V oldVal = null;
            //用 synchronized 锁住当前槽点，保证并发安全
            synchronized (f) {
                if (tabAt(tab, i) == f) {
                    //如果是链表的形式
                    if (fh >= 0) {
                        binCount = 1;
                        //遍历链表
                        for (Node<K, V> e = f; ; ++binCount) {
                            K ek;
                            //如果发现该 key 已存在，就判断是否需要进行覆盖，然后返回
                            if (e.hash == hash &&
                                    ((ek = e.key) == key ||
                                            (ek != null && key.equals(ek)))) {
                                oldVal = e.val;
                                if (!onlyIfAbsent) {
                                    e.val = value;
                                }
                                break;
                            }
                            Node<K, V> pred = e;
                            //到了链表的尾部也没有发现该 key，说明之前不存在，就把新值添加到链表的最后
                            if ((e = e.next) == null) {
                                pred.next = new Node<K, V>(hash, key,
                                        value, null);
                                break;
                            }
                        }
                    }
                    //如果是红黑树的形式
                    else if (f instanceof TreeBin) {
                        Node<K, V> p;
                        binCount = 2;
                        //调用 putTreeVal 方法往红黑树里增加数据
                        if ((p = ((TreeBin<K, V>) f).putTreeVal(hash, key,
                                value)) != null) {
                            oldVal = p.val;
                            if (!onlyIfAbsent) {
                                p.val = value;
                            }
                        }
                    }
                }
            }
            if (binCount != 0) {
                //检查是否满足条件并把链表转换为红黑树的形式，默认的 TREEIFY_THRESHOLD 阈值是 8
                if (binCount >= TREEIFY_THRESHOLD) {
                    treeifyBin(tab, i);
                }
                //putVal 的返回是添加前的旧值，所以返回 oldVal
                if (oldVal != null) {
                    return oldVal;
                }
                break;
            }
        }
    }
    addCount(1L, binCount);
    return null;
}
```

```java
public V get(Object key) {
    Node<K,V>[] tab; Node<K,V> e, p; int n, eh; K ek;
    //计算 hash 值
    int h = spread(key.hashCode());
    //如果整个数组是空的，或者当前槽点的数据是空的，说明 key 对应的 value 不存在，直接返回 null
    if ((tab = table) != null && (n = tab.length) > 0 &&
            (e = tabAt(tab, (n - 1) & h)) != null) {
        //判断头结点是否就是我们需要的节点，如果是则直接返回
        if ((eh = e.hash) == h) {
            if ((ek = e.key) == key || (ek != null && key.equals(ek)))
                return e.val;
        }
        //如果头结点 hash 值小于 0，说明是红黑树或者正在扩容，就用对应的 find 方法来查找
        else if (eh < 0)
            return (p = e.find(h, key)) != null ? p.val : null;
        //遍历链表来查找
        while ((e = e.next) != null) {
            if (e.hash == h &&
                    ((ek = e.key) == key || (ek != null && key.equals(ek))))
                return e.val;
        }
    }
    return null;
}
```

**get**:

计算 Hash 值，并由此值找到对应的槽点；
如果数组是空的或者该位置为 null，那么直接返回 null 就可以了；
如果该位置处的节点刚好就是我们需要的，直接返回该节点的值；
如果该位置节点是红黑树或者正在扩容，就用 find 方法继续查找；
否则那就是链表，就进行遍历链表查找。

**<font color="red">为什么Map桶中超过8转为红黑树</font>**

事实上，链表长度超过 8 就转为红黑树的设计，**更多的是为了防止用户自己实现了不好的哈希算法时导致链表过长，从而导致查询效率低**，而此时转为红黑树更多的是一种保底策略，用来保证极端情况下查询的效率。

通常如果 hash 算法正常的话，那么链表的长度也不会很长，那么红黑树也不会带来明显的查询时间上的优势，反而会增加空间负担。所以通常情况下，并没有必要转为红黑树，所以就选择了概率非常小，小于千万分之一概率，也就是长度为 8 的概率，把长度 8 作为转化的默认阈值。

所以如果平时开发中发现 HashMap 或是 ConcurrentHashMap 内部出现了红黑树的结构，这个时候往往就说明我们的哈希算法出了问题，需要留意是不是我们实现了效果不好的 hashCode 方法，并对此进行改进，以便减少冲突。



##### **CountDownLatch：**

计数器。任务A等待其他任务执行完毕再执行。

```java
public static void main(String[] args) throws InterruptedException {
		System.out.println("等待子线程执行完毕...");
		CountDownLatch countDownLatch = new CountDownLatch(2);
		new Thread(new Runnable() {

			@Override
			public void run() {
				System.out.println("子线程," + Thread.currentThread().getName() + "开始执行...");
				countDownLatch.countDown();// 每次减去1
				System.out.println("子线程," + Thread.currentThread().getName() + "结束执行...");
			}
		}).start();
		new Thread(new Runnable() {

			@Override
			public void run() {
				System.out.println("子线程," + Thread.currentThread().getName() + "开始执行...");
				countDownLatch.countDown();
				System.out.println("子线程," + Thread.currentThread().getName() + "结束执行...");
			}
		}).start();

		countDownLatch.await();// 调用当前方法主线程阻塞  countDown结果为0, 阻塞变为运行状态
		System.out.println("两个子线程执行完毕....");
		System.out.println("继续主线程执行..");
	}

}

```

##### CyclicBarrier:

循环栅栏，CyclicBarrier初始化时规定一个数目，然后计算调用了CyclicBarrier.await()进入等待的线程数。当线程数达到了这个数目时，所有进入等待状态的线程被唤醒并继续。

```java
class Writer extends Thread {
	private CyclicBarrier cyclicBarrier;
	public Writer(CyclicBarrier cyclicBarrier){
		 this.cyclicBarrier=cyclicBarrier;
	}
	@Override
	public void run() {
		System.out.println("线程" + Thread.currentThread().getName() + ",正在写入数据");
		try {
			Thread.sleep(3000);
		} catch (Exception e) {
			// TODO: handle exception
		}
		System.out.println("线程" + Thread.currentThread().getName() + ",写入数据成功.....");
		
		try {
			cyclicBarrier.await();
		} catch (Exception e) {
		}
		System.out.println("所有线程执行完毕..........");
	}

}

public class Test001 {

	public static void main(String[] args) {
		CyclicBarrier cyclicBarrier=new CyclicBarrier(5);
		for (int i = 0; i < 5; i++) {
			Writer writer = new Writer(cyclicBarrier);
			writer.start();
		}
	}

}

```

1. CountDownLatch**是线程组之间的等待，即一个(或多个)线程等待N个线程完成某件事情之后再执行；**而CyclicBarrier则是线程组内的等待，即**每个线程相互等待，即N个线程都被拦截之后，然后依次执行。**
2. **CountDownLatch是减计数方式，而CyclicBarrier是加计数方式。**
3. **CountDownLatch计数为0无法重置，而CyclicBarrier计数达到初始值，则可以重置。**
4. CountDownLatch不可以复用，而CyclicBarrier可以复用。

##### **semaphore:**

是一种基于计数的信号量。它可以设定一个阈值，基于此，多个线程竞争获取许可信号，做自己的申请后归还，超过阈值后，线程申请许可信号将会被阻塞

创建计数为1的Semaphore，将其作为一种类似互斥锁的机制，这也叫二元信号量，表示两种互斥状态。它的用法如下：

**比如上厕所问题，10个人上，2个坑位，阈值就是2，其余人等待。上完接着按顺序上。**

availablePermits函数用来获取当前可用的资源数量

wc.acquire(); //申请资源

wc.release();// 释放资源

```java
// 创建一个计数阈值为5的信号量对象  
    	// 只能5个线程同时访问  
    	Semaphore semp = new Semaphore(5);  
    	  
    	try {  
    	    // 申请许可  
    	    semp.acquire();  
    	    try {  
    	        // 业务逻辑  
    	    } catch (Exception e) {  
    	  
    	    } finally {  
    	        // 释放许可  
    	        semp.release();  
    	    }  
    	} catch (InterruptedException e) {  
    	  
    	}  

```

### **19、*并发队列***

##### **concurrentLinkedQueue:**

**非阻塞，**适用**于高并发、无锁、无界线程安全队列**。add 和offer() 都是加入元素的方法(在ConcurrentLinkedQueue中这俩个方法没有任何区别)
 poll() 和peek() 都是取头元素节点，区别在于前者会删除元素，后者不会.(使用CAS非阻塞算法+不停重试)

#### **BlockingQueue:**

**阻塞队列。** **线程安全**。在队列为空时，获取元素的线程会等待队列变为非空。
 当队列满时，存储元素的线程会等待队列可用。 阻塞队列常用于生产者和消费者的场景，生产者是往队列里添加元素的线程，消费者是从队列里拿元素的线程。阻塞队列就是生产者存放元素的容器，而消费者也只从容器里拿元素。（内部使用reentrantlock保证）

##### ArrayBlockingQueue:

**先进先出，有边界的阻塞队列****，它的内部实现是一个**数组**.**其初始化的时候指定它的容量大小，容量大小一旦指定就不可改变**

##### LinkedBlockingQueue：

**先进先出**，大小的配置是可选的，如果我们初始化时指定一个大小，它就是有边界的，如果不指定，它就是无边界的。说是**无边界，其实是采用了默认大小为Integer.MAX_VALUE的容量** 。它的内部实现是一个<u>链表</u>。

##### **PriorityBlockingQueue**

无边界，可以插入null对象，所有插入PriorityBlockingQueue的对象必须实现 java.lang.Comparable接口，实现自定义排序。

##### **SynchronousQueue**

**SynchronousQueue**队列内部仅允许容纳一个元素。**容量是0，不是持有元素，直接传递，**当一个线程插入一个元素后会被阻塞，除非这个元素被另一个线程消费。

##### DelayQueue

DelayQueue 这个队列比较特殊，**具有“延迟”的功能。我们可以设定让队列中的任务延迟多久之后执行**，比如 10 秒钟之后执行，这在例如“30 分钟后未付款自动取消订单”等需要延迟执行的场景中被大量使用。

它是**无界队列**，放**入的元素必须实现 Delayed 接口**，而 Delayed 接口又继承了 Comparable 接口，所以自然就拥有了比较和排序的能力，

```java
public interface Delayed extends Comparable<Delayed> {
    long getDelay(TimeUnit unit);
}
```

这里的 getDelay 方法返回的是“还剩下多长的延迟时间才会被执行”，如果返回 0 或者负数则代表任务已过期。

**元素会根据延迟时间的长短被放到队列的不同位置，越靠近队列头代表越早过期。**

DelayQueue **内部使用了 PriorityQueue** 的能力来进行排序，

**blockingQueue模拟生产和消费：**

```java
package com.abner.concurrent;

import java.util.concurrent.BlockingQueue;
import java.util.concurrent.LinkedBlockingQueue;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.atomic.AtomicInteger;

class ProducerThread implements  Runnable{
    private BlockingQueue queue;
    private volatile boolean flag = true;
    private static AtomicInteger count = new AtomicInteger();
    public ProducerThread(BlockingQueue queue) {
        this.queue = queue;
    }

    @Override
    public void run() {
        try {
            System.out.println("生产线程启动...");
            while (flag) {
//                System.out.println("正在生产数据....");
                String data = count.incrementAndGet()+"";
                // 将数据存入队列中
                boolean offer = queue.offer(data, 2, TimeUnit.SECONDS);
                if (offer) {
                    System.out.println("生产者,存入" + data + "到队列中,成功.");
                } else {
                    System.out.println("生产者,存入" + data + "到队列中,失败.");
                }
                Thread.sleep(1000);
            }
        } catch (Exception e) {

        } finally {
            System.out.println("生产者退出线程");
        }

    }
}


class ConsumerThread implements Runnable {
    private BlockingQueue<String> queue;
    private volatile boolean flag = true;

    public ConsumerThread(BlockingQueue<String> queue) {
        this.queue = queue;

    }

    @Override
    public void run() {
        System.out.println("消费线程启动...");
        try {
            while (flag) {
//                System.out.println("消费者,正在从队列中获取数据..");
                String data = queue.poll(2, TimeUnit.SECONDS);
                if (data != null) {
                    System.out.println("消费者,拿到队列中的数据data:" + data);
                    Thread.sleep(1000);
                } else {
                    System.out.println("消费者,超过2秒未获取到数据..");
                    flag = false;
                }


            }
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            System.out.println("消费者退出线程...");
        }

    }

}


public class BlocklingQueueDemo {

    public static void main(String[] args) throws InterruptedException {
        BlockingQueue<String> queue = new LinkedBlockingQueue<String>(10);
        ProducerThread producerThread1 = new ProducerThread(queue);
        ProducerThread producerThread2 = new ProducerThread(queue);
        ConsumerThread consumerThread1 = new ConsumerThread(queue);
        Thread t1 = new Thread(producerThread1);
        Thread t2 = new Thread(producerThread2);
        Thread c1 = new Thread(consumerThread1);
        t1.start();
        t2.start();
        c1.start();

        // 执行10s
        Thread.sleep(10 * 1000);
        t1.stop();
        t2.stop();

    }
}

```

##### 操作方法

![微信图片编辑_20201124170634](D:\dailySoftWare\typora\md\img\微信图片编辑_20201124170634.jpg)

#### deque

```java
public interface Deque<E> extends Queue<E> {//...}
```

Deque 的意思是**双端队列，**音标是 [dek]，是 double-ended-queue 的缩写，它**从头和尾都能添加和删除元素**；而普通的 Queue 只能从一端进入，另一端出去。这是 Deque 和 Queue 的不同之处

### 20、*原子类*

java.util.concurrent.atomic 下的类，就是具有原子性的类，可以原子性地执行添加、递增、递减等操作。比如之前多线程下的线程不安全的 i++ 问题，到了原子类这里，就可以用功能相同且线程安全的 getAndIncrement 方法来优雅地解决。

原子类的作用和锁有类似之处，是为了保证并发情况下线程安全。不过原子类相比于锁，有一定的优势：

**粒度更细：**原子变量可以把竞争范围缩小到变量级别，通常情况下，锁的粒度都要大于原子变量的粒度。
**效率更高：**除了高度竞争的情况之外，使用原子类的效率通常会比使用同步互斥锁的效率更高，因为原子类底层利用了 CAS 操作，不会阻塞线程。

#### 原子类和volatile比较

如果我们有一个**可见性问题，那么可以使用 volatile 关键字**，但如果我们的问题是**一个组合操作，需要用同步来解决原子性问题的话**，那么可以使用原子变量，而不能使用 volatile 关键字。

#### 原子类和synchronized比较

1、原子类cas原理，synchronized采用monitorenter 和monitorexit它实现

2、使用范围原子类仅仅是一个对象，synchronized比较广泛，如方法、代码等。

3、原子类的粒度到变量，synchronized锁粒度大于原子变量的粒度。

4、性能上来考虑的话，悲观锁的操作相对来讲是比较重量级的。因为 synchronized 在竞争激烈的情况下，会让拿不到锁的线程阻塞，而原子类是永远不会让线程阻塞的。不过，虽然 synchronized 会让线程阻塞，但是这并不代表它的性能就比原子类差。

因为悲**观锁的开销是固定的，也是一劳永逸的。随着时间的增加，这种开销并不会线性增长。**

而乐观锁虽然在短期内的开销不大，但是随着时间的增加，它的开销也是逐步上涨的。

所以从性能的角度考虑，它们没有一个孰优孰劣的关系，而是要区分具体的使用场景。在**竞争非常激烈的情况下，推荐使用 synchronized；而在竞争不激烈的情况下，使用原子类会得到更好的效果**

#### Atomic* 基本类型原子类

 AtomicInteger、AtomicLong、AtomicBoolean

```java
AtomicInteger 类有以下几个常用的方法：

public final int get() //获取当前的值
因为它本身是一个 Java 类，而不再是一个基本类型，所以要想获取值还是需要一些方法，比如通过 get 方法就可以获取到当前的值。

public final int getAndSet(int newValue) //获取当前的值，并设置新的值
接下来的几个方法和它平时的操作相关：

public final int getAndIncrement() //获取当前的值，并自增
public final int getAndDecrement() //获取当前的值，并自减
public final int getAndAdd(int delta) //获取当前的值，并加上预期的值
boolean compareAndSet(int expect, int update) //如果输入的数值等于预期值，则以原子方式将该值更新为输入值（update）
// 这个方法也是 CAS 的一个重要体现。
```







#### Atomic*Array 数组类型原子类 *

*AtomicIntegerArray、AtomicLongArray、AtomicReferenceArray*

```java
AtomicIntegerArray：整形数组原子类；
AtomicLongArray：长整形数组原子类；
AtomicReferenceArray ：引用类型数组原子类。
Atomic\Reference 引用类型原子类
```



#### Atomic*Reference 引用类型原子类 *

*AtomicReference、AtomicStampedReference、AtomicMarkableReference*

```java
AtomicStampedReference：它是对 AtomicReference 的升级，在此基础上还加了时间戳，用于解决 CAS 的 ABA 问题。
AtomicMarkableReference：和 AtomicReference 类似，多了一个绑定的布尔值，可以用于表示该对象已删除等场景
```





#### Atomic*FieldUpdater 升级类型原子类

 AtomicIntegerfieldupdater、AtomicLongFieldUpdater、AtomicReferenceFieldUpdater

```java
AtomicIntegerFieldUpdater：原子更新整形的更新器；
AtomicLongFieldUpdater：原子更新长整形的更新器；
AtomicReferenceFieldUpdater：原子更新引用的更新器。
```

如果我们之前已经有了一个变量，比如是整型的 int，实际它并不具备原子性。可是木已成舟，这个变量已经被定义好了，此时我们有没有办法可以让它拥有原子性呢？办法是有的，就是利用 Atomic*FieldUpdater，如果它是整型的，就**使用 AtomicIntegerFieldUpdater 把已经声明的变量进行升级，这样一来这个变量就拥有了 CAS 操作的能力。**

这里的非互斥同步手段，是把我们已经声明好的变量进行 CAS 操作以达到同步的目的。那么你可能会想，既然想让这个变量具备原子性，为什么不在一开始就声明为 AtomicInteger？这样也免去了升级的过程，难道是一开始设计的时候不合理吗？这里有以下几种情况：

第一种情况是出于历史原因考虑，那么如果出于历史原因的话，**之前这个变量已经被声明过了而且被广泛运用，那么修改它成本很高，所以我们可以利用升级的原子类。**

另外还有一个使用场景，如果我们在大部分情况下并不需要使用到它的原子性，只在少数情况，比如每天只有定时一两次需要原子操作的话，我们其实没有必要把原来的变量声明为原子类型的变量，因为 AtomicInteger 比普通的变量更加耗费资源。所以如果我们有成千上万个原子类的实例的话，它占用的内存也会远比我们成千上万个普通类型占用的内存高。所以在这种情况下，我们可以利用 AtomicIntegerFieldUpdater **进行合理升级，节约内存。**

下面我们看一段代码：

```java
public class AtomicIntegerFieldUpdaterDemo implements Runnable{
 
   static Score math;
   static Score computer;
 
   public static AtomicIntegerFieldUpdater<Score> scoreUpdater = AtomicIntegerFieldUpdater
           .newUpdater(Score.class, "score");
 
   @Override
   public void run() {
       for (int i = 0; i < 1000; i++) {
           computer.score++;
           scoreUpdater.getAndIncrement(math);
       }
   }
 
   public static class Score {
       volatile int score;
   }
 
   public static void main(String[] args) throws InterruptedException {
       math =new Score();
       computer =new Score();
       AtomicIntegerFieldUpdaterDemo2 r = new AtomicIntegerFieldUpdaterDemo2();
       Thread t1 = new Thread(r);
       Thread t2 = new Thread(r);
       t1.start();
       t2.start();
       t1.join();
       t2.join();
       System.out.println("普通变量的结果："+ computer.score);
       System.out.println("升级后的结果："+ math.score);
   }
}
```

这段代码就演示了这个类的用法，比如说我们有两个类，它们都是 Score 类型的，Score 类型内部会有一个分数，也叫作 core，那么这两个分数的实例分别叫作数学 math 和计算机  computer，然后我们还声明了一个 AtomicIntegerFieldUpdater，在它构造的时候传入了两个参数，第一个是 Score.class，这是我们的类名，第二个是属性名，叫作 score。

接下来我们看一下 run 方法，run 方法里面会对这两个实例分别进行自加操作。

第一个是 computer，这里的 computer 我们调用的是它内部的 score，也就是说我们直接调用了 int 变量的自加操作，这在多线程下是线程非安全的。

第二个自加是利用了刚才声明的 scoreUpdater 并且使用了它的 getAndIncrement 方法并且传入了 math，这是一种正确使用AtomicIntegerFieldUpdater 的用法，这样可以线程安全地进行自加操作。

接下来我们看下 main 函数。在 main 函数中，我们首先把 math 和 computer 定义了出来，然后分别启动了两个线程，每个线程都去执行我们刚才所介绍过的 run 方法。这样一来，两个 score，也就是 math 和 computer 都会分别被加 2000 次，最后我们在 join 等待之后把结果打印了出来，这个程序的运行结果如下：

普通变量的结果：1942
升级后的结果：2000

可以看出，正如我们所预料的那样，普通变量由于不具备线程安全性，所以在多线程操作的情况下，它虽然看似进行了 2000 次操作，但有一些操作被冲突抵消了，所以最终结果小于 2000。可是使用 AtomicIntegerFieldUpdater  这个工具之后，就可以做到把一个普通类型的 score 变量进行原子的自加操作，最后的结果也和加的次数是一样的，也就是 2000。可以看出，这个类的功能还是非常强大的。



#### Adder 累加器

 LongAdder、DoubleAdder

**高并发下 LongAdder 比 AtomicLong 效率更高。**

**LongAdder 引入了分段累加的概念**，内部<u>一共有两个参数参与计数：第一个叫作 base，它是一个变量，第二个是 Cell[] ，是一个数组。</u>

其中的 base 是用在竞争不激烈的情况下的，可以直接把累加结果改到 base 变量上。

那么，当竞争激烈的时候，就要用到我们的 Cell[] 数组了。一旦竞争激烈，各个线程会分散累加到自己所对应的那个 Cell[] 数组的某一个对象中，而不会大家共用同一个。

这样一来，LongAdder 会把不同线程对应到不同的 Cell 上进行修改，降低了冲突的概率，这是一种分段的理念，提高了并发性，这就和 Java 7 的 ConcurrentHashMap 的 16 个 Segment 的思想类似。

竞争激烈的时候，**LongAdder 会通过计算出每个线程的 hash 值来给线程分配到不同的 Cell 上去，每个 Cell 相当于是一个独立的计数器，这样一来就不会和其他的计数器干扰，Cell 之间并不存在竞争关系，所以在自加的过程中，就大大减少了刚才的 flush 和 refresh，以及降低了冲突的概率**，这就是为什么 LongAdder 的吞吐量比 AtomicLong 大的原因，本质是空间换时间，因为它有多个计数器同时在工作，所以占用的内存也要相对更大一些。

那么 LongAdder 最终是如何实现多线程计数的呢？答案就在最后一步的求和 sum 方法，执行 LongAdder.sum() 的时候，会把各个线程里的 Cell 累计求和，并加上 base，形成最终的总和。代码如下：

```java
public long sum() {
   Cell[] as = cells; Cell a;
   long sum = base;
   if (as != null) {
       for (int i = 0; i < as.length; ++i) {
           if ((a = as[i]) != null)
               sum += a.value;
       }
   }
   return sum;
}
```

**LongAdder 只提供了 add、increment 等简单的方法，适合的是统计求和计数的场景，场景比较单一，而 AtomicLong 还具有 compareAndSet 等高级方法，可以应对除了加减之外的更复杂的需要 CAS 的场景。**

**如果我们的场景仅仅是需要用到加和减操作的话，那么可以直接使用更高效的 LongAdder，但如果我们需要利用 CAS 比如 compareAndSet 等操作的话，就需要使用 AtomicLong 来完成**

#### Accumulator 积累器

实际上是一个更通用版本的Adder累加器

 LongAccumulator、DoubleAccumulator

#### **以 AtomicInteger 为例**，分析在 Java 中如何利用 CAS 实现原子操作？

让我们回到标题中的问题，在充分了解了原子类的作用和种类之后，我们来看下  AtomicInteger 是如何通过 CAS 操作实现并发下的累加操作的，以其中一个重要方法 getAndAdd 方法为突破口。

getAndAdd方法
这个方法的代码在 Java 1.8 中的实现如下：

复制代码

```java
//JDK 1.8实现
public final int getAndAdd(int delta) {
   return unsafe.getAndAddInt(this, valueOffset, delta);
}
```



Unsafe 类
Unsafe 其实是 CAS 的核心类。由于 Java 无法直接访问底层操作系统，而是需要通过 native 方法来实现。不过尽管如此，JVM 还是留了一个后门，在 JDK 中有一个 **Unsafe 类，****它提供了硬件级别的原子操作，我们可以利用它直接操作内存数据**。

那么我们就来看一下 AtomicInteger 的一些重要代码，如下所示：

复制代码

```java
public class AtomicInteger extends Number implements java.io.Serializable {
   // setup to use Unsafe.compareAndSwapInt for updates
   private static final Unsafe unsafe = Unsafe.getUnsafe();
   private static final long valueOffset;

   static {
       try {
           valueOffset = unsafe.objectFieldOffset
               (AtomicInteger.class.getDeclaredField("value"));
       } catch (Exception ex) { throw new Error(ex); }
   }

   private volatile int value;
   public final int get() {return value;}
   ...
}
```

可以看出，在数据定义的部分，首先还获取了 Unsafe 实例，并且定义了 valueOffset。我们往下看到 static 代码块，这个代码块会在类加载的时候执行，执行时我们会调用 Unsafe 的 objectFieldOffset 方法，从而得到当前这个原子类的 value 的偏移量，并且赋给 valueOffset 变量，这样一来我们就获取到了 value 的偏移量，它的含义是在内存中的偏移地址，因为 **Unsafe 就是根据内存偏移地址获取数据的原值的**，这样我们就能通过 Unsafe 来实现 CAS 了。

value 是用 volatile 修饰的，它就是我们原子类存储的值的变量，由于它被 volatile 修饰，我们就可以保证在多线程之间看到的 value 是同一份，保证了可见性。

接下来继续看 Unsafe 的 getAndAddInt 方法的实现，代码如下：

复制代码

```java
public final int getAndAddInt(Object var1, long var2, int var4) {
   int var5;
   do {
       var5 = this.getIntVolatile(var1, var2);
   } while(!this.compareAndSwapInt(var1, var2, var5, var5 + var4));
   return var5;
}
```



首先我们看一下结构，它是一个 do-while 循环，所以这是一个死循环，直到满足循环的退出条件时才可以退出。

那么我们来看一下 do 后面的这一行代码 v**ar5 = this.getIntVolatile(var1, var2)** 是什么意思。这是个 native 方法，**作用就是获取在 var1 中的 var2 偏移处的**值。

那传入的是什么呢？传入的两个参数，第一个就是当前原子类，第二个是我们最开始获取到的 offset，这样一来我们就可以获取到当前内存中偏移量的值，并且保存到 var5 里面。此时 var5 实际上代表当前时刻下的原子类的数值。

现在再来看 while 的退出条件，也就是 compareAndSwapInt 这个方法，它一共传入了 4 个参数，这 4 个参数是 var1、var2、var5、var5 + var4，为了方便理解，我们给它们取了新了变量名，分别 object、offset、expectedValue、newValue，具体含义如下：

第一个参数 object 就是将要操作的对象，传入的是 this，也就是 atomicInteger 这个对象本身；
第二个参数是 offset，也就是偏移量，借助它就可以获取到 value 的数值；
第三个参数 expectedValue，代表“期望值”，传入的是刚才获取到的 var5；
而最后一个参数 <u>newValue 是希望修改的数值 ，等于之前取到的数值 var5 再加上 var4，而 var4 就是我们之前所传入的 delta，delta 就是我们希望原子类所改变的数值，比如可以传入 +1，也可以传入 -1。</u>
所以 compareAndSwapInt 方法的作用就是，判断如果现在原子类里 value 的值和之前获取到的 var5 相等的话，那么就把计算出来的 var5 + var4 给更新上去，所以说这行代码就实现了 CAS 的过程。

一旦 CAS 操作成功，就会退出这个 while 循环，但是也有可能操作失败。如果操作失败就意味着在获取到 var5 之后，并且在 CAS 操作之前，value 的数值已经发生变化了，证明有其他线程修改过这个变量。

这样一来，就会再次执行循环体里面的代码，重新获取 var5 的值，也就是获取最新的原子变量的数值，并且再次利用 CAS 去尝试更新，直到更新成功为止，所以这是一个死循环。

我们总结一下，**Unsafe 的 getAndAddInt 方法是通过循环 + CAS 的方式来实现的，在此过程中，它会通过 compareAndSwapInt 方法来尝试更新 value 的值，如果更新失败就重新获取，然后再次尝试更新，直到更新成功。**

### *21、Future*

### 22、重排序

编译器、JVM 或者 CPU 都有可能出于优化等目的，对于实际指令执行的顺序进行调整，这就是重排序。

**重排序场景**

编译器（包括 JVM、JIT 编译器等）出于优化的目的

CPU 重排序。CPU 同样会有优化行为，这里的优化和编译器优化类似，都是通过乱序执行的技术来提高整体的执行效率。

内存的“重排序”：内存系统内不存在真正的重排序，但是内存会带来看上去和重排序一样的效果，所以这里的“重排序”打了双引号。由于内存有缓存的存在，在 JMM 里表现为主存和本地内存，而主存和本地内存的内容可能不一致，所以这也会导致程序表现出乱序的行为。

**原子操作**

除了 long 和 double 之外的基本类型（int、byte、boolean、short、char、float）的读/写操作，都天然的具备原子性；

所有引用 reference 的读/写操作；

加了 volatile 后，所有变量的读/写操作（包含 long 和 double）。这也就意味着 long 和 double 加了 volatile 关键字之后，对它们的读写操作同样具备原子性；

在 java.concurrent.Atomic 包中的一部分类的一部分方法是具备原子性的，比如 AtomicInteger 的 incrementAndGet 方法。

【long 和 double 的值需要占用 64 位的内存空间，而对于 64 位值的写入，可以分为两个 32 位的操作来进行。

这样一来，本来是一个整体的赋值操作，就可能被拆分为低 32 位和高 32 位的两个操作。如果在这两个操作之间发生了其他线程对这个值的读操作，就可能会读到一个错误、不完整的值。】

### 23、单例模式的双重检查锁模式为什么必须加 volatile？

````java
public class Singleton {
    private static volatile Singleton singleton;
    private Singleton() {
    }
    public static Singleton getInstance() {
        if (singleton == null) {
            synchronized (Singleton.class) {
                if (singleton == null) {
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}
// 双重检查锁模式  线程安全，而且延迟加载、效率也更高。

````

**为什么要 double-check?**
我们先来看第二次的 check，这时你需要考虑这样一种情况，有两个线程同时调用 getInstance 方法，由于 singleton 是空的 ，因此两个线程都可以通过第一重的 if 判断；然后由于锁机制的存在，会有一个线程先进入同步语句，并进入第二重 if 判断 ，而另外的一个线程就会在外面等待。

不过，当第一个线程执行完 new Singleton() 语句后，就会退出 synchronized 保护的区域，这时**如果没有第二重 if (singleton == null) 判断的话，那么第二个线程也会创建一个实例，此时就破坏了单例，这肯定是不行的。**

而**对于第一个 check 而言，如果去掉它，那么所有线程都会串行执行**，效率低下，所以两个 check 都是需要保留的。

**在双重检查锁模式中为什么需要使用** volatile 关键字?

禁止相关语句的重排序,要在于它可以防止避免拿到没完成初始化的对象，从而保证了线程安全。





## 九、线程池

### ***1、优点：***

 第一：降低资源消耗。通过重复利用已创建的线程降低线程创建和销毁造成的消耗。
 第二：提高响应速度。当任务到达时，任务可以不需要等到线程创建就能立即执行。
 第三：提高线程的可管理性。线程是稀缺资源，如果无限制地创建，不仅会消耗系统资源，
 还会降低系统的稳定性，使用线程池可以进行统一分配、调优和监控。

### ***2、属性***

**corePoolSize：** 核心池的大小。 当有任务来之后，就会创建一个线程去执行任务，当线程池中的线程数目达到corePoolSize后，就会把到达的任务放到缓存队列当中
 **maximumPoolSize：** 线程池最大线程数，它表示在线程池中最多能创建多少个线程；
 **keepAliveTime：** 表示线程没有任务执行时最多保持多久时间会终止。
 **unit：** 参数keepAliveTime的时间单位，有7种取值，在TimeUnit类中有7种静态属性：

**ThreadFactory:线**程工厂，用户生产线程执行任务。默认线程工厂创建的线程属于同一线程组，优先级一样，非守护线程。也可以自定义线程工厂，定制不同线程名。

**workQueue和handle：**阻塞队列和任务拒绝策略

### ***3、拒绝策略***

调用线程shutDown方法  / 线程池没有能力处理新提交的任务  ，会拒绝任务。

**AbortPolicy**：丢弃任务并抛出RejectedExecutionException异常。用户可以感知然后自己处理。

**DiscardPolicy：**丢弃任务，静默丢弃，不通知。容易数据丢失。

**DiscardOldestPolicy**：丢弃队列头节点，通常时存活时间最长的，这样可以腾出空间给新的任务。也存在数据丢失风险。

**CallerRunsPolicy：**任务交与提交任务的线程执行。谁提交任务，谁来执行。<u>这样新提交的任务不会丢失，不会造成业务丢失。二是</u>

<u>提交任务执行时，是比较耗时的，此线程被占用之后，后续不会有新的线程提交。然后线程池中任务也可以趁机消耗，相当于给了线程池缓冲。</u>



### ***4、分类：***

###### **1、newCachedThreadPool**

（线程数无限，不需要任务队列存储任务）

创建一个可缓存线程池，**如果线程池长度超过处理需要，可灵活回收空闲线程**，若无可回收，则新建线程。**线程池为无限大（最大线程2^31 - 1 基本无限大），当执行第二个任务时第一个任务已经完成，会复用执行第一个任务的线程，而不用每次新建线程。**核心线程0

######  **2、newFixedThreadPool** 

（任务队列容量无限）

创建一个定长线程池（核心线程和最大线程数一样），可控制线程最大并发数，**超出的线程会在队列中等待**。不需要考虑线程回收

######  **3、newScheduledThreadPool** 

创建一个定长线程池，支持**定时及周期性任务执行**。

**.schedule**，延时指定时间执行

**.scheduleAtFixedRate:**延时指定时间后，以固定频率执行。时间点一到就执行。

**.scheduleWithFixedDeley:**类似上一个，但是是任务执行完毕的时间点为下一次执行任务的时间点。

######  **4、newSingleThreadExecutor**

 创建一个单线程化的线程池，它只会用唯一的工作线程来执行任务，保证所有任务按照指定顺序(FIFO, LIFO, 优先级)执行。



###### **5、singleScheduledThreadPool**

类似**newScheduledThreadPool** 只有一个线程



###### **6、ForkJoinPool**（分裂->汇总）

jdk7加入  非斐波那契数列  0 1 1 2 3 5 8 13 21 34 

采取分裂-》 汇总的 模式来执行任务。（每个线程都有自己的双端队列来存储自己分裂的子任务）

工作队列的线程会分裂多个子任务，存储在自己的双端队列中deque。这样线程可以直接在自己的任务队列中获取处理，较少线程竞争。

第二，如果线程1任务繁重，分裂多个子线程。（线程1双端队列中，获取任务是LIFO 后进先出）， 而任务2空闲，线程2会偷取线程1的任务来执行（线程2双端队列中，获取任务是FIFO 先进先出），可以很好的平衡负载。这种模式叫'work-stealing'

##### **7、如何选择**

![微信图片编辑_20201124172736](D:\dailySoftWare\typora\md\img\微信图片编辑_20201124172736.jpg)

**功能**

第 1 个需要考虑的就是功能层面，比如是否需要阻塞队列帮我们排序，如**优先级排序、延迟执行等。如果有这个需要，我们就必须选择类似于 PriorityBlockingQueue 之类的有排序能力的阻塞队列。**
**容量**

第 2 个需要考虑的是容量，或者说是否有存储的要求，还是只需要“直接传递”。在考虑这一点的时候，我们知道前面介绍的那几种阻塞队列，有的是容量固定的，如 ArrayBlockingQueue；有的默认是容量无限的，如 LinkedBlockingQueue；而有的里面没有任何容量，如 SynchronousQueue；而对于 DelayQueue 而言，它的容量固定就是 Integer.MAX_VALUE。

所以不同阻塞队列的容量是千差万别的，我们需要根据任务数量来推算出合适的容量，从而去选取合适的 BlockingQueue。
**能否扩容**

第 3 个需要考虑的是能否扩容。因为有时我们并不能在初始的时候很好的准确估计队列的大小，因为业务可能有高峰期、低谷期。

如果一开始就固定一个容量，可能无法应对所有的情况，也是不合适的，有可能需要动态扩容。如果我们需要动态扩容的话，那么就不能选择 ArrayBlockingQueue ，因为它的容量在创建时就确定了，无法扩容。相反，PriorityBlockingQueue 即使在指定了初始容量之后，后续如果有需要，也可以自动扩容。

所以我们可以根据是否需要扩容来选取合适的队列。
**内存结构**

第 4 个需要考虑的点就是内存结构。在上一课时我们分析过 ArrayBlockingQueue 的源码，看到了它的内部结构是“数组”的形式。

和它不同的是，LinkedBlockingQueue 的内部是用链表实现的，所以这里就需要我们考虑到，ArrayBlockingQueue 没有链表所需要的“节点”，空间利用率更高。所以如果我们对性能有要求可以从内存的结构角度去考虑这个问题。
**性能**

第 5 点就是从性能的角度去考虑。比如 LinkedBlockingQueue 由于拥有两把锁，它的操作粒度更细，在并发程度高的时候，相对于只有一把锁的 ArrayBlockingQueue 性能会更好。

另外，SynchronousQueue 性能往往优于其他实现，因为它只需要“直接传递”，而不需要存储的过程。如果我们的场景需要直接传递的话，可以优先考虑 SynchronousQueue

### ***5、阻塞队列***

DelayedWorkQueue:内部元素按照延迟的时间长短对任务排序，采用堆的数据结构

### ***6、线程池原理：***

提交一个任务到线程池中，线程池的处理流程如下：

1、判断线程池里的核心线程是否都在执行任务，如果不是（核心线程空闲或者还有核心线程没有被创建）则创建一个新的工作线程来执行任务。如果核心线程都在执行任务，则进入下个流程。

2、线程池判断工作队列是否已满，如果工作队列没有满，则将新提交的任务存储在这个工作队列里。如果工作队列满了，则进入下个流程。

3、判断线程池里的线程是否都处于工作状态，如果没有，则创建一个新的工作线程来执行任务。如果已经满了，则交给饱和策略来处理这个任务。

![image-20201116163902587](C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201116163902587.png)

### *7、配置线程池*

CPU密集型时，任务可以少配置线程数，大概是机器的cpu核数1~2倍，这样可以使得每个线程都在执行任务

IO密集型时，大部分线程都阻塞，故需要多配置线程数，2*cpu核数（**<u>推荐计算方法 线程数 = CPU核心数 * (1+平均等待时间/平均工作时间)）</u>**

某些进程花费了**绝大多数时间在计算上**、压缩、解密、加密等，而其他则在**等待I/O上**花费了大多是时间，如数据库、文件读写、网络通信，

前者称为计算密集型（CPU密集型）computer-bound，后者称为I/O密集型，I/O-bound。

```markdown
注：IO密集型（某大厂实践经验）
       核心线程数 = CPU核数 / （1-阻塞系数）
或着
CPU密集型：核心线程数 = CPU核数 + 1
IO密集型：核心线程数 = CPU核数 * 2

```



ThreadPoolTaskExecutor 配置 

```java
//获取当前机器的核数
public static final int cpuNum = Runtime.getRuntime().availableProcessors();

@Override
    public Executor getAsyncExecutor() {
        ThreadPoolTaskExecutor taskExecutor = new ThreadPoolTaskExecutor();
        taskExecutor.setCorePoolSize(cpuNum);//核心线程大小
        taskExecutor.setMaxPoolSize(cpuNum * 2);//最大线程大小
        taskExecutor.setQueueCapacity(500);//队列最大容量
        //当提交的任务个数大于QueueCapacity，就需要设置该参数，但spring提供的都不太满足业务场景，可以自定义一个，也可以注意不要超过QueueCapacity即可
        taskExecutor.setRejectedExecutionHandler(new ThreadPoolExecutor.CallerRunsPolicy());
        taskExecutor.setWaitForTasksToCompleteOnShutdown(true); //任务全部结束 关闭线程池
        taskExecutor.setAwaitTerminationSeconds(60);
        taskExecutor.setThreadNamePrefix("BCarLogo-Thread-");
        taskExecutor.initialize();
        return taskExecutor;
    }


```







### ***8、关闭线程池***

**shutDown()**:不接受新任务提交，但是线程池中和工作队列中可能存在正在执行的任务。

**isShutDown()**:返回true不代表已经彻底关闭，仅代表开始了关闭的流程。但是线程池中和工作队列中可能存在正在执行的任务。

**isTerminated()：**线程池关闭，内部为空，为true,否则为false.

**awaitTermination(10, TimeUnit.SECONDS)**:判断线程池状态，调用之后等待一段时间，在此期间内，线程池关闭，内部为空返回true，否则超时返回false。

等待期间线程被中断，返回InterrupterException异常。

**shutDownNow()**:立即关闭，给线程池中线程发送中断信号，尝试中断（有可能不会中断，所有编写的代码需要有响应中断信号的功能），将任务队列中的正在等待的任务转移到List中 返回，便于根据返回结果做出补救措施（记录重试）。

```java
 public List<Runnable> shutdownNow() {
        List<Runnable> tasks;
        final ReentrantLock mainLock = this.mainLock;
        mainLock.lock();
        try {
            checkShutdownAccess();
            advanceRunState(STOP);
            interruptWorkers();
            tasks = drainQueue();
        } finally {
            mainLock.unlock();
        }
        tryTerminate();
        return tasks;
    }
```



### ***9、线程池复用原理***

execute - > addworker -> worker.runWorker(这里实现复用)

```java
 public void execute(Runnable command) {
        if (command == null)
            throw new NullPointerException();
   
        int c = ctl.get();
        if (workerCountOf(c) < corePoolSize) { // 小于 核心线程数  添加线程
            if (addWorker(command, true))
                return;
            c = ctl.get();
        }
        if (isRunning(c) && workQueue.offer(command)) { //大于核心线程数 ，线程池运行正常  添加线程至工作队列
            int recheck = ctl.get();
            if (! isRunning(recheck) && remove(command)) // 如果非运行 移除任务 执行拒绝策略
                reject(command);
            else if (workerCountOf(recheck) == 0)  // 否正 可能线程被回收或者意外终止 ，需要重新添加线程
                addWorker(null, false);
        }
        else if (!addWorker(command, false)) //  addWorker 第二个参数 true 代表比对核心线程数  false 比对最大线程数
            reject(command);
    }
```

```java
private boolean addWorker(Runnable firstTask, boolean core) {
        retry:
        for (;;) {
            int c = ctl.get();
            int rs = runStateOf(c);

            // Check if queue empty only if necessary.
            if (rs >= SHUTDOWN &&
                ! (rs == SHUTDOWN &&
                   firstTask == null &&
                   ! workQueue.isEmpty()))
                return false;

            for (;;) {
                int wc = workerCountOf(c);
                if (wc >= CAPACITY ||
                    wc >= (core ? corePoolSize : maximumPoolSize)) // 判断跟核心还是最大比较
                    return false;
                if (compareAndIncrementWorkerCount(c))
                    break retry;
                c = ctl.get();  // Re-read ctl
                if (runStateOf(c) != rs)
                    continue retry;
                // else CAS failed due to workerCount change; retry inner loop
            }
        }

        boolean workerStarted = false;
        boolean workerAdded = false;
        Worker w = null;
        try {
            w = new Worker(firstTask);
            final Thread t = w.thread;
            if (t != null) {
                final ReentrantLock mainLock = this.mainLock;
                mainLock.lock();
                try {
                    // Recheck while holding lock.
                    // Back out on ThreadFactory failure or if
                    // shut down before lock acquired.
                    int rs = runStateOf(ctl.get());

                    if (rs < SHUTDOWN ||
                        (rs == SHUTDOWN && firstTask == null)) {
                        if (t.isAlive()) // precheck that t is startable
                            throw new IllegalThreadStateException();
                        workers.add(w);
                        int s = workers.size();
                        if (s > largestPoolSize)
                            largestPoolSize = s;
                        workerAdded = true;
                    }
                } finally {
                    mainLock.unlock();
                }
                if (workerAdded) {
                    t.start(); // worker具体执行 见下
                    workerStarted = true;
                }
            }
        } finally {
            if (! workerStarted)
                addWorkerFailed(w);
        }
        return workerStarted;
    }
```

```java
final void runWorker(Worker w) { /
        Thread wt = Thread.currentThread();
        Runnable task = w.firstTask;
        w.firstTask = null;
        w.unlock(); // allow interrupts
        boolean completedAbruptly = true;
        try {
            while (task != null || (task = getTask()) != null) { // 这里 通过循环 来获取任务 而不是新建线程
                w.lock();
                // If pool is stopping, ensure thread is interrupted;
                // if not, ensure thread is not interrupted.  This
                // requires a recheck in second case to deal with
                // shutdownNow race while clearing interrupt
                if ((runStateAtLeast(ctl.get(), STOP) ||
                     (Thread.interrupted() &&
                      runStateAtLeast(ctl.get(), STOP))) &&
                    !wt.isInterrupted())
                    wt.interrupt();
                try {
                    beforeExecute(wt, task);
                    Throwable thrown = null;
                    try {
                        task.run();
                    } catch (RuntimeException x) {
                        thrown = x; throw x;
                    } catch (Error x) {
                        thrown = x; throw x;
                    } catch (Throwable x) {
                        thrown = x; throw new Error(x);
                    } finally {
                        afterExecute(task, thrown);
                    }
                } finally {
                    task = null;
                    w.completedTasks++;
                    w.unlock();
                }
            }
            completedAbruptly = false;
        } finally {
            processWorkerExit(w, completedAbruptly);
        }
    }
```



## 十、锁

### ***1、偏向锁/轻量级锁/重量级锁***

三种锁特指 synchronized 锁的状态，通过在对象头中的 mark word 来表明锁的状态

**偏向锁：**一个对象被初始化后，还没有任何线程来获取它的锁时，那么它就是可偏向的，当有第一个线程来访问它并尝试获取锁的时候，它就将这个线程记录下来，以后如果尝试获取锁的线程正是偏向锁的拥有者，就可以直接获得锁，开销很小，性能最好。

**轻量级锁**：指当锁原来是偏向锁的时候，被另一个线程访问，说明存在竞争，那么偏向锁就会升级为轻量级锁，线程会通过自旋的形式尝试获取锁，而不会陷入阻塞。

**重量级锁：**重量级锁是互斥锁，它是利用操作系统的同步机制实现的。当多个线程直接有实际竞争，且锁竞争时间长的时候，轻量级锁不能满足需求，锁就会膨胀为重量级锁。重量级锁会让其他申请却拿不到锁的线程进入阻塞状态

**<u>锁升级的路径：无锁→偏向锁→轻量级锁→重量级锁</u>**

综上<u>偏向锁性能最好，可以避免执行 CAS 操作。而轻量级锁利用自旋和 CAS 避免了重量级锁带来的线程阻塞和唤醒，性能中等。重量级锁则会把获取不到锁的线程阻塞，性能最差</u>

### ***2、可重入锁/非可重入锁***

可重入锁指的是线程当前**已经持有这把锁了，能在不释放这把锁的情况下，再次获取这把锁**。同理，不可重入锁指的是虽然线程当前持有了这把锁，但是如果想再次获取这把锁，也必须要先释放锁后才能再次尝试获取。

对于可重入锁而言，最典型的就是 ReentrantLock 了，正如它的名字一样，reentrant 的意思就是可重入，它也是 Lock 接口最主要的一个实现

ReentrantLock 和synchronized 都是 可重入锁

### ***3、共享锁/独占锁***

共享锁指的是我们同一把锁**可以被多个线程同时获得**，而独占锁指的就是，这把锁只能同时被一个线程获得。

<u>读写锁，就最好地诠释了共享锁和独占锁的理念。读写锁中的读锁，是共享锁，而写锁是独占锁。读锁可以被同时读，可以同时被多个线程持有，而写锁最多只能同时被一个线程持有。</u>

### ***4、公平锁/非公平锁***

公平锁的公平的含义在于如果线程现在拿不到这把锁，那么线程就都会进入等待，开始排队，在等待队列里等待时间长的线程会优先拿到这把锁，有**先来先得**的意思。而非公平锁就不那么“完美”了，它会在一定情况下，忽略掉已经在排队的线程，发生插队现象。**但由此也提高了整体的效率。**

**区别就在于**公平锁在获取锁时多了一个限制条件：**hasQueuedPredecessors() 为 false，**这个方法就是判断在等待队列中是否已经有线程在排队了。这也就是公平锁和非公平锁的核心区别，如果是公平锁，那么一旦已经有线程在排队了，当前线程就不再尝试获取锁；对于非公平锁而言，无论是否已经有线程在排队，都会尝试获取一下锁，获取不到的话，再去排队。

### ***5、悲观锁/乐观锁***

悲观锁的概念是在获取资源之前，必须先拿到锁，以便达到“独占”的状态，当前线程在操作资源的时候，其他线程由于不能拿到锁，所以其他线程不能来影响我。比如行锁，表锁等。synchronized  ReentrantLock

而乐观锁恰恰相反，它并不要求在获取资源前拿到锁，也不会锁住资源；相反，**乐观锁利用 CAS 理念**，在不独占资源的情况下，完成了对资源的修改。利用版本字段控制  原子类AutomicInteger

### ***6、自旋锁/非自旋锁***

自旋锁的理念是如果线程现在拿不到锁，**并不直接陷入阻塞或者释放 CPU 资源，而是开始利用循环，不停地尝试获取锁**，这个循环过程被形象地比喻为“自旋”，就像是线程在“自我旋转”。相反，非自旋锁的理念就是没有自旋的过程，如果拿不到锁就直接放弃，或者进行其他的处理逻辑，例如去排队、陷入阻塞等。

【自旋锁不会使线程状态发生切换，一直处于用户态，即线程一直都是active的；不会使线程进入阻塞状态，减少了不必要的上下文切换，执行速度快

非自旋锁在获取不到锁的时候会进入阻塞状态，从而进入内核态，当获取到锁的时候需要从内核态恢复，需要线程上下文切换。 （线程被阻塞后便进入内核（Linux）调度状态，这个会导致系统在用户态与内核态之间来回切换，严重影响锁的性能）】

### ***7、可中断锁/不可中断锁***

**synchronized** 关键字修饰的锁代表的是**不可中断锁**，一旦线程申请了锁，就没有回头路了，只能等到拿到锁以后才能进行其他的逻辑处理。而我们的 **ReentrantLock 是一种典型的可中断锁**，例如使用 lockInterruptibly 方法在获取锁的过程中，突然不想获取了，那么也可以在中断之后去做其他的事情，不需要一直傻等到获取到锁才离开。

### 8、CAS*无锁机制*

CAS 有三个操作数：内存值 V、预期值 A、要修改的值 B。CAS 最核心的思路就是，**仅当预期值 A 和当前的内存值 V 相同时，才将内存值修改为 B**。

**流程：**

CAS 会提前假定当前内存值 V 应该等于值 A，而**值 A 往往是之前读取到当时的内存值 V**。在执行 CAS 时，如果发现当前的内存值 V 恰好是值 A 的话，那 CAS 就会把内存值 V 改成值 B，而**值 B 往往是在拿到值 A 后，在值 A 的基础上经过计算而得到的**。如果执行 CAS 时发现此时内存值 V 不等于值 A，则说明在刚才计算 B 的期间内，内存值已经被其他线程修改过了，那么本次 CAS 就不应该再修改了，可以避免多人同时修改导致出错。这就是 CAS 的主要思路和流程。

**缺点：**

**ABA 问题**。从 A 变成了 B，再由 B 变回了 A，CAS 会认为变量的值在此期间没有发生过变化。所以，CAS 并不能检测出在此期间值是不是被修改过，它只能检查出现在的值和最初的值是不是一样。（添加一个**版本号**就可以解决。**1A→2B→3A**，）**AtomicStampedReference** 这个类，它是专门用来解决 ABA 问题的，解决思路正是利用版本号，AtomicStampedReference 会维护一种类似 <Object,int> 的数据结构，其中的 int 就是用于计数的，也就是版本号，它可以对这个对象和 int 版本号同时进行原子更新，从而也就解决了 ABA 问题

**自旋时间过长。**单次 CAS 不一定能执行成功，所以 **CAS 往往是配合着循环来实现的**，有的时候甚至是死循环，不停地进行重试，直到线程竞争不激烈的时候，才能修改成功。在高并发的场景下，通常 CAS 的效率是不高的。

**不能灵活控制线程安全的范围。**不能针对多个共享变量同时进行 CAS 操作。利用一个新的类，来整合刚才这一组共享变量，这个新的类中的多个成员变量就是刚才的那多个共享变量，然后再利用 atomic 包中的 AtomicReference 来把这个新对象整体进行 CAS 操作，这样就可以保证线程安全。



### 9、synchronized***锁原理***

通过javap查看汇编结果

同步代码块通过monitorenter 和 monitorexit指令实现加锁和解锁。

同步方法同年ACC_SYNCHTONIZED标识实现，本质还是通过monitorenter 和 monitorexit指令实现加锁和解锁。

### 10、synchronized和lock***选择***

1、都可保证可见性。

2、都具有可重入特点。

3、synchronized自动，synchronized内置锁，由jvm控制锁和释放锁。同时只能被一个线程拥有，不能设置是否公平。lock手动，同时可以被多个线程拥有。如读锁，可以设置是否公平。



**同步实现机制不同**

- synchronized 通过 Java 对象头锁标记和 Monitor 对象实现同步。
- ReentrantLock 通过CAS、AQS（AbstractQueuedSynchronizer）和 LockSupport（用于阻塞和解除阻塞）实现同步。

**可见性实现机制不同**

- synchronized 依赖 JVM 内存模型保证包含共享变量的多线程内存可见性。
- ReentrantLock 通过 AQS 的 volatile state 保证包含共享变量的多线程内存可见性。

**使用方式不同**

- synchronized 可以修饰实例方法（锁住实例对象）、静态方法（锁住类对象）、代码块（显示指定锁对象）。
- ReentrantLock 显示调用 tryLock 和 lock 方法，需要在 finally 块中释放锁。

**功能丰富程度不同**

- synchronized 不可设置等待时间、不可被中断（interrupted）。
- ReentrantLock 提供有限时间等候锁（设置过期时间）、可中断锁（lockInterruptibly）、condition（提供 await、condition（提供 await、signal 等方法）等丰富功能

**锁类型不同**

- synchronized 只支持非公平锁。
- ReentrantLock 提供公平锁和非公平锁实现。当然，在大部分情况下，非公平锁是高效的选择。





### ***11、Lock方法介绍***

#### lock()

```java
Lock lock = ...;
lock.lock();
try{
    //获取到了被本锁保护的资源，处理任务
    //捕获异常
}finally{
    lock.unlock();   //释放锁
}
```

lock() 方法不能被中断

#### tryLock()

tryLock() 用来尝试获取锁，如果当前锁没有被其他线程占用，则获取成功，返回 true，否则返回 false，代表获取锁失败。该方法会立即返回，即便在拿不到锁时也不会一直等待

不遵守设定的公平原则。

```java
public boolean tryLock() {
    return sync.nonfairTryAcquire(1);
}
```



```java
Lock lock = ...;
if(lock.tryLock()) {
     try{
         //处理任务
     }finally{
         lock.unlock();   //释放锁
     } 
}else {
    //如果不能获取锁，则做其他事情
}
```

创建 lock() 方法之后使用 tryLock() 方法并用 if 语句判断它的结果

#### tryLock(long time, TimeUnit unit)

会有一个超时时间，在拿不到锁时会等待一定的时间，如果在时间期限结束后，还获取不到锁，就会返回 false；如果一开始就获取锁或者等待期间内获取到锁，则返回 true。解决了 lock() 方法容易发生死锁的问题。

#### lockInterruptibly()

这个方法的作用就是去获取锁，如果这个锁当前是可以获得的，那么这个方法会立刻返回，但是如果这个锁当前是不能获得的（被其他线程持有），那么当前线程便会开始等待，除非它等到了这把锁或者是在等待的过程中被中断了，否则这个线程便会一直在这里执行这行代码。一句话总结就是，**<u>除非当前线程在获取锁期间被中断，否则便会一直尝试获取直到获取到为止。是可以响应中断的</u>**

```java
 public void lockInterruptibly() {
        try {
            lock.lockInterruptibly();
            try {
                System.out.println("操作资源");
            } finally {
                lock.unlock();
            }
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
```

#### unlock()

执行 unlock() 的时候，内部会把锁的“被持有计数器”减 1，直到减到 0 就代表当前这把锁已经完全释放了，如果减 1 后计数器不为 0，说明这把锁之前被“重入”了，那么锁并没有真正释放，仅仅是减少了持有的次数

### 12、***读写锁***

如果有一个线程已经占用了读锁，则此时其他线程如果要申请读锁，可以申请成功。

如果有一个线程已经占用了读锁，则此时其他线程如果要申请写锁，则申请写锁的线程会一直等待释放读锁，因为读写不能同时操作。

如果有一个线程已经占用了写锁，则此时其他线程如果申请写锁或者读锁，都必须等待之前的线程释放写锁，同样也因为读写不能同时，并且两个线程不应该同时写。

所以我们用一句话总结：要么是一个或多个线程同时有读锁，要么是一个线程有写锁，但是两者不会同时出现。也可以总结为：**读读共享、其他都互斥（写写互斥、读写互斥、写读互斥）**

### 13、***ReentrantLock插队/升降级策略***

插队策略

公平策略下，只要队列里有线程已经在排队，就不允许插队。

非公平策略下：

如果允许读锁插队，那么由于读锁可以同时被多个线程持有，所以可能造成源源不断的后面的线程一直插队成功，导致读锁一直不能完全释放，从而导致写锁一直等待，为了防止“饥饿”，在等待队列的头结点是尝试获取写锁的线程的时候，不允许读锁插队。

写锁可以随时插队，因为写锁并不容易插队成功，写锁只有在当前没有任何其他线程持有读锁和写锁的时候，才能插队成功，同时写锁一旦插队失败就会进入等待队列，所以很难造成“饥饿”的情况，允许写锁插队是为了提高效率。

升降级策略：只能从写锁降级为读锁，不能从读锁升级为写锁。

### ***14、JVM对锁的优化***

##### **自适应的自旋锁**

JDK 1.6 中引入了自适应的自旋锁来解决长时间自旋的问题。自适应意味着自旋的时间不再固定，而是会根据最近自旋尝试的成功率、失败率，以及当前锁的拥有者的状态等多种因素来共同决定。**自旋的持续时间是变化的，自旋锁变“聪明”了**。比如，如果最近尝试自旋获取某一把锁成功了，那么下一次可能还会继续使用自旋，并且允许自旋更长的时间；但是如果最近自旋获取某一把锁失败了，那么可能会省略掉自旋的过程，以便减少无用的自旋，提高效率

##### **锁消除**

如果发现某些对象不可能被其他线程访问到，那么就可以把它们当成栈上数据，栈上数据由于只有本线程可以访问，自然是线程安全的，也就无需加锁，所以会把这样的锁给自动去除掉。

##### **锁粗化**

如果我们释放了锁，紧接着什么都没做，又重新获取锁，例如下面这段代码所示：

```java
public void lockCoarsening() {
    synchronized (this) {
        //do something
    }
    synchronized (this) {
        //do something
    }
    synchronized (this) {
        //do something
    }
}
```

那么其实这种释放和重新获取锁是完全没有必要的，如果我们把同步区域扩大，也就是只在最开始加一次锁，并且在最后直接解锁，那么就可以把中间这些无意义的解锁和加锁的过程消除，相当于是把几个 synchronized 块合并为一个较大的同步块。这样做的好处在于在线程执行这些代码时，就无须频繁申请与释放锁了，这样就减少了性能开销。

锁粗化不适用于循环的场景，仅适用于非循环的场景。

锁粗化功能是默认打开的，用 -XX:-EliminateLocks 可以关闭该功能。

##### **偏向锁/轻量级锁/重量级锁**

## 十一、中间件

### **1、ngnix**

**正向代理**：为客户端代理。（访问国外服务器，国外搭建代理服务器，由服务器来转发。）

**反向代理**：为服务器代理。（我打电话给10086，10086总机会转发到具体的服务器来服务）

[nginx 分析总结](https://juejin.cn/post/6942607113118023710?utm_source=gold_browser_extension)

### 2、Mycat

#### 定义

开源的分布式数据库系统，是一个实现了MySQL 协议的的Server.

应用可以把它看作是一个**数据库代理**，用MySQL 客户端工具和命令行访问，而其本身可以用MySQL 原生（Native）协议与多个MySQL 服务器通信，也可以用JDBC 协议与大多数主流数据库服务器通信

**数据库中间件**，不仅仅可以用作读写分离、以及分表分库、容灾备份，而且可以用于多租户应用开发、云平台基础设施、让你的架构具备很强的适应性和灵活性。

#### 原理

Mycat 的原理中最重要的一个动词是“拦截”，它拦截了用户发送过来的SQL 语句，首先对SQL 语句做了一些特定的分析：如分片分析、路由分析、读写分离分析、缓存分析等，然后将此SQL 发往后端的真实数据库，

并将返回的结果做适当的处理，最终再返回给用户。

**当Mycat 收到一个SQL 时，会先解析这个SQL，查找涉及到的表，然后看此表的定义，如果有分片规则，则获取到SQL 里分片字段的值，并匹配分片函数，得到该SQL 对应的分片列表，然后将SQL 发往这些分片去执行，最后收集和处理所有分片返回的结果数据，并输出到客户端。**



## 十二、数据库

### **1、redis**

#### **1、介绍**

高性能key-value数据库，支持数据持久化，master-slave数据备份、提供string、set、list、hash、zset等数据结构存储。

| 数据类型   | 存储的值               | 读写能力                                                   |
| ---------- | ---------------------- | ---------------------------------------------------------- |
| String     | 字符串，整数或浮点数   | 对字符串或一部分字符串执行操作；对整数进行自增和自减操作等 |
| Hash       | 包含键值对的无序散列表 | 对单个 元素进行增、删、改；获取所以的键值对等              |
| List       | 链表上的节点字符串元素 | 推入、弹出元素；修剪、查找、移除元素等                     |
| Set        | 各不相同的字符串元素   | 对单个 元素进行增、删、改；计算集合 交，并补集等           |
| Sorted Set | 带分数的有序集合       | 对单个 元素进行增、删、改；按照分数范围查元素等            |

[各个数据类型的命令演示或者参照redis官网api](https://www.cnblogs.com/dmego/p/9770613.html)

#### **2、应用**

解决数据库压力，比如短息验证码有效期、session共享

#### 3、集群方式

##### **1、主从复制**

1：当一个从数据库启动时，会向主数据库发送sync命令，

2：主数据库接收到sync命令后会开始在后台保存快照（执行rdb操作），并将保存期间接收到的命令缓存起来

3：当快照完成后，redis会将快照文件发送到slave，slave保存到磁盘上，然后加载到内存中，接着master发送所有缓存的命令发送给从数据库，slave进行同步。

4：从数据库收到后，会载入快照文件并执行收到的缓存的命令。

**理解**

- 主从模式的一个作用是**备份数据**，这样当一个节点损坏（指不可恢复的硬件损坏）时，数据因为有备份，可以方便恢复。
- 另一个作用是**负载均衡**，所有客户端都访问一个节点肯定会影响Redis工作效率，有了主从以后，查询操作就可以通过查询从节点来完成。

1. 一个Master可以有多个Slaves
2. 默认配置下，master节点可以进行读和写，slave节点只能进行读操作，写操作被禁止

**缺点：**

- master节点挂了以后，redis就不能对外提供写服务了，因为剩下的slave不能成为master





**支持断点续传：**master node会在内存中常见一个backlog，master和slave都会保存一个replica offset还有一个master id，在backlog中的。如果master和slave网络连接断掉了，slave会让master从上次的replica offset开始继续复制。

但是如果没有找到对应的offset，那么就会执行一次resynchronization**

**无磁盘化复制**：master在内存中直接创建rdb，然后发送给slave，不会在自己本地落地磁盘了

repl-diskless-sync：无磁盘化同步
repl-diskless-sync-delay，等待一定时长再开始复制，因为要等更多slave重新连接过来

**过期key处理**

slave不会过期key，只会等待master过期key。如果master过期了一个key，或者通过LRU淘汰了一个key，那么会模拟一条del命令发送给slave。

##### **2、哨兵模式sentine**l

**监控**：哨兵(sentinel) 会不断地检查你的Master和Slave是否运作正常。

**通知**：当被监控的某个 Redis出现问题时, 哨兵(sentinel) 可以通过 API 向管理员或者其他应用程序发送通知

**自动故障转移：**当一个Master不能正常工作时，哨兵(sentinel) 会开始一次自动故障迁移操作,它会将失效Master的其中一个Slave升级为新的Master, 并让失效Master的其他Slave改为复制新的Master; 当客户端试图连接失效的Master时,集群也会向客户端返回新Master的地址,使得集群可以使用Master代替失效Master。

<u>哨兵(sentinel) 是一个**分布式系统**,你可以在一个架构中运行多个哨兵(sentinel) 进程,这些进程使用**流言协议(gossipprotocols)**来接收关于Master是否下线的信息,并使用**投票协议(agreement protocols)来决定是否执行自动故障迁移**,以及选择哪个Slave作为新的Master.</u>

其实是一个**运行在特殊模式下的 Redis 服务器**，你可以在启动一个普通 Redis 服务器时通过给定 --sentinel 选项来启动哨兵(sentinel).



**理解**

- sentinel模式是**建立在主从模式的基础上**，如果只有一个Redis节点，sentinel就没有任何意义
- 当master节点挂了以后，sentinel会在slave中选择一个做为master，并修改它们的配置文件，其他slave的配置文件也会被修改，比如slaveof属性会指向新的master
- 当master节点重新启动后，它将不再是master而是做为slave接收新的master节点的同步数据
- sentinel因为也是一个进程有挂掉的可能，所以**sentinel也会启动多个形成一个sentinel集群**
- 当主从模式配置密码时，sentinel也会同步将配置信息修改到配置文件中，不许要担心。
- 一个sentinel或sentinel集群可以管理多个主从Redis。
- sentinel最好不要和Redis部署在同一台机器，不然Redis的服务器挂了以后，sentinel也挂了
- sentinel监控的Redis集群都会定义一个master名字，这个名字代表Redis集群的master Redis。

 　**当使用sentinel模式的时候，客户端就不要直接连接Redis，而是连接sentinel的ip和port，**由sentinel来提供具体的可提供服务的Redis实现，这样当master节点挂掉以后，sentinel就会感知并将新的master节点提供给使用者。

　　sentinel模式基本可以满足一般生产的需求，具备高可用性。但是当数据量过大到一台服务器存放不下的情况时，主从模式或sentinel模式就不能满足需求了，这个时候需要对存储的数据进行分片，将数据存储到多个Redis实例中，

##### 3、cluster模式

- cluster可以说是sentinel和主从模式的结合体，通过cluster可以实现主从和master重选功能，所以如果配置两个副本三个分片的话，就需要六个Redis实例。
- 因为Redis的**数据是根据一定规则分配到cluster的不同机器的**，当数据量过大时，可以新增机器进行扩容

　　这种模式适合数据量巨大的缓存要求，当数据量不是很大使用sentinel即可。



#### **5、事务**

Redis 事务可以一次执行多个命令，隔离操作、原子操作。步骤：开始事务-》命令入队-》执行事务

**<u>el:** MULTI 开始一个事务， 然后将多个命令入队到事务中， 最后由 EXEC 命令触发事务</u>

#### **6、持久化**

**RDB：快照。**默认开启。是在某个时间 点将数据写入一个临时文件，持久化结束后，用这个临时文件替换上次持久化的文件，达到数据恢复。

<u>单独子线程来持久化，保证了高性能，但是如果持久化期间redis发生故障，会有数据丢失。</u>

```markdown
1)rdb持久化为redis开启的默认持久化方式，可通过配置文件灵活配置，默认如下
1
save 900 1          //15分钟内有一条数据写入时触发rdb持久化
save 300 10        //5分钟内有10条数据写入时触发rdb持久化
save 60 10000     //1分钟内有10000条数据写入时触发rdb持久化
1
2
3
(2)除了默认触发之外，我们也可以通过redis客户端发送命令主动触发rdb持久化，具体命令如下：
1
>save          //主进程执行rdb持久化操作
>bgsave      //生成后台进程执行rdb持久化(默认方式)
```

**: rdb持久化模式下，当机器宕机，会丢失多少数据？**
答: 从最近一次rdb保存到宕机时的数据都会丢失



这个执行数据写入到临时文件的时间点是可以通过配置来自己确定的，通过配置**redis 在 n 秒内如果超过 m 个 key 被修改**这执行一次 RDB 操

**AOF:append-only file：****默认关闭。**将“操作 + 数据”以格式化指令的方式追加到操作日志文件的尾部，“日志文件”保存了历史所有的操作过程；当 server 需要数据恢复时，可以直接 replay 此日志文件，即可还原所有的操作过程。

<u>保证了数据安全，但是文件会过大。恢复时间慢。</u> 恢复时需要人工检测文件的完整性。

#### **7、aof记录同步选项：**

**触发条件：**

redis默认不开启aof持久化方式，可通过修改如下配置开启

```sql
	appendonly yes #yes开启no关闭
1
```

aof持久化刷盘频率控制

```sql
	appendfsync always  //每次命令都刷盘
	appendfsync everysec //每秒刷盘一次(默认)
	appendfsync no  //从不刷盘，由内核去刷盘
```



**always**：每一条 aof 记录都**立即同步到文件**，这是最安全的方式，也以为更多的磁盘操作和阻塞延迟，是 IO 开支较大。

**everysec：每秒同步一次**，性能和安全都比较中庸的方式，也是 redis 推荐的方式。如果遇到物理服务器故障，有可能导致最近一秒内 aof 记录丢失(可能为部分丢失)。

no：redis 并不直接调用文件同步，而是交**给操作系统来处理**，操作系统可以根据 buffer 填充情况 / 通道空闲时间等择机触发同步；这是一种普通的文件操作方式。性能较好，在物理服务器故障时，数据丢失量会因 OS 配置有关

#### **8、aof重写：**

1. REWRITE: 在主线程中重写AOF，会阻塞工作线程，在生产环境中很少使用，处于废弃状态；
2. BGREWRITE: 在 后台（子进程）重写AOF, 不会阻塞工作线程，能正常服务，此方法最常用。

#### **9、发布和订阅**

Redis 发布订阅(pub/sub)是一种消息通信模式：发送者(pub)发送消息，订阅者(sub)接收消息。

#### **10、集群**

主从/sentinel/ cluster(cluster模式的出现就是为了解决单机Redis容量有限的问题，将Redis的数据根据一定的规则分配到多台机器。)

#### 12、key的失效处理

**定期删除和惰性删除**

定期删除:指的是redis默认是每隔100ms就随机抽取一些设置了过期时间的key，检查其是否过期，如果过期就删除。

惰性删除:在你获取某个key的时候，redis会检查一下 ，这个key如果设置了过期时间那么是否过期了,如果过期了此时就会删除，不会给你返回任何东西。

<u><font color=red>定期删除漏掉了很多过期key，然后你也没及时去查，也就没走惰性删除，此时会怎么样？如果大量过期key堆积在内存里，导致redis内存块耗尽了，咋整？</font></u>

**内存淘汰机制**

1）noeviction：当内存不足以容纳新写入数据时，新写入操作会报错，这个一般没人用吧，实在是太恶心了

2）allkeys-lru：当内存不足以容纳新写入数据时，在键空间中，移除最近最少使用的key（这个是最常用的）

3）allkeys-random：当内存不足以容纳新写入数据时，在键空间中，随机移除某个key，这个一般没人用吧，为啥要随机，肯定是把最近最少使用的key给干掉啊

4）volatile-lru：当内存不足以容纳新写入数据时，在设置了过期时间的键空间中，移除最近最少使用的key（这个一般不太合适）

5）volatile-random：当内存不足以容纳新写入数据时，在设置了过期时间的键空间中，随机移除某个key

6）volatile-ttl：当内存不足以容纳新写入数据时，在设置了过期时间的键空间中，有更早过期时间的key优先移除

#### 13、高并发/高可用

主从架构 -> 读写分离 -> 支撑10万+读QPS的架构，所有从节点负责读。

redis replicationI(根据以上主从复制)

redis主从架构 -> 读写分离架构 -> 可支持水平扩展的读高并发架构

master 持久化  本地备份数据

#### 14、与memcached比较

都是内存存储。

1、数据支持类型，redis比较丰富，memcache只支持k-v ，但是支持图片和视频缓存

2、数据安全方面呢，redis支持持久化和数据恢复，memcache不支持。

3、底层结构。单进程redis，memcache多线程非阻塞。

#### 15、使用场景

1、如果有持久方面的需求或对数据类型和处理有要求的应该选择redis。 2、如果简单的key/value 存储应该选择memcached。

#### 16、redis相关命令

```shell
redis-server --service-install redis.windows-service.conf --loglevel verbose # 指定文件 安装到服务 windows
redis-server --service-start redis.windows-service.conf # 指定文件启动
redis-server --service-stop # 停止
keys * # 查看所有key
config set requirepass 123456 #设置密码  或者配置文件也设置 requirepass 123456 重启
```

| set key value      | 设置 key 值为 value                                      |
| ------------------ | -------------------------------------------------------- |
| get key            | 读取 key 的值                                            |
| del key            | 删除 key                                                 |
| expire key seconds | 设置 key 的生存时间（seconds 秒后自动删除）              |
| ttl key            | 查看 key 剩余生存时间                                    |
| exists key         | 判断 key 是否存在                                        |
| ping               | 测试与服务端是否联通                                     |
| keys *             | 匹配数据库中所有 key                                     |
| dbsize             | 查询当前数据库中 key 的数量                              |
| info               | 返回关于 Redis 服务器的各种信息和统计数值                |
| flushdb            | 清空当前数据库中的所有 key                               |
| flushall           | 清空整个 Redis 服务器的数据( 删除所有数据库的所有 key ） |
| quit               | 请求服务器关闭与当前客户端的连接( 断开连接 )             |





### 2、mongoDB

MongoDB 是一个基于【分布式文件存储】的数据库，它属于NoSQL数据库。由 C++ 语言编写

它支持的数据结构非常松散，是**类似json的bson格式**，因此可以存储比较复杂的数据类型。**支持对数据建立索引。**

MongoDB就是**文档型NoSQL数据库**

![TIM截图20201125101806](D:\dailySoftWare\typora\md\img\TIM截图20201125101806.png)

一个collection（集合）中的所有field（域）是collection（集合）中所有document（文档）中包含的field（域） 的并集。

Mongodb的部署方案有单机部署、主从部署、副本集（主备）部署、分片部署、副本集与分片混合部署。

**副本集与分片混合部署**

 Mongodb的集群部署方案有三类角色：

实际数据存储节点，配置文件存储节点和路由接入节点。

 **实际数据存储节点**的作用就是存储数据，

 **路由接入节点**的作用是在分片的情况下起到负载均衡的作用。

 **存储配置存储节点**的作用其实存储的是片键与chunk 以及chunk 与server 的映射关系，

### 3、memcached

#### 介绍

是一个免费开源的、高性能的、具有分布式内存对象的缓存系统，它通过减轻数据库负载加速动态Web应用。**单进程多线程**

#### 特性

l 本质上就是一个内存key-value缓存；

l 协议简单，使用的是基于**文本行的协议**；

l **不支持数据的持久化**，服务器关闭之后数据全部丢失；

l 互不通信的Memcached之间具有分布特征 ；

l **没有安全机制**

支持集群，memcached节点之间是不会进行任何通信的

#### 适用场景

适合变化频繁，查询频繁，重点是不是要入库的场景。电商场景中用于页面数据的缓存，这是memcached适合的场景

page view（pv）页面展示次数，如果一些页面都没什么访问量就不要考虑memcached了。

#### hash算法

##### 余数分散

<img src="D:\dailySoftWare\typora\md\img\33.png" alt="33" style="zoom:50%;" />



##### 一致性hash算法

#### 内存分配

l 内存被拆分为多个SlabClass 

l 每个Slab Class中有多个Slab 每个Slab=1M 

l 每个Slab下有多个大小相等的Chunk 

l 不同Slab中的Chunk大小不等 

l 数据存储在Chunk中

#### 缓存过期策略

Memcached不会释放已分配的内存，其存储空间可以重复使用

Memcached内部不会监视数据是否过期，而是在**get时查看数据的时间戳，查看数据是否过期**。被称为lazy expiration(惰性过期) 

Memcached内存空间不足，即无法从slab class中获取到新的空间时，就从**最近未被使用的数据中搜索，将其空间分配给新的数据**。（如果要禁用LRU，使用-M参数，超出会报错）

## 十三、主流服务注册中心比较

### 1、Nacos 

支持基于 DNS 和基于 RPC 的服务发现（可以作为springcloud的注册中心）、**动态配置服务**（可以做配置中心，，Nacos采用Netty保持TCP长连接实时推送）、动态 DNS 服务

Nacos = Spring Cloud注册中心 + Spring Cloud配置中心。

通知遵循**CP原则（一致性+分离容忍） 和AP原则（可用性+分离容忍）**,根据服务注册选择临时和永久来决定走AP模式还是CP模式,

支持Dubbo 、SpringCloud、K8S集成

属于外部应用，侵入性小

在线服务治理



### 2、consul

遵循CP原则（一致性+分离容忍） 服务注册稍慢，由于其一致性导致了在Leader挂掉时重新选举期间真个consul不可用。

要求必须过半数的节点都写入成功才认为注册成功

Raft算法，比zookeeper使用的Paxos算法更加简单

支持SpringCloud K8S集成

HTTP/DNS

### 3、eureka

直接集成到应用中，依赖于应用自身完成服务的注册与发现

遵循AP（可用性+分离容忍）原则，有较强的可用性，服务注册快，但牺牲了一定的一致性。

目前已经不进行升级

只支持SpringCloud集成

HTTP

Eureka需要配合MQ实现配置动态刷新配置

Spring Cloud原生全家桶



### 4、zookeeper

zab协议

cp

## 十四、网络编程

### 1、socket

### 2、TCP和UDP

Transmission Control Protocol

User Datagram Protocol

|              | UDP                                            | TCP                                        |
| :----------- | :--------------------------------------------- | ------------------------------------------ |
| 是否连接     | **无连接**                                     | **面向连接**                               |
| 是否可靠     | 不可靠传输，不使用流量控制和拥塞控制           | 可靠传输，使用流量控制和拥塞控制           |
| 连接对象个数 | 支持一对一，一对多，多对一和多对多交互通信     | 只能是一对一通信                           |
| 传输方式     | **面向报文**                                   | **面向字节流**                             |
| 首部开销     | 首部开销小，仅8字节                            | 首部最小20字节，最大60字节                 |
| 适用场景     | 适用于**实时应用**（IP电话、视频会议、直播等） | 适用于要求**可靠传输的**应用，例如文件传输 |
|              | UDP不保证。                                    | TCP保证数据顺序                            |

### 3、三次握手

[参考](https://zhuanlan.zhihu.com/p/86426969)

第一次握手：主机A通过向主机B 发送一个**含有同步序列号的标志位**的数据段给主机B，向主机B 请求建立连接，通过这个数据段， 主机A告诉主机B 两件事：我想要和你通信；你可以用哪个序列号作为起始数据段来回应我。（**<u>同步位SYN=1，序号SEQ=x（表明传送数据时的第一个数据字节的序号是x</u>**））

第二次握手：主机B 收到主机A的请求后，用一个**带有确认应答（ACK）和同步序列号（SYN）标志位的数据段响应主机A**，也告诉主机A两件事：我已经收到你的请求了，你可以传输数据了；你要用那个序列号作为起始数据段来回应我（**<u>该报文段中同步位SYN=1，确认号ACK=x+1，序号SEQ=y；</u>**）

第三次握手：主机A收到这个数据段后，**再发送一个确认应答**，（**<u>ACK(ack=y+1)</u>**）确认已收到主机B 的数据段："我已收到回复，我现在要开始传输实际数据了，这样3次握手就完成了，主机A和主机B 就可以传输数据了。

*<u>为了保证服务端能收接受到客户端的信息并能做出正确的应答而进行前两次(第一次和第二次)握手，为了保证客户端能够接收到服务端的信息并能做出正确的应答而进行后两次(第二次和第三次)握手。</u>*

<img src="D:\dailySoftWare\typora\md\img\v2-2a54823bd63e16674874aa46a67c6c72_r.jpg" alt="v2-2a54823bd63e16674874aa46a67c6c72_r" style="zoom:50%;" />

#### **1.1 为什么需要三次握手，两次不行吗？**

第一次握手：客户端发送网络包，服务端收到了。

这样服务端就能得出结论：客户端的发送能力、服务端的接收能力是正常的。

第二次握手：服务端发包，客户端收到了。

这样客户端就能得出结论：服务端的接收、发送能力，客户端的接收、发送能力是正常的。不过此时服务器并不能确认客户端的接收能力是否正常。

第三次握手：客户端发包，服务端收到了。

这样服务端就能得出结论：客户端的接收、发送能力正常，服务器自己的发送、接收能力也正常。

因此，需要三次握手才能确认双方的接收与发送能力是否正常。

#### **1.2 什么是半连接队列？**

服务器第一次收到客户端的 SYN 之后，就会处于 SYN_RCVD 状态，此时**双方还没有完全建立其连接，**服务器会把此种状态下请求连接放在一个队列里，我们把这种队列称之为**半连接队列**。

当然还有一个全连接队列，就是已经完成三次握手，建立起连接的就会放在全连接队列中。如果队列满了就有可能会出现丢包现象。

#### **1.3 ISN(Initial Sequence Number)是固定的吗？**

当一端为建立连接而发送它的SYN时，它为连接选择一个初始序号。**ISN随时间而变化**，因此每个连接都将具有不同的ISN。ISN可以看作是一个32比特的计数器**，每4ms加1** 。这样选择序号的目的在于防止在网络中被延迟的分组在以后又被传送，而导致某个连接的一方对它做错误的解释。

三次握手的其中一个重要功能是客户端和服务端交换 ISN(Initial Sequence Number)，以便让对方知道接下来接收数据的时候如何按序列号组装数据。如果 **ISN 是固定的，攻击者很容易猜出后续的确认号，因此 ISN 是动态生成的。**

#### **1.4 三次握手过程中可以携带数据吗？**

其实**第三次握手的时候，是可以携带数据的。但是，第一次、第二次握手不可以携带数据**

为什么这样呢?大家可以想一个问题，假如第一次握手可以携带数据的话，如果有人要恶意攻击服务器，那他每次都在第一次握手中的 SYN 报文中放入大量的数据。因为攻击者根本就不理服务器的接收、发送能力是否正常，然后疯狂着重复发 SYN 报文的话，这会让服务器花费很多时间、内存空间来接收这些报文。

也就是说，第一次握手不可以放数据，其中一个简单的原因就是会**让服务器更加容易受到攻击了**。而对于第三次的话，此时客户端已经处于 ESTABLISHED 状态。对于客户端来说，他已经建立起连接了，并且也已经知道服务器的接收、发送能力是正常的了，所以能携带数据也没啥毛病。

#### **1.5 SYN攻击是什么？**

服务器端的资源分配是在二次握手时分配的，而客户端的资源是在完成三次握手时分配的，所以服务器容易受到SYN洪泛攻击。SYN攻击就是**Client在短时间内伪造大量不存在的IP地址，并向Server不断地发送SYN包，Server则回复确认包，并等待Client确认，由于源地址不存在，因此Server需要不断重发直至超时，这些伪造的SYN包将长时间占用未连接队列，导致正常的SYN请求因为队列满而被丢弃，从而引起网络拥塞甚至系统瘫痪**。SYN 攻击是一种典型的 DoS/DDoS 攻击。

检测 SYN 攻击非常的方便，当你在服务器上看到大量的半连接状态时，特别是源IP地址是随机的，基本上可以断定这是一次SYN攻击。在 Linux/Unix 上可以使用系统自带的 netstats 命令来检测 SYN 攻击。

```java
netstat -n -p TCP | grep SYN_RECV
```

常见的防御 SYN 攻击的方法有如下几种：

- 缩短超时（SYN Timeout）时间
- 增加最大半连接数
- 过滤网关防护
- SYN cookies技术



### 4、四次挥手

第一次： 当主机A完成数据传输后,将**控制位FIN置1**，提出停止TCP连接的请求 ；

第二次： 主机B收到FIN后对其作出响应，确认这一方向上的TCP连接将关闭,**将ACK置1；**

第三次： 由B 端再提出**反方向的关闭请求,将FIN置1** ；

第四次： 主机A对主机B的请求进行确认，**将ACK置1**，双方向的关闭结束.。

1、**ACK** 是TCP报头的控制位之一，对**数据进行确认**。确认由目的端发出， 用它来告诉发送端这个序列号之前的数据段都收到了。 比如确认号为X，则表示前X-1个数据段都收到了，只有当**ACK=1时,确认号才有效**，当ACK=0时，确认号无效，这时会要求重传数据，保证数据的完整性。

2、**SYN** 同步序列号，**TCP建立连接时将这个位置1**。

3、**FIN** 发送端完成发送任务位，当TCP完成数据传输**需要断开时,，提出断开连接的一方将这位置1。**

<img src="D:\dailySoftWare\typora\md\img\v2-c7d4b5aca66560365593f57385ce9fa9_r.jpg" alt="v2-c7d4b5aca66560365593f57385ce9fa9_r" style="zoom:50%;" />

##### **2.1 挥手为什么需要四次？**

因为当服务端收到客户端的SYN连接请求报文后，可以直接发送SYN+ACK报文。其中ACK报文是用来应答的，SYN报文是用来同步的。但是关闭连接时，当**服务端收到FIN报文时，很可能并不会立即关闭SOCKET，所以只能先回复一个ACK报文，告诉客户端，“你发的FIN报文我收到了”。只有等到我服务端所有的报文都发送完了，我才能发送FIN报文，因此不能一起发送**。故需要四次挥手。

##### **2.2 2MSL等待状态**

**TIME_WAIT状态也成为2MSL等待状态**。每个具体TCP实现必须选择一个报文段最大生存时间MSL（Maximum Segment Lifetime），它是**任何报文段被丢弃前在网络内的最长时间**。这个时间是有限的，因为TCP报文段以IP数据报在网络内传输，而IP数据报则有限制其生存时间的TTL字段。

对一个具体实现所给定的MSL值，处理的原则是：当TCP执行一个主动关闭，并发回最后一个ACK，**该连接必须在TIME_WAIT状态停留的时间为2倍的MSL**。这样可让TCP再次发送最后的ACK以防这个ACK丢失（另一端超时并重发最后的FIN）。

这种2MSL等待的另一个结果是这个TCP连接在2MSL等待期间，定义这个连接的插口（**客户的IP地址和端口号，服务器的IP地址和端口号）不能再被使用。这个连接只能在2MSL结束后才能再被使用。**

##### **2.3 四次挥手释放连接时，等待2MSL的意义?**

MSL是Maximum Segment Lifetime的英文缩写，可译为“最长报文段寿命”，它是任何报文在网络上存在的最长时间，超过这个时间报文将被丢弃。

为了保证客户端发送的最后一个ACK报文段能够到达服务器。因为这个ACK有可能丢失，从而导致处在LAST-ACK状态的服务器收不到对FIN-ACK的确认报文。服务器会超时重传这个FIN-ACK，接着客户端再重传一次确认，重新启动时间等待计时器。最后客户端和服务器都能正常的关闭。假设客户端不等待2MSL，而是在发送完ACK之后直接释放关闭，一但这个**ACK丢失的话，服务器就无法正常的进入关闭连接状态**。

两个理由：

- **保证客户端发送的最后一个ACK报文段能够到达服务端。**

这个ACK报文段有可能丢失，使得处于LAST-ACK状态的B收不到对已发送的FIN+ACK报文段的确认，服务端超时重传FIN+ACK报文段，而客户端能在2MSL时间内收到这个重传的FIN+ACK报文段，接着客户端重传一次确认，重新启动2MSL计时器，最后客户端和服务端都进入到CLOSED状态，若客户端在TIME-WAIT状态不等待一段时间，而是发送完ACK报文段后立即释放连接，则无法收到服务端重传的FIN+ACK报文段，所以不会再发送一次确认报文段，则服务端无法正常进入到CLOSED状态。

- **防止“已失效的连接请求报文段”出现在本连接中。**

客户端在发送完最后一个ACK报文段后，再经过2MSL，就可以使本连接持续的时间内所产生的所有报文段都从网络中消失，使下一个新的连接中不会出现这种旧的连接请求报文段

##### **2.4 为什么TIME_WAIT状态需要经过2MSL才能返回到CLOSE状态？**

理论上，四个报文都发送完毕，就可以直接进入CLOSE状态了，但是可能网络是不可靠的，有可能最后一个ACK丢失。所以**TIME_WAIT状态就是用来重发可能丢失的ACK报文。**

### 5、NIO

Non-blocking IO（非阻塞IO）

标准的IO基于字节流和字符流进行操作的，而NIO是基于通道（Channel）和缓冲区（Buffer）进行操作，数据总是从通道读取到缓冲区中，或者从缓冲区写入到通道中。

Java NIO引入了选择器Selectors（选择器）的概念，选择器用于监听多个通道的事件（比如：连接打开，数据到达）。因此，单个的线程可以监听多个数据通道。

### 7、Buffer

1）容量（capacity）：表示Buffer最大数据容量，缓冲区容量不能为负，并且建立后不能修改。

2）限制（limit）：第一个不应该读取或者写入的数据的索引，即位于limit后的数据不可以读写。缓冲区的限制不能为负，并且不能大于其容量（capacity）。

3）位置（position）：下一个要读取或写入的数据的索引。缓冲区的位置不能为负，并且不能大于其限制（limit）。

4）标记（mark）与重置（reset）：标记是一个索引，通过Buffer中的mark()方法指定Buffer中一个特定的position，之后可以通过调用reset()方法恢复到这个position。

```java
 // 1.指定缓冲区大小1024
        ByteBuffer buf = ByteBuffer.allocate(1024);
        System.out.println("--------------------");
        System.out.println(buf.position());
        System.out.println(buf.limit());
        System.out.println(buf.capacity());
        // 2.向缓冲区存放5个数据
        buf.put("abcd1".getBytes());
        System.out.println("--------------------");
        System.out.println(buf.position());
        System.out.println(buf.limit());
        System.out.println(buf.capacity());
        // 3.开启读模式
        buf.flip();
        System.out.println("----------开启读模式...----------");
        System.out.println(buf.position());
        System.out.println(buf.limit());
        System.out.println(buf.capacity());
        byte[] bytes = new byte[buf.limit()];
        buf.get(bytes);
        System.out.println(new String(bytes, 0, bytes.length));
        System.out.println("----------重复读模式...----------");
        // 4.开启重复读模式
        buf.rewind();
        System.out.println(buf.position());
        System.out.println(buf.limit());
        System.out.println(buf.capacity());
        byte[] bytes2 = new byte[buf.limit()];
        buf.get(bytes2);
        System.out.println(new String(bytes2, 0, bytes2.length));
        // 5.clean 清空缓冲区  数据依然存在,只不过数据被遗忘
        System.out.println("----------清空缓冲区...----------");
        buf.clear();
        System.out.println(buf.position());
        System.out.println(buf.limit());
        System.out.println(buf.capacity());
        System.out.println((char)buf.get());
/*
* --------------------
0
1024
1024
--------------------
5
1024
1024
----------开启读模式...----------
0
5
1024
abcd1
----------重复读模式...----------
0
5
1024
abcd1
----------清空缓冲区...----------
0
1024
1024
a
* */
```



标记（mark）与重置（reset）：标记是一个索引，通过Buffer中的mark()方法指定Buffer中一个特定的position，之后可以通过调用reset()方法恢复到这个position

```java
ByteBuffer buf = ByteBuffer.allocate(1024);
        String str = "abcd1";
        buf.put(str.getBytes());
        // 开启读取模式
        buf.flip();
        byte[] dst = new byte[buf.limit()];
        buf.get(dst, 0, 2);
        buf.mark();
        System.out.println(new String(dst, 0, 2));
        System.out.println(buf.position());
        buf.get(dst, 2, 2);
        System.out.println(new String(dst, 2, 2));
        System.out.println(buf.position());
        buf.reset();
        System.out.println("重置恢复到mark位置..");
        System.out.println(buf.position());
//    ab
//2
//    cd
//4
//    重置恢复到mark位置..
//            2
```

### 8、直接缓冲区和非直接缓冲区

非直接缓冲区：通过 allocate() 方法分配缓冲区，将缓冲区建立在 **JVM 的内存**中

直接缓冲区：通过 allocateDirect() 方法分配直接缓冲区，将缓冲区建立在**物理内存**中。可以提高效率

### 9、 Netty 

是一个基于 JAVA NIO 类库的异步通信框架，它的架构特点是：异步非阻塞、基于事件驱动、高性能、高可靠性和高可定制性。

1.分布式开源框架中dubbo、Zookeeper，RocketMQ底层rpc通讯使用就是netty。

2.游戏开发中，底层使用netty通讯

### 10、粘包和拆包

一个完整的业务可能会被TCP拆分成多个包进行发送，也有可能把多个小的包封装成一个大的数据包发送，这个就是TCP的拆包和封包问题。

### 11、序列化

序列化（serialization）就是将对象序列化为二进制形式（字节数组），一般也将序列化称为编码（Encode），主要用于网络传输、数据持久化等；

反序列化（deserialization）则是将从网络、磁盘等读取的字节数组还原成原始对象，以便后续业务的进行，一般也将反序列化称为解码（Decode），主要用于网络传输对象的解码，以便完成远程调用。

### 12、http和https

#### 1、http

##### 介绍

HTTP协议是**超文本传输协议**的缩写，英文是Hyper Text Transfer Protocol。它是从WEB服务器传输超文本标记语言(HTML)到本地浏览器的传送协议.

最初的目的是为了提供一种发布和接收HTML页面的方法。目前广泛使用的是HTTP/1.1版本。

##### 原理

HTTP是一个**基于TCP/IP通信协议来传递数据的协议**，传输的数据类型为HTML 文件,、图片文件, 查询结果等。

HTTP协议一般用于B/S架构（）。浏览器作为HTTP客户端通过URL向HTTP服务端即WEB服务器发送所有请求。

##### 特点

1. http协议支持客户端/服务端模式，也是一种请求/响应模式的协议。
2. 简单快速：客户向服务器请求服务时，只需传送请求方法和路径。请求方法常用的有GET、HEAD、POST。
3. 灵活：HTTP允许传输任意类型的数据对象。**传输的类型由Content-Type加以标记**。
4. 无连接：限制每次连接只处理一个请求。服务器处理完请求，并收到客户的应答后，即断开连接，但是却不利于客户端与服务器保持会话连接，为了弥补这种不足，产生了两项记录http状态的技术，一个叫做Cookie,一个叫做Session。
5. 无状态：无状态是指协议对于事务处理没有记忆，后续处理需要前面的信息，则必须重传。

##### URL和URI

HTTP使用统一资源标识符（Uniform Resource Identifiers, URI）来传输数据和建立连接。

- URI：Uniform Resource Identifier 统一资源**标识**符
- URL：Uniform Resource Location 统一资源**定位**符

URI 是用来**标示 一个具体的资源的**，我们可以通过 URI 知道一个资源是什么。

URL 则是用来**定位具体的资源的，**标示了一个具体的资源位置。互联网上的每个文件都有一个唯一的URL。

##### 问题

- 请求信息明文传输，容易被窃听截取。
- 数据的完整性未校验，容易被篡改
- 没有验证对方身份，存在冒充危险

#### 2、https

##### 介绍

**HTTPS 协议（HyperText Transfer Protocol over Secure Socket Layer）**：一般理解为HTTP+SSL/TLS，**通过 SSL证书来验证服务器的身份**，并为浏览器和服务器之间的通信进行加密。

**SSL（Secure Socket Layer，安全套接字层）**：1994年为 Netscape 所研发，SSL 协议位于 TCP/IP 协议与各种应用层协议之间，为数据通讯提供安全支持。

**TLS（Transport Layer Security，传输层安全）**：其前身是 SSL，它最初的几个版本（SSL 1.0、SSL 2.0、SSL 3.0）由网景公司开发，1999年从 3.1 开始被 IETF 标准化并改名，发展至今已经有 TLS 1.0、TLS 1.1、TLS 1.2 三个版本。SSL3.0和TLS1.0由于存在安全漏洞，已经很少被使用到。TLS 1.3 改动会比较大，目前还在草案阶段，目前使用最广泛的是TLS 1.1、TLS 1.2。

##### https传输流程

<img src="D:\dailySoftWare\typora\md\img\v2-a994fbf3094d737814fe01c2b919477b_r.jpg" alt="v2-a994fbf3094d737814fe01c2b919477b_r" style="zoom:50%;" />

1. 首先客户端通过URL访问服务器**建立SSL连接**。
2. 服务端收到客户端请求后，会**将网站支持的证书信息（证书中包含公钥）传送一份给客户端**。
3. 客户端的服务器开始**协商SSL连接的安全等级**，也就是信息加密的等级。
4. 客户端的浏览器根据双方同意的安全等级，**建立会话密钥，然后利用网站的公钥将会话密钥加密，并传送给网站**。
5. 服务器利用自己的**私钥解密出会话密钥**。
6. 服务器利用**会话密钥加密与客户端之间的通信**。

##### 缺点

- HTTPS协议多次握手，导致**页面的加载时间延长近50%**；
- HTTPS连接**缓存不如HTTP高效，会增加数据开销和功耗**；
- **申请SSL证书需要钱，功能越强大的证书费用越高**。
- SSL**涉及到的安全算法会消耗 CPU 资源**，对服务器资源消耗较大。

#### 3、总结

- HTTPS是HTTP协议的安全版本，HTTP协议的数据传输是明文的，是不安全的，HTTPS使用了SSL/TLS协议进行了加密处理。
- http和https使用连接方式不同，默认端口也不一样，http是80，https是443。

### 13、七层模型



## 十五、JVM

[大白话汇总](https://github.com/Snailclimb/JavaGuide/blob/master/docs/java/jvm/%5B%E5%8A%A0%E9%A4%90%5D%E5%A4%A7%E7%99%BD%E8%AF%9D%E5%B8%A6%E4%BD%A0%E8%AE%A4%E8%AF%86JVM.md)

### 1、JVM内存结构

#### 1、程序计数器 

较小的内存空间，线程私有。随着线程的创建而创建，销毁而销毁。可以看作是当前线程所执行的字节码的行号指示器。不会出现OutOfMemoryError

- 节码解释器通过改变程序计数器来依次读取指令，从而实现代码的流程控制。
- 在多线程情况下，程序计数器记录的是当前线程执行的位置，从而当线程切换回来时，就知道上次线程执行到哪了。

#### 2、虚拟机栈

描述 Java 方法运行过程的内存模型。

Java 虚拟机栈会为**每一个即将运行的 Java 方法创建一块叫做“栈帧”的区域**，用于存放该方法运行过程中的一些信息，如：

- 局部变量表
- 操作数栈
- 动态链接
- 方法出口信息
- ...

特点：

- 局部变量表随着栈帧的创建而创建，它的**大小在编译时确定**，创建时只需分配事先规定的大小即可。在方法运行过程中，局部变量表的大小不会发生改变。
- Java 虚拟机栈会出现两种异常：StackOverFlowError 和 OutOfMemoryError。
  - StackOverFlowError 若 Java 虚拟机栈的**大小不允许动态扩展，那么当线程请求栈的深度超过当前 Java 虚拟机栈的最大深度时**，抛出 StackOverFlowError 异常。
  - OutOfMemoryError 若允**许动态扩展，那么当线程请求栈时内存用完了，无法再动态扩展时，抛出 OutOfMemoryError** 异常。
- Java 虚拟机栈也**是线程私有，随着线程创建而创建，随着线程的结束而销毁。**

***<u>栈中存放一些基本类型的变量数据（int/short/long/byte/float/double/Boolean/char）和对象引用**</u>*

*<u>**数组引用变量是存放在栈内存中，数组元素是存放在堆内存中。</u>***

#### 3、本地方法栈

为 JVM 运行 Native 方法准备的空间

#### 4、堆

堆是用来存放对象的内存空间，**几乎所有的对象都存储在堆中。**

##### 对象和数组并不是都在堆上分配内存的？

逃逸分析(Escape Analysis)，可以**有效减少**Java 程序中**同步负载和内存堆分配压力**的跨函数全局数据流分析算法。分析出一个新的对象的引用的使用范围从而决定是否要将这个对象分配到堆上。

逃逸分析的基本行为就是分析对象动态作用域：**当一个对象在方法中被定义后，它可能被外部方法所引用，例如作为调用参数传递到其他地方中，称为方法逃逸。**

###### 逃逸分析优化点

一、同步省略。如果一个对象被发现只能从一个线程被访问到，那么**对于这个对象的操作可以不考虑同步**。

二、将**堆分配转化为栈分配**。如果一个对象在子程序中被分配，要使指向该对象的指针永远不会逃逸，对象可能是栈分配的候选，而不是堆分配。

三、**分离对象或标量替换**。有的对象可能不需要作为一个连续的内存结构存在也可以被访问到，那么**对象的部分（或全部）可以不存储在内存，而是存储在CPU寄存器中。**



开启逃逸（-XX:+DoEscapeAnalysis)

-XX:-DoEscapeAnalysis  关闭

jdk 1.7开始已经默认开始逃逸分析，如需关闭，需要指定`-XX:-DoEscapeAnalysis`

###### 结论

不一定，随着JIT编译器的发展，在编译期间，如果JIT经过逃逸分析，发现有些对象没有逃逸出方法，那么有可能**堆内存分配会被优化成栈内存分配**。但是这也并不是绝对的。在开启逃逸分析之后，也并不是所有User对象都没有在堆上分配。



JIT（即时编译）

当JVM发现某个方法或代码块运行特别频繁的时候，就会认为这是“热点代码”（Hot Spot Code)。然后JIT会把部分“热点代码”翻译成本地机器相关的机器码，并进行优化，然后再把翻译后的机器码缓存起来，以备下次使用。





特点：

- 线程共享，整个 Java 虚拟机只有一个堆，所有的线程都访问同一个堆。而程序计数器、Java 虚拟机栈、本地方法栈都是一个线程对应一个。
- 在虚拟机启动时创建。
- 是**垃圾回收的主要场所**。
- 进一步可分为：新生代(Eden 区 From Survior To Survivor)、老年代。

#### 5、方法区

Java 虚拟机规范中定义方法区**是堆的一个逻辑部分**。方法区存放以下信息：

- 已经被虚拟机加载的类信息
- 常量（存放在方法区的**运行时常量池中**）
- 静态变量
- 即时编译器编译后的代码

特点：

- 线程共享。 方法区是堆的一个逻辑部分，因此和堆一样，都是线程共享的。整个虚拟机中只有一个方法区。

- 永久代。 方法区中的信息一般需要长期存在，而且它又是堆的逻辑分区，**因此用堆的划分方法，把方法区称为“永久代”。**（ **方法区和永久代的关系很像 Java 中接口和类的关系，类实现了接口，而永久代就是 HotSpot 虚拟机对虚拟机规范中方法区的一种实现方式。** 也就是说，永久代是 HotSpot 的概念，方法区是 Java 虚拟机规范中的定义，是一种规范，而永久代是一种实现，一个是标准一个是实现，

  JDK1.8 hotspot移除了永久代用元空间(Metaspace)取而代之, 这时候字符串常量池还在堆, 运行时常量池还在方法区, 只不过**方法区的实现从永久代变成了元空间(Metaspace)****）

- 内存回收效率低。 方法区中的信息一般需要长期存在，回收一遍之后可能只有少量信息无效。主要回收目标是：对常量池的回收；对类型的卸载。

- Java 虚拟机规范对方法区的要求比较宽松。 和堆一样，允许固定大小，也允许动态扩展，还允许不实现垃圾回收。

**直接内存**

直接内存是除 Java 虚拟机之外的内存，但也可能被 Java 使用。

在 NIO 中引入了一种基于通道和缓冲的 IO 方式**。它可以通过调用本地方法直接分配 Java 虚拟机之外的内存，然后通过一个存储在堆中的`DirectByteBuffer`对象直接操作该内存，而无须先将外部内存中的数据复制到堆中再进行操作，从而提高了数据操作的效率。**

直接内存的大小不受 Java 虚拟机控制，但既然是内存，当内存不足时就会抛出 OutOfMemoryError 异常。

### 2、HotSpot 虚拟机对象探秘

#### 1、对象创建

1. 类加载检查

   虚拟机在解析`.class`文件时，若遇到一条 new 指令，首先它会去检查常量池中是否有这个类的符号引用，并且检查这个符号引用所代表的类是否已被加载、解析和初始化过。如果没有，那么必须先执行相应的类加载过程。

2. 分配内存

   - **指针碰撞**
     如果 Java **堆中内存绝对规整**（说明采用的是“**复制算法**”或“**标记整理法**”），空闲内存和已使用内存中间放着一个指针作为分界点指示器，那么分配内存时只需要把指针向空闲内存挪动一段与对象大小一样的距离，这种分配方式称为“**指针碰撞**”。
   - **空闲列表**
     如果 Java **堆中内存并不规整**，已使用的内存和空闲内存交错（说明采用的是**标记-清除法**，有碎片），此时没法简单进行指针碰撞， VM 必须维护一个列表，记录其中哪些内存块空闲可用。分配之时从空闲列表中找到一块足够大的内存空间划分给对象实例。这种方式称为“**空闲列表**”。

3. 初始化

   分配完内存后，为对象中的成员变量赋上初始值，设置对象头信息，调用对象的构造函数方法进行初始化。

#### 2、对象访问方式

**所有对象的存储空间都是在堆中分配的，但是这个对象的引用却是在堆栈中分配的**。也就是说在建立一个对象时两个地方都分配内存，在堆中分配的内存实际建立这个对象，而在堆栈中分配的内存只是一个指向这个堆对象的指针（引用）而已。 那么根据引用存放的地址类型的不同，对象有不同的访问方式。

##### 1、句柄访问方式

堆中需要有一块叫做“句柄池”的内存空间，句柄中包含了对象实例数据与类型数据各自的具体地址信息。

引用类型的变量存放的是该对象的句柄地址（reference）。访问对象时，**首先需要通过引用类型的变量找到该对象的句柄，然后根据句柄中对象的地址找到对象。**

##### 2、直接指针访问方式

引用类型的变量直接存放对象的地址，从而不需要句柄池，通过引用能够直接访问对象。但对象所在的内存空间需要额外的策略存储对象所属的类信息的地址。

需要说明的是，HotSpot 采用第二种方式，即直接指针方式来访问对象，只需要一次寻址操作，所以在性能上比句柄访问方式快一倍。但像上面所说，它需要**额外的策略**来存储对象在方法区中类信息的地址。

使用句柄来访问的最大好处是 reference 中存储的是稳定的句柄地址，在对象被移动时只会改变句柄中的实例数据指针，而 reference 本身不需要修改。

#### 3、对象内存布局

**对象头**、**实例数据**和**对齐填充**。

**Hotspot 虚拟机的对象头包括两部分信息**，**第一部分用于存储对象自身的运行时数据**（哈希码、GC 分代年龄、锁状态标志等等），**另一部分是类型指针**，即对象指向它的类元数据的指针，虚拟机通过这个指针来确定这个对象是那个类的实例。

**实例数据部分是对象真正存储的有效信息**，也是在程序中所定义的各种类型的字段内容。

**对齐填充部分不是必然存在的，也没有什么特别的含义，仅仅起占位作用。** 因为 Hotspot 虚拟机的自动内存管理系统要求对象起始地址必须是 8 字节的整数倍，换句话说就是对象的大小必须是 8 字节的整数倍。而对象头部分正好是 8 字节的倍数（1 倍或 2 倍），因此，当对象实例数据部分没有对齐时，就需要通过对齐填充来补全。

### 3、垃圾回收策略和算法

#### 1、判断对象是否存活

若一个对象不被任何对象或变量引用，那么它就是无效对象，需要被回收。

##### 引用计数法

在对象头维护着一个 counter 计数器，对象被引用一次则计数器 +1；若引用失效则计数器 -1。当计数器为 0 时，就认为该对象无效了。

引用计数算法的实现简单，判定效率也很高，在大部分情况下它都是一个不错的算法。但是主流的 Java 虚拟机里没有选用引用计数算法来管理内存，主要是因为它很难解决对象之间循环引用的问题。

> 举个栗子 👉 对象 objA 和 objB 都有字段 instance，令 objA.instance = objB 并且 objB.instance = objA，由于它们互相引用着对方，导致它们的引用计数都不为 0，于是引用计数算法无法通知 GC 收集器回收它们。

##### 可达性分析法

所有和 GC Roots 直接或间接关联的对象都是有效对象，和 GC Roots 没有关联的对象就是无效对象。

GC Roots 是指：

- Java 虚拟机栈（栈帧中的本地变量表）中引用的对象
- 本地方法栈中引用的对象
- 方法区中常量引用的对象
- 方法区中类静态属性引用的对象

GC Roots 并不包括堆中对象所引用的对象，这样就不会有循环引用的问题

#### 2、引用种类

##### 强引用（Strong Reference）

类似于**必不可少的生活用品**，类似 "Object obj = new Object()" 这类的引用，就是强引用，只要强引用存在，垃圾收集器永远不会回收被引用的对象。但是，如果我们**错误地保持了强引用**，比如：赋值给了 static 变量，那么对象在很长一段时间内不会被回收，会产生内存泄漏。

##### 软引用（Soft Reference）

类似于**可有可无的生活用品**，软引用是一种相对强引用弱化一些的引用，可以让对象豁免一些垃圾收集，只有当 JVM 认为内存不足时，才会去试图回收软引用指向的对象。JVM 会确保在抛出 OutOfMemoryError 之前，清理软引用指向的对象。软引用通常用来**实现内存敏感的缓存**，如果还有空闲内存，就可以暂时保留缓存，当内存不足时清理掉，这样就保证了使用缓存的同时，不会耗尽内存。

##### 弱引用（Weak Reference）

弱引用的**强度比软引用更弱**一些。当 JVM 进行垃圾回收时，**无论内存是否充足，都会回收**只被弱引用关联的对象。

##### 虚引用（Phantom Reference）

虚引用也称幽灵引用或者幻影引用，它是**最弱**的一种引用关系。一个对象是否有虚引用的存在，完全不会对其生存时间构成影响。它仅仅是提供了一种确保对象被 finalize 以后，做某些事情的机制，比如，通常用来做所谓的 Post-Mortem 清理机制**。虚引用必须和引用队列（ReferenceQueue）联合使用**

#### 3、判断废弃常量

**只要常量池中的常量不被任何变量或对象引用，那么这些常量就会被清除掉**。比如，一个字符串 "bingo" 进入了常量池，但是当前系统没有任何一个 String 对象引用常量池中的 "bingo" 常量，也没有其它地方引用这个字面量，必要的话，"bingo"常量会被清理出常量池。

#### 4、判断无用类

判定一个类是否是“无用的类”，条件较为苛刻。

- 该类的所有对象都已经被清除
- 加载该类的 ClassLoader 已经被回收
- 该类的 java.lang.Class 对象没有在任何地方被引用，无法在任何地方通过反射访问该类的方法。

> 一个类被虚拟机加载进方法区，那么在堆中就会有一个代表该类的对象：java.lang.Class。这个对象在类被加载进方法区时创建，在方法区该类被删除时清除。

#### 5、垃圾收集算法

##### 1、标记-清除算法

**标记**的过程是：遍历所有的 `GC Roots`，然后将所有 `GC Roots` 可达的对象**标记为存活的对象**。

**清除**的过程将遍历堆中所有的对象，将没有标记的对象全部清除掉。与此同时，清除那些被标记过的对象的标记，以便下次的垃圾回收。

这种方法有两个**不足**：

- 效率问题：标记和清除两个过程的效率都不高。
- 空间问题：标记清除之后会产生大量不连续的内存碎片，碎片太多可能导致以后需要分配较大对象时，无法找到足够的连续内存而不得不提前触发另一次垃圾收集动作。

##### 2、复制算法（新生代）

为了解决效率问题，“复制”收集算法出现了。它将可用内存按容量划分为大小相等的两块，每次只使用其中的一块。当这一块内存用完，需要进行垃圾收集时，就将存活者的对象复制到另一块上面，然后将第一块内存全部清除。这种算法有优有劣：

- 优点：不会有内存碎片的问题。
- 缺点：内存缩小为原来的一半，浪费空间。

为了解决空间利用率问题，可以将内存分为三块： Eden、From Survivor、To Survivor，比例是 8:1:1，每次使用 Eden 和其中一块 Survivor。回收时，将 Eden 和 Survivor 中还存活的对象一次性复制到另外一块 Survivor 空间上，最后清理掉 Eden 和刚才使用的 Survivor 空间。这样只有 10% 的内存被浪费。

但是我们无法保证每次回收都只有不多于 10% 的对象存活，当 Survivor 空间不够，需要依赖其他内存（指老年代）进行分配担保。

###### 分配担保

为对象分配内存空间时，如果 Eden+Survivor 中空闲区域无法装下该对象，会触发 MinorGC 进行垃圾收集。但如果 Minor GC 过后依然有超过 10% 的对象存活，这样存活的对象直接通过分配担保机制进入老年代，然后再将新对象存入 Eden 区。

##### 3、标记-整理算法（老年代）

**标记**：它的第一个阶段与**标记/清除算法**是一模一样的，均是遍历 `GC Roots`，然后将存活的对象标记。

**整理**：移动所有**存活的对象**，**且按照内存地址次序依次排列，然后将末端内存地址以后的内存全部回收。**因此，第二阶段才称为整理阶段。

这是一种老年代的垃圾收集算法。老年代的对象一般寿命比较长，因此每次垃圾回收会有大量对象存活，如果采用复制算法，每次需要复制大量存活的对象，效率很低。

##### 4、分代收集算法

根据对象存活周期的不同，将内存划分为几块。一般是把 Java 堆分为新生代和老年代，针对各个年代的特点采用最适当的收集算法。

- **新生代：复制算法**
- **老年代：标记-清除算法、标记-整理算法**

#### 6、垃圾收集器

##### 1、新生代垃圾收集器

###### 1、Serial 垃圾收集器（单线程）

只开启**一条** GC 线程进行垃圾回收，并且在垃圾收集过程中停止一切用户线程(Stop The World)。

一般客户端应用所需内存较小，不会创建太多对象，而且堆内存不大，因此垃圾收集器回收时间短，即使在这段时间停止一切用户线程，也不会感觉明显卡顿。因此 Serial 垃圾收集器**适合客户端**使用。

由于 Serial 收集器只使用一条 GC 线程，避免了线程切换的开销，从而简单高效。

###### 2、ParNew 垃圾收集器（多线程）

ParNew 是 Serial 的多线程版本。由多条 GC 线程并行地进行垃圾清理。但清理过程依然需要 Stop The World。

ParNew 追求“**低停顿时间**”,与 Serial 唯一区别就是使用了多线程进行垃圾收集，在多 CPU 环境下性能比 Serial 会有一定程度的提升；但**线程切换需要额外的开销**，因此在单 CPU 环境中表现不如 Serial。

###### 3、Parallel Scavenge 垃圾收集器（多线程）

Parallel Scavenge 和 ParNew 一样，都是多线程、新生代垃圾收集器。但是两者有巨大的不同点：

- Parallel Scavenge：**追求 CPU 吞吐量，能够在较短时间内完成指定任务，因此适合没有交互的后台计算**。
- ParNew：追求降低用户停顿时间，适合交互式应用。

吞吐量 = 运行用户代码时间 / (运行用户代码时间 + 垃圾收集时间)

追求高吞吐量，可以通过减少 GC 执行实际工作的时间，然而，仅仅偶尔运行 GC 意味着每当 GC 运行时将有许多工作要做，因为在此期间积累在堆中的对象数量很高。单个 GC 需要花更多的时间来完成，从而导致更高的暂停时间。而考虑到低暂停时间，最好频繁运行 GC 以便更快速完成，反过来又导致吞吐量下降。

- 通过参数 -XX:GCTimeRadio 设置垃圾回收时间占总 CPU 时间的百分比。
- 通过参数 -XX:MaxGCPauseMillis 设置垃圾处理过程最久停顿时间。
- 通过命令 -XX:+UseAdaptiveSizePolicy 开启自适应策略。我们只要设置好堆的大小和 MaxGCPauseMillis 或 GCTimeRadio，收集器会自动调整新生代的大小、Eden 和 Survivor 的比例、对象进入老年代的年龄，以最大程度上接近我们设置的 MaxGCPauseMillis 或 GCTimeRadio。

##### 2、老年代垃圾收集器

###### 1、Serial Old 垃圾收集器（单线程）

Serial Old 收集器是 Serial 的老年代版本，都是单线程收集器，只启用一条 GC 线程，都适合客户端应用。它们唯一的区别就是：**Serial Old 工作在老年代，使用“标记-整理”算法；Serial 工作在新生代，使用“复制”算法。**

###### 2、Parallel Old 垃圾收集器（多线程）

Parallel Old 收集器是 Parallel Scavenge 的老年代版本，追求 CPU 吞吐量。

###### 3、CMS 垃圾收集器

**CMS(Concurrent Mark Sweep，**并发标记清除)收集器是以获取最短回收停顿时间为目标的收集器（追求低停顿），它在垃圾收集时使得用户线程和 GC 线程并发执行，因此在垃圾收集过程中用户也不会感到明显的卡顿。

- 初始标记：Stop The World，仅使用一条初始标记线程对所有与 GC Roots 直接关联的对象进行标记。
- 并发标记：使用**多条**标记线程，与用户线程并发执行。此过程进行可达性分析，标记出所有废弃对象。速度很慢。
- 重新标记：Stop The World，使用多条标记线程并发执行，将刚才并发标记过程中新出现的废弃对象标记出来。
- 并发清除：只使用一条 GC 线程，与用户线程并发执行，清除刚才标记的对象。这个过程非常耗时。

并发标记与并发清除过程耗时最长，且可以与用户线程一起工作，因此，**总体上说**，CMS 收集器的内存回收过程是与用户线程**一起并发执行**的。

CMS 的缺点：

- 吞吐量低
- 无法处理浮动垃圾，导致频繁 Full GC
- 使用“标记-清除”算法产生碎片空间

对于产生碎片空间的问题，可以通过开启 -XX:+UseCMSCompactAtFullCollection，在每次 Full GC 完成后都会进行一次内存压缩整理，将零散在各处的对象整理到一块。设置参数 -XX:CMSFullGCsBeforeCompaction 告诉 CMS，经过了 N 次 Full GC 之后再进行一次内存整理。

##### 3、G1 通用垃圾收集器

G1 是一款面向服务端应用的垃圾收集器，**它没有新生代和老年代的概念，而是将堆划分为一块块独立的 Region（区域）。当要进行垃圾收集时，首先估计每个 Region 中垃圾的数量，每次都从垃圾回收价值最大的 Region 开始回收，因此可以获得最大的回收效率。**

从整体上看， G**1 是基于“标记-整理”算法实现的收集器，从局部（两个 Region 之间）上看是基于“复制”算法实现的**，这意味着运行期间不会产生内存空间碎片。

这里抛个问题 👇
一个对象和它内部所引用的对象可能不在同一个 Region 中，那么当垃圾回收时，是否需要扫描整个堆内存才能完整地进行一次可达性分析？

并不！每个 **Region 都有一个 Remembered Set，用于记录本区域中所有对象引用的对象所在的区域**，进行可达性分析时，只要在 GC Roots 中再加上 Remembered Set 即可防止对整个堆内存进行遍历。

如果不计算维护 Remembered Set 的操作，G1 收集器的工作过程分为以下几个步骤：

- 初始标记：Stop The World，仅使用一条初始标记线程对所有与 GC Roots 直接关联的对象进行标记。
- 并发标记：使用**一条**标记线程与用户线程并发执行。此过程进行可达性分析，速度很慢。
- 最终标记：Stop The World，使用多条标记线程并发执行。
- 筛选回收：回收废弃对象，此时也要 Stop The World，并使用多条筛选回收线程并发执行。

#### 7、内存分配和回收策略

##### 1、对象优先在 Eden 分配

大多数情况下，对象在新生代 Eden 区中分配。当 Eden 区没有足够空间进行分配时，虚拟机将发起一次 Minor GC。

👇**Minor GC** vs **Major GC**/**Full GC**：

- Minor GC：回收新生代（包括 Eden 和 Survivor 区域），因为 Java 对象大多都具备朝生夕灭的特性，所以 Minor GC 非常频繁，一般回收速度也比较快。
- Major GC / Full GC: 回收老年代，出现了 Major GC，经常会伴随至少一次的 Minor GC，但这并非绝对。Major GC 的速度一般会比 Minor GC 慢 10 倍 以上。

> 在 JVM 规范中，Major GC 和 Full GC 都没有一个正式的定义，所以有人也简单地认为 Major GC 清理老年代，而 Full GC 清理整个内存堆。

##### 2、大对象直接进入老年代

大对象是指需要大量连续内存空间的 Java 对象，如很长的字符串或数据。

一个大对象能够存入 Eden 区的概率比较小，发生分配担保的概率比较大，而分配担保需要涉及大量的复制，就会造成效率低下。

虚拟机提供了一个 -XX:PretenureSizeThreshold 参数，令大于这个设置值的对象直接在老年代分配，这样做的目的是避免在 Eden 区及两个 Survivor 区之间发生大量的内存复制。（还记得吗，新生代采用复制算法回收垃圾）

##### 3、长期存活的对象将进入老年代

JVM 给每个对象定义了一个对象年龄计数器。当新生代发生一次 Minor GC 后，存活下来的对象年龄 +1，当年龄超过一定值时，就将超过该值的所有对象转移到老年代中去。

使用 -XXMaxTenuringThreshold 设置新生代的最大年龄，只要超过该参数的新生代对象都会被转移到老年代中去。

##### 4、动态对象年龄判定

**如果当前新生代的 Survivor 中，相同年龄所有对象大小的总和大于 Survivor 空间的一半，年龄 >= 该年龄的对象就可以直接进入老年代，无须等到 MaxTenuringThreshold 中要求的年龄。**

##### 5、空间分配担保

JDK 6 Update 24 之前的规则是这样的：
在发生 Minor GC 之前，虚拟机会先检查**老年代最大可用的连续空间是否大于新生代所有对象总空间**， 如果这个条件成立，Minor GC 可以确保是安全的； 如果不成立，则虚拟机会查看 HandlePromotionFailure 值是否设置为允许担保失败， 如果是，那么会继续检查老年代最大可用的连续空间是否大于历次晋升到老年代对象的平均大小， 如果大于，将尝试进行一次 Minor GC,尽管这次 Minor GC 是有风险的； 如果小于，或者 HandlePromotionFailure 设置不允许冒险，那此时也要改为进行一次 Full GC。

JDK 6 Update 24 之后的规则变为：
**只要老年代的连续空间大于新生代对象总大小或者历次晋升的平均大小，就会进行 Minor GC，否则将进行 Full GC。**

**通过清除老年代中废弃数据来扩大老年代空闲空间，以便给新生代作担保。**

这个过程就是分配担保。

------

👇 总结一下有哪些情况可能会触发 JVM 进行 Full GC。

1. System.gc() 方法的调用
   此方法的调用是建议 JVM 进行 Full GC，注意这**只是建议而非一定**，但在很多情况下它会触发 Full GC，从而增加 Full GC 的频率。通常情况下我们只需要让虚拟机自己去管理内存即可，我们可以通过 -XX:+ DisableExplicitGC 来禁止调用 System.gc()。
2. 老年代空间不足
   老年代空间不足会触发 Full GC 操作，若进行该操作后空间依然不足，则会抛出如下错误：
   `java.lang.OutOfMemoryError: Java heap space`
3. 永久代空间不足
   JVM 规范中运行时数据区域中的方法区，在 HotSpot 虚拟机中也称为永久代（Permanet Generation），存放一些类信息、常量、静态变量等数据，当系统要加载的类、反射的类和调用的方法较多时，永久代可能会被占满，会触发 Full GC。如果经过 Full GC 仍然回收不了，那么 JVM 会抛出如下错误信息：
   `java.lang.OutOfMemoryError: PermGen space`
4. CMS GC 时出现 promotion failed 和 concurrent mode failure
   promotion failed，就是上文所说的担保失败，而 concurrent mode failure 是在执行 CMS GC 的过程中同时有对象要放入老年代，而此时老年代空间不足造成的。
5. 统计得到的 Minor GC 晋升到旧生代的平均大小大于老年代的剩余空间

#### 8、内存溢出/内存泄漏

###### **内存溢出：**

（out of memory）通俗理解就是**内存不够**，通常在运行大型软件或游戏时，软件或游戏所需要的内存远远超出了你主机内安装的内存所承受大小，就叫内存溢出。

###### **内存泄漏：**

（Memory Leak）是指程序中**己动态分配的堆内存由于某种原因程序未释放或无法释放**，造成系统内存的浪费，导致程序运行速度减慢甚至系统崩溃等严重后果

**场景**

 **1.内存中加载的**数据量过于庞大，如一次从数据库取出过多数据； **

**2.集合类中有对对象的引用，使用完后未清空，使得JVM不能回收；**

3.代码中存在死循环或循环产生过多重复的对象实体； 

4.使用的第三方软件

**解决**

**1、修改JVM启动参数，直接增加内存。(-Xms，-Xmx参数一定不要忘记加。) **

**第二步，检查错误日志，查看“OutOfMemory”错误前是否有其它异常或错误。**

第三步，对代码进行走查和分析，找出可能发生内存溢出的位置。**（

 **1.检查代码中是否有死循环或递归调用。 2.检查是否有大循环重复产生新对象实体。3.检查List、MAP等集合对象是否有使用完后，未清除的问题。List、MAP等集合对象会始终存有对对象的引用，使 得这些对象不能被GC回收**）

###### 内存泄漏实战分析

[分析过程](https://blog.csdn.net/fishinhouse/article/details/80781673)

### 4、类文件结构

![68747470733a2f2f6d792d626c6f672d746f2d7573652e6f73732d636e2d6265696a696e672e616c6979756e63732e636f6d2f323031392d362f25453725423125424225453625393625383725453425424225423625453525414425393725453825384125383225](D:\dailySoftWare\typora\md\img\68747470733a2f2f6d792d626c6f672d746f2d7573652e6f73732d636e2d6265696a696e672e616c6979756e63732e636f6d2f323031392d362f25453725423125424225453625393625383725453425424225423625453525414425393725453825384125383225.png)

##### 1、Class 文件结构

Class 文件是二进制文件，它的内容具有严格的规范，文件中没有任何空格，全都是连续的 0/1。Class 文件 中的所有内容被分为两种类型：无符号数、表。

- 无符号数 无符号数表示 Class 文件中的值，这些值没有任何类型，但有不同的长度。u1、u2、u4、u8 分别代表 1/2/4/8 字节的无符号数。
- 表 由多个无符号数或者其他表作为数据项构成的复合数据类型。

Class 文件具体由以下几个构成:

- 魔数
- 版本信息
- 常量池
- 访问标志
- 类索引、父类索引、接口索引集合
- 字段表集合
- 方法表集合
- 属性表集合

##### 2、魔数

Class 文件的头 4 个字节称为魔数，用来表示这个 Class 文件的类型。

Class 文件的魔数是用 16 进制表示的“CAFE BABE”，是不是很具有浪漫色彩？

> 魔数相当于文件后缀名，只不过后缀名容易被修改，不安全，因此在 Class 文件中标识文件类型比较合适。

##### 3、版本信息

紧接着魔数的 4 个字节是版本信息，5-6 字节表示次版本号，7-8 字节表示主版本号，它们表示当前 Class 文件中使用的是哪个版本的 JDK。

高版本的 JDK 能向下兼容以前版本的 Class 文件，但不能运行以后版本的 Class 文件，即使文件格式并未发生任何变化，虚拟机也必需拒绝执行超过其版本号的 Class 文件。

##### 4、常量池

版本信息之后就是常量池，常量池中存放两种类型的常量：

- 字面值常量

  字面值常量就是我们在程序中定义的字符串、被 final 修饰的值。

- 符号引用

  符号引用就是我们定义的各种名字：类和接口的全限定名、字段的名字和描述符、方法的名字和描述符。

###### 常量池的特点

- 常量池中常量数量不固定，因此常量池开头放置一个 u2 类型的无符号数，用来存储当前常量池的容量。
- 常量池的每一项常量都是一个表，表开始的第一位是一个 u1 类型的标志位（tag），代表当前这个常量属于哪种常量类型。

###### 常量池中常量类型

| 类型                             | tag  | 描述                   |
| -------------------------------- | ---- | ---------------------- |
| CONSTANT_utf8_info               | 1    | UTF-8 编码的字符串     |
| CONSTANT_Integer_info            | 3    | 整型字面量             |
| CONSTANT_Float_info              | 4    | 浮点型字面量           |
| CONSTANT_Long_info               | 5    | 长整型字面量           |
| CONSTANT_Double_info             | 6    | 双精度浮点型字面量     |
| CONSTANT_Class_info              | 7    | 类或接口的符号引用     |
| CONSTANT_String_info             | 8    | 字符串类型字面量       |
| CONSTANT_Fieldref_info           | 9    | 字段的符号引用         |
| CONSTANT_Methodref_info          | 10   | 类中方法的符号引用     |
| CONSTANT_InterfaceMethodref_info | 11   | 接口中方法的符号引用   |
| CONSTANT_NameAndType_info        | 12   | 字段或方法的符号引用   |
| CONSTANT_MethodHandle_info       | 15   | 表示方法句柄           |
| CONSTANT_MethodType_info         | 16   | 标识方法类型           |
| CONSTANT_InvokeDynamic_info      | 18   | 表示一个动态方法调用点 |

对于 CONSTANT_Class_info（此类型的常量代表一个类或者接口的符号引用），它的二维表结构如下：

| 类型 | 名称       | 数量 |
| ---- | ---------- | ---- |
| u1   | tag        | 1    |
| u2   | name_index | 1    |

tag 是标志位，用于区分常量类型；name_index 是一个索引值，它指向常量池中一个 CONSTANT_Utf8_info 类型常量，此常量代表这个类（或接口）的全限定名，这里 name_index 值若为 0x0002，也即是指向了常量池中的第二项常量。

CONSTANT_Utf8_info 型常量的结构如下：

| 类型 | 名称   | 数量   |
| ---- | ------ | ------ |
| u1   | tag    | 1      |
| u2   | length | 1      |
| u1   | bytes  | length |

tag 是当前常量的类型；length 表示这个字符串的长度；bytes 是这个字符串的内容（采用缩略的 UTF8 编码）

##### 5、访问标志

在常量池结束之后，紧接着的两个字节代表访问标志，这个标志用于识别一些类或者接口层次的访问信息，包括：这个 Class 是类还是接口；是否定义为 public 类型；是否被 abstract/final 修饰。

##### 6、类索引、父类索引、接口索引集合

类索引和父类索引都是一个 u2 类型的数据，而接口索引集合是一组 u2 类型的数据的集合，Class 文件中由这三项数据来确定类的继承关系。类索引用于确定这个类的全限定名，父类索引用于确定这个类的父类的全限定名。

由于 Java 不允许多重继承，所以父类索引只有一个，除了 java.lang.Object 之外，所有的 Java 类都有父类，因此除了 java.lang.Object 外，所有 Java 类的父类索引都不为 0。一个类可能实现了多个接口，因此用接口索引集合来描述。这个集合第一项为 u2 类型的数据，表示索引表的容量，接下来就是接口的名字索引。

类索引和父类索引用两个 u2 类型的索引值表示，它们各自指向一个类型为 CONSTANT_Class_info 的类描述符常量，通过该常量总的索引值可以找到定义在 CONSTANT_Utf8_info 类型的常量中的全限定名字符串。

##### 7、字段表集合

字段表集合存储本类涉及到的成员变量，包括实例变量和类变量，但不包括方法中的局部变量。

每一个字段表只表示一个成员变量，本类中的所有成员变量构成了字段表集合。字段表结构如下：

| 类型 | 名称             | 数量             | 说明                                                         |
| ---- | ---------------- | ---------------- | ------------------------------------------------------------ |
| u2   | access_flags     | 1                | 字段的访问标志，与类稍有不同                                 |
| u2   | name_index       | 1                | 字段名字的索引                                               |
| u2   | descriptor_index | 1                | 描述符，用于描述字段的数据类型。 基本数据类型用大写字母表示； 对象类型用“L 对象类型的全限定名”表示。 |
| u2   | attributes_count | 1                | 属性表集合的长度                                             |
| u2   | attributes       | attributes_count | 属性表集合，用于存放属性的额外信息，如属性的值。             |

> 字段表集合中不会出现从父类（或接口）中继承而来的字段，但有可能出现原本 Java 代码中不存在的字段，譬如在内部类中为了保持对外部类的访问性，会自动添加指向外部类实例的字段。

##### 8、方法表集合

方法表结构与属性表类似。

volatile 关键字 和 transient 关键字不能修饰方法，所以方法表的访问标志中没有 ACC_VOLATILE 和 ACC_TRANSIENT 标志。

方法表的属性表集合中有一张 Code 属性表，用于存储当前方法经编译器编译后的字节码指令。

##### 9、属性表集合

每个属性对应一张属性表，属性表的结构如下：

| 类型 | 名称                 | 数量             |
| ---- | -------------------- | ---------------- |
| u2   | attribute_name_index | 1                |
| u4   | attribute_length     | 1                |
| u1   | info                 | attribute_length |

### 5、类加载过程

一个类的完整生命周期如下：

![TIM截图20201127101903](D:\dailySoftWare\typora\md\img\TIM截图20201127101903.png)

#### 1、加载

类加载过程的第一步，主要完成下面3件事情：

1. 通过全类名获取定义此类的二进制字节流
2. **将字节流所代表的静态存储结构转换为方法区的运行时数据结构**
3. **在内存中生成一个代表该类的 Class 对象,作为方法区这些数据的访问入口**

虚拟机规范多上面这3点并不具体，因此是非常灵活的。比如："通过全类名获取定义此类的二进制字节流" 并没有指明具体从哪里获取、怎样获取。比如：比较常见的就是从 ZIP 包中读取（日后出现的JAR、EAR、WAR格式的基础）、其他文件生成（典型应用就是JSP）等等。

**一个非数组类的加载阶段（加载阶段获取类的二进制字节流的动作）是可控性最强的阶段，这一步我们可以去完成还可以自定义类加载器去控制字节流的获取方式（重写一个类加载器的 `loadClass()` 方法）。数组类型不通过类加载器创建，它由 Java 虚拟机直接创建。**

类加载器、双亲委派模型也是非常重要的知识点，这部分内容会在后面的文章中单独介绍到。

加载阶段和连接阶段的部分内容是交叉进行的，加载阶段尚未结束，连接阶段可能就已经开始了。

#### 2、验证

**验证阶段确保 Class 文件的字节流中包含的信息符合当前虚拟机的要求，并且不会危害虚拟机自身的安全。**

![TIM截图20201127102018](D:\dailySoftWare\typora\md\img\TIM截图20201127102018.png)

#### 3、准备

**准备阶段是正式为类变量分配内存并设置类变量初始值的阶段****，这些内存都将在方法区中分配。**对于该阶段有以下几点需要注意：

1. 这时候进行内存分配的仅包括类变量（static），而不包括实例变量，实例变量会在对象实例化时随着对象一块分配在 Java 堆中。
2. 这里所设置的初始值"通常情况"下是数据类型默认的零值（如0、0L、null、false等），比如我们定义了`public static int value=111` ，那么 value 变量在准备阶段的初始值就是 0 而不是111（初始化阶段才会赋值）。特殊情况：比如给 value 变量加上了 fianl 关键字`public static final int value=111` ，那么准备阶段 value 的值就被赋值为 111。

**基本数据类型的零值：**

![TIM截图20201127102046](D:\dailySoftWare\typora\md\img\TIM截图20201127102046.png)

#### 4、解析

**解析阶段是虚拟机将常量池内的符号引用替换为直接引用的过程。**解析动作主要针对类或接口、字段、类方法、接口方法、方法类型、方法句柄和调用限定符7类符号引用进行。**（符号引用比如我现在import java.util.ArrayList这就算符号引用，直接引用就是指针或者对象地址，注意引用对象一定是在内存进行）**

符号引用就是一组符号来描述目标，可以是任何字面量。**直接引用**就是直接指向目标的指针、相对偏移量或一个间接定位到目标的句柄。在程序实际运行时，只有符号引用是不够的，举个例子：在程序执行方法时，系统需要明确知道这个方法所在的位置。Java 虚拟机为每个类都准备了一张方法表来存放类中所有的方法。当需要调用一个类的方法的时候，只要知道这个方法在方发表中的偏移量就可以直接调用该方法了。通过解析操作符号引用就可以直接转变为目标方法在类中方法表的位置，从而使得方法可以被调用。

综上，解析阶段是虚拟机将常量池内的符号引用替换为直接引用的过程，也就是得到类或者字段、方法在内存中的指针或者偏移量。

#### 5、初始化

初始化是类加载的最后一步，也是真正执行类中定义的 Java 程序代码(字节码)，初始化阶段是执行初始化方法 `<clinit> ()`方法的过程。

对于`<clinit>（）` 方法的调用，虚拟机会自己确保其在多线程环境中的安全性。因为 `<clinit>（）` 方法是带锁线程安全，所以在多线程环境下进行类初始化的话可能会引起死锁，并且这种死锁很难被发现。

对于初始化阶段，虚拟机严格规范了有且只有5种情况下，必须对类进行初始化(只有主动去使用类才会初始化类)：

1. 当遇到 new 、 getstatic、putstatic或invokestatic 这4条直接码指令时，比如 new 一个类，读取一个静态字段(未被 final 修饰)、或调用一个类的静态方法时。
   - 当jvm执行new指令时会初始化类。即当程序创建一个类的实例对象。
   - 当jvm执行getstatic指令时会初始化类。即程序访问类的静态变量(不是静态常量，常量会被加载到运行时常量池)。
   - 当jvm执行putstatic指令时会初始化类。即程序给类的静态变量赋值。
   - 当jvm执行invokestatic指令时会初始化类。即程序调用类的静态方法。
2. 使用 `java.lang.reflect` 包的方法对类进行反射调用时如Class.forname("..."),newInstance()等等。 ，如果类没初始化，需要触发其初始化。
3. 初始化一个类，如果其父类还未初始化，则先触发该父类的初始化。
4. 当虚拟机启动时，用户需要定义一个要执行的主类 (包含 main 方法的那个类)，虚拟机会先初始化这个类。
5. MethodHandle和VarHandle可以看作是轻量级的反射调用机制，而要想使用这2个调用， 就必须先使用findStaticVarHandle来初始化要调用的类。
6. 当一个接口中定义了JDK8新加入的默认方法（被default关键字修饰的接口方法）时，如果有这个接口的实现类发生了初始化，那该接口要在其之前被初始化。

#### 6、卸载

**卸载类即该类的Class对象被GC。**

卸载类需要满足3个要求:

1. 该类的所有的实例对象都已被GC，也就是说堆不存在该类的实例对象。
2. 该类没有在其他任何地方被引用
3. 该类的类加载器的实例已被GC

所以，在JVM生命周期类，由jvm自带的类加载器加载的类是不会被卸载的。但是由我们自定义的类加载器加载的类是可能被卸载的。

只要想通一点就好了，jdk自带的BootstrapClassLoader,PlatformClassLoader,AppClassLoader负责加载jdk提供的类，所以它们(类加载器的实例)肯定不会被回收。而我们自定义的类加载器的实例是可以被回收的，所以使用我们自定义加载器加载的类是可以被卸载掉的。

### 6、类加载器

- **启动类加载器（Bootstrap ClassLoader）**： 负责将存放在 `<JAVA_HOME>\lib` 目录中的，并且能被虚拟机识别的（仅按照文件名识别，如 rt.jar，名字不符合的类库即使放在 lib 目录中也不会被加载）类库加载到虚拟机内存中。
- **扩展类加载器（Extension ClassLoader**）： 负责加载 `<JAVA_HOME>\lib\ext` 目录中的所有类库，开发者可以直接使用扩展类加载器。
- **应用程序类加载器（Application ClassLoader）**： 由于这个类加载器是 ClassLoader 中的 getSystemClassLoader() 方法的返回值，所以一般也称它为“系统类加载器”。**它负责加载用户类路径（classpath）上所指定的类库，**开发者可以直接使用这个类加载器，如果应用程序中没有自定义过自己的类加载器，一般情况下这个就是程序中默认的类加载器。

### 7、双亲委派模型

#### 1、什么是双亲委派模型

**双亲委派模型是描述类加载器之间的层次关系**。它要求除了顶层的启动类加载器外，其余的类加载器都应当有自己的父类加载器。（父子关系一般不会以继承的关系实现，而是以组合关系来复用父加载器的代码）

#### 2、工作过程

如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是**把这个请求委派给父类加载器去完成**，每一个层次的类加载器都是如此，因此所有的加载请求最终都应该传送到顶层的启动类加载器中，**只有当父加载器反馈自己无法完成这个加载请求（找不到所需的类）时，子加载器才会尝试自己去加载。**

在 java.lang.ClassLoader 中的 loadClass() 方法中实现该过程。

#### 3、为什么使用双亲委派模型

像 java.lang.Object 这些存放在 rt.jar 中的类，无论使用哪个类加载器加载，最终都会委派给最顶端的启动类加载器加载，从而使得不同加载器加载的 Object 类都是同一个。

相反，如果没有使用双亲委派模型，**由各个类加载器自行去加载的话，如果用户自己编写了一个称为 java.lang.Object 的类，并放在 classpath 下，那么系统将会出现多个不同的 Object 类，Java 类型体系中最基础的行为也就无法保证。**

#### 4、如何打破双亲委派模型





### 8、jvm性能调优

[参考](https://blog.csdn.net/weixin_42447959/article/details/81637909)

#### 1、目标

使用较小的内存占用来获得较高的吞吐量或者较低的延迟。

- 内存占用：程序正常运行需要的内存大小。
- 延迟：由于垃圾收集而引起的程序停顿时间。
- 吞吐量：用户程序运行时间占用户程序和垃圾收集占用总时间的比值。

#### 2、问题

cpu load过高、请求延迟、tps降低等，甚至出现内存泄漏（每次垃圾收集使用的时间越来越长，垃圾收集频率越来越高，每次垃圾收集清理掉的垃圾数据越来越少）、内存溢出导致系统崩溃

#### 3、调优工具

##### 1、日志数据等分析

参考的数据有**系统运行日志**、**堆栈错误信息**、**gc日志**、**线程快照**、**堆转储快照**等。

###### ①系统运行日志：

系统运行日志就是在程序代码中打印出的日志，描述了代码级别的系统运行轨迹（执行的方法、入参、返回值等），一般系统出现问题，系统运行日志是首先要查看的日志。

###### ②堆栈错误信息：

当系统出现异常后，可以根据堆栈信息初步定位问题所在，比如根据“java.lang.OutOfMemoryError: Java heap space”可以判断是堆内存溢出；根据“java.lang.StackOverflowError”可以判断是栈溢出；根据“java.lang.OutOfMemoryError: PermGen space”可以判断是方法区溢出等。

###### ③GC日志：

程序启动时用 **-XX:+PrintGCDetails** 和 **-Xloggc:/data/jvm/gc.log** 可以在程序运行时把gc的详细过程记录下来，或者直接配置“**-verbose:gc**”参数把gc日志打印到控制台，通过记录的gc日志可以分析每块内存区域gc的频率、时间等，从而发现问题，进行有针对性的优化。

 ```shell
2018-08-02T14:39:11.560-0800: 10.171: [GC [PSYoungGen: 30128K->4091K(30208K)] 51092K->50790K(98816K), 0.0140970 secs] [Times: user=0.02 sys=0.03, real=0.01 secs] 
2018-08-02T14:39:11.574-0800: 10.185: [Full GC [PSYoungGen: 4091K->0K(30208K)] [ParOldGen: 46698K->50669K(68608K)] 50790K->50669K(98816K) [PSPermGen: 2635K->2634K(21504K)], 0.0160030 secs] [Times: user=0.03 sys=0.00, real=0.02 secs] 
2018-08-02T14:39:14.045-0800: 12.656: [GC [PSYoungGen: 14097K->4064K(30208K)] 64766K->64536K(98816K), 0.0117690 secs] [Times: user=0.02 sys=0.01, real=0.01 secs] 
2018-08-02T14:39:14.057-0800: 12.668: [Full GC [PSYoungGen: 4064K->0K(30208K)] [ParOldGen: 60471K->401K(68608K)] 64536K->401K(98816K) [PSPermGen: 2634K->2634K(21504K)], 0.0102020 secs] [Times: user=0.01 sys=0.00, real=0.01 secs]

 ```

“2018-08-02T14:39:11.560-0800”是精确到了毫秒级别的UTC 通用标准时间格式，配置了“-XX:+PrintGCDateStamps”这个参数可以跟随gc日志打印出这种时间戳.

“10.171”是从JVM启动到发生gc经过的秒数。

第一行日志正文开头的“[GC”说明这次GC没有发生Stop-The-World（用户线程停顿），第二行日志正文开头的“[Full GC”说明这次GC发生了Stop-The-World，所以说，[GC和[Full GC跟新生代和老年代没关系，和垃圾收集器的类型有关系，如果直接调用System.gc()，将显示[Full GC(System)。

接下来的“[PSYoungGen”、“[ParOldGen”表示GC发生的区域，具体显示什么名字也跟垃圾收集器有关，比如这里的“[PSYoungGen”表示Parallel Scavenge收集器，“[ParOldGen”表示Serial Old收集器，此外，Serial收集器显示“[DefNew”，ParNew收集器显示“[ParNew”等。

再往后的“30128K->4091K(30208K)”表示进行了这次gc后，该区域的内存使用空间由30128K减小到4091K，总内存大小为30208K。

每个区域gc描述后面的“51092K->50790K(98816K), 0.0140970 secs”进行了这次垃圾收集后，整个堆内存的内存使用空间由51092K减小到50790K，整个堆内存总空间为98816K，gc耗时0.0140970秒。

###### ④线程快照：

顾名思义，根据线程快照可以看到线程在某一时刻的状态，<u>当系统中可能存在请求超时、死循环、死锁等情况是，可以根据线程快照来进一步确定问题</u>。通过执行虚拟机自带的“**jstack pid**”命令，可以dump出当前进程中线程的快照信息，更详细的使用和分析网上有很多例，这篇文章写到这里已经很长了就不过多叙述了，贴一篇博客供参考：http://www.cnblogs.com/kongzhongqijing/articles/3630264.html

###### ⑤堆转储快照：

程序启动时可以使用 “**-XX:+HeapDumpOnOutOfMemory**” 和 “**-XX:HeapDumpPath=/data/jvm/dumpfile.hprof**”，当程序发生内存溢出时，把当时的内存快照以文件形式进行转储（也可以直接用**jma**p命令转储程序运行时任意时刻的内存快照），事后对当时的内存使用情况进行分析。

##### 2、调优工具

###### 1、jps(jvm process status)

查看虚拟机启动的所有**进程、执行主类的全名、JVM启动参数**，比如当执行了JPSTest类中的main方法后（**main方法持续执行**），执行 **jps -l**可看到下面的JPSTest类的pid为31354，加上**-v参数**还可以看到JVM启动参数

```powershell
3265 
32914 sun.tools.jps.Jps
31353 org.jetbrains.jps.cmdline.Launcher
31354 com.danny.test.code.jvm.JPSTest
380
```

###### 2、jstat（JVM Statistics Monitoring Tool）

**监视虚拟机信息** 

jstat -gc pid 500 10 ：**每500毫秒**打印一次Java堆状况（各个区的**容量、使用容量、gc时间**等信息），**打印10次**

```shell
[admin@bak-RiskQuota ~]$ jstat -gc 106768  500 10
 S0C    S1C    S0U    S1U      EC       EU        OC         OU       MC     MU    CCSC   CCSU   YGC     YGCT    FGC    FGCT     GCT   
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078
14848.0 32256.0 14482.8  0.0   1138176.0 257035.2  374272.0   270407.8  141720.0 138523.5 17328.0 16674.8    184    4.585   4      1.493    6.078

```

###### 3、jmap（Memory Map for Java）

**查看堆内存信息** 

执行**jmap -histo pid**可以打印出当前堆中所有每个类的实例数量和内存占用，如下，class name是每个类的类名（[B是byte类型，[C是char类型，[I是int类型），bytes是这个类的所有示例占用内存大小，instances是这个类的实例数量

```shell

num     #instances         #bytes  class name
----------------------------------------------
  1:          2291       29274080  [B
  2:         15252        1961040  <methodKlass>
  3:         15252        1871400  <constMethodKlass>
  4:         18038         721520  java.util.TreeMap$Entry
  5:          6182         530088  [C
  6:         11391         273384  java.lang.Long
  7:          5576         267648  java.util.TreeMap
  8:            50         155872  [I
  9:          6124         146976  java.lang.String
 10:          3330         133200  java.util.LinkedHashMap$Entry
 11:          5544         133056  javax.management.openmbean.CompositeDataSupport
```

 **jmap -dump:format=b,file=/data/jvm/dumpfile_jmap.hprof 3361** 可以把当前堆内存的快照转储到dumpfile_jmap.hprof文件中，然后可以对内存快照进行分析   **idea 使用jprofier 导入分析**  eclipse 用mat分析 或者 jvisualvm 也可以

###### 4、jconsole、jvisualvm

jconsole、jvisualvm分析内存信息(各个区如Eden、Survivor、Old等内存变化情况)，如果查看的是远程服务器的JVM，程序启动需要加上如下参数

```shell
"-Dcom.sun.management.jmxremote=true" 
"-Djava.rmi.server.hostname=12.34.56.78" 
"-Dcom.sun.management.jmxremote.port=18181" 
"-Dcom.sun.management.jmxremote.authenticate=false" 
"-Dcom.sun.management.jmxremote.ssl=false"
```

可以观测堆内存使用量、线程数、类加载数和CPU占用率

###### 5、分析堆转储快照

jhat（JVM Heap Analysis Tool） 命令来分析内存快照，它的本质实际上内嵌了一个微型的服务器

 jhat -port 9810 -J-Xmx4G /data/jvm/dumpfile_jmap.hprof 表示以9810端口启动 jhat 内嵌的服务器

```shell
Reading from /Users/dannyhoo/data/jvm/dumpfile_jmap.hprof...
Dump file created Fri Aug 03 15:48:27 CST 2018
Snapshot read, resolving...
Resolving 276472 objects...
Chasing references, expect 55 dots.......................................................
Eliminating duplicate references.......................................................
Snapshot resolved.
Started HTTP server on port 9810
Server is ready.
```

http://127.0.0.1:9810/ 可以看到对快照中的每个类进行分析的结果

##### 3、调优经验

- -Xms和-Xmx的值设置成相等，堆大小默认为-Xms指定的大小，默认空闲堆内存小于40%时，JVM会扩大堆到-Xmx指定的大小；空闲堆内存大于70%时，JVM会减小堆到-Xms指定的大小。如果在Full GC后满足不了内存需求会动态调整，这个阶段比较耗费资源。
- **新生代尽量设置大一些**，让对象在新生代多存活一段时间，每次Minor GC 都要尽可能多的收集垃圾对象，防止或延迟对象进入老年代的机会，以减少应用程序发生Full GC的频率。
- **老年代如果使用CMS收集器，新生代可以不用太**大，因为CMS的并行收集速度也很快，收集过程比较耗时的并发标记和并发清除阶段都可以与用户线程并发执行。
- 方法区大小的设置，1.6之前的需要考虑系统运行时动态增加的常量、静态变量等，1.7只要差不多能装下启动时和后期动态加载的类信息就行。
- **避免创建过大的对象及数组**：过大的对象或数组在新生代没有足够空间容纳时会直接进入老年代，如果是短命的大对象，会提前出发Full GC。
- **避免同时加载大量数据**，如一次从数据库中取出大量数据，或者一次从Excel中读取大量记录，可以分批读取，用完尽快清空引用。
- 当集合中有对象的引用，这些**对象使用完之后要尽快把集合中的引用清空**，这些无用对象尽快回收避免进入老年代。
- 可以在合适的场景（如实现缓存）采用软引用、弱引用，比如用软引用来为ObjectA分配实例：SoftReference objectA=new SoftReference(); 在发生内存溢出前，会将objectA列入回收范围进行二次回收，如果这次回收还没有足够内存，才会抛出内存溢出的异常。 
  避免产生死循环，产生死循环后，循环体内可能重复产生大量实例，导致内存空间被迅速占满。
- 尽量**避免长时间等待外部资源（数据库、网络、设备资源等）的情况**，缩小对象的生命周期，避免进入老年代，如果不能及时返回结果可以适当采用异步处理的方式等。

##### 4、jvm参数参考

| 参数                    | 说明                                                         | 实例                     |
| :---------------------- | :----------------------------------------------------------- | :----------------------- |
| -Xms                    | 初始堆大小，默认物理内存的1/64                               | -Xms512M                 |
| -Xmx                    | 最大堆大小，默认物理内存的1/4                                | -Xms2G                   |
| -Xmn                    | 新生代内存大小，官方推荐为整个堆的3/8                        | -Xmn512M                 |
| -Xss                    | 线程堆栈大小，jdk1.5及之后默认1M，之前默认256k               | -Xss512k                 |
| -XX:NewRatio=n          | 设置新生代和年老代的比值。如:为3，表示年轻代与年老代比值为1：3，年轻代占整个年轻代年老代和的1/4 | -XX:NewRatio=3           |
| -XX:SurvivorRatio=n     | 年轻代中Eden区与两个Survivor区的比值。注意Survivor区有两个。如:8，表示Eden：Survivor=8:1:1，一个Survivor区占整个年轻代的1/8 | -XX:SurvivorRatio=8      |
| -XX:PermSize=n          | 永久代初始值，默认为物理内存的1/64                           | -XX:PermSize=128M        |
| -XX:MaxPermSize=n       | 永久代最大值，默认为物理内存的1/4                            | -XX:MaxPermSize=256M     |
| -verbose:class          | 在控制台打印类加载信息                                       |                          |
| -verbose:gc             | 在控制台打印垃圾回收日志                                     |                          |
| -XX:+PrintGC            | 打印GC日志，内容简单                                         |                          |
| -XX:+PrintGCDetails     | 打印GC日志，内容详细                                         |                          |
| -XX:+PrintGCDateStamps  | 在GC日志中添加时间戳                                         |                          |
| -Xloggc:filename        | 指定gc日志路径                                               | -Xloggc:/data/jvm/gc.log |
| -XX:+UseSerialGC        | 年轻代设置串行收集器Serial                                   |                          |
| -XX:+UseParallelGC      | 年轻代设置并行收集器Parallel Scavenge                        |                          |
| -XX:ParallelGCThreads=n | 设置Parallel Scavenge收集时使用的CPU数。并行收集线程数。     | -XX:ParallelGCThreads=4  |
| -XX:MaxGCPauseMillis=n  | 设置Parallel Scavenge回收的最大时间(毫秒)                    | -XX:MaxGCPauseMillis=100 |
| -XX:GCTimeRatio=n       | 设置Parallel Scavenge垃圾回收时间占程序运行时间的百分比。公式为1/(1+n) | -XX:GCTimeRatio=19       |
| -XX:+UseParallelOldGC   | 设置老年代为并行收集器ParallelOld收集器                      |                          |
| -XX:+UseConcMarkSweepGC | 设置老年代并发收集器CMS                                      |                          |
| -XX:+CMSIncrementalMode | 设置CMS收集器为增量模式，适用于单CPU情况。                   |                          |

##### 5、jvm调优案例

JVM服务问题排查 https://blog.csdn.net/jacin1/article/details/44837595

次让人难以忘怀的排查频繁Full GC过程 http://caogen81.iteye.com/blog/1513345

线上FullGC频繁的排查 https://blog.csdn.net/wilsonpeng3/article/details/70064336/

【JVM】线上应用故障排查 https://www.cnblogs.com/Dhouse/p/7839810.html

一次JVM中FullGC问题排查过程 http://iamzhongyong.iteye.com/blog/1830265

JVM内存溢出导致的CPU过高问题排查案例 https://blog.csdn.net/nielinqi520/article/details/78455614

一个java内存泄漏的排查案例 https://blog.csdn.net/aasgis6u/article/details/54928744

***linux排查java程序CPU占用过高问题。***

```shell
top # 查看系统资源占用情况   shift + h 会排序 可以看到高占用的进程  ->获取进程ID
```

```shell
ps -mp pid -o THREAD,tid,time # 显示 该进程的线程信息 tid线程ID time线程已运行时间  ->获取具体cpu占用高的线程ID -m显示所有线程 -p pid 进程使用cpu的时间 -o自定义显示格式
```

```shell
printf “%x\n” number # 转换线程ID 为16进制  方便在 jstack中查找  ->获取16进制  如3ec7
```

```shell
jstack -pid|grep 3ec7 # 根据 进程ID 以及线程ID的16进制数据   查看进程堆栈信息，定位到具体执行类以及方法
```



## 十六、分布式session

分布式session是解决分布式环境session不一致问题的

### 1、基于nginx的ip_hash

 nginx中的ip_hash技术能够将某个ip的请求固定到同一台后端应用服务器，这样一来这个ip下的某个客户端和某个后端就能建立起稳固的session，ip_hash是在upstream配置中定义的：

```
upstream backend {
server 127.0.0.1:8001;
server 127.0.0.1:8002;
server 127.0.0.1:8003;
ip_hash;
}
```

​    优点：ip_hash算法可以把一个ip映射到一台服务器上，这样可以解决session同步的问题。这样每个访客固定访问一个后端服务器，可以解决session的问题；

​    缺点：使用ip_hash进行session共享，它的原理是为每个访问者提供一个固定的访问ip，让用户只能在当前访问的服务器上进行操作，保持了session同步的，但是也造成了负载不均衡的问题，**如果当前用户访问的服务器挂了的话，那就会出现问题了，session会失效，另外ip_hash需要重新计算**；

### 2、tomcat + redis

`Tomcat RedisSessionManager` 的东西，让所有我们部署的 tomcat 都将 session 数据存储到 redis 即可

```xml
<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />

<Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager"
         host="{redis.host}"
         port="{redis.port}"
         database="{redis.dbnum}"
         maxInactiveInterval="60"/>
```

```xml
<Valve className="com.orangefunction.tomcat.redissessions.RedisSessionHandlerValve" />
<Manager className="com.orangefunction.tomcat.redissessions.RedisSessionManager"
	 sentinelMaster="mymaster"
	 sentinels="<sentinel1-ip>:26379,<sentinel2-ip>:26379,<sentinel3-ip>:26379"
	 maxInactiveInterval="60"/>
```

与 tomcat 容器重耦合，**依赖于web容器**

### 3、spring session + redis

session 相关操作都会交给 spring session 来管理。接着在代码中，就用原生的 session 操作，就是直接基于 spring sesion 从 redis 中获取数据了。

总体思路是**通过一个过滤器SessionRepositoryFilter，然后重新包装request和reponse以及session。** 在SpringSession实现过程中DelegatingFilterProxy就是这个过滤器入口。

#### 1、引入依赖

```xml
<dependencies>
	<!-- ... -->

	<dependency>
		<groupId>org.springframework.session</groupId>
		<artifactId>spring-session-data-redis</artifactId>
	</dependency>
</dependencies>
```

#### 2、springboot配置

```properties
spring.session.store-type = redis ＃会话存储类型，等同于手动添加@EnableRedisHttpSession注释的配置
server.servlet.session.timeout =＃会话超时。如果未指定持续时间后缀，则使用秒。
spring.session.redis.flush-mode = on_save＃会话刷新模式。
spring.session.redis.namespace = spring：session＃用于存储会话的键的命名空间。
spring.redis.host = localhost＃Redis服务器主机。
spring.redis.password =＃Redis服务器的登录密码。
spring.redis.port = 6379＃Redis服务器端口
```

或者spring配置

```xml
<bean id="redisHttpSessionConfiguration"
     class="org.springframework.session.data.redis.config.annotation.web.http.RedisHttpSessionConfiguration">
    <property name="maxInactiveIntervalInSeconds" value="600"/>
</bean>

<bean id="jedisPoolConfig" class="redis.clients.jedis.JedisPoolConfig">
    <property name="maxTotal" value="100" />
    <property name="maxIdle" value="10" />
</bean>

<bean id="jedisConnectionFactory"
      class="org.springframework.data.redis.connection.jedis.JedisConnectionFactory" destroy-method="destroy">
    <property name="hostName" value="${redis_hostname}"/>
    <property name="port" value="${redis_port}"/>
    <property name="password" value="${redis_pwd}" />
    <property name="timeout" value="3000"/>
    <property name="usePool" value="true"/>
    <property name="poolConfig" ref="jedisPoolConfig"/>
</bean>
```

web.xml配置

```xml
<filter>
    <filter-name>springSessionRepositoryFilter</filter-name>
    <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
</filter>
<filter-mapping>
    <filter-name>springSessionRepositoryFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
```

#### 3、代码

```java
@RestController
@RequestMapping("/test")
public class TestController {

    @RequestMapping("/putIntoSession")
    public String putIntoSession(HttpServletRequest request, String username) {
        request.getSession().setAttribute("name",  "leo");
        return "ok";
    }

    @RequestMapping("/getFromSession")
    public String getFromSession(HttpServletRequest request, Model model){
        String name = request.getSession().getAttribute("name");
        return name;
    }
}
```

### 4、基于shiro的session共享

第一步：我们需要自定义SessionDAO，比如RedisSessionDAO继承AbstractSessionDAO，实现对session操作的方法，可以用redis、mongoDB等进行实现

第二步: 我们需要自定义redis缓存的RedisCacheManager存储实现类

第三步：我们需要自定义session管理器

参考：[shiro方案文章尾部](https://blog.csdn.net/qq_28089993/article/details/109093269)

## 十七、mybatis

MyBatis 是一款优秀的持久层框架，它支持自定义 SQL、存储过程以及高级映射。可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录

## 十八、认证

### OAuth

[OAuth认证方式理解](http://www.ruanyifeng.com/blog/2019/04/oauth-grant-types.html)

#### 理解

**简单说，OAuth 就是一种授权机制。数据的所有者告诉系统，同意授权第三方应用进入系统，获取这些数据。系统从而产生一个短期的进入令牌（token），用来代替密码，供第三方应用使用。**

（1）令牌是短期的，到期会自动失效，用户自己无法修改。密码一般长期有效，用户不修改，就不会发生变化。

（2）令牌可以被数据所有者撤销，会立即失效。以上例而言，屋主可以随时取消快递员的令牌。密码一般不允许被他人撤销。

（3）令牌有权限范围（scope），比如只能进小区的二号门。对于网络服务来说，只读令牌就比读写令牌更安全。密码一般是完整权限。

#### 授权方式

注意，不管哪一种授权方式，第三方应用申请令牌之前，都必须先到系统备案，说明自己的身份，然后会拿到两个身份识别码：客户端 ID（client ID）和客户端密钥（client secret）。这是为了防止令牌被滥用，没有备案过的第三方应用，是不会拿到令牌的

##### **授权码（authorization code）**

**第三方应用先申请一个授权码，然后再用该码获取令牌**

授权码通过前端传送，令牌则是储存在后端，而且所有与资源服务器的通信都在后端完成。这样的前后端分离，可以避免令牌泄漏。

##### 隐藏式（implicit）

纯前端应用。没有后端。**允许直接向前端颁发令牌。这种方式没有授权码这个中间步骤，所以称为（授权码）"隐藏式"（implicit）**

##### 密码式

**如果你高度信任某个应用，RFC 6749 也允许用户把用户名和密码，直接告诉该应用。该应用就使用你的密码，申请令牌，这种方式称为"密码式"（password）**

##### **凭证式（client credentials）**

**适用于没有前端的命令行应用，即在命令行下请求令牌**

## 十九、性能优化

### JProfiler

[激活码](https://www.cnblogs.com/yjd_hycf_space/p/7743049.html)

[IDEA安装和使用以及JRebel与JProfiler同时使用](https://blog.csdn.net/wytocsdn/article/details/79258247)

[JProfiler性能优化实践](https://segmentfault.com/a/1190000017795841)

### 埋点

[代码埋点、可视化买点、无埋点的区别](https://www.jianshu.com/p/37cbb7607ca4)

[埋点的意义](https://www.zhihu.com/question/36411025)

## 二十、VUE

### 生命周期

 **beforeCreate**(创建前)   实例初始化之后，此时的数据观察和事件机制都未形成，**不能获得DOM节点**。

**created**(创建后)  vue实例已经创建，**仍然不能获取DOM元素。**

**beforeMount**(载入前)  依然得不到具体的DOM元素，但**vue挂载的根节点已经创建**，beforeMount这个阶段是过渡性的，一般一个项目只能用到一两次。

 **mounted**(载入后)  <u>**数据和DOM都已被渲染出来。**</u>

 **beforeUpdate**(更新前) vue遵循数据驱动DOM的原则。beforeUpdate函数在数据更新后虽然没立即更新数据，但是DOM中的数据会改变，这是Vue双向数据绑定的作用。

**updated**（更新后)   DOM会和更改过的内容同步。

**beforeDestroy(**销毁前)  上一阶段Vue已经成功的通过数据驱动DOM更新，当我们不再需要vue操纵DOM时， 就要销毁Vue,也就是清除vue实例与DOM的关联，调用destroy方法可以销毁当前组件。在销毁前会触发beforeDestroy钩 子函数。

**destroyed**（销毁后) 在销毁后，会触发destroyed钩子函数。

**组件之间切换以上八种生命周期钩子将失效。取而代之的时activate和deactivated**

activate：是在被包裹组件被激活的状态下使用的生命周期钩子 

deactivated：在被包裹组件停止使用时调用

### 路由传参

#### 一、router-link路由导航

**父组件:** 使用`<router-link to = "/跳转路径/传入的参数"></router-link>`

例如：`<router-link to="/a/123">routerlink传参</router-link>`

**子组件:** this.$route.params.num接收父组件传递过来的参数

```text
mounted () {
  this.num = this.$route.params.num
}
```

**路由配置:**：`{path: '/a/:num', name: A, component: A}`

**地址栏中的显示:**：`http://localhost:8080/#/a/123`

#### 二、调用$router.push实现路由传参

**父组件:** 绑定点击事件，编写跳转代码

```text
<button @click="deliverParams(123)">push传参</button>
  methods: {
    deliverParams (id) {
      this.$router.push({
        path: `/d/${id}`
      })
    }
  }
```

**子组件:** this.$route.params.id接收父组件传递过来的参数

```text
mounted () {
  this.id = this.$route.params.id
}
```

**路由配置:**：`{path: '/d/:id', name: D, component: D}`

**地址栏中的显示:**：`http://localhost:8080/#/d/123`

#### 三、通过路由属性中的name匹配路由，再根据params传递参数

**父组件:** 匹配路由配置好的属性名

```text
<button @click="deliverByName()">params传参</button>
    deliverByName () {
      this.$router.push({
        name: 'B',
        params: {
          sometext: '一只羊出没'
        }
      })
    }
```

**子组件:**

```text
<template>
  <div id="b">
    This is page B!
    <p>传入参数：{{this.$route.params.sometext}}</p>
  </div>
</template>
```

**路由配置:** 路径后面不需要再加传入的参数，但是name必须和父组件中的name一致
`{path: '/b', name: 'B', component: B}`

**地址栏中的显示:** 可以看出地址栏**不会带**有传入的参数，且再次刷新页面后**参数会丢失**
`http://localhost:8080/#/b`

#### 四、通过query来传递参数

**父组件:**

```text
<button @click="deliverQuery()">query传参</button>
    deliverQuery () {
      this.$router.push({
        path: '/c',
        query: {
          sometext: '这是小羊同学'
        }
      })
    }
```

**子组件:**

```text
<template>
  <div id="C">
    This is page C!
    <p>这是父组件传入的数据: {{this.$route.query.sometext}}</p>
  </div>
</template>
```

**路由配置:** 不需要做任何修改
`{path: '/c', name: 'C', component: C}`









## 二十一、分布式ID

### 要求

- 全局唯一，区别于单点系统的唯一，全局是要求分布式系统内唯一。
- 有序性，通常都需要保证生成的 ID 是有序递增的。例如，在数据库存储等场景中，有序 ID 便于确定数据位置，往往更加高效。

### 方案

1、基于数据库自增序列的实现。这种方式优缺点都非常明显，好处是简单易用，但是在扩展性和可靠性等方面存在局限性。

2、基于 Twitter 早期开源的[Snowflake](https://github.com/twitter/snowflake)的实现，以及相关改动方案。这是目前应用相对比较广泛的一种方式，其结构定义你可以参考下面的示意图。

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201217091249.png" alt="TIM截图20201217091249" style="zoom:50%;" />

整体长度通常是 64 （1 + 41 + 10+ 12 = 64）位，适合使用 Java 语言中的 long 类型来存储。

头部是 1 位的**正负标识位**。

紧跟着的高位部分包含 **41 位时间戳**，通常使用 System.currentTimeMillis()。

后面是 10 位的 **WorkerID**，标准定义是 5 位数据中心 + 5 位机器 ID，组成了机器编号，以区分不同的集群节点。

最后的 12 位就**是单位毫秒内可生成的序列号数目的理论极限。**

3、MongoDB 的[ObjectId](http://mongodb.github.io/node-mongodb-native/2.0/tutorials/objectid/)提供了一个 12 byte（96 位）的 ID 定义，其中 32 位用于记录以秒为单位的时间，机器 ID 则为 24 位，16 位用作进程 ID，24 位随机起始的计数序列。

**Snowflake 是否受冬令时切换影响？**

它是返回当前时间和 1970 年 1 月 1 号 UTC 时间相差的毫秒数，这个数值与夏 / 冬令时并没有关系，所以并不受其影响。

## 二十二、分布式协议和算法

### 拜占庭将军问题

#### 方式一

n位将军，最多容忍(n-1)/3位叛将

如果叛将人数为 m，将军人数不能少于 3m + 1

#### 方式二

**签名消息型拜占庭问题之解**

忠诚将军的签名无法伪造，而且对他签名消息的内容进行任何更改都会被发现； 任何人都能验证将军签名的真伪。

在计算机分布式系统中，最常用的是**非拜占庭容错算法**，即故障容错算法（**Crash Fault Tolerance，CFT**）。CFT 解决的是分布式的系统中存在故障，但不存在恶意节点的场景下 的共识问题。 也就是说，这个场景可能会丢失消息，或者有消息重复，但不存在错误消 息，或者伪造消息的情况。常见的算法有 **Paxos 算法、Raft 算法、ZAB 协议**

### CAP

CAP 指的是：一致性（Consistency）、可用性（Availability）、分区容错性（Partition tolerance）。

**分布式系统理论上 不可能选择 CA 架构，只能选择 CP 或者 AP 架构。**

<u>一致性强调 的不是数据完整，而是各节点间的数据一致</u>。

<u>可用性强调的是服务可用，但不保证数据的一致。</u>

分区容错性：当节点间出现任意数量的消息丢失或高延迟的时候，系统仍然可 以继续提供服务。<u>强调的是集群对分区故障的容 错能力。</u>



### BASE

往往在分布式系统中无法实现完全一致性.

 BASE 理论，它是对 CAP 定律的进一步扩充,指的是： 

 Basically Available（基本可用） ： 分布式系统在出现故障时，允许损失部分可用功能，保证核心功能可用 （流量削峰、延迟响应、体验降级、过载 保护）

Soft state（软状态） ： 允许系统中存在中间状态，这个状态不影响系统可用性 

Eventually consistent（最终一致性） ： 经过一段时间后，所有节点数据都将会达到一致 

**最终一致性实现方式：**

(**读时修复**：在读取数据时，检测数据的不一致，进行修复。比如 Cassandra 的 Read Repair 实现，具体来说，在向 Cassandra 系统查询数据的时候，如果检测到不同节点 的副本数据不一致，系统就自动修复数据。 

**写时修复**：在写入数据，检测数据的不一致时，进行修复。<u>优先。不需要做数据一致性对比，性能消耗比较低</u> 

**异步修复**：这个是最常用的方式，通过定时对账检测副本数据的一致性，并修复。)

 BASE 理论核心思想就是：我们无法做到强一致，但每个应用都可以根据自身的业务特点，采用适当的方式来使系统达到最终一致性

### PAXOS

一个是 Basic Paxos 算法，描述的是多节点之间如何就某个值（提案 Value）达成共 识； 

另一个是 Multi-Paxos 思想，描述的是执行多个 Basic Paxos 实例，就一系列值达成共 识。

**提议者代表的是接入和协调功能**，收到客户端请求后，发起二阶段提交，进行共识协 商；

 **接受者代表投票协商和存储数据，对提议的值进行投票，并接受达成共识的值**，存储保 存；

 **学习者代表存储数据，不参与共识协商，只接受达成共识的值**，存储保存。一般来说，<u>学习者是数据备份节点</u>，比如“Master-Slave”模型中的 Slave，被 动地接受数据，容灾备份。

<u>Basic Paxos 是通过二阶段提交的方式来达成共识的</u>

### Raft算法

从本质上说，Raft 算法是通过一切以 领导者为准的方式，实现一系列值的共识和各节点日志的一致

#### 节点通讯

是远程过程调用（RPC）

1. 请求投票（RequestVote）RPC，是由**候选人在选举期间发起，通知各节点进行投票**； 
2. 日志复制（AppendEntries）RPC，是由**领导者**发起，用来**复制日志和提供心跳消息**。

#### 任期

每个任期由单调递增的数字（任期编号）标识，任期编号是随着选举的举行而变化的。

1、在 Raft 算法中约定，如果一个候选人或者领导者，**发现自己的任期编号比其他节点小， 那么它会立即恢复成跟随者状态**。比如分区错误恢复后，任期编号为 3 的领导者节点 B，收到来自新领导者的，包含任期编号为 4 的心跳消息，那么节点 B 将立即恢复成跟 随者状态。 

2、还约定如果**一个节点接收到一个包含较小的任期编号值的请求，那么它会直接拒绝这个 请求**。比如节点 C 的任期编号为 4，收到包含任期编号为 3 的请求投票 RPC 消息，那 在这里 它将拒绝这个消息

## 二十三、设计模式

### 行为型模式

**关注对象之间的通信**

#### 责任链模式

chain of responsibility

##### 定义

**将接收者对象连成一条链，并在该链上传递请求，直到有一个接收者对象处理它。**通过让更多对象有机会处理请求，**避免了发送者和接收者之间的耦合**。

在责任链中，作为请求接收者的多个对象**通过对其后继的引用而连接起来形成一条链。**

##### 实现

基础版  封装版 参照 `E:\codeSpace\study\design-pattern\src\com\abner\pattern\chain\advance`

```java
package com.abner.pattern.chain.base;

public abstract  class ChainHandler {

    public void setSuccessor(ChainHandler successor) {
        this.successor = successor;
    }

   /**
    * 后继者
    */
    protected  ChainHandler successor;

    /**
     *  1 业务方法调用 2 后继者的调用  出发链条向 下一个节点 调用
     */
    public  void handle(){
        handleProcess();
        if(successor!=null){
            // 后继者的继续调用
            successor.handle();
        }
    }

    /**
     * 实际业务方法
     *@author  wyz
     *@date 2020/12/23 16:18
     */
    public  abstract  void handleProcess();
}

```

```java
package com.abner.pattern.chain.base;

/**
 * 责任链模式的 基础使用
 *@author  wyz
 *@date 2020/12/23 16:20
 */
public class ChainClient {
    static  class  ChainHandlerA extends ChainHandler {

        @Override
        public void handleProcess() {
            System.out.printf("%s 处理\n",this.getClass().getName());
        }
    }
    static  class  ChainHandlerB extends ChainHandler {
        @Override
        public void handleProcess() {
            System.out.printf("%s 处理\n",this.getClass().getName());
        }
    }

    public static void main(String[] args) {
        ChainHandler handlera=new ChainHandlerA();
        ChainHandler handlerb=new ChainHandlerB();
        // 设置 后继者
        handlera.setSuccessor(handlerb);
        handlera.handle();
    }
}
     /*
        * com.abner.pattern.chain.base.ChainClient$ChainHandlerA 处理
     com.abner.pattern.chain.base.ChainClient$ChainHandlerB 处理
* */
```

##### 应用场景

在请求处理者不明确的情况下向对个对象中的一个提交一个请求。
需要动态处理一组对象处理请求。

比如

Spring Security 使用责任链模式，可以动态地添加或删除责任（处理 request 请求）

Spring AOP 通过责任链模式来管理 Advisor

#### 模板方法模式

##### 定义

定义一个操作中的算法的骨架（**抽象基类**），而将一些步骤延迟到子类中。自类重写一些方法，和钩子函数，可以不改变一个算法的结构即可重定义该算法的某些特定步骤。

**继承**实现、 **final关键词修饰避免子类修改** 、 protected 修饰 重写的方法 适用于 子类  朋友 等。 所谓钩子函数，就是影响整体步骤的判断。可以是默认的空的实现。

##### 实现

##### 使用场景

### 创建型模式

**创建对象的同时隐藏创建逻辑的方式，而不是使用 new 运算符直接实例化对象**

### 结构型模式

**类和对象的组合。**继承的概念被用来组合接口和定义组合对象获得新功能的方式

### J2EE模式

**关注表示层**

## 二十四、gradle

### 定义

开源的项目自动化构建工具，在ant 和maven概念基础上，引入基于Groovy的特定领域语言（DSL  Domain Specific Language），而不再使用xml形式管理构建脚本。

**相比较maven ，更加使用groovy脚本更加简洁，而task机制比maven插件更加灵活。**

### Groovy

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201224162708923.png" alt="image-20201224162708923" style="zoom:50%;" />

**与java比较**

1、完全兼容java语法、

2、分号可选

3、类、方法是public

4、编译器自动给属性添加setter/getter方法

5、属性可以直接用点号获取

6、最后一个表达式的值会被作为返回值。

7、== 等同于equals，不会有NullPointerExceptions

**特性**

assert语句 / 可选类型定义  / 可选括号 / 字符串形式多样  / 集合API / 闭包

```groovy
//public class ProjectVersion{
//
//    private int major;
//    private int minor  // 分号可选
//
//    ProjectVersion(int major, int minor) {
//        this.major = major
//        this.minor = minor
//    }
//
//    int getMinor() {
//       minor   // 最后一个表达式的值会被作为返回值
//    }
//
//    void setMinor(int minor) {
//        this.minor = minor
//    }
//}
//
//ProjectVersion v1=new ProjectVersion(1,2);
//println v1.major;
//ProjectVersion v2=null  // 这里会报异常 version已经是1  断言报错
//println v1==v2

//def version =1
//
//println(version)
//
////assert  version =2
//
//def s1='1' // 普通字符串
//def s2="version is ${version}"  // 可进行变量的替换
//// 三个引号 可进行换行
//def s3='''ceshi huan
//hang'''
//println s1
//println s2
//println s3

// 集合
def list=['ant','maven']
list << 'gradle'
assert  list.size()==3
assert  list.getClass() == ArrayList
// map
def map=['ant':2000]
map.maven=3000
println map.ant
println map['ant']
println map.getClass()
println map.size()

// 闭包  简单来说 是一个代码块   可以被赋值为变量 也可以 作为变量传递
def c1={
    v-> println v
}

def c2={
    println 'hello'
}

def method1(Closure closure){
    closure("param")
}
def method2(Closure closure){
    closure()
}

method1(c1)
method2(c2)
```

### 实战

#### 应用程序版本

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201224171759653.png" alt="image-20201224171759653" style="zoom:50%;" />、

#### 自定义任务

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225110148904.png" alt="image-20201225110148904" style="zoom:50%;" />

#### 构建生命周期

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225110335364.png" alt="image-20201225110335364" style="zoom:50%;" />

初始化：初始化哪些项目参与到构建中

配置：生成task的依赖关系和执行图

执行：执行task的动作

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225110510151.png" alt="image-20201225110510151" style="zoom:50%;" />

#### 常用仓库

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225110849174.png" alt="image-20201225110849174" style="zoom:50%;" />



<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225111647155.png" alt="image-20201225111647155" style="zoom:50%;" />





#### 依赖关系图

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225111115601.png" alt="image-20201225111115601" style="zoom:50%;" />



#### 依赖版本冲突

gradle默认按最高版本解决

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225111844626.png" alt="image-20201225111844626" style="zoom:50%;" />

解决

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225111924110.png" alt="image-20201225111924110" style="zoom:50%;" />

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225111950217.png" alt="image-20201225111950217" style="zoom:50%;" />

#### 依赖传递

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225113054524.png" alt="image-20201225113054524" style="zoom:50%;" />

依赖另一个模块 通过

```groovy
commpile project(":moduleName")
```

#### 多模块引用

**所有模块引用java 部署  1.8编译  allprojects标 识来引入统一配置     subprojects来统一引入依赖**

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225134811329.png" alt="image-20201225134811329" style="zoom:50%;" />

**统一配置group 和version,根项目建立gradle.properties添加**

#### 发布

<img src="C:\Users\10674\AppData\Roaming\Typora\typora-user-images\image-20201225140340128.png" alt="image-20201225140340128" style="zoom:50%;" />

配置Publish插件 /  配置 发布仓库 /  发布

## 二十五、DDD领域驱动

### 核心思想

个人理解：基于（领域）业务驱动行为。领域划分、领域协作。

### 角色职权

#### 领域事件

比如 订单提交

#### 技术事件

比如表单提交

#### 命令

请求执行

事件 执行完成   在浏览器中填写完表单，单击“提交”按钮，后端系统将执行，然后返回结果。

#### 微服务有限上下文

服务内部（的上下文）/ 服务的API（的上下文）  / 服务集群（的上下文） / 服务之间的交互（的上下文）

#### 子域

 核心子域 / 支持子域  / 通用子域

#### 上下文关系   

**共享内核**  ---指两个有界上下文共同使用一份代码内核（例如一个库）。这种方式已经很少使用，因为共享一份代码，如同共享一个数
据库一样，单点风险大。
**开放主机服务** ---也是一种上下文关系的映射，也称为上下游关系映射或API调用，一个上下文通过RPC等同步方式调用另外一个上下文的API，调用者是被调用者的客户端。
注意<u>网络中断</u>等问题，引入断路器等模式防止故障级联爆炸，进行<u>业务事务的重试，同时确保服务的幂等性</u>。断路器模式会有很多中间件去实现。但是这些实现大都没有从业务事务的角度考虑，而只是从弹性角度设计。仅仅有弹性是不够的，怎样保证服务之间的调用故障不会影响业务流程？调用失败再重试后，业务流程是否重新执行了一遍？对业务规则的执行有没有影响？会不会发生数据重复等？如果重试失败或快速失败后，是不是这个调用流程中涉及的所有步骤都能回滚，都恢复到调用之前的状态？  
需要引入**防腐层，防止两个上下文系统直接耦合**，旧的上下文系统会影响新上下文系统的代码编写思路，因此必须引入第三层解耦。
**发布/订阅模式**：---一个有界上下文是发布者，另外一个有界上下文订阅这个发布者，当发布者有事件发生时，及时将事件发布给所有订阅者（这非常类似微信，当你订阅公众号以后，它们有更新时会及时通知你），这样两个上下文之间不再互相依赖，而是只依赖事件或消息，使得两者之间实现最大化的松耦合，这也是集成模式的主要实现方式

#### 聚合Aggregation

聚合是DDD中的一个重要概念，它对外代表的是一个整体，类似于一个大的对象，**内部是由有主从之分的很多对象组成的**。
**聚合是一个行为在逻辑上高度一致的对象群，注意，它是一个对象群体的总称**。
聚合的内部结构如同一棵树，每个聚合都有一个根，其他对象和聚合根之间都是枝叶与树根的关系
**传递性**：如果A是B的一部分，B是C的部分，那么A就是C的一部分。
**反对称性**：如果A是B的一部分，那么B不会是A的一部分。
组合是一种较强的聚合关系，这两种关系基本相同，不同之处在于，在**组合关系中，部件对象任何时候只能从属于一个整体对象，两者的生命周期是一样的。**
业务逻辑的一致性需要从两个方面去保证：业务数据和业务行为。
迪米特法则（Law of Demeter，LOD）可以帮助设计聚合根的行为方法。一个对象（聚合根）的行为方法只应该调用下面这些对象（聚合边界内的对象）的行为方法。
将<u>聚合根对象看成一个演员</u>（拟人化），演员如果扮演一个角色，那他应该知道哪些事情、会做那些事情，能够控制或决定什么事情？可以从这些途径收集职责：业务规则、当前有界上下文、特别的需求和特征、命令和领域事件。如果对职责还不是很理解，可以使用责任、能力、权力等词语来近似理解。

#### 实体

**实体的标识主要涉及实体对象实例的创建以及它从生到死的生命周期管理**，这个过程需要标识来标记，如果没有标识，将无法管理一个个实体对象实例，也就无法管理它们代表的业务数据和逻辑。
实体命名和标识发现
复杂的对象创建推荐使用Builder模式，所谓复杂有两种情况。
1）构造函数输入参数超过三个。
2）构造函数输入参数有其他对象类型，而不都是基本类型。

#### 值对象

**值对象是没有唯一标识的对象，是一堆数据值的容器**
值对象中的数据值一旦被构建，就不能改变，这是不变性的特性，
值对象的**构建一般是由聚合根实体负责**的，任何聚合外界需要使用聚合内的信息，都需要通过聚合根访问。

#### 仓储

仓储与DAO的主要区别是：**仓储主要为了保证聚合根对象的加载和保存，同时兼顾一些实体的直接访问**；但是DAO没有这些约束，可以说它是数据库的直接访问接口，没有数据所有权概念，没有聚合概念。

#### 六边形架构

六边形架构体现了一种**关注点分离**：将对**业务逻辑的关注和对技术架构的关注实现分离领域**（六边形的内部）是隔离的，并且与技术部分（六边形外
部的基础结构）无关，

#### 清洁架构

清洁（Clean）架构是**内部不依赖外部，而外部则依赖内部**。这种依赖包含代码名称、类的函数、变量或任何其他命名软件实体。

#### 失血、贫血、充血

失血、贫血、充血和胀血模型应该是老马提出的（此老马非马老师，是 Martin Fowler），讲述的是基于领域模型的丰满程度下如何定义一个模型，有点像：瘦、中等、健壮和胖。胀血（胖）模型太胖。

##### **失血模型**：

基于数据库的领域设计方式其实就是典型的失血模型，以 Java 为例，POJO 只有简单的基于 field 的 setter、getter 方法，POJO 之间的关系隐藏在对象的某些 ID 里，由外面的 manager 解释，比如 son.fatherId，Son 并不知道他跟 Father 有关系，但 manager 会通过 son.fatherId 得到一个 Father。

##### **贫血模型**：

儿子不知道自己的父亲是谁是不对的，不能每次都通过中间机构（Manager）验 DNA(son.fatherId) 来找爸爸，领域模型可以更丰富一点。

````java
public class Son{
    private Father father;
    public Father getFather(){return this.father;}
}
````

##### **充血模型**

充血模型的存在让 domain object 失去了血统的纯正性，他不再是一个纯的内存对象，这个对象里埋藏了一个对数据库的操作，这对测试是不友好的

```java
public class Father{
    //private Son son; 删除这个引用
    private SonRepository sonRepo;// 添加一个 Son 的 repo
    private getSon(){return sonRepo.getByFatherId(this.id);}
}

```



### 工程样例

#### user interface

该层包含与其他系统/客户进行交互的接口与通信设施。该层主要由facade、dto和assembler三类组件构成，三类组件均是典型的j2ee模式

 dto的作用最初主要是以粗粒度的[数据结构](http://www.makaidong.com/search.jspx?q=数据结构)减少[网络通信](http://www.makaidong.com/search.jspx?q=网络通信)并简化调用接口。在领域驱动设计中，采用dto模型，可以起到隐藏领域细节，帮助实现独立封闭的领域模型的作用。

**dto与领域对象之间的相互转换工作多由assembler（汇编器）承担，**也有一些系统使用反射机制自动实现dto与领域对象之间的相互转换，如apache common beanutils。

**facade（门面）的用意在于为远程客户端提供粗粒度的调用接口**。facade本身不处理任何的业务逻辑，它的主要工作就是将一个用户请求委派给一个或多个service进行处理，同时借助assembler将service传入或传出的领域对象转化为dto进行传输。

#### application

 application层中主要组件就是service.service只负责协调并委派业务逻辑给领域对象进行处理。和传统面向过程设计是不一致的。

#### domain

domain层是整个系统的核心层，该层维护一个使用[面向对象](http://www.makaidong.com/search.jspx?q=面向对象)技术实现的领域模型，几乎全部的业务逻辑会在该层实现。domain层包含**entity（实体）、valueobject(值对象)、domain event（领域事件）和repository（仓储）**等多种重要的领域组件。

#### infrastructure（['ɪnfrə.strʌktʃər]）

infrastructure（基础设施层）为interfaces、application和domain三层提供支撑。所有与具体平台、框架相关的实现会在infrastructure中提供，避免三层特别是domain层掺杂进这些实现，从而“污染”领域模型。infrastructure中最常见的一类设施是对象持久化的具体实现。

### 实战疑问

### 参考

[领域驱动设计理解](https://blog.csdn.net/wwd0501/article/details/95062535)

## 二十六、service mesh(服务网格)

一代service mesh 它将**分布式服务的通信抽象为单独一层**，在这一层中实现负载均衡、服务发现、认证授权、监控追踪、流量控制等分布式系统所需要的功能，作为一个和服务对等的代理服务，**和服务部署在一起，接管服务的流量**，通过代理之间的通信间接完成服务之间的通信请求.

<img src="D:\dailySoftWare\typora\md\img\v2-e5660d35a311467c3323f10ebf2fb9a5_r.jpg" alt="v2-e5660d35a311467c3323f10ebf2fb9a5_r" style="zoom:50%;" />

<img src="D:\dailySoftWare\typora\md\img\v2-8a9cc161a34d97f36ead06d0abc5b1fb_r.jpg" alt="v2-8a9cc161a34d97f36ead06d0abc5b1fb_r" style="zoom:50%;" />

<img src="D:\dailySoftWare\typora\md\img\v2-ee0bde35f9ec79bf38feda98550b8f71_r.jpg" alt="v2-ee0bde35f9ec79bf38feda98550b8f71_r" style="zoom:50%;" />



二代service mesh **为了提供统一的上层运维入口，演化出了集中式的控制面板**，所有的单机代理组件**通过和控制面板交互进行网络拓扑策略的更新和单机数据的汇报。**

<img src="D:\dailySoftWare\typora\md\img\v2-546ed82e25d83a2cb404b0a3f526f9c6_r.jpg" alt="v2-546ed82e25d83a2cb404b0a3f526f9c6_r" style="zoom:50%;" />

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201229105201.png" alt="TIM截图20201229105201" style="zoom:50%;" />



服务网格是一个***基础设施层\***，用于处理服务间通信。云原生应用有着复杂的服务拓扑，服务网格保证***请求在这些拓扑中可靠地穿梭\***。在实际应用当中，服务网格通常是由一系列轻量级的***网络代理\***组成的，它们与应用程序部署在一起，但***对应用程序透明\***

***基础设施层\***+***请求在这些拓扑中可靠穿梭\***：这两个词加起来描述了Service Mesh的定位和功能，是不是似曾相识？没错，你一定想到了TCP；

***网络代理\***：这描述了Service Mesh的实现形态；

***对应用透明\***：这描述了Service Mesh的关键特点，正是由于这个特点，Service Mesh能够解决以Spring Cloud为代表的第二代微服务框架所面临的三个本质问题；



**优点：**

- 屏蔽分布式系统通信的复杂性(负载均衡、服务发现、认证授权、监控追踪、流量控制等等)，服务只用关注业务逻辑；
- 真正的语言无关，服务可以用任何语言编写，只需和Service Mesh通信即可；
- 对应用透明，Service Mesh组件可以单独升级；

**Service Mesh目前也面临一些挑战**：

- Service Mesh组件**以代理模式计算并转发请求，一定程度上会降低通信系统性能，并增加系统资源开销**；
- Service Mesh组件接管了网络流量，因此**服务的整体稳定性依赖于Service Mesh，同时额外引入的大量Service Mesh服务实例的运维和管理也是一个挑战；**

## 二十七、springCloud Alibaba

### 描述

Spring Cloud Alibaba 是阿里巴巴提供的微服务开发一站式解决方案，是阿里巴巴开源中间件与 Spring Cloud 体系的融合。

### 组件

<img src="D:\dailySoftWare\typora\md\img\v2-46c0b9e0d41c441d222390c79a4cd53b_r.jpg" alt="v2-46c0b9e0d41c441d222390c79a4cd53b_r" style="zoom:50%;" />

#### **开源**

Nacos：一个更易于构建云原生应用的**动态服务发现、配置管理和服务管理**平台。

Sentinel：把流量作为切入点，从**流量控制、熔断降级、系统负载保护**等多个维度保护服务的稳定性。

RocketMQ：开源的分布式消息系统，基于高可用分布式集群技术，提供低延时的、高可靠的消息发布与订阅服务。

Dubbo：这个就不用多说了，在国内应用非常广泛的一款高性能 Java RPC 框架。

Seata：阿里巴巴开源产品，一个易于使用的高性能微服务**分布式事务解决方案**。

Arthas：开源的**Java动态追踪工具，基于字节码增强技术**，功能非常强大。

#### **商业**

Alibaba Cloud ACM：一款在分布式架构环境中对应用配置进行集中管理和推送的**应用配置中心产品**。

Alibaba Cloud OSS：阿里云**对象存储服务**（Object Storage Service，简称 OSS），是阿里云提供的云存储服务。

Alibaba Cloud SchedulerX：阿里中间件团队开发的一款**分布式任务调度产品，**提供秒级、精准的定时（基于 Cron 表达式）任务调度服务。

### 功能描述

#### 服务注册与发现

Spring Cloud Alibaba 基于 Nacos 提供 **spring-cloud-alibaba-starter-nacos-discovery** & **spring-cloud-alibaba-starter-nacos-config** 实现了**服务注册 & 配置管理**功能。依靠 @EnableDiscoveryClient 进行服务的注册，兼容 RestTemplate & OpenFeign 的客户端进行服务调用。

适配 Spring Cloud 服务注册与发现标准，**默认集成了 Ribbon 的**支持。

#### 支持多协议的服务调用

Spring Cloud 默认的服务调用依赖 OpenFeign 或 RestTemplate 使用 REST 进行调用。

使用 **@DubboTransported** 注解可将底层的 Rest 协议无缝切换成 Dubbo RPC 协议，进行 RPC 调用。

```java
@FeignClient("dubbo-provider")
@DubboTransported(protocol = "dubbo")
public interface DubboFeignRestService {
  @GetMapping(value = "/param")
  String param(@RequestParam("param") String param);

  @PostMapping("/saveB")
  String saveB(@RequestParam("a") int a, @RequestParam("b") String b);
}
```

#### 服务限流降级

Spring Cloud Alibaba 基于 **Sentinel**( ['sentɪn(ə)l] )，对 Spring 体系内基本所有的客户端，网关进行了适配，

默认支持 WebServlet、WebFlux, OpenFeign、RestTemplate、Spring Cloud Gateway, Zuul, Dubbo 和 RocketMQ 限流降级功能的接入。

<u>Sentinel应用比较简单，只需引入 starter，即可生效，可以在运行时通过控制台实时修改限流降级规则，还支持查看限流降级 Metrics 监控。</u>

#### 微服务消息驱动

支持为微服务应用构建消息驱动能力，基于 Spring Cloud Stream 提供 Binder 的新实现: Spring Cloud Stream RocketMQ Binder，

也新增了 Spring Cloud Bus 消息总线的新实现 Spring Cloud Bus RocketMQ。

#### 分布式事务

使用 **Seata** 解决微服务场景下面临的分布式事务问题。

使用 **@GlobalTransactional** 注解，在微服务中传递事务上下文，可以对业务零侵入地解决分布式事务问题

### spring cloud alibaba和组件版本关系

| Spring Cloud Alibaba Version                    | Sentinel Version | Nacos Version | RocketMQ Version | Dubbo Version | Seata Version |
| :---------------------------------------------- | :--------------- | :------------ | :--------------- | :------------ | :------------ |
| 2.2.1.RELEASE                                   | 1.7.1            | 1.2.1         | 4.4.0            | 2.7.6         | 1.1.0         |
| 2.2.0.RELEASE                                   | 1.7.1            | 1.1.4         | 4.4.0            | 2.7.4.1       | 1.0.0         |
| 2.1.2.RELEASE or 2.0.2.RELEASE                  | 1.7.1            | 1.2.1         | 4.4.0            | 2.7.6         | 1.1.0         |
| 2.1.1.RELEASE or 2.0.1.RELEASE or 1.5.1.RELEASE | 1.7.0            | 1.1.4         | 4.4.0            | 2.7.3         | 0.9.0         |
| 2.1.0.RELEASE or 2.0.0.RELEASE or 1.5.0.RELEASE | 1.6.3            | 1.1.1         | 4.4.0            | 2.7.3         | 0.7.1         |

### 和spring cloud spring boot 版本关系

| Spring Cloud Version        | Spring Cloud Alibaba Version | Spring Boot Version |
| :-------------------------- | :--------------------------- | :------------------ |
| Spring Cloud Hoxton.SR3     | 2.2.1.RELEASE                | 2.2.5.RELEASE       |
| Spring Cloud Hoxton.RELEASE | 2.2.0.RELEASE                | 2.2.X.RELEASE       |
| Spring Cloud Greenwich      | 2.1.2.RELEASE                | 2.1.X.RELEASE       |
| Spring Cloud Finchley       | 2.0.2.RELEASE                | 2.0.X.RELEASE       |
| Spring Cloud Edgware        | 1.5.1.RELEASE                | 1.5.X.RELEASE       |

### 实战

#### nacos

##### 描述

[下载地址](https://github.com/alibaba/nacos/releases)

[参考学习](https://cloud.tencent.com/developer/inventory/778/article/1727271)

支持模式：

- 单机模式 - 用于测试和单机试用。
- 集群模式 - 用于生产环境，确保高可用。
- 多集群模式 - 用于多数据中心场景。

- nacos默认端口是：8848
- 默认用户名：nacos
- 默认密码：nacos

访问http://127.0.0.1:8848/nacos/index.html

##### 使用

###### **作为服务注册中心使用**

1、引入依赖

````xml
<dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
    </dependency>
````

2、配置

```yaml
server:
  port: 9001
spring:
  application:
    name: nacos-discovery-server
  cloud:
    nacos:
      discovery:
        server-addr: 127.0.0.1:8848
```

```yaml
在springcloud E版本的时候，对服务注册进行了优化，在依赖了spring-cloud-starter-alibaba-nacos-discovery之后，默认会将服务注册到注册中心。
如果我们不想让我们的服务注册到nacos应该怎么做？
spring:
  cloud:
    nacos:
      discovery:
        enabled: false
```

###### **作为配置中心使用**

1、引入依赖

```xml
<dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
    </dependency>
```

**注意：不能使用原来的application.yml作为配置文件，而是新建一个bootstrap.yml作为配置文件**

**配置文件加载的优先级（由高到低）**

**bootstrap.properties ->bootstrap.yml -> application.properties -> application.yml**

2、配置

```properties
server:
  port: 9002
spring:
  profiles:
    active: dev
  application:
    name: nacos-config-server
  cloud:
    nacos:
      config:
        server-addr: 127.0.0.1:8848 # 配置中心
        file-extension: yaml # 这里指定的文件格式需要和nacos上新建的配置文件后缀相同，否则读不到
```

<img src="D:\dailySoftWare\typora\md\img\TIM截图20201231171049.png" alt="TIM截图20201231171049" style="zoom:50%;" />

- Data ID：默认为 ${spring.application.name}-${spring.profile.active}.${spring.cloud.nacos.config.file-extension} 或 ${spring.application.name}.${spring.cloud.nacos.config.file-extension}
- Group：对应配置文件中的${spring.cloud.nacos.config.group}，默认为DEFAULT_GROUP
- 配置格式：对应配置文件中的${spring.cloud.nacos.config.file-extension}，
- 配置内容：根据你的配置格式按对应的格式填写即可。

**@Value注解可以获取到配置中心的值**

在TestController上加个**@RefreshScope注解**，然后我们去nacos客户端手动修改config.info的信息，然后重新调用这个/test接口，会发现响应的是修改后的内容。

###### 多环境配置的三种方式

最开始的时候我们也说过微服务项目会有多个环境，我们如何实现和管理这些环境呢？

**1.通过Data ID 和profiles实现**

我们可以在配置文件中指定spring.profiles.active = **，然后在nocas客户端新建对应的${spring.cloud.nacos.config.prefix}`-`${spring.profiles.active}`.`${spring.cloud.nacos.config.file-extension}配置来区分不同的环境。

**2.通过Group实现**

我们可以为不同的环境新建不同的分组，然后的配置文件中指定spring.cloud.nacos.config.group=组名，这样也可以实现不同环境的区分。

**3.通过Namespace实现**

这种方式是**官方建议**的方式，在nacos客户端中新建不同的分组，然后再配置文件中指定namespace就可以区分不同的环境了。 

###### 自定义扩展的Data ID

大多数时候我们可能更加倾向于将不同的配置分开写到不同的配置文件中，比如我想把文件类和日志类的配置拆分开写到两个配置中，nacos也是支持这种写法的。

1. 我们在nacos中新建两个Data ID 分别是log.yaml 和 file.yaml 的文件。

我们在配置文件中分别加入以下内容：log:level: 2，file:url: "[http://123.com](http://123.com/)"。

1. 如何配置呢

```properties
spring:
  cloud:
    nacos:
      config:
        extension-configs[0]:
          data-id: log.yaml
          group: DEFAULT_GROUP   # 默认为DEFAULT_GROUP
          refresh: true   # 是否动态刷新，默认为false
        extension-configs[1]:
          data-id: file.yaml
          group: DEFAULT_GROUP
          refresh: true
```

为了更加清晰的在多个应用间配置共享的 Data Id，官方推荐使用如下配置：

```properties
spring:
  cloud:
    nacos:
      config:
        shared-configs[0]:
          data-id: log.yaml
          group: DEFAULT_GROUP   # 默认为DEFAULT_GROUP
          refresh: true   # 是否动态刷新，默认为false
        shared-configs[1]:
          data-id: file.yaml
          group: DEFAULT_GROUP
          refresh: true
```

1. 深入思考，既然我们有两个配置文件，假如两个配置文件中出现一样的key值，这样我们程序中会加载哪个配置呢，其实nacos在设计的时候也考虑到了优先级问题，下面我们一起来看看。

我们将file.yaml中的配置改成log:level: 22。这时候我们加载写个接口取一下配置。看看它取到的是哪个文件的内容。

```js
	RestController
    @RefreshScope
    class TestController {
        
        @Value("${log.level}")
        private String log;

        @GetMapping("/test")
        public String hello() {
            return "log.lelve="+log;
        }

    }
```

结果取到的是file.yaml中的配置，这是因为**多个 Data Id 同时配置时，他的优先级关系是 `spring.cloud.nacos.config.extension-configs[n].data-id` 其中 n 的值越大，优先级越高。**

**注意：`spring.cloud.nacos.config.extension-configs[n].data-id` 的值必须带文件扩展名，文件扩展名既可支持 properties，又可以支持 yaml/yml。 此时 `spring.cloud.nacos.config.file-extension` 的配置对自定义扩展配置的 Data Id 文件扩展名没有影响。**

###### 扩展：不同方式配置加载优先级

Spring Cloud Alibaba Nacos Config 目前提供了三种配置能力从 Nacos 拉取相关的配置。

- A: 通过 `spring.cloud.nacos.config.shared-configs[n].data-id` 支持多个共享 Data Id 的配置
- B: 通过 `spring.cloud.nacos.config.extension-configs[n].data-id` 的方式支持多个扩展 Data Id 的配置
- C: 通过内部相关规则(spring.cloud.nacos.config.prefix`、`spring.cloud.nacos.config.file-extension`、`spring.cloud.nacos.config.group)自动生成相关的 Data Id 配置

当三种方式共同使用时，他们的一个优先级关系是:A < B < C

#### gateway

[参考文档](https://cloud.tencent.com/developer/inventory/778/article/1727272)

#### sentinel

[官方文档](https://sentinelguard.io/zh-cn/)

[参考文档](https://cloud.tencent.com/developer/inventory/778/article/1727370)

#### seata

[参考文档](https://cloud.tencent.com/developer/inventory/778/article/1494598)

## 二十八、Resilience4J

### 描述

Resilience4j 是一个**轻量级的容错组件**，其灵感来自于 [Hystrix](https://www.oschina.net/p/hystrix)，但主要**为 Java 8 和函数式编程所设**计。轻量级体现在其**只用 [Vavr](https://www.oschina.net/p/vavr) 库**（前身是 Javaslang），没有任何外部依赖。而 Hystrix 依赖了 Archaius ，Archaius 本身又依赖很多第三方包，例如 Guava、Apache Commons Configuration 等。

[rɪ'zɪljəns]

<img src="D:\dailySoftWare\typora\md\img\5db397701f7086257dc0bc50d77b9ba4.png" alt="5db397701f7086257dc0bc50d77b9ba4" style="zoom:50%;" />

https://www.e-learn.cn/topic/3728612

https://www.oschina.net/p/vavr

https://www.oschina.net/p/resilience4j?hmsr=aladdin1e1

https://blog.csdn.net/qwe86314/article/details/98873884



