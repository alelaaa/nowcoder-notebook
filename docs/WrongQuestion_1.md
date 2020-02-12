@[TOC](目录)

## ASCII码值--执行语句“int a= ’ 2 ’ ”后，a的值是（ ）
50。常见字符的ASCII码值如下：空格的ASCII码值为32；数字0到9的ASCII码值分别为48到57；大写字母“A”到“Z”的ASCII码值分别为65到90；小写字母“a”到“z”的ASCII码值分别为97到到122。

## 多线程--执行以下程序，最终输出可能是（*代表空格）：![在这里插入图片描述](https://img-blog.csdnimg.cn/20200212141114758.png)
0012314*01223344**。每个线程输出0，1，2，3，4，’空格， 输出空格前必有线程输出了0-4。

## 形式参数--下列语句正确的是：

 - 形式参数可被字段修饰符修饰
 - 形式参数不可以是对象
 - 形式参数为方法被调用时真正被传递的参数
 - 形式参数可被视为local variable

正确答案: D。
A：形式参数只能被final修饰
B：形式参数可以是对象
C：形式参数被调用时被传递的是实际参数的拷贝
D：local variable：局部变量 

## 类装载器--关于Java中的ClassLoader下面的哪些描述是错误的：( )

 - 默认情况下，Java应用启动过程涉及三个ClassLoader: Boostrap, Extension, System
 - 一般的情况不同ClassLoader装载的类是不相同的，但接口类例外，对于同一接口所有类装载器装载所获得的类是相同的
 - 类装载器需要保证类装载过程的线程安全
 - ClassLoader的loadClass在装载一个类时，如果该类不存在它将返回null
 - ClassLoader的父子结构中，默认装载采用了父优先
 - 所有ClassLoader装载的类都来自CLASSPATH环境指定的路径

正确答案: B D F。
A.Java系统提供3种类加载器：启动类加载器（Bootstrap ClassLoader）  扩展类加载器（Extension ClassLoader） 应用程序类加载器（Application ClassLoader）. A正确
B.《深入理解Java虚拟机》P228：对于任意一个类，都需要由加载它的类加载器和这个类本身一同确立其在Java虚拟机中的唯一性，每一个类加载器，都拥有一个独立的类名称空间。这句话可以表达得更通俗一些：比较两个类是否“相等”，只有在这两个类是由同一个类加载器加载的前提下才有意义，否则，即使这两个类来源于同一个Class文件，被同一个虚拟机加载，只要加载它们的类加载器不同，那么这两个类必定不相等。接口类是一种特殊类，因此对于同一接口不同的类装载器装载所获得的类是不相同的。B错误
C.类只需加载一次就行，因此要保证类加载过程线程安全，防止类加载多次。C正确
D. Java程序的类加载器采用双亲委派模型，实现双亲委派的代码集中在java.lang.ClassLoader的loadClass()方法中，此方法实现的大致逻辑是：先检查是否已经被加载，若没有加载则调用父类加载器的loadClass()方法，若父类加载器为空则默认使用启动类加载器作为父类加载器。如果父类加载失败，抛出ClassNotFoundException异常。D错误
E.双亲委派模型的工作过程：如果一个类加载器收到了类加载的请求，它首先不会自己去尝试加载这个类，而是把这个请求委派给父类加载器去完成，每一个层次的类加载器都是如此，因此所有的加载请求最终都应该传送到顶层的启动类加载器中，只有当父加载器反馈自己无法完成这个加载请求时，子加载器才会尝试自己去加载。E正确
F.应用程序类加载器（Application ClassLoader）负责加载用户类路径（ClassPath）上所指定的类库，不是所有的ClassLoader都加载此路径。F错误

## 符号运算

```java
public class Test{
static{
   int x=5;
}
static int x,y;
public static void main(String args[]){
   x--;
   myMethod( );
   System.out.println(x+y+ ++x);
}
public static void myMethod( ){
  y=x++ + ++x;    //注意这个运算  ++x 已经是x++ 的下一个指令了，因此，x 已经+1
 }
}
```

 - compiletime error
 - prints:1
 - prints:2
 - prints:3
 - prints:7
 - prints:8

正确答案: D。
1.静态语句块中x为局部变量，不影响静态变量x的值
2.x和y为静态变量，默认初始值为0，属于当前类，其值得改变会影响整个类运行。
3.java中自增操作非原子性的 
main方法中：
执行x--后 x=-1
调用myMethod方法，x执行x++结果为-1(后++)，但x=0，++x结果1，x=1 ，则y=0
x+y+ ++x,先执行x+y，结果为1，执行++x结果为2，得到最终结果为3

