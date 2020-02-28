##### 1.下面论述正确的是（）？

A 如果两个对象的hashcode相同，那么它们作为同一个HashMap的key时，必然返回同样的值
 B 如果a,b的hashcode相同，那么a.equals(b)必须返回true
 C 对于一个类，其所有对象的hashcode必须不同
 D 如果a.equals(b)返回true，那么a,b两个对象的hashcode必须相同

答案 D
 hashCode()方法和equals()方法的作用其实是一样的，在Java里都是用来对比两个对象是否相等一致。
 那么equals()既然已经能实现对比的功能了，为什么还要hashCode()呢？因为重写的equals()里一般比较的比较全面比较复杂，这样效率就比较低，而利用hashCode()进行对比，则只要生成一个hash值进行比较就可以了，效率很高。
 那么hashCode()既然效率这么高为什么还要equals()呢？ 因为hashCode()并不是完全可靠，有时候不同的对象他们生成的hashcode也会一样（生成hash值得公式可能存在的问题），所以hashCode()只能说是大部分时候可靠，并不是绝对可靠，
 所以我们可以得出：
 1.equals()相等的两个对象他们的hashCode()肯定相等，也就是用equals()对比是绝对可靠的。

2.hashCode()相等的两个对象他们的equal()不一定相等，也就是hashCode()不是绝对可靠的。

所有对于需要大量并且快速的对比的话如果都用equals()去做显然效率太低，所以解决方式是，每当需要对比的时候，首先用hashCode()去对比，如果hashCode()不一样，则表示这两个对象肯定不相等（也就是不必再用equal()去再对比了）,如果hashCode()相同，此时再对比他们的equals()，如果equals()也相同，则表示这两个对象是真的相同了，这样既能大大提高了效率也保证了对比的绝对正确性！

##### 2.一个Java源程序文件中定义几个类和接口，则编译该文件后生成几个以.class为后缀的字节码文件。

A 正确
 B 错误

