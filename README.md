

# Java

[100道面试题](https://www.bilibili.com/video/BV1Eb4y1R7zd)

[leetCode](https://leetcode-cn.com/)

[学习计划表](学习计划表.xlsx)

[学习路线](Java 学习路线导图.xmind)

## 工具下载

### Git

[git下载](https://git-scm.com/downloads)

#### Git命令

> git init	# 初始化本地git仓库（创建新仓库）
>
> mkdir+文件夹名	# 新建文件夹
>
> git config --global user.name "xxx"	# 配置用户名
>
> git config --global user.email "xxx@xxx.com"	\# 配置邮件

配置ssh key

```css
ssh-keygen -t rsa -C "954144110@qq.com" // 生成key，然后在对应目录找到.pub文件，即公钥，配置到github上

ssh -v git@github.com
ssh -T git@github.com
git remote set-url origin git@github.com:q954144110/test.git
```

## MD语法

[MD语法链接](https://github.com/younghz/Markdown)

## 面试题

### 面向对象

> 面向对象与面向过程是处理问题的两种不同的角度，一个注重过程（步骤），一个注重对象（参与者）
>
> A = 1
>
> B = 2 
>
> C = A + B
>
> 面向过程：1 + 2
>
> 面向对象：A + B

- 封装

  - 属性私有化，提供外部访问方法，外部调用无需关注内部实现
  - 经典案例
    - javabean的属性私有，提供get/set方法对外访问
    - orm框架

- 继承

  - 共性抽取，特性独立
  - 子类共性的方法或属性直接使用父类的，不需要再自己定义，只需扩展自己的特性

- 多态

  - 继承
  - 方法
  - 父类引用指向子类对象    

  ```java
  父类类型 变量名 = new 子类对象;
  变量名.方法名();
  ```

  - 无法调用子类特有方法

### String、StringBuffer、StringBulider

- String是final修饰，不可变，每次操作new对象
- StringBuffer和StringBuilder都是操作原对象
- StringBuffer是线程安全的，StringBuilder线程不安全
- StringBuffer方法都是synchronized修饰的
- 性能：StringBuilder > StringBuffer > String
- 优先使用StringBuilder，多线程使用共享变量时使用StringBuffer

### JDK、JRE、JVM

- **JDK**：Java Develpment Kit    Java开发工具
- **JRE**： Java Runtime Environment    Java运行时环境
- **JVM**：Java Virtual Machine    Java虚拟机

### ==和equals比较

- ==对比的是栈中的值。在栈中，基本数据类型储存的是变量值，引用类型储存的是堆中对象的地址
- equals：object中默认也是采用==比较，通常会重写

### final

- 修饰的类不可被继承
- 修饰的方法不可别重写
- 修饰的变量需初始化赋值，不可被更改
  - 修饰类变量：声明时赋值、在静态代码块中赋值
  - 修饰成员变量：声明时赋值、在非静态代码块中赋值、构造器中赋值
  - 修饰局部变量：由程序员显示的初始化，在使用前赋值，且只能赋值一次
  - 修饰基本数据类型的变量：初始化后不能更改
  - 修饰引用类型的变量：初始化后不能指向别的对象。**引用的值可改变**
- 局部内部类和匿名内部类只能访问局部final变量
  - 编译之后，内部类和外部类会生成各自的class文件，因此内部类不会随着外部类的方法回收。正常来说当外部类方法结束时，局部变量就会销毁。内部类对象可能还在引用这个变量，因此会将局部变量复制一份作为内部类的成员变量，为保持变量一致，必须用final修饰。

### 重写和重载

- **重载**：发生在同一个类中，方法名相同，参数列表不同（个数不同、顺序不同、修饰符不同）
- **重写**：发生在父子类中，方法名和参数列表都相同，返回值范围小于等于父类，抛出异常类型小于等于父类，访问修饰符范围大于等于父类；如果父类方法定义为private，则不能重写

### 接口和抽象类

- 抽象类可以存在普通方法，而接口中只能存在public abstract方法
- 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只，能是public static final类型的，即常量
- 抽象类只能继承一个，接口可以实现多个

> 接口的设计目的是对类的行为进行约束，提供一种机制，可以强制要求不同的类具有相同的行为。只约束行为的有无，不限制实现。
>
> 抽象类的设计目的是代码的复用。当不同类具有相同行为，且一部分行为实现方法一致时，可以让这些类都派生于一个抽象类。
>
> 抽象类是对类本质的抽象，表达的是is a的关系，包含并实现子类通用特性，差异特性由子类自己实现。
>
> 接口是对行为的抽象，表达的是like a的关系。
>
> 当关注一个事物的本质时，用抽象类；当关注一个操作时，用接口。
>
> 抽象类的功能要远超接口，但是定义抽象类堆代价高。

### List和Set

- List：有序，按对象进入的顺序保存对象，可重复，允许多个null元素对象，可以使用Iterator取出所有元素进行遍历，也可get(int index)获取指定下标的元素
- Set：无序，不可重复，只允许一个null元素对象，只能使用Iterator取出所有的元素进行遍历

### hashCode和equals

- hashCode()作用是获取哈希码
- 两个对象相等，hashCode()一定相同，equals()返回true
- hashCode()相等，equals()不一定为true
- 若重写equals()，必须重写hashCode()
- hashCode()默认行为时对堆上的对象产生独特值。如果没有重写，则两个class对象一定不相等。

### ArrayList和LinkedList区别

- ArrayList：动态数组，连续内存存储，适合下标访问（随机访问）
- 扩容机制：超长会新建数组，将老数组的数据拷贝到新数组
- 非尾插法插入数据会涉及数据移动
- 使用尾插法并制定初始容量可以极大提升性能
- LinkedList：链表，分散内存存储，适合做数据插入及删除操作，不适合查询
- 遍历LinkedList必须使用Iterator，不能使用for循环，因为每次使用for循环通过get(i)取元素时，都会对list重新遍历，性能消耗极大
- 使用indexOf返回元素索引时，会遍历list，结果为空时，会遍历整个list

### HashMap和HashTable

- HashMap线程不安全，HashTable线程安全（synchronized）
- HashMap允许key和value为null，HashTable不允许
- HashMap 数组 + 链表，元素以内部类node节点储存
- key为null时，储存在下标0位置
- 计算key的hash值，没有产生hash冲突，则直接存放，产生hash冲突，则进行equals比较，如果相同则覆盖，不同则判断链表高度，插入链表。java8后引入红黑树，链表高度到8、数组长度超过64，转红黑树，长度小于6后转回链表

### ConcurrentHashMap

- jdk7
  - 数据结构：ReentrantLock + Segment + HashEntry，每个Segment中有一个HashEntry，每个HashEntry又是一个链表结构
  - 元素查询：二次hash，第一个找Segment，第二次找head节点
  - 锁：Segment分段锁，Segment继承ReentrantLock，锁定操作的Segment，其他Segment不受影响，并发度为Segment个数，Segment个数可由构造函数指定，扩容不会影响其他Segment
  - get不需要加锁，由volatile保证
- jdk8
  - 数据结构：synchronized + CAS + Node +红黑树，Node中的val和next都用volatile修饰，保证可见性
  - 元素操作：查找、替换、赋值操作都用CAS（Compare And Swap）乐观锁
  - 锁：锁链表的head节点，不影响其他元素读写，锁的粒度更细，效率更高，扩容时阻塞所有的读写操作、并发扩容
  - 读操作无锁，因为Node中的val和next都用volatile修饰了

### IOC容器的实现

- 配置文件中指定需要扫描的包路径
- 定义注解，分别表示控制层、业务服务层、数据持久化层、依赖注入注解、获取配置文件注解
- 从配置文件中获取需要扫描的包路径，获取到当前路径下的文件信息及文件夹信息，我们当前路径下所有以.class结尾的文件添加到一个Set集合中进行存储
- 遍历这个Set集合，获取在类上有指定注解的类，并将其交给IOC容器，定义一个安全的Map来储存这些对象
- 遍历这个IOC容器，获取到每一个类的实例，判断里面是否有依赖其他类的实例，递归注入

### 字节码

- 字节码即.class文件
- Java源码--->编译器--->.class--->jvm--->jvm解释器--->二进制机器码--->运行程序
- 编译和解释拆分，提高执行效率

### Java类加载器

- BootStrapClassLoader是ExtClassLoader的父类加载器，默认加载%JAVA_HOME%lib下的jar包和class文件
- ExtClassLoader是AppClassLoader的父类加载器，负责加载%JAVA_HOME%lib/ext下的jar包和class文件
- AppClassLoader是自定义加载器的父类，负责加载classpath下的class文件。也是线程上下文加载器
- 继承ClassLoader实现自定义加载器

### 双亲委派

![img](https://upload-images.jianshu.io/upload_images/7634245-7b7882e1f4ea5d7d.png)



### Java中的异常体系

![img](https://img-blog.csdn.net/20160331115514210)

### GC回收对象

- 引用计数法：每个对象都有一个引用计数属性，新增一个引用时计数加1，减少一个引用时计数减1，为0时对象被回收。
- 可达性分析法：从GC Roots开始向下搜索，搜索走过的路径称为引用链。当一个对象到GC Roots没有任何引用链时，则标记此对象 可回收。然后判断对象有没有需要执行的finalize方法，有则执行，无则直接回收
- GC Roots对象
  - 栈中引用的对象
  - 方法区中类静态属性引用的对象
  - 方发区中常量引用的对象
  - 本地方法栈中JNI引用的对象

### 线程的生命周期

-  创建：创建了一个新的线程
-  就绪：调用了start()后，进入可运行线程池中，等待获取CUP资源
-  运行：就绪线程获取了CUP资源，执行代码
-  阻塞：暂停运行
   - 等待阻塞：运行的线程执行中wait()，释放所有资源，进入等待池。必须其他线程调用notify()或者notifyAll方法才能被唤醒。wait()是object中的方法，同步控制方法或控制块中使用，会释放锁，不需要捕获异常
   - 同步阻塞：运行时的线程在获取对象的同步锁时，该锁被占用，则进入锁池等待
   - 其他阻塞：运行时的线程执行了sleep()、join()，或发出I/O请求，线程会进入阻塞状态。当sleep()超时、join()等待线程终止或超时、I/O处理完毕时，线程重回就绪状态。sleep()是Thread中的静态方法，只对当前对象有效，不会释放锁，需要捕获异常
-  死亡：线程执行完毕，或出现异常退出线程

### sleep()、wait()、join()、yield()

- 锁池：需要竞争同步锁的线程都会放在锁池中
- 等待池：调用wait()后，线程会进入等待池，不会去竞争同步锁，只有调用了notify()或notifyAll()后，等待池的线程才会去竞争锁，notify()是随机从等待池中选取一个线程放到锁池，notifyAll()是将等待池中所有线程放入锁池
- sleep()是Thread类的**静态本地方法**，wait()是Object类的**本地方法**
- sleep()不会释放锁，wait()会释放锁且加入等待队列中
- sleep()不依赖同步器synchronized，但wait()需要
- sleep()不需要被唤醒，wait()需要
- sleep()一般用于当前线程休眠，或轮询暂停操作，wait()多用于线程间通信
- sleep()会让出CPU执行时间且强制上下文切换，而wait()不一定，wait()后还有可能重新竞争到锁继续执行
- yield()后释放CPU资源，立马进入就绪状态
- join()后线程进入阻塞状态，B中A.join()，B进入阻塞队列，待A线程结束或中断，B才继续执行

### 线程安全

- 当多个线程访问一个对象时，就可能出现线程不安全。

- 堆是进程和线程共有空间，分全局堆和局部堆。全局堆就是所有没有分配的空间，局部堆就是用户分配的空间。堆在操作系统对进程初始化的时候分配，运行过程中也可以分配额外的堆，但用完需要释放空间，否则会造成内存泄漏。

  > 在Java中，堆是JVM所管理的内存中最大的一块，是所有线程共享的一块内存区域，在JVM启动时创建。堆所存在的内存区域的唯一目的就是存放对象实例，几乎所有的对象实例以及数组都在这里分配内存

- 栈是每个线程独有的，保存其运行状态和局部自动变量。操作系统在切换线程时会自动切换对应的栈。

- 进程相互独立由操作系统保证，进程中的所有线程都能访问此进程的堆空间，这就可能造成线程不安全。

### Thread和Runnable

- Thread是一个类
- Runnable是一个接口

### 守护线程

- 守护线程：为所有非守护线程提供服务的线程，随着main结束而结束
- GC是Java中的经典守护线程，当我们的程序中不再有任何运行中的Thread，程序就不会再产生垃圾，GC结束

### ThreadLocal

- 每个Thread对象均含有一个ThreadLocalMap类型的成员变量threadLocals，它储存本线程中所有的ThreadLocal对象及其对应的值

- ThreadLocalMap是由一个个Entry对象构成

- Entry继承WeakReference<ThreadLocal<?>>，key为弱引用

  ```java
  /**
   * 是继承自WeakReference的一个类，该类中实际存放的key是
   * 指向ThreadLocal的弱引用和与之对应的value值(该value值
   * 就是通过ThreadLocal的set方法传递过来的值)
   * 由于是弱引用，当get方法返回null的时候意味着坑能引用
   */
  static class Entry extends WeakReference<ThreadLocal<?>> {
      /** value就是和ThreadLocal绑定的 */
      Object value;
  
      //k：ThreadLocal的引用，被传递给WeakReference的构造方法
      Entry(ThreadLocal<?> k, Object v) {
          super(k);
          value = v;
      }
  }
  //WeakReference构造方法(public class WeakReference<T> extends Reference<T> )
  public WeakReference(T referent) {
      super(referent); //referent：ThreadLocal的引用
  }
  
  //Reference构造方法
  Reference(T referent) {
      this(referent, null);//referent：ThreadLocal的引用
  }
  
  Reference(T referent, ReferenceQueue<? super T> queue) {
      this.referent = referent;
      this.queue = (queue == null) ? ReferenceQueue.NULL : queue;
  }
  ```

- set()

  ```java
  public void set(T value) {
      // 1.获取当前线程（调用者线程）
      Thread t = Thread.currentThread();
      // 2.以当前线程作为key值，去查找对应线程的threadLocals变量，找到对应的map
      ThreadLocalMap map = getMap(t);
      // 3.如果map不为null，就直接添加本地变量，key为当前定义的ThreadLocal变量的this引用，值为添加的本地变量值
      if (map != null)
          map.set(this, value);
      // 4.如果map为null，说明首次添加，需要首先创建出对应的map
      else
          createMap(t, value);
  }
  ```

- get()

  ```java
  public T get() {
      // 1.获取当前线程
      Thread t = Thread.currentThread();
      // 2.获取当前线程的threadLocals变量
      ThreadLocalMap map = getMap(t);
      // 3.如果threadLocals变量不为null，就可以在map中查找到本地变量的值
      if (map != null) {
          ThreadLocalMap.Entry e = map.getEntry(this);
          if (e != null) {
              @SuppressWarnings("unchecked")
              T result = (T)e.value;
              return result;
          }
      }
      // 4.执行到此处，threadLocals为null，调用该更改初始化当前线程的threadLocals变量
      return setInitialValue();
  }
  
  private T setInitialValue() {
      //protected T initialValue() {return null;}
      T value = initialValue();
      // 获取当前线程
      Thread t = Thread.currentThread();
      // 以当前线程作为key值，去查找对应的线程变量，找到对应的map
      ThreadLocalMap map = getMap(t);
      // 如果map不为null，就直接添加本地变量，key为当前线程，值为添加的本地变量值
      if (map != null)
          map.set(this, value);
      // 如果map为null，说明首次添加，需要首先创建出对应的map
      else
          createMap(t, value);
      return value;
  }
  ```

- remove()

  ```java
  public void remove() {
      // 获取当前线程绑定的threadLocals
       ThreadLocalMap m = getMap(Thread.currentThread());
       // 如果map不为null，就移除当前线程中指定ThreadLocal实例的本地变量
       if (m != null)
           m.remove(this);
   }
  ```

- 使用场景

  - 在进行对象夸层传递时，使用ThreadLocal避免多次传递，打破层次间的约束

  - 线程间数据隔离

  - 进行事务操作，储存线程事务信息

  - 数据库连接，Session会话管理

    > Spring框架在事务开始时会给当前线程绑定一个JDBC Connection，在事务整个过程中都是使用该线程绑定的Connection来执行数据库操作，实现了事务的隔离性。这里就是用的ThreadLocal来实现的。

### ThreadLocal内存泄漏

- 不在被使用的对象或变量占用的内存不被回收，导致内存泄漏
- **强引用**在GC时，即便空间不足，抛出OutOfMemoryError，也不会被回收。显示赋值为null可取消强引用
- **弱引用**，只要GC便会回收
- ThreadLocal中key为弱引用，value为强引用，GC时当key被回收，value不会被回收，则会造成内存泄漏
- 当key为null时，调用set()、get()、remove()都会清除value
  - 因此每次使用完ThreadLocal后都调用它的setInitialValue()方法
  - ~~将ThreadLocal变量定义为private static，这样就一直存在ThreadLocal的强引用，也就能保证任何时候都能通过ThreadLocal的弱引用访问到Entry的value值，进而清除~~

### 并发、并行、窜行

- 窜行：依次执行任务
- 并行：互不干扰的同时执行多个任务
- 并发：两个任务彼此干扰，交替执行

### 并发三大特性

- 并发需保证原子性、可见性、有序性才能保证线程安全

- **原子性**：要么所有的指令都执行，要么都不执行。这样才能保证并发操作的安全性和一致性。

- **可见性**：一个线程对共享变量的修改，另外一个线程能够立刻看到，我们称为可见性。

- **有序性**：有序性指的是程序按照代码的先后顺序执行。编译器为了优化性能，有时候会改变程序中语句的先后顺序，但是不会影响最终的执行结果。有序性比较经典的例子就是利用双重检查创建单例对象。

  ```java
  public class Singleton {
    static Singleton instance;
    static Singleton getInstance(){
      if (instance == null) {
        synchronized(Singleton.class) {
          if (instance == null)
            instance = new Singleton();
          }
      }
      return instance;
    }
  }
  ```

### 线程池

### 线程池处理流程

### 线程池中的阻塞队列

### 线程池复用的原理

### spring

### AOP

### IOC

### BeanFactory和ApplicationContext

### spring bean的生命周期

### spring bean 的作用域

### spring 单例bean的线程

### spring 中的设计模式

### spring事务实现

- Spring 事务的本质其实就是数据库对事务的支持和扩展
- 编程式：由程序员编写代码实现
- 申明式：采用@Transactional 注解申明实现，申明式事务管理是建立在 AOP 之上的。Spring会使用AOP的思想，对你的这个方法在执行之前，先去开启事务，执行完毕之后根据方法是否报错，决定回滚或者提交事务。
- 声明式事务最大的优点就是不需要在业务逻辑代码中掺杂事务管理的代码，只需在配置文件中做相关的事务规则声明或通过@Transactional 注解的方式，便可以将事务规则应用到业务逻辑中。
- 声明式事务管理要优于编程式事务管理，这正是 spring 倡导的非侵入式的开发方式，使业务代码不受污染，只要加上注解就可以获得完全的事务支持。唯一不足地方是，最细粒度只能作用到方法级别，无法做到像编程式事务那样可以作用到代码块级别。
- 声明式事务本质是通过 AOP 功能，对方法前后进行拦截，将事务处理的功能编织到拦截的方法中，也就是在目标方法开始之前加入一个事务，在执行完目标方法之后根据执行情况提交或者回滚事务。
- spring中事务的隔离级别
  - ISOLATION_DEFAULT：这是个 PlatfromTransactionManager 默认的隔离级别，使用数据库默认的事务隔离级别。
  - ISOLATION_READ_UNCOMMITTED：读未提交，允许另外一个事务可以看到这个事务未提交的数据。
  - ISOLATION_READ_COMMITTED：读已提交，保证一个事务修改的数据提交后才能被另一事务读取，而且能看到该事务对已有记录的更新。
  - ISOLATION_REPEATABLE_READ：可重复读，保证一个事务修改的数据提交后才能被另一事务读取，但是不能看到该事务对已有记录的更新。
  - ISOLATION_SERIALIZABLE：一个事务在执行的过程中完全看不到其他事务对数据库所做的更新。

### spring事务的传播

- 按照编写代码时定义的传播机制进行传播 **@Transactional(propagation=Propagation.REQUIRED // propagation 枚举值)**
- spring事务的7大传播机制（a.b）
  - PROPAGATION_REQUIRED（spring默认值）：如果a存在一个事务，则b支持当前事务。如果a没有事务则b开启一个新的事务。
  - PROPAGATION_SUPPORTS：如果a存在一个事务，b支持当前事务。如果a没有事务，则b非事务的执行。但是对于事务同步的事务管理器，PROPAGATION_SUPPORTS与不使用事务有少许不同。
  - PROPAGATION_MANDATORY：如果a存在一个事务，b支持当前事务。如果a没有一个活动的事务，则抛出异常。
  - PROPAGATION_REQUIRES_NEW：b总是开启一个新的事务。如果a已经存在事务，则将a的事务挂起。
  - PROPAGATION_NOT_SUPPORTED：b总是非事务地执行，并挂起a存在的任何事务。
  - PROPAGATION_NEVER：b总是非事务地执行，如果a存在一个活动事务，则抛出异常。
  - PROPAGATION_NESTED：如果a有一个活动的事务存在，则b运行在一个嵌套的事务中. 如果没有活动事务, 则按TransactionDefinition.PROPAGATION_REQUIRED 属性执行。

### spring事务失效

[事务失效](https://www.cnblogs.com/ldsweely/p/12160078.html)

- **数据库引擎不支持事务**：MySQL 其 MyISAM 引擎是不支持事务操作的，InnoDB 才是支持事务的引擎。从 MySQL 5.5.5 开始的默认存储引擎是：InnoDB，之前默认的都是：MyISAM
- **没有被 Spring 管理** 
- **方法不是 public 的：**`@Transactional` 只能用于 public 的方法上，否则事务不会失效，如果要用在非 public 方法上，可以开启 `AspectJ` 代理模式。
- **自身调用**：使用this自身调用则不会经过spring代理类，因此不会获取bean对象，AOP不生效，事务失效。
- **异常被吃了**：异常try - catch ，事务发生异常且异常被捕获，因此不会回滚，事务失效。
- **异常类型错误**：默认回滚的异常是：RuntimeException，如果你想触发其他异常的回滚，需要在注解上配置一下**@Transactional(rollbackFor = Exception.class)**
- **数据源没有配置事务管理器**
- **不支持事务**

### bean的自动装配

[资料](https://www.cnblogs.com/zuochengsi-9/p/9047111.html)

> Spring3.0以后的版本中，Bean的自动装配通过autowire参数控制，有以下几种方式：

- byName 根据id/name，根据bean的属性名称进行自动装配。
- byType 根据类名，根据bean的属性类型进行自动装配。

- constructor 根据构造参数，根据bean的构造器参数类型进行自动装配。
- no 人工指定（默认），通过“ref”属性手动设定
- ~~autodetect方法，有默认构造器则使用constructor，没有则使用byType，在3.0版本以后已被遗弃。~~

### Spring、SpringMVC、Spring Boot

[资料](https://blog.51cto.com/u_14622073/2536453)

- **Spring**是一个轻量级的控制反转（IoC）和面向切面（AOP）的容器框架。
- **SpringMVC**是一种基于Spring实现了Web MVC设计模式的请求驱动类型的轻量级Web框架，使用了MVC架构模式的思想，将web层进行职责解耦，并管理应用所需对象的生命周期，为简化日常开发，提供了很大便利。**Spring MVC需要有Spring的架包作为支撑才能跑起来**
- **Spring Boot** 是spring提供的一个快速开发的工具包，简化配置，整合框架，实现**开箱即用，快速启动**。

### SpringMVC工作流程

[资料](https://blog.csdn.net/qq_36761831/article/details/89053314)

1. 用户发送请求至前端控制器DispatcherServlet。
2. DispatcherServlet收到请求调用HandlerMapping处理器映射器。
3. 处理器映射器找到具体的处理器(可以根据xml配置、注解进行查找)，生成处理器对象及处理器拦截器(如果有则生成)一并返回给DispatcherServlet。
4. DispatcherServlet调用HandlerAdapter处理器适配器。
5. HandlerAdapter经过适配调用具体的处理器(Controller，也叫后端控制器)。
6. Controller执行完成返回ModelAndView。
7. HandlerAdapter将controller执行结果ModelAndView返回给DispatcherServlet。
8. DispatcherServlet将ModelAndView传给ViewReslover视图解析器。
9. ViewReslover解析后返回具体View。
10. DispatcherServlet根据View进行渲染视图（即将模型数据填充至视图中）。
11. DispatcherServlet响应用户。

![img](https://images2015.cnblogs.com/blog/249993/201612/249993-20161212142542042-2117679195.jpg)

### SpringMVC主要组件

[资料](https://www.cnblogs.com/mlck/p/14283968.html)

1. **HandlerMapping(处理器映射器)**：主要作用是根据请求的资源uri来查找对应的handler
2. **HandlerAdapter(处理器适配器)**：处理找到的Handler
3. **HandlerExceptionResolver(异常处理器)**：当我们在寻找和处理Handler时难免会出现一些问题(异常),这个时候就需要一个专门来处理异常的角色
4. **ViewResolver(页面渲染处理器)**：根据视图名(String类型)和Locale(语言环境)，获得最终的View类型的视图
5. **RequestToViewNameTranslator(视图名称翻译器)**：当没有ViewName时,从请求中解析获取视图名
6. **LocaleResolver(当前环境处理器)**：协助view的解析。SpringMVC主要有两个地方用到了Locale
   1. ViewResolver视图解析的时候
   2. 用到国际化资源或者主题的时候
7. **ThemeResolver(主题处理器)**：主题处理器用于解析主题,相当于解析系统的整体样式和风格
8. **MultipartResolver(文件处理器)**：用于处理上传请求。处理方法是将普通的request包装成MultipartHttpServletRequest，后者可以直接调用getFile方法获取File，如果上传多个文件，还可以调用getFileMap得到FileName->File结构的Map。此组件中一共有三个方法，作用分别是判断是不是上传请求，将request包装成MultipartHttpServletRequest、处理完后清理上传过程中产生的临时资源。
9. **FlashMapManager(参数传递管理器)**：用于重定向。FlashMap 借助 session 重定向前通过 FlashMapManager将信息放入FlashMap,重定向后 再借助 FlashMapManager 从 session中找到重定向后需要的 FalshMap

### Spring Boot自动配置原理

> @Import + @Configuration + SPring spi
>
> 自动配置类由各个starter提供，使用@Configuration + @Bean定义配置类，放到META-INF/spring.factories下
>
> 使用Spring spi扫描META-INF/spring.factories下的配置类
>
> 使用@Import导入自动配置类



![img](https://img-blog.csdnimg.cn/20200215163555350.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2dvcmdlb3VzdHVkeQ==,size_16,color_FFFFFF,t_70)

### Spring Boot中的Starter

> Starter即一个定义了starter的jar包，置于META-INF/spring.factories下，主要用于自动装配

### 嵌入式服务器

> Spring Boot已经内置了tomcat.jar（此时tomcat即嵌入式服务器），运行main方法时会去启动tomcat，并利用tomcat的spi机制加载SpringMVC。无需程序员去下载配置tomcat，应用也不需要再打war包，然后放到webapp目录下再运行。

### MyBatis的优缺点

- 优点
  1. 基于SQL语句编程，相当灵活，不会对应用程序或者数据库的现有设计造成任何影响，SQL写在XML里，解除sql与程序代码的耦合，便于统一管理；提供XML标签，支持编写动态SQL语句，并可重用。
  2. 与JDBC相比，减少了50%以上的代码量，消除了JDBC大量冗余的代码，不需要手动开关连接。
  3. 很好的与各种数据库兼容（因为MyBatis使用JDBC来连接数据库，所以只要JDBC支持的数据库MyBatis都支持）。
  4. 能够与Spring很好的集成。
  5. 提供映射标签，支持对象与数据库的ORM字段关系映射；提供对象关系映射标签，支持对象关系。
- 缺点
  1. SQL语句的编写工作量较大，尤其当字段多、关联表多时，对开发人员编写SQL语句的功底有一定要求。
  2. SQL语句依赖于数据库，导致数据库移植性差，不能随意更换数据库。

### MyBatis和Hibernate

- 相同点
  1. Hibernate与MyBatis都可以是通过SessionFactoryBuider由XML配置文件生成SessionFactory，然后由SessionFactory 生成Session，最后由Session来开启执行事务和SQL语句。其中SessionFactoryBuider，SessionFactory，Session的生命周期都是差不多的。
  2. Hibernate和MyBatis都支持JDBC和JTA事务处理。

- 不同点
  1. **Hibernate是全自动，而MyBatis是半自动**。Hibernate完全可以通过对象关系模型实现对数据库的操作，拥有完整的JavaBean对象与数据库的映射结构来自动生成sql。而MyBatis仅有基本的字段映射，对象数据以及对象实际关系仍然需要通过手写sql来实现和管理。
  2. **Hibernate数据库移植性远大于MyBatis**。Hibernate通过它强大的映射结构和hql语言，大大降低了对象与数据库（Oracle、MySQL等）的耦合性，而MyBatis由于需要手写sql，因此与数据库的耦合性直接取决于程序员写sql的方法，如果sql不具通用性而用了很多某数据库特性的sql语句的话，移植性也会随之降低很多，成本很高。
  3. **Hibernate拥有完整的日志系统，MyBatis则欠缺一些**。Hibernate日志系统非常健全，涉及广泛，包括：sql记录、关系异常、优化警告、缓存提示、脏数据警告等；而MyBatis则除了基本记录功能外，功能薄弱很多。
  4. **MyBatis相比Hibernate需要关心很多细节**。**Hibernate配置要比MyBatis复杂的多，学习成本也比MyBatis高**。但也正因为MyBatis使用简单，才导致它要比Hibernate关心很多技术细节。MyBatis由于不用考虑很多细节，开发模式上与传统JDBC区别很小，因此很容易上手并开发项目，但忽略细节会导致项目前期bug较多，因而开发出相对稳定的软件很慢，而开发出软件却很快。Hibernate则正好与之相反。但是如果使用Hibernate很熟练的话，实际上开发效率丝毫不差于甚至超越MyBatis。
  5. **sql直接优化上，MyBatis要比Hibernate方便很多**。由于MyBatis的sql都是写在xml里，因此优化sql比Hibernate方便很多。而Hibernate的sql很多都是自动生成的，无法直接维护sql；虽有hql，但功能还是不及sql强大，见到报表等变态需求时，hql也歇菜，也就是说hql是有局限的；Hibernate虽然也支持原生sql，但开发模式上却与orm不同，需要转换思维，因此使用上不是非常方便。总之写sql的灵活度上Hibernate不及MyBatis。
  6. **缓存机制上，Hibernate要比MyBatis更好一些**。MyBatis的二级缓存配置都是在每个具体的表-对象映射中进行详细配置，这样针对不同的表可以自定义不同的缓存机制。并且Mybatis可以在命名空间中共享相同的缓存配置和实例，通过Cache-ref来实现。而Hibernate对查询对象有着良好的管理机制，用户无需关心SQL。所以在使用二级缓存时如果出现脏数据，系统会报出错误并提示。

### #{}与${}的区别

- \#{}是预编译处理、占位符，${}是字符串替换、拼接符。
- Mybatis 在处理#{}时，会将 sql 中的#{}替换为?号，调用 PreparedStatement 的 set 方法来赋值。
- 因此使用#{}可以有效的防止 SQL 注入，提高系统安全性。

