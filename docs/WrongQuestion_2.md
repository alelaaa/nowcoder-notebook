##### 1. HashSet子类依靠()方法区分重复元素。

A toString(),equals()
 B clone(),equals()
 C hashCode(),equals()
 D getClass(),clone()

答案 C
 HashSet内部使用Map保存数据，即将HashSet的数据作为Map的key值保存，这也是HashSet中元素不能重复的原因。而Map中保存key值前，会去判断当前Map中是否含有该key对象，内部是先通过key的hashCode，确定有相同的hashCode之后，再通过equals方法判断是否相同。

##### 2.说明输出结果。



```java
package test;
import java.util.Date; 
public class SuperTest extends Date{ 
    private static final long serialVersionUID = 1L; 
    private void test(){ 
       System.out.println(super.getClass().getName()); 
    } 
      
    public static void main(String[]args){ 
       new SuperTest().test(); 
    } 
}
```

A SuperTest
 B SuperTest.class
 C test.SuperTest
 D test.SuperTest.class

解析：

> TestSuper和Date的getClass都没有重写，他们都是调用Object的getClass，而Object的getClass作用是返回的是运行时的类的名字。这个运行时的类就是当前类，所以
>  super.getClass().getName()
>  返回的是test.SuperTest，与Date类无关
>  要返回Date类的名字需要写super.getClass().getSuperclass()

##### 3.jre 判断程序是否执行结束的标准是（）

A 所有的前台线程执行完毕
 B 所有的后台线程执行完毕
 C 所有的线程执行完毕
 D 和以上都无关

> main()函数即主函数，是一个前台线程，前台进程是程序中必须执行完成的，而后台线程则是java中所有前台结束后结束，不管有没有完成，后台线程主要用与内存分配等方面。
>  前台线程和后台线程的区别和联系：
>  1、后台线程不会阻止进程的终止。属于某个进程的所有前台线程都终止后，该进程就会被终止。所有剩余的后台线程都会停止且不会完成。
>  2、可以在任何时候将前台线程修改为后台线程，方式是设置Thread.IsBackground 属性。
>  3、不管是前台线程还是后台线程，如果线程内出现了异常，都会导致进程的终止。
>  4、托管线程池中的线程都是后台线程，使用new Thread方式创建的线程默认都是前台线程。
>  说明：
>  应用程序的主线程以及使用Thread构造的线程都默认为前台线程
>  使用Thread建立的线程默认情况下是前台线程，在进程中，只要有一个前台线程未退出，进程就不会终止。主线程就是一个前台线程。而后台线程不管线程是否结束，只要所有的前台线程都退出（包括正常退出和异常退出）后，进程就会自动终止。一般后台线程用于处理时间较短的任务，如在一个Web服务器中可以利用后台线程来处理客户端发过来的请求信息。而前台线程一般用于处理需要长时间等待的任务，如在Web服务器中的监听客户端请求的程序，或是定时对某些系统资源进行扫描的程序

##### 3.下面有关java的一些细节问题，描述错误的是？

A 构造方法不需要同步化
 B 一个子类不可以覆盖掉父类的同步方法
 C 定义在接口中的方法默认是public的
 D 容器保存的是对象的引用

答案B
 构造方法每次都是构造出新的对象，不存在多个线程同时读写同一对象中的属性的问题，所以不需要同步 。
 如果父类中的某个方法使用了 synchronized关键字，而子类中也覆盖了这个方法，默认情况下子类中的这个方法并不是同步的，必须显示的在子类的这个方法中加上 synchronized关键字才可。当然，也可以在子类中调用父类中相应的方法，这样虽然子类中的方法并不是同步的，但子类调用了父类中的同步方法，也就相当子类方法也同步了。

##### 4.下列说法正确的是

A 在类方法中可用this来调用本类的类方法
 B 在类方法中调用本类的类方法可直接调用
 C 在类方法中只能调用本类的类方法
 D 在类方法中绝对不能调用实例方法
 答案B
 A this指当前对象只能在实际方法和构造函数中调用。C 可以调用其他类的非私有类方法。D 不能直接调用，到先生成对象。通过对象即可调用实例方法。