## switch语句

```java
void main(void) {
    char *s = "1314520";
    int v1 = 0, v2 = 0, v3 = 0, v4 =0;
    for (int i = 0; s[i]; i++) {
        switch(s[i]) {
            default: v4++;
            case '1': v1++;
            case '2': v2++;
            cas3 '3': v3++;
        }
    }
    printf("%d, %d, %d, %d", v4,v1,v2,v3)
}
```

 - 3,5,6,7
 - 7,7,7,7
 - 7,2,1,1
 - 0,2,1,1

正确答案: A。
default顾名思义是缺省情况，只有任何条件都不匹配的情况下才会执行，故会匹配到s[i]为‘4’，‘5’，‘0’ 的情况。于是v4++三次，v4=3.并且这个default后没有使用break语句，于是case‘1’、‘2’、‘3’都会执行三次。注意到所以语句都没有加break，则语句执行过之后会继续下面的case语句，另外由于s[i]中有两个1，故v1,v2,v3此时为5.另外有一个2，v2,v3++后为6，还有一个case3 于是v3++.最终v3为7.

## 正则表达式

以下代码将打印出

```java
 public static void main (String[] args) { 
    String classFile = "com.jd.". replaceAll(".", "/") + "MyClass.class";
    System.out.println(classFile);
}
```

 - com. jd
 - com/jd/MyClass.class
 - ///////MyClass.class
 - com.jd.MyClass

正确答案: C。
由于replaceAll方法的第一个参数是一个正则表达式，而"."在正则表达式中表示任何字符，所以会把前面字符串的所有字符都替换成"/"。如果想替换的只是"."，那么久要写成"\\.".

## 下面有关 JAVA 异常类的描述,说法正确的有()

 - 异常的继承结构:基类为 Throwable,Error 和 Exception 实现 Throwable,RuntimeException
   和 IOException 等继承 Exception
 - 非 RuntimeException 一般是外部错误(不考虑Error的情况下),其必须在当前类被 try{}catch 语句块所捕获
 - Error 类体系描述了 Java 运行系统中的内部错误以及资源耗尽的情形,Error 不需要捕捉
 - RuntimeException 体系包括错误的类型转换、数组越界访问和试图访问空指针等等,必须 被 try{}catch 语句块所捕获

正确答案: A B C。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200212162506992.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FsZWxhXw==,size_16,color_FFFFFF,t_70)
都是Throwable的子类： 
1.Exception（异常） :是程序本身可以处理的异常。 
2.Error（错误）: 是程序无法处理的错误。这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，一般不需要程序处理。
3.检查异常（编译器要求必须处置的异常） ：  除了Error，RuntimeException及其子类以外，其他的Exception类及其子类都属于可查异常。这种异常的特点是Java编译器会检查它，也就是说，当程序中可能出现这类异常，要么用try-catch语句捕获它，要么用throws子句声明抛出它，否则编译不会通过。
4.非检查异常(编译器不要求处置的异常): 包括运行时异常（RuntimeException与其子类）和错误（Error）。

## 从以下哪一个选项中可以获得Servlet的初始化参数?

 - Servlet
 - ServletContext
 - ServletConfig
 - GenericServlet

正确答案: C 。
ServletContext对象：servlet容器在启动时会加载web应用，并为每个web应用创建唯一的servlet context对象，可以把ServletContext看成是一个Web应用的服务器端组件的共享内存，在ServletContext中可以存放共享数据。ServletContext对象是真正的一个全局对象，凡是web容器中的Servlet都可以访问。
   整个web应用只有唯一的一个ServletContext对象
servletConfig对象：用于封装servlet的配置信息。从一个servlet被实例化后，对任何客户端在任何时候访问有效，但仅对servlet自身有效，一个servlet的ServletConfig对象不能被另一个servlet访问。

## 判断一块内存空间是否符合垃圾收集器收集的标准有哪些？

 - 给对象赋予了空值null,以下再没有调用过
 - 对象重新分配了内存空间
 - 给对象赋予了空值null
 - 给对象赋予了新值

正确答案: A B D。
在java语言中，判断一块内存空间是否符合垃圾收集器收集标准的标准只有两个：
1.给对象赋值为null，以下没有调用过。
2.给对象赋了新的值，重新分配了内存空间。