![img](https:////upload-images.jianshu.io/upload_images/1824809-abbd947d9853e0f6.png?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

##### 3.命令javac-d参数的用途是？（）

A 指定编译后类层次的根目录
 B 指定编译时需要依赖类的路径
 C 指定编译时的编码
 D 没有这一个参数
 答案 A



![img](https:////upload-images.jianshu.io/upload_images/1824809-61a303a741a31df3.png?imageMogr2/auto-orient/strip|imageView2/2/w/641/format/webp)

image.png

##### 4.BufferedReader的父类是以下哪个？

A FilterReader
 B InputStreamReader
 C PipedReader
 D Reader
 答案D



![img](https:////upload-images.jianshu.io/upload_images/1824809-9d54f322236421a4.png?imageMogr2/auto-orient/strip|imageView2/2/w/599/format/webp)

##### 5.有如下一段代码，请选择其运行结果（）



```swift
public class StringDemo{
  private static final String MESSAGE="taobao";
  public static void main(String [] args) {
    String a ="tao"+"bao";
    String b="tao";
    String c="bao";
    System.out.println(a==MESSAGE);
    System.out.println((b+c)==MESSAGE);
  }
}
```

A true true
 B false false
 C true false
 D false true

答案 C

##### 6.java语言的下面几种数组复制方法中，哪个效率最高？

A for 循环逐一复制
 B System.arraycopy
 C Array.copyOf
 D 使用clone方法
 答案 B
 (1) 从速度上看：System.arraycopy > clone > Arrays.copyOf > for
 (2) for的速度之所以最慢是因为下标表示法每次都从起点开始寻位到指定下标处（现代编译器应该对其有进行优化，改为指针），另外就是它每一次循环都要判断一次是否达到数组最大长度和进行一次额外的记录下标值的加法运算。
 (3) 查看Arrays.copyOf的源码可以发现，它其实本质上是调用了System.arraycopy。之所以时间差距比较大，是因为很大一部分开销全花在了Math.min函数上了。

##### 7.以下代码将打印出

A com. jd
 B com/jd/MyClass.class
 C ///////MyClass.class
 D com.jd.MyClass

答案 C
 由于replaceAll方法的第一个参数是一个正则表达式，而"."在正则表达式中表示任何字符，所以会把前面字符串的所有字符都替换成"/"。如果想替换的只是"."，那么久要写成"\.".

##### 8.final、finally和finalize的区别中，下述说法正确的有？

A final用于声明属性，方法和类，分别表示属性不可变，方法不可覆盖，类不可继承。
 B finally是异常处理语句结构的一部分，表示总是执行。
 C finalize是Object类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法，可以覆盖此方法提供垃圾收集时的其他资源的回收，例如关闭文件等。
 D 引用变量被final修饰之后，不能再指向其他对象，它指向的对象的内容也是不可变的。
 答案 A B

#### 一.final

如果一个类被声明为final，意味着它不能再派生出新的子类，不能作为父类被继承。因此一个类不能既被声明为 abstract的，又被声明为final的。将变量或方法声明为final，可以保证它们在使用中不被改变。被声明为final的变量必须在new一个对象时初始化（即只能在声明变量或构造器或代码块内初始化），而在以后的引用中只能读取，不可修改。被声明为final的方法也同样只能使用，不能覆盖(重写)。

#### 二.finally

在异常处理时提供 finally 块来执行任何清除操作。如果抛出一个异常，那么相匹配的 catch 子句就会执行，然后控制就会进入 finally 块（如果有的话）。

#### 三.finalize

方法名。Java 技术允许使用 finalize() 方法在垃圾收集器将对象从内存中清除出去之前做必要的清理工作。这个方法是由垃圾收集器在确定这个对象没有被引用时对这个对象调用的。它是在 Object 类中定义的，因此所有的类都继承了它。子类覆盖 finalize() 方法以整理系统资源或者执行其他清理工作。finalize() 方法是在垃圾收集器删除对象之前对这个对象调用的。注意：finalize不一定被jvm调用，只有当垃圾回收器要清除垃圾时才被调用。

C，finalize方法，这个选项错就错在，这个方法一个对象只能执行一次，只能在第一次进入被回收的队列，而且对象所属于的类重写了finalize方法才会被执行。第二次进入回收队列的时候，不会再执行其finalize方法，而是直接被二次标记，在下一次GC的时候被GC。
 放一张图吧



![img](https:////upload-images.jianshu.io/upload_images/1824809-9e6affc1770b6b9c.png?imageMogr2/auto-orient/strip|imageView2/2/w/1199/format/webp)

image.png

##### 8.可以把任何一种数据类型的变量赋给Object类型的变量。

A 对
 B 错
 答案 A

对象类型的不必多说可以赋值；而八大基础数据类型会自动装箱后赋值给Object，所以编译运行都不会报错
 Java中一切都是对象，Object是所有类的根类！

##### 9.一个以”.java”为后缀的源文件

A 只能包含一个类，类名必须与文件名相同
 B 只能包含与文件名相同的类以及其中的内部类
 C 只能有一个与文件名相同的public类，可以包含其他类
 D 可以包含任意类
 答案 C



```cpp
public class SameName{}
class Outer {
    class SameName{}
}
```

##### 10.下面不属于HttpServletRequest接口完成功能的是？

A 读取cookie
 B 读取HTTP头
 C 设定响应的content类型
 D 读取路径信息
 答案 C



```dart
 HttpServletRequest类主要处理：

1.读取和写入HTTP头标

2.取得和设置cookies

3.取得路径信息

4.标识HTTP会话

A: request.getCookies();
B: request.getHeader(String s);
C: response.setContentType("text/html;charset=utf-8");
C: request.getContextPath();/request.getServletPath();
```

##### 11.下列程序的运行结果



```csharp
public static void main(String args[]) {
    Thread t = new Thread() {
        public void run() {
            pong();
        }
    };
    t.run();
    System.out.print("ping");
}
static void pong() {
    System.out.print("pong");
}
```

A pingpong
 B pongping
 C pingpong和pongping都有可能
 D 都不输出

答案 B
 若调用start，则先执行主线程的，后执行子线程的，即结果为pingpong
 若调用run，相当于函数调用，顺序执行，即结果为pongping

##### 12.一般情况下，以下哪个选项不是关系数据模型与对象模型之间匹配关系？

A 表对应类
 B 记录对应对象
 C 表的字段对应类的属性
 D 表之间的参考关系对应类之间的依赖关系
 答案 D



```undefined
一般关系数据模型和对象数据模型之间有以下对应关系：表对应类，记录对应对象，表的字段对应类的属性
```

##### 13.java 的字符类型采用的是 Unicode 编码方案，每个 Unicode 码占用（）个比特位。

A 8
 B 16
 C 32
 D 64
 答案 B
 区分编码和编码格式
 编码： 编码就是一个编号(数字)到字符的一种映射关系，就仅仅是一种一对一的映射而已，可以理解成一个很大的对应表格
 java默认的字符集是Unicode（占两个字节byte，一个字节=8比特位bit，所以每个Unicode占用16比特位）
 编码格式：编码格式 是用来序列化或存储编码中提到的那个“编号(数字)”的一种“格式”，包括gbk和utf-8
 gbk： 是指中国的中文字符，其它它包含了简体中文与繁体中文字符
 UTF-8： 它是一种全国家通过的一种编码

##### 14.Which statement is true?



```dart
void waitForSignal()
{
    Object obj = new Object();
    synchronized(Thread.currentThread())
    {
        obj.wait();
        obj.notify();
    }
}
```

A This code may throw an InterruptedException
 B This code may throw an IllegalStateException
 C This code may throw a TimeOutException after ten minutes
 D This code will not compile unless”obj.wait()”is replaced with”(Thread)obj).wait()”
 E Reversing the order of obj.wait()and obj.notify()may cause this method to complete normally

答案 A
 这题有两个错误的地方，第一个错误是 wait() 方法要以 try/catch 包覆，或是掷出 InterruptedException 才行
 因此答案就是因为缺少例外捕捉的   InterruptedException

第二个错误的地方是， synchronized 的目标与 wait() 方法的物件不相同，会有 IllegalMonitorStateException ，不过 InterruptedException 会先出现，所以这不是答案

最后正确的程式码应该是这样：



```dart
     void waitForSignal() {

Object obj = new Object();

         synchronized (obj) {

             try {

obj.wait();

} catch (InterruptedException e) {

e.printStackTrace();

}

obj.notify();

}

}
```

##### 15.下面哪个行为被打断不会导致InterruptedException：（ ）？

A Thread.join
 B Thread.sleep
 C Object.wait
 D CyclicBarrier.await
 E Thread.suspend

答案 E
 CyclicBarrier是一个屏障类，它的await方法可以简单的理解为：等待多个线程同时到达之后才能继续进行，在此之前它就是这些线程的屏障，线程不能继续进行，而对于失败的同步尝试，CyclicBarrier 使用了一种要么全部要么全不 (all-or-none) 的破坏模式：如果因为中断、失败或者超时等原因，导致线程过早地离开了屏障点，那么在该屏障点等待的其他所有线程也将通过 BrokenBarrierException（如果它们几乎同时被中断，则用 interruptedException）以反常的方式离开。因此它被中断也是可以抛出interruptedException的

suspend方法(已过时)作用是阻塞一个线程，不会释放锁，直到其他的线程调用resume方法，才能继续向下执行。被打断不会导致InterruptedException。

##### 16.在java语言中，如果你编写一个多线程序，可以使用的方法是（）

A 扩展类Thread
 B 实现Runnable接口
 C 扩展类 Runnable
 D 实现接口Thread
 答案 A B

1.继承Thread类（Override它的run方法）
 2.实现Runnable接口（实现run方法）
 3.使用ExecutorService、Callable、Future实现有返回结果的多线程

##### 17.关于ThreadLocal类 以下说法正确的是

A ThreadLocal继承自Thread
 B ThreadLocal实现了Runnable接口
 C ThreadLocal重要作用在于多线程间的数据共享
 D ThreadLocal是采用哈希表的方式来为每个线程都提供一个变量的副本
 E ThreadLocal保证各个线程间数据安全，每个线程的数据不会被另外线程访问和破坏

答案 DE

1、ThreadLocal的类声明：
 public class ThreadLocal<T>
 可以看出ThreadLocal并没有继承自Thread，也没有实现Runnable接口。所以AB都不对。
 2、ThreadLocal类为每一个线程都维护了自己独有的变量拷贝。每个线程都拥有了自己独立的一个变量。
 所以ThreadLocal重要作用并不在于多线程间的数据共享，而是数据的独立，C选项错。
 由于每个线程在访问该变量时，读取和修改的，都是自己独有的那一份变量拷贝，不会被其他线程访问，
 变量被彻底封闭在每个访问的线程中。所以E对。
 3、ThreadLocal中定义了一个哈希表用于为每个线程都提供一个变量的副本：



```dart
 static class ThreadLocalMap {

        static class Entry extends WeakReference<ThreadLocal> {
            /** The value associated with this ThreadLocal. */
            Object value;

            Entry(ThreadLocal k, Object v) {
                super(k);
                value = v;
            }
        }

        /**
         * The table, resized as necessary.
         * table.length MUST always be a power of two.
         */
        private Entry[] table;
}
```

##### 18.以下哪项不属于java类加载过程？

A 生成java.lang.Class对象
 B int类型对象成员变量赋予默认值
 C 执行static块代码
 D 类方法解析
 答案 B
 类的加载包括：加载，验证，准备，解析，初始化。
 选项A：生成java.lang.Class对象是在加载时进行的。生成Class对象作为方法区这个类的各种数据的访问入口。
 选项B：既然是对象成员，那么肯定在实例化对象后才有。在类加载的时候会赋予初值的是类变量，而非对象成员。
 选项C：这个会调用。可以用反射试验。
 选项D：类方法解析发生在解析过程。

##### 19.以下哪些继承自 Collection 接口（）

A List
 B Set
 C Map
 D Array

答案 A B
 Collection
 ├List

│├LinkedList

│├ArrayList

│└Vector

│　└Stack

└Set

Map

├Hashtable

├HashMap

└WeakHashMap

##### 20.有以下类定义：



```java
abstract class Animal{
    abstract void say();
}
public class Cat extends Animal{
    public Cat(){
        System.out.printf("I am a cat");
    }
    public static void main(String[] args) {
        Cat cat=new Cat();
    }
}
```

A I am a cat
 B Animal能编译，Cat不能编译
 C Animal不能编译，Cat能编译
 D 编译能通过，但是没有输出结果
 答案 B

基类是抽象类，子类继承父类，但是没有实现基类的抽象方法，那么子类也是抽象类。抽象类不能创建对象，所以在主函数中创建对象编译不会通过。

包含抽象方法的类称为抽象类，但并不意味着抽象类中只能有抽象方法，它和普通类一样，同样可以拥有成员变量和普通的成员方法。注意，抽象类和普通类的主要有三点区别：

1）抽象方法必须为public或者protected（因为如果为private，则不能被子类继承，子类便无法实现该方法），缺省情况下默认为public。

2）抽象类不能用来创建对象；

3）如果一个类继承于一个抽象类，则子类必须实现父类的抽象方法。如果子类没有实现父类的抽象方法，则必须将子类也定义为为abstract类。

在其他方面，抽象类和普通的类并没有区别。

##### 21.代码片段：



```csharp
byte b1=1,b2=2,b3,b6; 
final byte b4=4,b5=6; 
b6=b4+b5; 
b3=(b1+b2); 
System.out.println(b3+b6);
```

关于上面代码片段叙述正确的是（）
 A 输出结果：13
 B 语句：b6=b4+b5编译出错
 C 语句：b3=b1+b2编译出错
 D 运行期抛出异常
 答案C
 被final修饰的变量是常量，这里的b6=b4+b5可以看成是b6=10；在编译时就已经变为b6=10了
 而b1和b2是byte类型，java中进行计算时候将他们提升为int类型，再进行计算，b1+b2计算后已经是int类型，赋值给b3，b3是byte类型，类型不匹配，编译不会通过，需要进行强制转换。
 Java中的byte，short，char进行计算时都会提升为int类型。

##### 22.java中Hashtable, Vector, TreeSet, LinkedList哪些线程是安全的？

A Hashtable
 B Vector
 C TreeSet
 D LinkedList

答案 A B
 vector ：就比 arraylist 多了个同步化机制（线程安全），因为效率较低，现在已经不太建议使用。

statck ：堆栈类，先进后出；

hashtable ：就比 hashmap 多了个线程安全

enumeration ：枚举，相当于迭代器

StringBuffer 是线程安全，而 StringBuilder 是线程不安全的。

Properties

##### 23.关于OutOfMemoryError，下面说法正确的是（）？

A java.lang.OutOfMemoryError: PermGen space 增加-XX:MaxPermSize这个参数的值的话，这个问题通常会得到解决。
 B java.lang.OutOfMemoryError: Requested array size exceeds VM limit当你正准备创建一个超过虚拟机允许的大小的数组时，这条错误将会出现
 C java.lang.OutOfMemoryError: Java heap space 一般情况下解决这个问题最快的方法就是通过-Xmx参数来增加堆的大小
 D java.lang.OutOfMemoryError: nativeGetNewTLA这个异常只有在jRockit虚拟机时才会碰到

答案 A B C

> java.lang.OutOfMemoryError: PermGen space
>  查了一下为"永久代"内存大小不足，“永久代”的解释应该为JVM中的方法区，主要用于存储类信息，常量，静态变量，即时编译器编译后代码等。本错误仅限于Hotspot虚拟机，本区进行垃圾回收很少，不够直接加大简单粗暴。

> java.lang.OutOfMemoryError: Requested array size exceeds VM limit
>  直接翻译报错信息：数组过长导致堆内存溢出，加大堆内存或者减少数组长度。

> java.lang.OutOfMemoryError: Java heap space
>  堆内存不足，直接增大堆内存。