##### 5.java中，StringBuilder和StringBuffer的区别，下面说法错误的是？

A StringBuffer是线程安全的
 B StringBuilder是非线程安全的
 C StringBuffer对 String 类型进行改变的时候其实都等同于生成了一个新的 String 对象，然后将指针指向新的 String 对象。
 D 效率比较String<StringBuffer<StringBuilder，但是在 String S1 = “This is only a” + “ simple” + “ test”时，String效率最高。

答案 C

String对String  类型进行改变的时候其实都等同于生成了一个新的  String  对象，然后将指针指向新的  String  对象，而不是StringBuffer；StringBuffer每次结果都会对  StringBuffer  对象本身进行操作，而不是生成新的对象，再改变对象引用。

##### 6.下面哪种情况会导致持久区jvm堆内存溢出？

A 循环上万次的字符串处理
 B 在一段代码内申请上百M甚至上G的内存
 C 使用CGLib技术直接操作字节码运行，生成大量的动态类
 D 不断创建对象

答案 C

简单的来说 java的堆内存分为两块:permantspace（持久带） 和 heap space。
 持久带中主要存放用于存放静态类型数据，如 Java Class, Method 等， 与垃圾收集器要收集的Java对象关系不大。
 而heapspace分为年轻带和年老带
 年轻代的垃圾回收叫 Young GC， 年老代的垃圾回收叫 Full GC。
 在年轻代中经历了N次（可配置）垃圾回收后仍然存活的对象，就会被复制到年老代中。因此，可以认为年老代中存放的都是一些生命周期较长的对象
 年老代溢出原因有  循环上万次的字符串处理、创建上千万个对象、在一段代码内申请上百M甚至上G的内存，既A B D选项
 持久代溢出原因  动态加载了大量Java类而导致溢出

## 原理

JVM堆内存分为2块：Permanent Space 和 Heap Space。

- Permanent 即 持久代（Permanent Generation），主要存放的是Java类定义信息，与垃圾收集器要收集的Java对象关系不大。
- Heap = { Old + NEW = {Eden, from, to} }，Old 即 年老代（Old Generation），New 即 年轻代（Young Generation）。年老代和年轻代的划分对垃圾收集影响比较大。

### 年轻代

所有新生成的对象首先都是放在年轻代。年轻代的目标就是尽可能快速的收集掉那些生命周期短的对象。年轻代一般分3个区，1个Eden区，2个Survivor区（from 和 to）。

大部分对象在Eden区中生成。当Eden区满时，还存活的对象将被复制到Survivor区（两个中的一个），当一个Survivor区满时，此区的存活对象将被复制到另外一个Survivor区，当另一个Survivor区也满了的时候，从前一个Survivor区复制过来的并且此时还存活的对象，将可能被复制到年老代。

2个Survivor区是对称的，没有先后关系，所以同一个Survivor区中可能同时存在从Eden区复制过来对象，和从另一个Survivor区复制过来的对象；而复制到年老区的只有从另一个Survivor区过来的对象。**而且，因为需要交换的原因，Survivor区至少有一个是空的**。特殊的情况下，根据程序需要，Survivor区是可以配置为多个的（多于2个），这样可以增加对象在年轻代中的存在时间，减少被放到年老代的可能。

针对年轻代的垃圾回收即 Young GC。

### 年老代

在年轻代中经历了N次（可配置）垃圾回收后仍然存活的对象，就会被复制到年老代中。因此，可以认为年老代中存放的都是一些生命周期较长的对象。

针对年老代的垃圾回收即 Full GC。

### 持久代

用于存放静态类型数据，如 Java Class, Method 等。持久代对垃圾回收没有显著影响。但是有些应用可能动态生成或调用一些Class，例如 Hibernate CGLib 等，在这种时候往往需要设置一个比较大的持久代空间来存放这些运行过程中动态增加的类型。

所以，当一组对象生成时，**内存申请过程**如下：

