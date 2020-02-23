##### 1.下列哪些语句关于内存回收的说明是正确的? (  )

A 程序员必须创建一个线程来释放内存
 B 内存回收程序负责释放无用内存
 C 内存回收程序允许程序员直接释放内存
 D 内存回收程序可以在指定的时间释放内存对象
 答案 B

A、JVM一旦启动，就会创建一个守护线程来监测是否需要有对象内存被释放。
 C、无法直接释放。
 D、不可以指定时间，System.gc()，只是提醒JVM可以进行一次Full GC，但是什么时候真正执行，还是不知道的。

![img](https:////upload-images.jianshu.io/upload_images/1824809-324e6bd6911a3e33.png?imageMogr2/auto-orient/strip|imageView2/2/w/1199/format/webp)

##### 2.Java程序中的类名称必须与存放该类的文件名相同。

A 对
 B 错

答案：B
 声明为public类型的类名必须与文件名相同，默认权限的可以不同
 并且内部类的类名一般与文件名不同

##### 3.ArrayList list = new ArrayList(20);中的list扩充几次

A 0
 B 1
 C 2
 D 3

答案

本题需要注意的是：调用的是带参的构造方法。

另外也要注意：

1、如果不指定容量，而初始大小为10，动态增长时，增长到当前容量的1.5倍。

2、与之类似的还有，HashMap的初始大小为16，增长时，直接容量翻番，如源代码。



```csharp
void addEntry(int hash, K key, V value, int bucketIndex) {
    if ((size >= threshold) && (null != table[bucketIndex])) {
        resize(2 * table.length);
        hash = (null != key) ? hash(key) : 0;
        bucketIndex = indexFor(hash, table.length);
    }
 
    createEntry(hash, key, value, bucketIndex);
}
```

3、Vector的初始大小为10，如果没有指定每次增长的大小，则默认是翻倍增长。

##### 4.关于匿名内部类叙述正确的是？ ( )

A 匿名内部类可以继承一个基类，不可以实现一个接口
 B 匿名内部类不可以定义构造器
 C 匿名内部类不能用于形参
 D 以上说法都不正确

答案 B

匿名内部类的创建格式为：



```cpp
new 父类构造器（参数列表）|实现接口（）{
//匿名内部类的类体实现
}
```

1. 使用匿名内部类时，必须继承一个类或实现一个接口
2. 匿名内部类由于没有名字，因此不能定义构造函数
3. 匿名内部类中不能含有静态成员变量和静态方法

##### 5.以下程序的输出结果为



```csharp
class Base{
    public Base(String s){
        System.out.print("B");
    }
}
public class Derived extends Base{
    public Derived (String s) {
        System.out.print("D");
    }
    public static void main(String[] args){
        new Derived("C");
    }
}
```

A BD
 B DB
 C C
 D 编译错误
 答案 D

在调用子类构造器之前，会先调用父类构造器，当子类构造器中没有使用"super(参数或无参数)"指定调用父类构造器时，是默认调用父类的无参构造器，如果父类中包含有参构造器，却没有无参构造器，则在子类构造器中一定要使用“super(参数)”指定调用父类的有参构造器，不然就会报错。

##### 6.下列说法正确的是（）？

A 对于局部内部类，只有在方法的局部变量被标记为final或局部变量是effctively final的，内部类才能使用它们
 B 成员内部类位于外部类内部，可以直接调用外部类的所有方法（静态方法和非静态方法）
 C 由于匿名内部类只能用在方法内部，所以匿名内部类的用法与局部内部类是一致的
 D 静态内部类可以访问外部类的成员变量
 答案 AB



![img](https:////upload-images.jianshu.io/upload_images/1824809-0c37ff4a8fc3a9d2.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

image.png

##### 7.关于下面的程序Test.java说法正确的是(    )。



```csharp
public class Test {
    static String x="1";
    static int y=1;
    public static void main(String args[]) {
        static int z=2;
        System.out.println(x+y+z);
    }
}
```

A 3
 B 112
 C 13
 D 程序有编译错误
 答案 D
 被static修饰的变量称为静态变量，静态变量属于整个类，而局部变量属于方法，只在该方法内有效，所以static不能修饰局部变量

##### 8.关于访问权限说法正确的是 ？ (    )

A 类定义前面可以修饰public,protected和private
 B 内部类前面可以修饰public,protected和private
 C 局部内部类前面可以修饰public,protected和private
 D 以上说法都不正确
 答案 B
 对于外部类来说，只有两种修饰，public和默认（default），因为外部类放在包中，只有两种可能，包可见和包不可见。
 对于内部类来说，可以有所有的修饰，因为内部类放在外部类中，与成员变量的地位一致，所以有四种可能。

##### 9.Servlet的生命周期可以分为初始化阶段，运行阶段和销毁阶段三个阶段，以下过程属于初始化阶段是（）。

A 加载Servlet类及.class对应的数据
 B 创建servletRequest和servletResponse对象
 C 创建ServletConfig对象
 D 创建Servlet对象
 答案 A C D



![img](https:////upload-images.jianshu.io/upload_images/1824809-c28709a44657ae05.png?imageMogr2/auto-orient/strip|imageView2/2/w/1022/format/webp)

image.png

Servlet的生命周期可以分为初始化阶段，运行阶段和销毁阶段三个阶段，以下过程属于初始化阶段是

1. 加载Servlet类及.class对应的数据
2. 创建ServletConfig对象
3. 创建Servlet对象
    每一次请求来到容器时，会产生HttpServletRequest与HttpServlceResponse对象，并在调用service()方法时当做参数传入。
    在WEB容器启动后，会读取Servlet设置信息，将Servlet类加载并实例化，并为每个Servlet设置信息产生一个ServletConfig对象，而后调用Servlet接口的init()方法，并将产生的ServletConfig对象当作参数传入。

##### 10.下列关于Java并发的说法中正确的是（）

A CopyOnWriteArrayList适用于写多读少的并发场景
 B ReadWriteLock适用于读多写少的并发场景
 C ConcurrentHashMap的写操作不需要加锁，读操作需要加锁
 D 只要在定义int类型的成员变量i的时候加上volatile关键字，那么多线程并发执行i++这样的操作的时候就是线程安全的了

答案 B

A，CopyOnWriteArrayList适用于**写少读多**的并发场景

B，ReadWriteLock即为读写锁，他要求写与写之间互斥，读与写之间互斥，

读与读之间可以并发执行。在读多写少的情况下可以提高效率

C，ConcurrentHashMap是同步的HashMap，读写都加锁

D，volatile只保证多线程操作的可见性，不保证原子性

##### 9.在运行时，由java解释器自动引入，而不用import语句引入的包是()。

A java.lang
 B java.system
 C java.io
 D java.util

答案 A
 java.lang包是java语言的核心包，lang是language的缩写
 java.lang包定义了一些基本的类型，包括Integer,String之类的，是java程序必备的包，有解释器自动引入，无需手动导入

##### 10.关于java编译和运行命令叙述不正确的是？  ( )

A 运行“java Scut.class”
 B 运行“java Scut”
 C 运行“javac Scut.java”的输出文件是Scut.class
 D java这个命令的运行对象是Scut.class

答案 A
 A  错误 运行命令是 java + 你的 Java 程序的名字但是不加后缀 所以这道题错在多了 .class这个后缀
 B  正确
 C  javac 是编译命令，后跟 你的 Java 程序名字加后缀，也就是 YourClassName.java 所以答案正确
 D JVM （Java 虚拟机）运行的是编译后的字节码文件（以.class为后缀的文件），也就是 YourClassName.class 所以答案正确

##### 11.假设如下代码中，若t1线程在t2线程启动之前已经完成启动。代码的输出是（）



```java
public static void main(String[]args)throws Exception {
    final Object obj = new Object();
    Thread t1 = new Thread() {
        public void run() {
            synchronized (obj) {
                try {
                    obj.wait();
                    System.out.println("Thread 1 wake up.");
                } catch (InterruptedException e) {
                }
            }
        }
    };
    t1.start();
    Thread.sleep(1000);//We assume thread 1 must start up within 1 sec.
    Thread t2 = new Thread() {
        public void run() {
            synchronized (obj) {
                obj.notifyAll();
                System.out.println("Thread 2 sent notify.");
            }
        }
    };
    t2.start();
}
```

A
 Thread 1 wake up
 Thread 2 sent notify.
 B
 Thread 2 sent notify.
 Thread 1 wake up
 C A、B皆有可能
 D  程序无输出卡死

答案 B
 执行obj.wait();时已释放了锁，所以t2可以再次获得锁，然后发消息通知t1执行，但这时t2还没有释放锁，所以肯定是执行t2，然后释放锁，之后t1才有机会执行。

##### 12.下列说法正确的有：（）

A class中的constructor不可省略
 B constructor必须与class同名，但方法不能与class同名
 C constructor在一个对象被new 时执行
 D 一个class只能定义一个constructor

答案 C

A.constructor可以省略会有一个默认的无参构造方法

B. 方法可以和类名同名的，和构造方法唯一的区别就是，构造方法没有返回值。

D.一个class可以有多个重在的构造方法

##### 13.观察以下代码：



```java
class Car extends Vehicle
{
    public static void main (String[] args)
    {
        new  Car(). run();
    }
    private final void run()
    {
        System. out. println ("Car");
    }
}
class Vehicle
{
    private final void run()
    {
        System. out. println("Vehicle");
    }
}
```

下列哪些针对代码运行结果的描述是正确的？
 A Car
 B Vehicle
 C Compiler error at line 3
 D Compiler error at line 5
 E Exception thrown at runtime
 答案 A

首先final声明的方法是不能被覆盖的，但是这里并不错误，因为方法是private的，也就是子类没有继承父类的run方法，因此子类的run方法跟父类的run方法无关，并不是覆盖。new Car().run()也是调用子类的run方法。

##### 14.关于JAVA的垃圾回收机制，下面哪些结论是正确？

A 程序可以任意指定释放内存的时间
 B JAVA程序不能依赖于垃圾回收的时间或者顺序
 C 程序可明确地标识某个局部变量的引用不再被使用
 D 程序可以显式地立即释放对象占有的内存
 答案 B
 GC是完全自动的，不能确定具体的回收时间

##### 15.在开发中使用泛型取代非泛型的数据类型（比如用ArrayList<String>取代ArrayList），程序的运行时性能会变得更好。

A 对
 B 错
 答案 B
 泛型仅仅是java的一颗语法糖，它不会影响java虚拟机生成的汇编代码，在编译阶段，虚拟机就会把泛型的类型擦除，还原成没有泛型的代码，顶多编译速度稍微慢一些，执行速度是完全没有什么区别的。

##### 16.对于文件的描述正确的是（ ）

A 文本文件是以“.txt”为后缀名的文件，其他后缀名的文件是二进制文件。
 B File类是Java中对文件进行读写操作的基本类。
 C 无论文本文件还是二进制文件，读到文件末尾都会抛出EOFException异常。
 D Java中对于文本文件和二进制文件，都可以当作二进制文件进行操作。
 答案 D
 A.文件分为文本文件和二进制文件，计算机只认识二进制，所以实际上都是二进制的不同解释方式。文本文件是以不同编码格式显示的字符，例如Ascii、Unicode等，window中文本文件的后缀名有".txt",".log",各种编程语言的源码文件等；二进制文件就是用文本文档打开是看不懂乱码，只要能用文本打开的文件都可以算是文本文件，只是显示的结果不是你想要的，二进制文件只有用特殊的应用才能读懂的文件，例如".png",".bmp"等，计算机中大部分的文件还是二进制文件。
 B.File类是对文件整体或者文件属性操作的类，例如创建文件、删除文件、查看文件是否存在等功能，不能操作文件内容；文件内容是用IO流操作的。
 C.当输入过程中意外到达文件或流的末尾时，抛出EOFException异常,正常情况下读取到文件末尾时，返回一个特殊值表示文件读取完成，例如read()返回-1表示文件读取完成。
 D.上面A选项已经说了，不论是文本文件还是二进制文件，在计算机中都是以二进制形式存储的，所以都当做二进制文件读取。

##### 17.以下代码的输出结果是？



```csharp
public class B
{
    public static B t1 = new B();
    public static B t2 = new B();
    {
        System.out.println("构造块");
    }
    static
    {
        System.out.println("静态块");
    }
    public static void main(String[] args)
    {
        B t = new B();
    }
}
```

A 静态块 构造块 构造块 构造块
 B 构造块 静态块 构造块 构造块
 C 构造块 构造块 静态块 构造块
 D 构造块 构造块 构造块 静态块
 答案 C

开始时JVM加载B.class，对所有的静态成员进行声明，t1 t2被初始化为默认值，为null，又因为t1 t2需要被显式初始化，所以对t1进行显式初始化，初始化代码块→构造函数（没有就是调用默认的构造函数），咦！静态代码块咋不初始化？因为在开始时已经对static部分进行了初始化，虽然只对static变量进行了初始化，但在初始化t1时也不会再执行static块了，因为JVM认为这是第二次加载类B了，所以static会在t1初始化时被忽略掉，所以直接初始化非static部分，也就是构造块部分（输出''构造块''）接着构造函数（无输出）。接着对t2进行初始化过程同t1相同（输出'构造块'），此时就对所有的static变量都完成了初始化，接着就执行static块部分（输出'静态块'），接着执行，main方法，同样也，new了对象，调用构造函数输出（'构造块'）

##### 18.下面有关java类加载器，说法正确的是？

A 引导类加载器（bootstrap class loader）：它用来加载 Java 的核心库，是用原生代码来实现的
 B 扩展类加载器（extensions class loader）：它用来加载 Java 的扩展库。
 C 系统类加载器（system class loader）：它根据 Java 应用的类路径（CLASSPATH）来加载 Java 类
 D tomcat为每个App创建一个Loader，里面保存着此WebApp的ClassLoader。需要加载WebApp下的类时，就取出ClassLoader来使用
 答案 A B C D

##### 19.JDK提供的用于并发编程的同步器有哪些？

A Semaphore
 B CyclicBarrier
 C CountDownLatch
 D Counter

答案：ABC
 A，Java 并发库 的Semaphore 可以很轻松完成信号量控制，Semaphore可以控制某个资源可被同时访问的个数，通过 acquire() 获取一个许可，如果没有就等待，而 release() 释放一个许可。
 B，CyclicBarrier 主要的方法就是一个：await()。await() 方法没被调用一次，计数便会减少1，并阻塞住当前线程。当计数减至0时，阻塞解除，所有在此 CyclicBarrier 上面阻塞的线程开始运行。
 C，直译过来就是倒计数(CountDown)门闩(Latch)。倒计数不用说，门闩的意思顾名思义就是阻止前进。在这里就是指 CountDownLatch.await() 方法在倒计数为0之前会阻塞当前线程。
 D，Counter不是并发编程的同步器

##### 20.有关线程的叙述正确的是()

A 可以获得对任何对象的互斥锁定
 B 通过继承Thread类或实现Runnable接口，可以获得对类中方法的互斥锁定
 C 线程通过使用synchronized关键字可获得对象的互斥锁定
 D 线程调度算法是平台独立的
 答案 C D

线程调度分为协同式调度和抢占式调度，Java使用的是抢占式调度，也就是每个线程将由操作系统来分配执行时间，线程的切换不由线程本身来决定（协同式调度）。这就是平台独立的原因。
 D正确

