##### 1.若所用变量都已正确定义，以下选项中，非法的表达式是（）

A a!= 4||b==1
 B ’a’ % 3
 C ’a’ = 1/3
 D ’A’ + 32
 答案 C
 'a'是个常数，不能赋值

##### 2.下列关于异常处理的描述中，错误的是()。

A 程序运行时异常由Java虚拟机自动进行处理
 B 使用try-catch-finally语句捕获异常
 C 可使用throw语句抛出异常
 D 捕获到的异常只能在当前方法中处理，不能在其他方法中处理
 答案 D
 捕获到的异常不仅可以在当前方法中处理，还可以将异常抛给调用它的上一级方法来处理。

##### 3.对于abstract声明的类，下面说法正确的是

A 可以实例化
 B 不可以被继承
 C 子类为abstract
 D 只能被继承
 E 可以被抽象类继承
 答案 E

D选项 抽象类可以直接被调用



```kotlin
public abstract class FanLi {

public abstract void nouse();取消发表

public static void main(String[] args) {

FanLi.fun();

}

public static void fun() {

System.out.println("我是反例");

}

}
```

##### 4.对于下面这段代码，以下说法正确的是：



```csharp
public class Test
{
    public int x;
    public static void main(String []args)
    {
        System. out. println("Value is" + x);
    }
}
```

A 程序会打出 "Value is 0"
 B 程序会抛出 NullPointerException
 C 非静态变量不能够被静态方法引用
 D 编译器会抛出 "possible reference before assignment"的错误
 答案 C
 当类加载时，static静态方法随着类加载而初始化，此时实例对象还未被创建，但是非静态成员变量需要等到实例对象创建才会被初始化，故无法被引用。

##### 5.阅读如下代码。 请问，对语句行 test.hello(). 描述正确的有（）



```csharp
package NowCoder;
class Test {
    public static void hello() {
        System.out.println("hello");
    }
}
public class MyApplication {
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Test test=null;
        test.hello();
    }
}
```

A 能编译通过，并正确运行
 B 因为使用了未初始化的变量，所以不能编译通过
 C 以错误的方式访问了静态方法
 D 能编译通过，但因变量为null，不能正常运行
 答案 A
 因为Test类的hello方法是静态的，所以是属于类的，当实例化该类的时候，静态会被优先加载而且只加载一次，所以不受实例化new Test();影响，只要是使用到了Test类，都会加载静态hello方法！
 值得一说的是有些人以为是空指针，这里你们所说的空指针必须是去引用堆对象才会有空指针
 而这个hello是static类型的，人家static的方法本身就没有指针，所以当然不会有空指针

##### 6.下列Java代码中的变量a、b、c分别在内存的____存储区存放。

A 堆区、栈区、栈区
 B 堆区、堆区、栈区
 C 静态区、栈区、堆区
 D 静态区、栈区、栈区
 答案 A

堆区：只存放类对象，线程共享；
 方法区：又叫静态存储区，存放class文件和静态数据，线程共享;
 栈区：存放方法局部变量，基本类型变量区、执行环境上下文、操作指令区，线程不共享;

### **成员变量和局部变量的区别**



```undefined
   成员变量：

      ①成员变量定义在类中，在整个类中都可以被访问。

      ②成员变量随着对象的建立而建立，随着对象的消失而消失，存在于对象所在的堆内存中。

      ③成员变量有默认初始化值。

  局部变量：

      ①局部变量只定义在局部范围内，如：函数内，语句内等，只在所属的区域有效。

      ②局部变量存在于栈内存中，作用的范围结束，变量空间会自动释放。

      ③局部变量没有默认初始化值
```

##### 7.局部内部类可以用哪些修饰符修饰？

A public
 B private
 C abstract
 D final
 答案 C D