1. JVM会试图为相关Java对象在年轻代的Eden区中初始化一块内存区域。
2. 当Eden区空间足够时，内存申请结束。否则执行下一步。
3. JVM试图释放在Eden区中所有不活跃的对象（Young GC）。释放后若Eden空间仍然不足以放入新对象，JVM则试图将部分Eden区中活跃对象放入Survivor区。
4. Survivor区被用来作为Eden区及年老代的中间交换区域。当年老代空间足够时，Survivor区中存活了一定次数的对象会被移到年老代。
5. 当年老代空间不够时，JVM会在年老代进行完全的垃圾回收（Full GC）。
6. Full GC后，若Survivor区及年老代仍然无法存放从Eden区复制过来的对象，则会导致JVM无法在Eden区为新生成的对象申请内存，即出现“Out of Memory”。

**OOM（“Out of Memory”）异常一般主要有如下2种原因**：

1. 年老代溢出，表现为：java.lang.OutOfMemoryError:Javaheapspace

这是最常见的情况，产生的原因可能是：设置的内存参数Xmx过小或程序的内存泄露及使用不当问题。

**例如循环上万次的字符串处理、创建上千万个对象、在一段代码内申请上百M甚至上G的内存。**还有的时候虽然不会报内存溢出，却会使系统不间断的垃圾回收，也无法处理其它请求。这种情况下除了检查程序、打印堆内存等方法排查，还可以借助一些内存分析工具，比如MAT就很不错。

1. 持久代溢出，表现为：java.lang.OutOfMemoryError:PermGenspace

**通常由于持久代设置过小，动态加载了大量Java类而导致溢出**，解决办法唯有将参数 -XX:MaxPermSize 调大（一般256m能满足绝大多数应用程序需求）。将部分Java类放到容器共享区（例如Tomcat share lib）去加载的办法也是一个思路，但前提是容器里部署了多个应用，且这些应用有大量的共享类库

##### 7.下面叙述那个是正确的？（）

A java中的集合类（如Vector）可以用来存储任何类型的对象，且大小可以自动调整。但需要事先知道所存储对象的类型，才能正常使用。
 B 在java中，我们可以用违例（Exception）来抛出一些并非错误的消息，但这样比直接从函数返回一个结果要更大的系统开销。
 C java接口包含函数声明和变量声明。
 D java中，子类不可以访问父类的私有成员和受保护的成员。
 答案C
 A.vector是线程安全的ArrayList，在内存中占用连续的空间。初始时有一个初始大小，当数据条数大于这个初始大小后会重写分配一个更大的连续空间。如果Vector定义为保存Object则可以存放任意类型。

B.try{}catch{}会增加额外的开销

C.接口中声明的'变量'必须为public final static,所以为常量

D.子类可以访问父类受保护的成员

##### 8.对于子类的构造函数说明，下列叙述中错误的是（    ）。

A 子类可以继承父类的构造函数。
 B 子类中调用父类构造函数不可以直接书写父类构造函数，而应该用super();。
 C 用new创建子类的对象时，若子类没有带参构造函数，将先执行父类的无参构造函数，然后再执行自己的构造函数。
 D 子类的构造函数中可以调用其他函数。

答案 A
 A.java继承中对构造函数是不继承的，只是显式或者隐式调用

##### 9.String与StringBuffer的区别。

A String是不可变的对象，StringBuffer是可以再编辑的
 B 字符串是常量，StringBuffer是变量
 C String是可变的对象，StringBuffer是不可以再编辑的
 D 以上说法都不正确

答案 AB
 String, StringBuffer,StringBuilder的区别

java中String、StringBuffer、StringBuilder是编程中经常使用的字符串类，他们之间的区别也是经常在面试中会问到的问题。现在总结一下，看看他们的不同与相同。

1.可变与不可变

String类中使用字符数组保存字符串，如下就是，因为有“final”修饰符，所以可以知道string对象是不可变的。

private final char value[];



```dart
  String 为不可变对象,一旦被创建,就不能修改它的值. . 对于已经存在的String对象的修改都是重新创建一个新的对象,然后把新的值保存进去.
```

StringBuilder与StringBuffer都继承自AbstractStringBuilder类，在AbstractStringBuilder中也是使用字符数组保存字符串，如下就是，可知这两种对象都是可变的。

char[] value;



```dart
 StringBuffer:是一个可变对象,当对他进行修改的时候不会像String那样重新建立对象 , 它只能通过构造函数来建立,  如： StringBuffer sb = new StringBuffer();
```

不能通过赋值符号对他进行付值. ， 如 sb = "welcome to here!";//error
 对象被建立以后,在内存中就会分配内存空间,并初始保存一个null.向StringBuffer中赋值的时候可以通过它的append方法.      sb.append("hello");

2.是否多线程安全

String中的对象是不可变的，也就可以理解为常量， 显然线程安全 。

AbstractStringBuilder是StringBuilder与StringBuffer的公共父类，定义了一些字符串的基本操作，如expandCapacity、append、insert、indexOf等公共方法。

StringBuffer对方法加了同步锁或者对调用的方法加了同步锁，所以是 线程安全的 。看如下源码：



```java
   public   synchronized  StringBuffer reverse() {
       super .reverse();
       return   this ;
  }

  

   public   int  indexOf(String str) {
      return  indexOf(str, 0);         //存在 public synchronized int indexOf(String str, int fromIndex) 方法
  }
```

StringBuilder并没有对方法进行加同步锁，所以是 非线程安全的 。

3.StringBuilder与StringBuffer共同点

StringBuilder与StringBuffer有公共父类AbstractStringBuilder( 抽象类 )。

抽象类与接口的其中一个区别是：抽象类中可以定义一些子类的公共方法，子类只需要增加新的功能，不需要重复写已经存在的方法；而接口中只是对方法的申明和常量的定义。

StringBuilder、StringBuffer的方法都会调用AbstractStringBuilder中的公共方法，如super.append(...)。只是StringBuffer会在方法上加synchronized关键字，进行同步。

最后，如果程序不是多线程的，那么使用StringBuilder效率高于StringBuffer。

效率比较String < StringBuffer < StringBuilder，但是在String S1 =“This is only a”+“simple”+“test”时，String效率最高。

##### 10.下面描述属于java虚拟机功能的是？

A 通过 ClassLoader 寻找和装载 class 文件
 B 解释字节码成为指令并执行，提供 class 文件的运行环境
 C 进行运行期间垃圾回收
 D 提供与硬件交互的平台

答案 A B C D
 通过 ClassLoader 寻找和装载 class 文件
 解释字节码成为指令并执行，提供 class 文件的运行环境
 进行运行期间垃圾回收
 提供与硬件交互的平台

##### 11.接口不能扩展（继承）多个接口。（ ）

A 正确
 B 错误
 答案 B
 java类是单继承的。classB Extends classA
 java接口可以多继承。Interface3 Extends Interface0, Interface1, interface……



```swift
    不允许类多重继承的主要原因是，如果A同时继承B和C，而b和c同时有一个D方法，A如何决定该继承那一个呢？
    但接口不存在这样的问题，接口全都是抽象方法继承谁都无所谓，所以接口可以继承多个接口。
```

##### 12.接口不能扩展（继承）多个接口。（ ）

A class中的constructor不可省略
 B constructor必须与class同名，但方法不能与class同名
 C constructor在一个对象被new时执行
 D 一个class只能定义一个constructor

答案：C

A.构造函数可以省略，省略构造函数则new对象实例时，所有的数据类型赋值为0，bool类型赋值为FALSE，引用类型赋值为NULL。

B.构造函数必须与类同名，而且不能有返回类型。而方法是可以与类同名的，但是必须声明返回数据类型。

C.正确，当new对象是首先调用静态初始数据块（可省略），然后调用父类构造函数（不是子类则不调用），最后调用自己的构造函数（一定调用），这样才能生成一个对象的实例。

D.构造函数是可以重载的，重载的要求是参数不同。

##### 13.在使用super 和this关键字时，以下描述正确的是

A 在子类构造方法中使用super（）显示调用父类的构造方法，super（）必须写在子类构造方法的第一行，否则编译不通过
 B super（）和this（）不一定要放在构造方法内第一行
 C this（）和super（）可以同时出现在一个构造函数中
 D this（）和super（）可以在static环境中使用，包括static方法和static语句块

答案 A
 1）调用super()必须写在子类构造方法的第一行，否则编译不通过。每个子类构造方法的第一条语句，都是隐含地调用super()，如果父类没有这种形式的构造函数，那么在编译的时候就会报错。