![img](https:////upload-images.jianshu.io/upload_images/1824809-09684dc1ac9a6f57.png?imageMogr2/auto-orient/strip|imageView2/2/w/474/format/webp)

image.png

局部内部类是放在代码块或方法中的，不能有访问控制修饰符，且不能用static修饰

##### 7.以下 _____ 不是 Object 类的方法

A clone（）
 B finalize()
 C toString()
 D hasNext()
 答案 D



![img](https:////upload-images.jianshu.io/upload_images/1824809-77f8a40c26735195.png?imageMogr2/auto-orient/strip|imageView2/2/w/950/format/webp)

##### 8.的输出是？



```csharp
class Foo {
    final int i;
    int j;
    public void doSomething() {
        System.out.println(++j + i);
    }
}
```

A 0
 B 1
 C 2
 D 不能执行，因为编译有错
 答案 D
 类的final成员变量必须满足以下其中一个条件
 1、在构造函数中赋值
 2、初始化赋值

##### 9.对于构造方法，下列叙述正确的是（ ）。

A 构造方法的优先级一般比代码块低。
 B 构造方法的返回类型只能是void型。
 C 构造方法的主要作用是完成对类的对象的初始化工作。
 D 一般在创建新对象时，系统会自动调用构造方法。
 答案 A C D
 A：静态成员变量或静态代码块>main方法>非静态成员变量或非静态代码块>构造方法

##### 10.关于访问权限说法正确 的是 ？ ( )

A 外部类前面可以修饰public,protected和private
 B 成员内部类前面可以修饰public,protected和private
 C 局部内部类前面可以修饰public,protected和private
 D 以上说法都不正确
 答案 B

外部类，最大的类，修饰符有public(表示该类在项目所有类中可以被导入），default(该类只能在同一个package中使用）,abstract,final

可以把局部内部类当做一个局部变量，所以它是不需要加任何修饰符的

局部内部类前不能用修饰符public和private,protected

内部类就随意了。

##### 11.下面有关java classloader说法错误的是?

A Java默认提供的三个ClassLoader是BootStrap ClassLoader，Extension ClassLoader，App ClassLoader
 B ClassLoader使用的是双亲委托模型来搜索类的
 C JVM在判定两个class是否相同时，只用判断类名相同即可，和类加载器无关
 D ClassLoader就是用来动态加载class文件到内存当中用的
 答案 C
 JVM在判定两个class是否相同时，不仅要判断两个类名是否相同，而且要判断是否由同一个类加载器实例加载的。

**在JVM中，一个类用其全限定类名和其类加载器作为唯一标识，**

**如果在pg包下，有一个Person类，classloade k1 、** **classloade k2分别加载Person类**

**则** **Person类在JVM中对应的Class对象为** **（** **Person，pg，k1** **）与** **（** **Person，pg，k2** **）**

**是不同的**

##### 12.下面有关JVM内存，说法错误的是？

A 程序计数器是一个比较小的内存区域，用于指示当前线程所执行的字节码执行到了第几行，是线程隔离的
 B Java方法执行内存模型，用于存储局部变量，操作数栈，动态链接，方法出口等信息，是线程隔离的
 C 方法区用于存储JVM加载的类信息、常量、静态变量、即时编译器编译后的代码等数据，是线程隔离的
 D 原则上讲，所有的对象都在堆区上分配内存，是线程之间共享的

答案 C
 运行时数据区包括：虚拟机栈区，堆区，方法区，本地方法栈，程序计数器

虚拟机栈区 ：也就是我们常说的栈区，线程私有，存放基本类型，对象的引用和 returnAddress ，在编译期间完成分配。

堆区 ， JAVA 堆，也称 GC 堆，所有线程共享，存放对象的实例和数组， JAVA 堆是垃圾收集器管理的主要区域。

方法区 ：所有线程共享，存储已被虚拟机加载的类信息，常量，静态变量，即时编译器编译后的代码等数据。这个区域的内存回收目标主要是针对常量池的对象的回收和对类型的卸载。

程序计数器 ：线程私有，每个线程都有自己独立的程序计数器，用来指示下一条指令的地址。

##### 13.以下不是修饰符final的作用的是( )。

A 修饰常量
 B 修饰不可被继承的类
 C 修饰不可变类
 D 修饰不可覆盖的方法
 答案 C
 final的作用：
 \1. 修饰变量，使用final修饰基本类型的变量，一旦对该变量赋值之后，就不能重新赋值了。但是对于引用类型变量，他保存的只是引用，final只能保证引用类型变量所引用的地址不改变，但不保证这个对象不改变，这个对象完全可以发生改变。
 \2. 修饰方法，方法不可被重写，但是还是可以重载
 \3. 修饰类，类不可继承。

不可变类，说的是一个类一旦被实例化，就不可改变自身的状态。常见的比如String和基本数据类型的包装类，对于这种不可变类，一旦在进行引用传递的时候，形参一开始就和实际参数指向的不是一个地址，所以在方法中对形参的改变，并不会影响实际参数。

##### 14.instanceof运算符能够用来判断一个对象是否为:

A 一个类的实例
 B 一个实现指定接口的类的实例
 C 一个子类的实例
 D 全部正确
 答案 D

##### 15.当编译并运行下面程序时会发生什么结果（）



```java
public class Bground extends Thread{
    public static void main(String argv[]){
        Bground b = new Bground();
        b.run();
    }
    public void start(){
        for(int i=0;i<10;i++){
            System.out.println("Value of i = "+i);
        }
    }
}
```

A 编译错误，指明run方法没有定义
 B 运行错误，Threadrun方法没有定义
 C 编译通过并输出0到9
 D 编译通过，但无输出
 答案 D
 对于线程而言，start是让线程从new变成runnable。run方法才是执行体的入口。
 但是在Thread中，run方法是个空方法，没有具体实现。
 Bground继承了Thread，但是没有重写run方法，那么调用run方法肯定是无输出。

##### 16.下列代码执行结果为（）



```csharp
public static void main(String args[])throws InterruptedException{
            Thread t=new Thread(new Runnable() {
                public void run() {
                    try {
                        Thread.sleep(2000);
                    } catch (InterruptedException e) {
                        throw new RuntimeException(e);
                    }
                    System.out.print("2");
                }
            });
            t.start();
             
            t.join();
            System.out.print("1");
        }
```

A 21
 B 12
 C 可能为12，也可能为21
 D 以上答案都不对
 答案 A
 join()的作用是：“等待该线程终止”，这里需要理解的就是该线程是指的主线程等待子线程的终止。也就是在子线程调用了join()方法后面的代码，只有等到子线程结束了才能执行。



```csharp
t.join();      //使调用线程 t 在此之前执行完毕。 
t.join(1000);  //等待 t 线程，等待时间是1000毫秒
```

##### 17.下列关于管道（Pipe）通信的叙述中，正确的是（）？

A 进程对管道进行读操作和写操作都可能被阻塞
 B 一个管道只能有一个进程或一个写进程对其操作
 C 一个管道可实现双向数据传输
 D 管道的容量仅受磁盘容量大小限制
 答案 A
 A.正确，因为管道为空，读操作会被阻塞；管道满了，写操作会被阻塞
 B.可以有多个进程对其读；也可以有多个进程写，只不过不能同时写。并且题目没有说“同时”，B不对
 C.匿名管道只能单向；命名管道可以双向；所以C过于绝对
 D.管道是内存中的，所以D不对

##### 18.以下代码执行的结果是多少（）？



```php
        public class Demo {
    public static void main(String[] args) {
        Collection<?>[] collections = 
{new HashSet<String>(), new ArrayList<String>(), new HashMap<String, String>().values()};
                Super subToSuper = new Sub();
                for(Collection<?> collection: collections) {
    System.out.println(subToSuper.getType(collection));
}
}
abstract static class Super {
    public static String getType(Collection<?> collection) {
        return “Super:collection”;
}
public static String getType(List<?> list) {
        return “Super:list”;
}
public String getType(ArrayList<?> list) {
        return “Super:arrayList”;
}
public static String getType(Set<?> set) {
        return “Super:set”;
}
public String getType(HashSet<?> set) {
        return “Super:hashSet”;
}
}
static class Sub extends Super {
    public static String getType(Collection<?> collection) {
            return "Sub"; }
}
}
```

A
 Sub:collection
 Sub:collection
 Sub:collection
 B
 Sub:hashSet
 Sub:arrayList
 Sub:collection
 C
 Super:collection
 Super:collection
 Super:collection
 D
 Super:hashSet
 Super:arrayList
 Super:collection

答案 C

这是静态分派的过程，在编译时已经决定了使用super的方法，因为subToSuper 是指super对象，可是为什么会选择collection呢，for循环出来他们实际上指的是collection对象表示的，即类似于Collection    col = new  HashSet<>();这样传入方法getType（）中的参数就是col，左边是静态类型，右边是实际类型。由于重载实际上是使用静态分派的，重载时是通过参数的静态类型而不是实际类型作为判定依据的。



```csharp
public class A {
    public static String staticStr = "A's static field"; 
    public String nonStaticStr = "A's nonstatic field"; 
    public static void staticMethod(){ 
        System.out.println("A's static method"); 
    } 
    public void nonStaticMethod(){ 
        System.out.println("A's nonstatic method"); 
    } 
} 
public class B extends A{
    public static String staticStr = "B's static field"; 
    public String nonStaticStr = "B's nonstatic field"; 
    public static void staticMethod(){ 
        System.out.println("B's static method"); 
    } 
}
public class C extends A{
   
}
public class Test { 
   
    public static void main(String[] args) { 
        C c = new C(); 
        System.out.println(c.nonStaticStr);  //A's nonstatic field
        System.out.println(c.staticStr);  //A's static field
        c.staticMethod(); //A's static method
        
        System.out.println("-------------------------------"); 
           
        A c1 = new C(); 
        System.out.println(c1.nonStaticStr);  //A's nonstatic field
        System.out.println(c1.staticStr);  //A's static field
        c1.staticMethod(); //A's static method
          
        // 以上这说明java中静态属性和静态方法可以被继承
         
        System.out.println("-------------------------------"); 
        B b = new B(); 
        System.out.println(b.nonStaticStr); // B's nonstatic field
        System.out.println(b.staticStr);   //B's static field
        b.staticMethod();  //B's static method
         
        System.out.println("-------------------------------"); 
        A b1 = new B(); 
        System.out.println(b1.nonStaticStr);  //A's nonstatic field
        System.out.println(b1.staticStr);  //A's static field
        b1.staticMethod(); //A's static method
        //b1.nonStaticStr  输出的是父类的非静态属性，说明非静态属性不可以被重写，不能实现多态
        //b1.staticStr     输出的是父类的静态属性，说明静态属性不可以被重写，不能实现多态
        //b1.staticMethod()输出的是父类A的静态方法，不是子类B改写后的，所以没有实现多态
         
         
        //结论是：静态属性和静态方法只是可以继承没有表现出多态性。
        //因为静态方法和静态属性没有采用动态绑定。具体表现就是，
        //将子类实例向上转型则会调用到基类中的静态方法和属性，
        //不转型就调用子类自身的静态方法和属性。
        //编译器不推荐通过实例去调用静态方法和属性，因为这种调用方式容易造成混淆。
         
        //实际上，在Java的规范中，Java对于类的方法和属性采用了两种完全不同的处理机制：
        //对于方法，使用重载机制实现了多态性；对于属性，使用的是同名属性隐藏机制。
        //所谓的同名属性隐藏机制是指：在具有父子关系的两个类中，
        //子类中相同名字的属性会使得从父类中继承过来的同名属性变得不可见，
        //不管类型是否一致，名称一致的两个属性就是同名属性。
        //在子类中，无法简单地通过属性名称来获取父类中的属性，
        //而是必须通过父类名称加属性名称(super.变量名)的方法才可以访问父类中的该属性。
        //一般而言，为了代码容易阅读，极其不建议在父类和子类中使用同名属性。
    } 
   
}
```

##### 19.关于 JAVA 堆,下面说法错误的是()

A 所有类的实例和数组都是在堆上分配内存的
 B 对象所占的堆内存是由自动内存管理系统回收
 C 堆内存由存活和死亡的对象,空闲碎片区组成
 D 数组是分配在栈中的
 答案 D

把内存分成两种，一种叫做栈内存，一种叫做堆内存。

对象存储在堆内存，引用变量存储在栈内存。栈内存指向堆内存。
 数组是一种对象。

##### 20.下面有关java内存模型的描述，说法错误的是？

A JMM通过控制主内存与每个线程的本地内存之间的交互，来为java程序员提供内存可见性保证
 B “synchronized” — 保证在块开始时都同步主内存的值到工作内存，而块结束时将变量同步回主内存
 C “volatile” — 保证修饰后在对变量读写前都会与主内存更新。
 D 如果在一个线程构造了一个不可变对象之后（对象仅包含final字段），就可以保证了这个对象被其他线程正确的查看
 答案 D



```java
public class FinalExample{
    final int i;
    static FinalExample obj;
    public FinalExample(){
        i=1;//(1)
        obj=this;//(2)
             //(1),(2)可能被重排序
    }
    //线程1
    public static void writer(){
        new FinalExample();
    }
    //线程2
    public static void reader(){
        if(obj !=null){
            int temp =obj.i;   
        }
    }
}
```

由于（1），（2）可能被重排序，当线程1开始执行，被构造的对象的引用会在构造函数内溢出，然后线程2开始执行就访问到了还未赋值的final 变量 i, 最后线程1才在构造函数内部给 i 赋值。这就错误的查看了。

##### 21.下列关于java并发的说法中正确的是：

A copyonwritearraylist适用于写多读少的并发场景
 B readwritelock适用于读多写少的并发场景
 C concurrenthashmap的写操作不需要加锁，读操作需要加锁
 D 只要在定义int类型的成员变量i的时候加上volatile关键字，那么多线程并发执行i++这样的操作的时候就是线程安全的了
 答案 B

**1.CopyOnWirteArrayList  ，JUC下线程安全的ArrayList，适用于写少读多的并发场景。下面放一段源码中的定义**



```php
/** The lock protecting all mutators */

final transient ReentrantLock lock = new  ReentrantLock();

/** The array, accessed only via getArray/setArray. */

private transient volatile Object[] array;
```

**根据源码，我们发现，引入了可重入的读写锁和volatile修饰的array，transient是为了反序列化，volatile是为了保证可见性和禁止指令重排序。**

**在进行读取数据的时候，可以多个线程获取数组。但是写入和修改数组时，必须要拿到数组中的可重入锁。所以适合读多写少**

**2.ReadWriteLock  即为读写锁，要求写与写之间互斥，读与写之间互斥，读与读之间可以并发执行，在读多写少的情况下可以提高效率。**

**3.ConcurrentHashMap是同步的HashMap，读写都加锁。**

**4.volatile只保证多线程操作的可见性，不保证原子性。只有synchronized才保证了原子性和可见性。**

##### 22.以下哪几种方式可用来实现线程间通知和唤醒：( )

A Object.wait/notify/notifyAll
 B ReentrantLock.wait/notify/notifyAll
 C Condition.await/signal/signalAll
 D Thread.wait/notify/notifyAll

答案 A C
 wait()、notify()和notifyAll()是 Object类 中的方法 ；
 Condition是在java 1.5中才出现的，它用来替代传统的Object的wait()、notify()实现线程间的协作，相比使用Object的wait()、 notify()，使用Condition1的await()、signal()这种方式实现线程间协作更加安全和高效。