2）super()和this()类似,区别是，super从子类中调用父类的构造方法，this()在同一类内调用其它方法。

3）super()和this()均需放在构造方法内第一行。

4）尽管可以用this调用一个构造器，但却不能调用两个。

5）this和super不能同时出现在一个构造函数里面，因为this必然会调用其它的构造函数，其它的构造函数必然也会有super语句的存在，所以在同一个构造函数里面有相同的语句，就失去了语句的意义，编译器也不会通过。

6）this()和super()都指的是对象，所以，均不可以在static环境中使用。包括：static变量,static方法，static语句块。

7）从本质上讲，this是一个指向本对象的指针, 然而super是一个Java关键字。

##### 14.下列语句正确的是（ ）

A 形式参数可被视为local variable
 B 形式参数可被所有的字段修饰符修饰
 C 形式参数为方法被调用时，是真正被传递的参数
 D 形式参数不可以是对象

答案 A
 **A：**形式参数可被视为local variable。**形参和局部变量一样都不能离开方法**。都只有在方法内才会发生作用，也只有在方法中使用，不会在方法外可见。

**B：** **对于形式参数只能用final修饰符**，其它任何修饰符都会引起编译器错误。但是用这个修饰符也有一定的限制，就是在方法中不能对参数做任何修改。 不过一般情况下，一个方法的形参不用final修饰。只有在特殊情况下，那就是：方法内部类。  一个方法内的内部类如果使用了这个方法的参数或者局部变量的话，这个参数或局部变量应该是final。

**C：**形参的值在调用时根据调用者更改，实参则用自身的值更改形参的值（指针、引用皆在此列），也就是说**真正被传递的是实参。**

**D：**方法的参数列表指定要传递给方法什么样的信息，**采用的都是对象的形式**。因此，在参数列表中必须指定每个所传递对象的类型及名字。想JAVA中任何传递对象的场合一样，这里传递的实际上也是引用，并且引用的类型必须正确。

##### 15.java如何接受request域中的参数?

A request.getRequestURL()
 B request. getAttribute()
 C request.getParameter()
 D request.getWriter()

答案 C
 request.getAttribute 其实是取的web容器里面的值，而不是页面通过get或者post方式传上来的参数值。 一个request就是一个对象，setAttribute，其实就是在request scope里面添加了一个变量。我们打个比方，request里有一个map，setAttribute就是map.put。 request.getParameter("username") 只是处理参数，但是在有username这个参数的情况下，你可以认为是等价。 但是paramter是个string返回值。 request.setAttribute()和getAttribute()方法传递的数据只会存在于Web容器内部，在具有转发关系的web组件之间共享。 这两个方法能够设置Object类型的共享数据。

##### 16.指出下列程序运行的结果（）



```csharp
public class Example{
    String str = new String("good");
    char[ ] ch = { 'a' , 'b' , 'c' };
    public static void main(String args[]){
        Example ex = new Example();
        ex.change(ex.str,ex.ch);
        System.out.print(ex.str + " and ");
        System.out.print(ex.ch);
    }
    public void change(String str,char ch[ ]){
        str = "test ok";
        ch[0] = 'g';
    }
}
```

A good and  abc
 B good and gbc
 C test ok and abc
 D test ok and gbc

答案 B
 首先说下String确实是个不可变对象，这个不可变是JDK特有的，写JAVA的人特意针对的
 但是这与本题无关，题目中的形参str只是原引用ex.str的一个引用副本，传的是一个副本地址值，这个值与ex.str地址值是不一样的,但是它们同时指向了堆中的对象new String("good")，当你在函数中改变形参也就是地址的副本值也就是这句str="test ok"只是将副本地址指向常量"test ok"，并没有改变原ex.str的指向方向，它还是指向对象new String("good")的
 char数组与String一样传的也是地址的副本，但是关键是形参ch它没有新的指向 ch[0]只是ch在指向原对象时改变了对象的内部结构, 所以在ex.ch指向与它是同一个对象的情况下当然也会随之变化

##### 17.HashMap和HashTable的描述，错误的是？

A 他们都实现了Map接口。
 B HashMap非线程安全，在多个线程访问Hashtable时，不需要自己为它的方法实现同步，而HashMap就必须为之提供额外同步。
 C HashMap允许将null作为一个entry的key或者value，而Hashtable不允许。
 D 通过contains方法可以判断一个对象是否存在于HashMap或者Hashtable中。

答案 D



```java
//HashMap的源码
public class HashMap<K,V>
    extends AbstractMap<K,V>
    implements Map<K,V>, Cloneable, Serializable
-----------------------------------
//Hashtable的源码
public class Hashtable<K,V>
    extends Dictionary<K,V>
    implements Map<K,V>, Cloneable, java.io.Serializable
----------------------------------
```



```csharp
public V put(K key, V value) //HashMap的put方法，没有同步
 
public synchronized V put(K key, V value) //Hashtable的put方法
//当然，Hashtable的其他方法，如get，size，remove等方法，
//都加了synchronized关键词同步操作
```



```csharp
//Hashtable的put方法有以下语句块，大伙看了都知道
// Make sure the value is not null
if (value == null) {
    throw new NullPointerException();
}
 
//那么，我们再来看下HashMap的put方法中，有如下语句
//调用某个方法直接把key为null，值为value的键值对插入进去。
if (key == null)
    return putForNullKey(value);
```



```tsx
//以下是Hashtable的方法
public synchronized boolean contains(Object value)
public synchronized boolean containsKey(Object key)
public boolean containsValue(Object value)
 
//以下是HashMap中的方法，注意，没有contains方法，所以，D错误
public boolean containsKey(Object key)
public boolean containsValue(Object value)
```

关于HashMap的一些说法：

> a)  HashMap实际上是一个“链表散列”的数据结构，即数组和链表的结合体。HashMap的底层结构是一个数组，数组中的每一项是一条链表。
>  b)  HashMap的实例有俩个参数影响其性能： “初始容量” 和 装填因子。
>  c)  HashMap实现不同步，线程不安全。  HashTable线程安全
>  d)  HashMap中的key-value都是存储在Entry中的。
>  e)  HashMap可以存null键和null值，不保证元素的顺序恒久不变，它的底层使用的是数组和链表，通过hashCode()方法和equals方法保证键的唯一性
>  f)  解决冲突主要有三种方法：定址法，拉链法，再散列法。HashMap是采用拉链法解决哈希冲突的。
>  注： 链表法是将相同hash值的对象组成一个链表放在hash值对应的槽位；
>  用开放定址法解决冲突的做法是：当冲突发生时，使用某种探查(亦称探测)技术在散列表中形成一个探查(测)序列。 沿此序列逐个单元地查找，直到找到给定 的关键字，或者碰到一个开放的地址(即该地址单元为空)为止（若要插入，在探查到开放的地址，则可将待插入的新结点存人该地址单元）。
>  拉链法解决冲突的做法是： 将所有关键字为同义词的结点链接在同一个单链表中 。若选定的散列表长度为m，则可将散列表定义为一个由m个头指针组成的指针数 组T[0..m-1]。凡是散列地址为i的结点，均插入到以T[i]为头指针的单链表中。T中各分量的初值均应为空指针。在拉链法中，装填因子α可以大于1，但一般均取α≤1。拉链法适合未规定元素的大小。

1. Hashtable和HashMap的区别：

> a)   继承不同。
>  public class Hashtable extends Dictionary implements Map
>  public class HashMap extends  AbstractMap implements Map
>  b)  Hashtable中的方法是同步的，而HashMap中的方法在缺省情况下是非同步的。在多线程并发的环境下，可以直接使用Hashtable，但是要使用HashMap的话就要自己增加同步处理了。
>  c)  Hashtable 中， key 和 value 都不允许出现 null 值。 在 HashMap 中， null 可以作为键，这样的键只有一个；可以有一个或多个键所对应的值为 null 。当 get() 方法返回 null 值时，即可以表示 HashMap 中没有该键，也可以表示该键所对应的值为 null 。因此，在 HashMap 中不能由 get() 方法来判断 HashMap 中是否存在某个键， 而应该用 containsKey() 方法来判断。
>  d)  两个遍历方式的内部实现上不同。Hashtable、HashMap都使用了Iterator。而由于历史原因，Hashtable还使用了Enumeration的方式 。
>  e)  哈希值的使用不同，HashTable直接使用对象的hashCode。而HashMap重新计算hash值。
>  f)  Hashtable和HashMap它们两个内部实现方式的数组的初始大小和扩容的方式。HashTable中hash数组默认大小是11，增加的方式是old*2+1。HashMap中hash数组的默认大小是16，而且一定是2的指数。

注：  HashSet子类依靠hashCode()和equal()方法来区分重复元素。
 HashSet内部使用Map保存数据，即将HashSet的数据作为Map的key值保存，这也是HashSet中元素不能重复的原因。而Map中保存key值的,会去判断当前Map中是否含有该Key对象，内部是先通过key的hashCode,确定有相同的hashCode之后，再通过equals方法判断是否相同。

##### 18.volatile关键字的说法错误的是

A 能保证线程安全
 B volatile关键字用在多线程同步中，可保证读取的可见性
 C JVM保证从主内存加载到线程工作内存的值是最新的
 D volatile能禁止进行指令重排序

答案 A
 出于运行速率的考虑，java编译器会把经常经常访问的变量放到缓存（严格讲应该是工作内存）中，读取变量则从缓存中读。但是在多线程编程中,内存中的值和缓存中的值可能会出现不一致。volatile用于限定变量只能从内存中读取，保证对所有线程而言，值都是一致的。但是volatile不能保证原子性，也就不能保证线程安全。

##### 19.运行下面代码，输出的结果是（）



```csharp
    class A {

        static {
            System.out.println("class A static");
        }

        {
            System.out.println("I'm A class");
        }

        public A() {

            System.out.println("class A");

        }

    }

    public class B extends A {

        static {
            System.out.println("class B static");
        }

        {
            System.out.println("I'm B class");
        }

        public B() {

            System.out.println("class B");
        }

        public static void main(String[] args) {
            new B();
        }
    }
```

答案



```ruby
class A static        
class B static           
I'm A class             
class A               
I'm B class 
class B
```

B继承A  new B会
 1.把A的静态的执行完 执行B的静态的
 2.再执行A的初始化代码块，构造函数
 3.再执行B的初始化代码块，构造函数

##### 20.设有下面两个赋值语句：



```bash
a = Integer.parseInt("1024");

b = Integer.valueOf("1024").intValue();
```

下述说法正确的是（）
 A a是整数类型变量，b是整数类对象。
 B a是整数类对象，b是整数类型变量。
 C a和b都是整数类对象并且它们的值相等。
 D a和b都是整数类型变量并且它们的值相等。

答案D
 intValue()是把Integer对象类型变成int的基础数据类型；
 parseInt()是把String 变成int的基础数据类型；
 Valueof()是把String 转化成Integer对象类型；（现在JDK版本支持自动装箱拆箱了。）
 本题：parseInt得到的是基础数据类型int，valueof得到的是装箱数据类型Integer，然后再通过valueInt转换成int，所以选择D

##### 21.对文件名为Test.java的java代码描述正确的是()



```java
class Person {
    String name = "No name";
    public Person(String nm) {
        name = nm;
    }
}
class Employee extends Person {
    String empID = "0000";
    public Employee(String id) {
        empID = id;
    }
}
public class Test {
    public static void main(String args[]) {
        Employee e = new Employee("123");
        System.out.println(e.empID);
    }
}
```

A 输出：0000
 B 输出：123
 C 编译报错
 D 输出：No name

答案 C
 子类的构造方法总是先调用父类的构造方法，如果子类的构造方法没有明显地指明使用父类的哪个构造方法，子类就调用父类不带参数的构造方法。
 而父类没有无参的构造函数，所以子类需要在自己的构造函数中显示的调用父类的构造函数。

##### 22.下列关于容器集合类的说法正确的是？

A LinkedList继承自List
 B AbstractSet继承自Set
 C HashSet继承自AbstractSet
 D WeakMap继承自HashMap

答案 C
 首先这道题很多人都对接口以及抽象实现类认识混乱。
 A.LinkedList是继承自AbstractSequentialList（抽象类，实现了List接口）的，并且实现了List接口。所以A错误。
 B.AbstractSet是实现了Set接口的，本身是一个抽象类。继承自AbstractCollection（抽象类，实现了Collection接口）。所以B错误。

C.HashSet是继承自AbstractSet，实现了Set接口。所以C正确。
 D.WeakMap不存在于java集合框架的。只有一个叫做WeakHashMap（继承自AbstractMap）。
 最后附上java集合框架图。



![img](https:////upload-images.jianshu.io/upload_images/1824809-146baaaff4af1efa.png?imageMogr2/auto-orient/strip|imageView2/2/w/973/format/webp)

image.png

##### 23.以下关于对象序列化描述正确的是

A 使用FileOutputStream可以将对象进行传输
 B 使用PrintWriter可以将对象进行传输
 C 使用transient修饰的变量不会被序列化
 D 对象序列化的所属类需要实现Serializable接口

答案 C、D。

A、B 对象传输有专门的对象流。

C、序列化的过程中只有属性可以被序列化，方法不可以。同时一旦属性被transient或者static修饰。属性不可序列化。

D、看了一下有人说可以利用外部序列化，但是这个外部序列化的接口可是继承了序列化的接口啊 public interface Externalizable extends java.io.Serializable

##### 24.下面几个关于Java里queue的说法哪些是正确的（）？

A LinkedBlockingQueue是一个可选有界队列，不允许null值
 B PriorityQueue，LinkedBlockingQueue都是线程不安全的
 C PriorityQueue是一个无界队列，不允许null值，入队和出队的时间复杂度是O（log(n)）
 D PriorityQueue，ConcurrentLinkedQueue都遵循FIFO原则

答案 A、C
 1、LinkedBlockingQueue：基于链接节点的可选限定的blocking queue 。 这个队列排列元素FIFO（先进先出）。 队列的头部是队列中最长的元素。 队列的尾部是队列中最短时间的元素。 新元素插入队列的尾部，队列检索操作获取队列头部的元素。 链接队列通常具有比基于阵列的队列更高的吞吐量，但在大多数并发应用程序中的可预测性能较低。
 blocking queue说明：不接受null元素；可能是容量有限的；实现被设计为主要用于生产者 - 消费者队列；不支持任何类型的“关闭”或“关闭”操作，表示不再添加项目实现是线程安全的；

2、PriorityQueue：
 2.1、基于优先级堆的无限优先级queue 。 优先级队列的元素根据它们的有序natural ordering ，或由一个Comparator在队列构造的时候提供，这取决于所使用的构造方法。 优先队列不允许null元素。 依靠自然排序的优先级队列也不允许插入不可比较的对象（这样做可能导致ClassCastException ）。
 2.2、该队列的头部是相对于指定顺序的最小元素。 如果多个元素被绑定到最小值，那么头就是这些元素之一 - 关系被任意破坏。 队列检索操作poll ， remove ， peek和element访问在队列的头部的元件。
 2.3、优先级队列是无限制的，但是具有管理用于在队列上存储元素的数组的大小的内部容量 。 它始终至少与队列大小一样大。 当元素被添加到优先级队列中时，其容量会自动增长。 没有规定增长政策的细节。
 2.4、该类及其迭代器实现Collection和Iterator接口的所有可选方法。 方法iterator()中提供的迭代器不能保证以任何特定顺序遍历优先级队列的元素。 如果需要有序遍历，请考虑使用Arrays.sort(pq.toArray()) 。
 2.5、请注意，此实现不同步。 如果任何线程修改队列，多线程不应同时访问PriorityQueue实例。 而是使用线程安全的PriorityBlockingQueue类。
 实现注意事项：此实现提供了O（log(n)）的时间入队和出队方法（ offer ， poll ， remove()和add ）; remove(Object)和contains(Object)方法的线性时间; 和恒定时间检索方法（ peek ， element和size ）。

3、ConcurrentLinkedQueue：基于链接节点的无界并发deque(deque是双端队列) 。 并发插入，删除和访问操作可以跨多个线程安全执行。 A ConcurrentLinkedDeque是许多线程将共享对公共集合的访问的适当选择。像大多数其他并发集合实现一样，此类不允许使用null元素。