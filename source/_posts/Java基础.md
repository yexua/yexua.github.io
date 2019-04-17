---
title: Java基础
date: 2019-03-11 13:57:42
categories: Java基础
tags: 
---



一些Java基础的总结

[![img](https://ws1.sinaimg.cn/large/006QzbZDly1g0yp3blkboj31hc0u0qii.jpg)](https://ws1.sinaimg.cn/large/006QzbZDly1g0yp3blkboj31hc0u0qii.jpg)

<!-- more -->

转自[Github-JavaGuide](https://github.com/Snailclimb/JavaGuide/blob/master/Java/Java%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86.md)并做了一些添加和修改

## 面向对象和面向过程的区别

### 面向过程

**优点：** 性能比面向对象高，因为类调用时需要实例化，开销比较大，比较消耗资源;比如单片机、嵌入式开发、Linux/Unix等一般采用面向过程开发，性能是最重要的因素。

**缺点：** 没有面向对象易维护、易复用、易扩展

### 面向对象

**优点：** 易维护、易复用、易扩展，由于面向对象有封装、继承、多态性的特性，可以设计出低耦合的系统，使系统更加灵活、更加易于维护

**缺点：** 性能比面向过程低

## Java 语言有哪些特点

1. 简单易学；
2. 面向对象（封装，继承，多态）；
3. 平台无关性（ Java 虚拟机实现平台无关性）；
4. 可靠性；
5. 安全性；
6. 支持多线程（ C++ 语言没有内置的多线程机制，因此必须调用操作系统的多线程功能来进行多线程程序设计，而 Java 语言却提供了多线程支持）；
7. 支持网络编程并且很方便（ Java 语言诞生本身就是为简化网络编程设计的，因此 Java 语言不仅支持网络编程而且很方便）；
8. 编译与解释并存；

## 关于 JVM JDK 和 JRE 最详细通俗的解答

### JVM

Java虚拟机（JVM）是运行 Java 字节码的虚拟机。JVM有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码，它们都会给出相同的结果。

**什么是字节码?采用字节码的好处是什么?**

> 在 Java 中，JVM可以理解的代码就叫做`字节码`（即扩展名为 `.class` 的文件），它不面向任何特定的处理器，只面向虚拟机。Java 语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以 Java 程序运行时比较高效，而且，由于字节码并不专对一种特定的机器，因此，Java程序无须重新编译便可在多种不同的计算机上运行。

**Java 程序从源代码到运行一般有下面3步：**

[![Java程序运行过程](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/Java%20%E7%A8%8B%E5%BA%8F%E8%BF%90%E8%A1%8C%E8%BF%87%E7%A8%8B.png)](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/Java%20%E7%A8%8B%E5%BA%8F%E8%BF%90%E8%A1%8C%E8%BF%87%E7%A8%8B.png)

我们需要格外注意的是 .class->机器码 这一步。在这一步 jvm 类加载器首先加载字节码文件，然后通过解释器逐行解释执行，这种方式的执行速度会相对比较慢。而且，有些方法和代码块是经常需要被调用的，也就是所谓的热点代码，所以后面引进了 JIT 编译器，JIT 属于运行时编译。当 JIT 编译器完成第一次编译后，其会将字节码对应的机器码保存下来，下次可以直接使用。而我们知道，机器码的运行效率肯定是高于 Java 解释器的。这也解释了我们为什么经常会说 Java 是编译与解释共存的语言。

> HotSpot采用了惰性评估(Lazy Evaluation)的做法，根据二八定律，消耗大部分系统资源的只有那一小部分的代码（热点代码），而这也就是JIT所需要编译的部分。JVM会根据代码每次被执行的情况收集信息并相应地做出一些优化，因此执行的次数越多，它的速度就越快。JDK 9引入了一种新的编译模式AOT(Ahead of Time Compilation)，它是直接将字节码编译成机器码，这样就避免了JIT预热等各方面的开销。JDK支持分层编译和AOT协作使用。但是 ，AOT 编译器的编译质量是肯定比不上 JIT 编译器的。

总结：Java虚拟机（JVM）是运行 Java 字节码的虚拟机。JVM有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码，它们都会给出相同的结果。字节码和不同系统的 JVM 实现是 Java 语言“一次编译，随处可以运行”的关键所在。

### JDK 和 JRE

JDK是Java Development Kit，它是功能齐全的Java SDK。它拥有JRE所拥有的一切，还有编译器（javac）和工具（如javadoc和jdb）。它能够创建和编译程序。

JRE 是 Java运行时环境。它是运行已编译 Java 程序所需的所有内容的集合，包括 Java虚拟机（JVM），Java类库，java命令和其他的一些基础构件。但是，它不能用于创建新程序。

如果你只是为了运行一下 Java 程序的话，那么你只需要安装 JRE 就可以了。如果你需要进行一些 Java 编程方面的工作，那么你就需要安装JDK了。但是，这不是绝对的。有时，即使您不打算在计算机上进行任何Java开发，仍然需要安装JDK。例如，如果要使用JSP部署Web应用程序，那么从技术上讲，您只是在应用程序服务器中运行Java程序。那你为什么需要JDK呢？因为应用程序服务器会将 JSP 转换为 Java servlet，并且需要使用 JDK 来编译 servlet。

## Oracle JDK 和 OpenJDK 的对比

可能在看这个问题之前很多人和我一样并没有接触和使用过 OpenJDK 。那么Oracle和OpenJDK之间是否存在重大差异？下面通过我通过我收集到一些资料对你解答这个被很多人忽视的问题。

对于Java 7，没什么关键的地方。OpenJDK项目主要基于Sun捐赠的HotSpot源代码。此外，OpenJDK被选为Java 7的参考实现，由Oracle工程师维护。关于JVM，JDK，JRE和OpenJDK之间的区别，Oracle博客帖子在2012年有一个更详细的答案：

> 问：OpenJDK存储库中的源代码与用于构建Oracle JDK的代码之间有什么区别？
>
> 答：非常接近 - 我们的Oracle JDK版本构建过程基于OpenJDK 7构建，只添加了几个部分，例如部署代码，其中包括Oracle的Java插件和Java WebStart的实现，以及一些封闭的源代码派对组件，如图形光栅化器，一些开源的第三方组件，如Rhino，以及一些零碎的东西，如附加文档或第三方字体。展望未来，我们的目的是开z源Oracle JDK的所有部分，除了我们考虑商业功能的部分。

总结：

1. Oracle JDK版本将每三年发布一次，而OpenJDK版本每三个月发布一次；
2. OpenJDK 是一个参考模型并且是完全开源的，而Oracle JDK是OpenJDK的一个实现，并不是完全开源的；
3. Oracle JDK 比 OpenJDK 更稳定。OpenJDK和Oracle JDK的代码几乎相同，但Oracle JDK有更多的类和一些错误修复。因此，如果您想开发企业/商业软件，我建议您选择Oracle JDK，因为它经过了彻底的测试和稳定。某些情况下，有些人提到在使用OpenJDK 可能会遇到了许多应用程序崩溃的问题，但是，只需切换到Oracle JDK就可以解决问题；
4. 在响应性和JVM性能方面，Oracle JDK与OpenJDK相比提供了更好的性能；
5. Oracle JDK不会为即将发布的版本提供长期支持，用户每次都必须通过更新到最新版本获得支持来获取最新版本；
6. Oracle JDK根据二进制代码许可协议获得许可，而OpenJDK根据GPL v2许可获得许可。

## Java和C++的区别

我知道很多人没学过 C++，但是面试官就是没事喜欢拿咱们 Java 和 C++ 比呀！没办法！！！就算没学过C++，也要记下来！

- 都是面向对象的语言，都支持封装、继承和多态
- Java 不提供指针来直接访问内存，程序内存更加安全
- Java 的类是单继承的，C++ 支持多重继承；虽然 Java 的类不可以多继承，但是接口可以多继承。
- Java 有自动内存管理机制，不需要程序员手动释放无用内存

## 什么是 Java 程序的主类 应用程序和小程序的主类有何不同

一个程序中可以有多个类，但只能有一个类是主类。在 Java 应用程序中，这个主类是指包含 main（）方法的类。而在 Java 小程序中，这个主类是一个继承自系统类 JApplet 或 Applet 的子类。应用程序的主类不一定要求是 public 类，但小程序的主类要求必须是 public 类。主类是 Java 程序执行的入口点。

## Java 应用程序与小程序之间有那些差别

简单说应用程序是从主线程启动(也就是 main() 方法)。applet 小程序没有main方法，主要是嵌在浏览器页面上运行(调用init()线程或者run()来启动)，嵌入浏览器这点跟 flash 的小游戏类似。

## 字符型常量和字符串常量的区别

1. 形式上: 字符常量是单引号引起的一个字符 字符串常量是双引号引起的若干个字符
2. 含义上: 字符常量相当于一个整形值( ASCII 值),可以参加表达式运算 字符串常量代表一个地址值(该字符串在内存中存放位置)
3. 占内存大小 字符常量只占2个字节 字符串常量占若干个字节(至少一个字符结束标志) (**注意： char在Java中占两个字节**)

> java编程思想第四版：2.2.2节
> [![img](http://my-blog-to-use.oss-cn-beijing.aliyuncs.com/18-9-15/86735519.jpg)](http://my-blog-to-use.oss-cn-beijing.aliyuncs.com/18-9-15/86735519.jpg)

## 构造器 Constructor 是否可被 override

在讲继承的时候我们就知道父类的私有属性和构造方法并不能被继承，所以 Constructor 也就不能被 override（重写）,但是可以 overload（重载）,所以你可以看到一个类中有多个构造函数的情况。

## 重载和重写的区别

**重载：** 发生在同一个类中，方法名必须相同，参数类型不同、个数不同、顺序不同，方法返回值和访问修饰符可以不同，发生在编译时。 　　

**重写：** 发生在父子类中，方法名、参数列表必须相同，返回值范围小于等于父类，抛出的异常范围小于等于父类，访问修饰符范围大于等于父类；如果父类方法访问修饰符为 private 则子类就不能重写该方法。

## Java 面向对象编程三大特性: 封装 继承 多态

### 封装

封装把一个对象的属性私有化，同时提供一些可以被外界访问的属性的方法，如果属性不想被外界访问，我们大可不必提供方法给外界访问。但是如果一个类没有提供给外界访问的方法，那么这个类也没有什么意义了。

### 继承

继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。通过使用继承我们能够非常方便地复用以前的代码。

**关于继承如下 3 点请记住：**

1. 子类拥有父类非 private 的属性和方法。
2. 子类可以拥有自己属性和方法，即子类可以对父类进行扩展。
3. 子类可以用自己的方式实现父类的方法。（以后介绍）。

### 多态

所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量到底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。

在Java中有两种形式可以实现多态：继承（多个子类对同一方法的重写）和接口（实现接口并覆盖接口中同一方法）。

## String StringBuffer 和 StringBuilder 的区别是什么 String 为什么是不可变的

**可变性** 　

简单的来说：String 类中使用 final 关键字字符数组保存字符串，`private　final　char　value[]`，所以 String 对象是不可变的。而StringBuilder 与 StringBuffer 都继承自 AbstractStringBuilder 类，在 AbstractStringBuilder 中也是使用字符数组保存字符串`char[]value` 但是没有用 final 关键字修饰，所以这两种对象都是可变的。

StringBuilder 与 StringBuffer 的构造方法都是调用父类构造方法也就是 AbstractStringBuilder 实现的，大家可以自行查阅源码。

AbstractStringBuilder.java

```
abstract class AbstractStringBuilder implements Appendable, CharSequence {
    char[] value;
    int count;
    AbstractStringBuilder() {
    }
    AbstractStringBuilder(int capacity) {
        value = new char[capacity];
    }
}
```

**线程安全性**

String 中的对象是不可变的，也就可以理解为常量，线程安全。AbstractStringBuilder 是 StringBuilder 与 StringBuffer 的公共父类，定义了一些字符串的基本操作，如 expandCapacity、append、insert、indexOf 等公共方法。StringBuffer 对方法加了同步锁或者对调用的方法加了同步锁，所以是线程安全的。StringBuilder 并没有对方法进行加同步锁，所以是非线程安全的。 　　

**性能**

每次对 String 类型进行改变的时候，都会生成一个新的 String 对象，然后将指针指向新的 String 对象。StringBuffer 每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象并改变对象引用。相同情况下使用 StringBuilder 相比使用 StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。

**对于三者使用的总结：**

1. 操作少量的数据 = String
2. 单线程操作字符串缓冲区下操作大量数据 = StringBuilder
3. 多线程操作字符串缓冲区下操作大量数据 = StringBuffer

## Java支持的数据类型有哪些？ 自动装箱与拆箱

基本数据类型：

整数值型：byte,short,int,long,

字符型：char

浮点类型：float,double

布尔型：boolean

整数默认int型，小数默认是double型。Float和long类型的必须加后缀。

首先知道String是引用类型不是基本类型，引用类型声明的变量是指该变量在内存中实际存储的是一个引用地址，实体在堆中。引用类型包括类、接口、数组等。String类还是final修饰的。 而包装类就属于引用类型，自动装箱和拆箱就是基本类型和引用类型之间的转换，至于为什么要转换，因为基本类型转换为引用类型后，就可以new对象，从而调用包装类中封装好的方法进行基本类型之间的转换或者toString（当然用类名直接调用也可以，便于一眼看出该方法是静态的），还有就是如果集合中想存放基本类型，泛型的限定类型只能是对应的包装类型。

**装箱**：将基本类型用它们对应的引用类型包装起来；

**拆箱**：将包装类型转换为基本数据类型；

## ”static”关键字是什么意思？Java中是否可以覆盖(override)一个private或者是static的方法？

Static表示静态的意思，可用于修饰成员变量和成员函数，被静态修饰的成员函数只能访问静态成员，不可以访问非静态成员。静态是随着类的加载而加载的，因此可以直接用类进行访问。 重写是子类中的方法和子类继承的父类中的方法一样（函数名，参数，参数类型，反回值类型），但是子类中的访问权限要不低于父类中的访问权限。重写的前提是必须要继承，private修饰不支持继承，因此被私有的方法不可以被重写。静态方法形式上可以被重写，即子类中可以重写父类中静态的方法。但是实际上从内存的角度上静态方法不可以被重写。

## 在 Java 中定义一个不做事且没有参数的构造方法的作用

　Java 程序在执行子类的构造方法之前，如果没有用 super() 来调用父类特定的构造方法，则会调用父类中“没有参数的构造方法”。因此，如果父类中只定义了有参数的构造方法，而在子类的构造方法中又没有用 super() 来调用父类中特定的构造方法，则编译时将发生错误，因为 Java 程序在父类中找不到没有参数的构造方法可供执行。解决办法是在父类里加上一个不做事且没有参数的构造方法。

## Java中的方法重写(Overriding)和方法重载(Overload)是什么意思？

### 方法重写的原则：

1. 重写方法的方法名称、参数列表必须与原方法的相同，返回类型可以相同也可以是原类型的子类型(从Java SE5开始支持)。
2. 重写方法不能比原方法访问性差（即访问权限不允许缩小）。
3. 重写方法不能比原方法抛出更多的异常。
4. 被重写的方法不能是final类型，因为final修饰的方法是无法重写的。
5. 被重写的方法不能为private，否则在其子类中只是新定义了一个方法，并没有对其进行重写。
6. 被重写的方法不能为static。如果父类中的方法为静态的，而子类中的方法不是静态的，但是两个方法除了这一点外其他都满足重写条件，那么会发生编译错误；反之亦然。即使父类和子类中的方法都是静态的，并且满足重写条件，但是仍然不会发生重写，因为静态方法是在编译的时候把静态方法和类的引用类型进行匹配。
7. 重写是发生在运行时的，因为编译期编译器不知道并且没办法确定该去调用哪个方法，JVM会在代码运行的时候作出决定。

### 方法重载的原则：

1. 方法名称必须相同。
2. 参数列表必须不同（个数不同、或类型不同、参数类型排列顺序不同等）。
3. 方法的返回类型可以相同也可以不相同。
4. 仅仅返回类型不同不足以成为方法的重载。
5. 重载是发生在编译时的，因为编译器可以根据参数的类型来选择使用哪个方法。

### 重写和重载的不同：

1. 方法重写要求参数列表必须一致，而方法重载要求参数列表必须不一致。
2. 方法重写要求返回类型必须一致(或为其子类型)，方法重载对此没有要求。
3. 方法重写只能用于子类重写父类的方法，方法重载用于同一个类中的所有方法。
4. 方法重写对方法的访问权限和抛出的异常有特殊的要求，而方法重载在这方面没有任何限制。
5. 父类的一个方法只能被子类重写一次，而一个方法可以在所有的类中可以被重载多次。
6. 重载是编译时多态，重写是运行时多态。　

## import java和javax有什么区别

刚开始的时候 JavaAPI 所必需的包是 java 开头的包，javax 当时只是扩展 API 包来说使用。然而随着时间的推移，javax 逐渐的扩展成为 Java API 的组成部分。但是，将扩展从 javax 包移动到 java 包将是太麻烦了，最终会破坏一堆现有的代码。因此，最终决定 javax 包将成为标准API的一部分。

所以，实际上java和javax没有区别。这都是一个名字。

## 关于 final 关键字的一些总结

final关键字主要用在三个地方：变量、方法、类。

1. 对于一个final变量，如果是基本数据类型的变量，则其数值一旦在初始化之后便不能更改；如果是引用类型的变量，则在对其初始化之后便不能再让其指向另一个对象。
2. 当用final修饰一个类时，表明这个类不能被继承。final类中的所有成员方法都会被隐式地指定为final方法。
3. 使用final方法的原因有两个。第一个原因是把方法锁定，以防任何继承类修改它的含义；第二个原因是效率。在早期的Java实现版本中，会将final方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升（现在的Java版本已经不需要使用final方法进行这些优化了）。类中所有的private方法都隐式地指定为final。

## 接口和抽象类的区别是什么

1. 接口的方法默认是 public，所有方法在接口中不能有实现(Java 8 开始接口方法可以有默认实现），抽象类可以有非抽象的方法
2. 接口中的实例变量默认是 final 类型的，而抽象类中则不一定
3. 一个类可以实现多个接口，但最多只能实现一个抽象类
4. 一个类实现接口的话要实现接口的所有方法，而抽象类不一定
5. 接口不能用 new 实例化，但可以声明，但是必须引用一个实现该接口的对象 从设计层面来说，抽象是对类的抽象，是一种模板设计，接口是行为的抽象，是一种行为的规范。

备注:在JDK8中，接口也可以定义静态方法，可以直接用接口名调用。实现类和实现是不可以调用的。如果同时实现两个接口，接口中定义了一样的默认方法，必须重写，不然会报错。(详见issue:<https://github.com/Snailclimb/JavaGuide/issues/146>)

## 成员变量与局部变量的区别有那些

1. 从语法形式上，看成员变量是属于类的，而局部变量是在方法中定义的变量或是方法的参数；成员变量可以被 public,private,static 等修饰符所修饰，而局部变量不能被访问控制修饰符及 static 所修饰；但是，成员变量和局部变量都能被 final 所修饰；
2. 从变量在内存中的存储方式来看:如果成员变量是使用`static`修饰的，那么这个成员变量是属于类的，如果没有使用使用`static`修饰，这个成员变量是属于实例的。而对象存在于堆内存，局部变量存在于栈内存
3. 从变量在内存中的生存时间上看:成员变量是对象的一部分，它随着对象的创建而存在，而局部变量随着方法的调用而自动消失。
4. 成员变量如果没有被赋初值:则会自动以类型的默认值而赋值（一种情况例外被 final 修饰的成员变量也必须显示地赋值）；而局部变量则不会自动赋值。

## 创建一个对象用什么运算符?对象实体与对象引用有何不同?

new运算符，new创建对象实例（对象实例在堆内存中），对象引用指向对象实例（对象引用存放在栈内存中）。一个对象引用可以指向0个或1个对象（一根绳子可以不系气球，也可以系一个气球）;一个对象可以有n个引用指向它（可以用n条绳子系住一个气球）。

## 什么是方法的返回值?返回值在类的方法里的作用是什么?

方法的返回值是指我们获取到的某个方法体中的代码执行后产生的结果！（前提是该方法可能产生结果）。返回值的作用:接收出结果，使得它可以用于其他的操作！

## 一个类的构造方法的作用是什么 若一个类没有声明构造方法,该程序能正确执行吗 ?为什么?

主要作用是完成对类对象的初始化工作。可以执行。因为一个类即使没有声明构造方法也会有默认的不带参数的构造方法。

## 构造方法有哪些特性

1. 名字与类名相同；
2. 没有返回值，但不能用void声明构造函数；
3. 生成类的对象时自动执行，无需调用。

## 静态方法和实例方法有何不同

1. 在外部调用静态方法时，可以使用”类名.方法名”的方式，也可以使用”对象名.方法名”的方式。而实例方法只有后面这种方式。也就是说，调用静态方法可以无需创建对象。
2. 静态方法在访问本类的成员时，只允许访问静态成员（即静态成员变量和静态方法），而不允许访问实例成员变量和实例方法；实例方法则无此限制.

## 对象的相等与指向他们的引用相等,两者有什么不同?

对象的相等，比的是内存中存放的内容是否相等。而引用相等，比较的是他们指向的内存地址是否相等。

## 在调用子类构造方法之前会先调用父类没有参数的构造方法,其目的是?

帮助子类做初始化工作。

## 继承和多态

类的 复用有两种方式：组成(has-a)和继承(is-a) 1）组成就是在新的类中直接创建旧类的对象，这里我们复用的只是代码的功能而不是它的形式。 2）继承是在原有的类的基础上建立一个新类，新类具有旧类的形式，但也加入了一些新的特性。

继承：指一个新的类继承原有类的基本特性，并增加了新的特性。（Java不允许多继承，而C++可以）

多态性： 指允许不同类的对象对同一消息做出响应。即同一消息可以根据发送对象的不同而采用多种不同的行为方式。

1）多态存在的三个必要条件

①要有继承 ②要有重写 ③父类引用指向子类对象（向上转型）

2）实现多态性的三种形式

①方法的重载 ②通过继承机制而产生方法覆盖 ③通过接口实现方法覆盖

3）多态的分类

多态分为编译时多态和运行时多态。其中编译 时多态是静态的，主要是指方法的重载，它是根据参数列表的不同来区分不同的函数，通过编译之后会变成两个不同的函数，在运行时谈不上多态。而运行时多态是动态的，它是通过动态绑定来实现的，也就是我们平常所说的多态性。

## == 与 equals的区别

**==** : 它的作用是判断两个对象的地址是不是相等。即，判断两个对象是不是同一个对象。(基本数据类型==比较的是值，引用数据类型==比较的是内存地址)

**equals()** : 它的作用也是判断两个对象是否相等。但它一般有两种使用情况：

- 情况1：类没有覆盖 equals() 方法。则通过 equals() 比较该类的两个对象时，等价于通过“==”比较这两个对象。
- 情况2：类覆盖了 equals() 方法。一般，我们都覆盖 equals() 方法来两个对象的内容相等；若它们的内容相等，则返回 true (即，认为这两个对象相等)。

**举个例子：**

```
public class test1 {
    public static void main(String[] args) {
        String a = new String("ab"); // a 为一个引用
        String b = new String("ab"); // b为另一个引用,对象的内容一样
        String aa = "ab"; // 放在常量池中
        String bb = "ab"; // 从常量池中查找
        if (aa == bb) // true
            System.out.println("aa==bb");
        if (a == b) // false，非同一对象
            System.out.println("a==b");
        if (a.equals(b)) // true
            System.out.println("aEQb");
        if (42 == 42.0) { // true
            System.out.println("true");
        }
    }
}
```

**说明：**

- String 中的 equals 方法是被重写过的，因为 object 的 equals 方法是比较的对象的内存地址，而 String 的 equals 方法比较的是对象的值。
- 当创建 String 类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对象，如果有就把它赋给当前引用。如果没有就在常量池中重新创建一个 String 对象。

## hashCode 与 equals

面试官可能会问你：“你重写过 hashcode 和 equals 么，为什么重写equals时必须重写hashCode方法？”

### hashCode（）介绍

hashCode() 的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode() 定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode() 函数。

散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！（可以快速找到所需要的对象）

### 为什么要有 hashCode

**我们以“HashSet 如何检查重复”为例子来说明为什么要有 hashCode：**

当你把对象加入 HashSet 时，HashSet 会先计算对象的 hashcode 值来判断对象加入的位置，同时也会与其他已经加入的对象的 hashcode 值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同 hashcode 值的对象，这时会调用 equals（）方法来检查 hashcode 相等的对象是否真的相同。如果两者相同，HashSet 就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。（摘自我的Java启蒙书《Head first java》第二版）。这样我们就大大减少了 equals 的次数，相应就大大提高了执行速度。

### hashCode（）与equals（）的相关规定

1. 如果两个对象相等，则hashcode一定也是相同的
2. 两个对象相等,对两个对象分别调用equals方法都返回true
3. 两个对象有相同的hashcode值，它们也不一定是相等的
4. **因此，equals 方法被覆盖过，则 hashCode 方法也必须被覆盖**
5. hashCode() 的默认行为是对堆上的对象产生独特值。如果没有重写 hashCode()，则该 class 的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）

------

## 为什么Java中只有值传递

[为什么Java中只有值传递？](https://github.com/Snailclimb/Java-Guide/blob/master/%E9%9D%A2%E8%AF%95%E5%BF%85%E5%A4%87/%E6%9C%80%E6%9C%80%E6%9C%80%E5%B8%B8%E8%A7%81%E7%9A%84Java%E9%9D%A2%E8%AF%95%E9%A2%98%E6%80%BB%E7%BB%93/%E7%AC%AC%E4%B8%80%E5%91%A8%EF%BC%882018-8-7%EF%BC%89.md)

### Java集合类框架的基本接口有哪些？

总共有两大接口：Collection 和Map ，一个元素集合，一个是键值对集合； 其中List和Set接口继承了Collection接口，一个是有序元素集合，一个是无序元素集合； 而ArrayList和 LinkedList 实现了List接口，HashSet实现了Set接口，这几个都比较常用； HashMap 和HashTable实现了Map接口，并且HashTable是线程安全的，但是HashMap性能更好；

#### java.util.Collection [I]

```
|—java.util.List [I]

    |—java.util.ArrayList [C]

    |—java.util.LinkedList [C]

    |—java.util.Vector [C]

        |—java.util.Stack [C]

|—java.util.Set [I]

    |—java.util.HashSet [C]

    |—java.util.SortedSet [I]

        |—java.util.TreeSet [C]
```

#### java.util.Map [I]

```
|—java.util.SortedMap [I]

    |—java.util.TreeMap [C]

|—java.util.Hashtable [C]

|—java.util.HashMap [C]

    |—java.util.LinkedHashMap [C]

|—java.util.WeakHashMap [C]
```

[![img](https://ws1.sinaimg.cn/large/006QzbZDly1g0z42z57z5j30sz0p776p.jpg)](https://ws1.sinaimg.cn/large/006QzbZDly1g0z42z57z5j30sz0p776p.jpg)
[![img](https://ws1.sinaimg.cn/large/006QzbZDly1g0z40z6dlpj315b0lxn01.jpg)](https://ws1.sinaimg.cn/large/006QzbZDly1g0z40z6dlpj315b0lxn01.jpg)

## 为什么集合类没有实现Cloneable和Serializable接口？

克隆(cloning)或者是序列化(serialization)的语义和含义是跟具体的实现相关的。因此，应该由集合类的具体实现来决定如何被克隆或者是序列化。
实现Serializable序列化的作用
将对象的状态保存在存储媒体中以便可以在以后重写创建出完全相同的副本；
按值将对象从一个从一个应用程序域发向另一个应用程序域。
实现 Serializable接口的作用就是可以把对象存到字节流，然后可以恢复。所以你想如果你的对象没有序列化，怎么才能进行网络传输呢？要网络传输就得转为字节流，所以在分布式应用中，你就得实现序列化。如果你不需要分布式应用，那就没必要实现实现序列化。

------

## 什么是迭代器(Iterator)？

迭代器是一种设计模式，它是一个对象，它可以遍历并选择序列中的对象，而开发人员不需要了解该序列的底层结构。迭代器通常被称为“轻量级”对象，因为创建它的代价小。

Java中的Iterator功能比较简单，并且只能单向移动：

(1) 使用方法iterator()要求容器返回一个Iterator。第一次调用Iterator的next()方法时，它返回序列的第一个元素。注意：iterator()方法是java.lang.Iterable接口,被Collection继承。

(2) 使用next()获得序列中的下一个元素。

(3) 使用hasNext()检查序列中是否还有元素。

(4) 使用remove()将迭代器新返回的元素删除。

Iterator是Java迭代器最简单的实现，为List设计的ListIterator具有更多的功能，它可以从两个方向遍历List，也可以从List中插入和删除元素。

------

## Iterator和ListIterator的区别是什么？

我们在使用List,Set的时候,为了实现对其数据的遍历,我们经常使用到了Iterator(迭代器)。 使用迭代器，你不需要干涉其遍历的过程，只需要每次取出一个你想要的数据进行处理就可以了。但是在使用的时候也是有不同的。 List和Set都有iterator()来取得其迭代器。对List来说，你也可以通过listIterator()取得其迭代器，两种迭代器在有些时候是不能通用的，Iterator和ListIterator主要区别在以下方面：

1. `ListIterator`有add()方法，可以向List中添加对象，而Iterator不能
2. `ListIterator`和`Iterator`都有hasNext()和next()方法，可以实现顺序向后遍历，但是`ListIterator`有hasPrevious()和previous()方法，可以实现逆向（顺序向前）遍历。`Iterator`就不可以。
3. `ListIterator`可以定位当前的索引位置，nextIndex()和previousIndex()可以实现。Iterator没有此功能。
4. 都可实现删除对象，但是`ListIterator`可以实现对象的修改，set()方法可以实现。`Iierator`仅能遍历，不能修改。 因为`ListIterator`的这些功能，可以实现对`LinkedList`等`List`数据结构的操作。 其实,数组对象也可以用迭代器来实现。 `org.apache.commons.collections.iterators.ArrayIterator`就可以实现此功能。 一般情况下，我们使用Iterator就可以了，如果你需要进行记录的前后反复检索的话，你就可以使用`ListIterator`来扩展你的功能，（有点象JDBC中的滚动结果集）。 `ListIterator`是一个双向迭代器。`ListIterator`没有当前元素，它的当前游标是位于调用`next()`和`previsous()`返回的元素之间。不过下面举的例子有点问题：下面的例子是n+1个元素。如果有n个元素，那么游标索引就是0…n共n+1个。 注意：romove和set方法不是针对当前游标的操作，而是针对最后一次的`next()`或者`previous()`调用`Iterator`，`ListIterator`

## 简述线程,程序,进程的基本概念.以及他们之间关系是什么?

**线程**与进程相似，但线程是一个比进程更小的执行单位。一个进程在其执行的过程中可以产生多个线程。与进程不同的是同类的多个线程共享同一块内存空间和一组系统资源，所以系统在产生一个线程，或是在各个线程之间作切换工作时，负担要比进程小得多，也正因为如此，线程也被称为轻量级进程。

**程序**是含有指令和数据的文件，被存储在磁盘或其他的数据存储设备中，也就是说程序是静态的代码。

**进程**是程序的一次执行过程，是系统运行程序的基本单位，因此进程是动态的。系统运行一个程序即是一个进程从创建，运行到消亡的过程。简单来说，一个进程就是一个执行中的程序，它在计算机中一个指令接着一个指令地执行着，同时，每个进程还占有某些系统资源如CPU时间，内存空间，文件，文件，输入输出设备的使用权等等。换句话说，当程序在执行时，将会被操作系统载入内存中。
线程是进程划分成的更小的运行单位。线程和进程最大的不同在于基本上各进程是独立的，而各线程则不一定，因为同一进程中的线程极有可能会相互影响。从另一角度来说，进程属于操作系统的范畴，主要是同一段时间内，可以同时执行一个以上的程序，而线程则是在同一程序内几乎同时执行一个以上的程序段。

### 进程和线程的区别

1. 进程是运行中的程序，线程是进程的内部的一个执行序列
2. 进程是资源分配的单元，线程是执行行单元
3. 进程间切换代价大，线程间切换代价小
4. 进程拥有资源多，线程拥有资源少
5. 多个线程共享进程的资源

## 创建线程有哪几种方式？

①继承Thread类（真正意义上的线程类），是Runnable接口的实现。

②实现Runnable接口，并重写里面的run方法。

③使用Executor框架创建线程池。Executor框架是juc里提供的线程池的实现。

调用线程的start()：启动此线程；调用相应的run()方法

继承于Thread类的线程类，可以直接调用start方法启动线程（使用static也可以实现资源共享）.一个线程（对象）只能够执行一次start()，而且不能通过Thread实现类对象的run()去启动一个线程。

实现Runnable接口的类需要再次用Thread类包装后才能调用start方法。（三个Thread对象包装一个类对象，就实现了资源共享）。

线程的使用的话，注意锁和同步的使用。（多线程访问共享资源容易出现线程安全问题）

一般情况下，常见的是第二种。

- Runnable接口有如下好处：

*①避免点继承的局限，一个类可以继承多个接口。

*②适合于资源的共享

/*

- Thread的常用方法：
- 1.start()：启动线程并执行相应的run()方法
- 2.run():子线程要执行的代码放入run()方法中
- 3.currentThread()：静态的，调取当前的线程
- 4.getName():获取此线程的名字
- 5.setName():设置此线程的名字
- 6.yield():调用此方法的线程释放当前CPU的执行权（很可能自己再次抢到资源）
- 7.join():在A线程中调用B线程的join()方法，表示：当执行到此方法，A线程停止执行，直至B线程执行完毕，
- A线程再接着join()之后的代码执行
- 8.isAlive():判断当前线程是否还存活
- 9.sleep(long l):显式的让当前线程睡眠l毫秒 (只能捕获异常，因为父类run方法没有抛异常)
- 10.线程通信（方法在Object类中）：wait() notify() notifyAll()
- 

*设置线程的优先级（非绝对，只是相对几率大些）

- getPriority()：返回线程优先值
- setPriority(int newPriority)：改变线程的优先级

*/

## 线程有哪些基本状态?

Java 线程在运行的生命周期中的指定时刻只可能处于下面6种不同状态的其中一个状态（图源《Java 并发编程艺术》4.1.4节）。

[![Java线程的状态](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/19-1-29/Java%E7%BA%BF%E7%A8%8B%E7%9A%84%E7%8A%B6%E6%80%81.png)](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/19-1-29/Java%E7%BA%BF%E7%A8%8B%E7%9A%84%E7%8A%B6%E6%80%81.png)

线程在生命周期中并不是固定处于某一个状态而是随着代码的执行在不同状态之间切换。Java 线程状态变迁如下图所示（图源《Java 并发编程艺术》4.1.4节）：

[![Java线程状态变迁](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/19-1-29/Java%20%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E5%8F%98%E8%BF%81.png)](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/19-1-29/Java%20%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E5%8F%98%E8%BF%81.png)

由上图可以看出：

线程创建之后它将处于 **NEW（新建）** 状态，调用 `start()` 方法后开始运行，线程这时候处于 **READY（可运行）** 状态。可运行状态的线程获得了 cpu 时间片（timeslice）后就处于 **RUNNING（运行）** 状态。

> 操作系统隐藏 Java虚拟机（JVM）中的 RUNNABLE 和 RUNNING 状态，它只能看到 RUNNABLE 状态（图源：[HowToDoInJava](https://howtodoinjava.com/)：[Java Thread Life Cycle and Thread States](https://howtodoinjava.com/java/multi-threading/java-thread-life-cycle-and-thread-states/)），所以 Java 系统一般将这两个状态统称为 **RUNNABLE（运行中）** 状态 。

[![RUNNABLE-VS-RUNNING](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-3/RUNNABLE-VS-RUNNING.png)](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-3/RUNNABLE-VS-RUNNING.png)

当线程执行 `wait()`方法之后，线程进入 **WAITING（等待）**状态。进入等待状态的线程需要依靠其他线程的通知才能够返回到运行状态，而 **TIME_WAITING(超时等待)** 状态相当于在等待状态的基础上增加了超时限制，比如通过 `sleep（long millis）`方法或 `wait（long millis）`方法可以将 Java 线程置于 TIMED WAITING 状态。当超时时间到达后 Java 线程将会返回到 RUNNABLE 状态。当线程调用同步方法时，在没有获取到锁的情况下，线程将会进入到 **BLOCKED（阻塞）** 状态。线程在执行 Runnable 的`run()`方法之后将会进入到 **TERMINATED（终止）** 状态。

## 同步方法和同步代码块的区别是什么？

为何要使用同步？ java允许多线程并发控制，当多个线程同时操作一个可共享的资源变量时（如数据的增删改查）， 将会导致数据不准确，相互之间产生冲突，因此加入同步锁以避免在该线程没有完成操作之前，被其他线程的调用， 从而保证了该变量的唯一性和准确性。

1.同步方法 即有synchronized关键字修饰的方法。 由于java的每个对象都有一个内置锁，当用此关键字修饰方法时， 内置锁会保护整个方法。在调用该方法前，需要获得内置锁，否则就处于阻塞状态。

```
代码如： 
public synchronized void save(){}
```

注： synchronized关键字也可以修饰静态方法，此时如果调用该静态方法，将会锁住整个类

2.同步代码块 即有synchronized关键字修饰的语句块。 被该关键字修饰的语句块会自动被加上内置锁，从而实现同步

```
代码如： 
synchronized(object){ 
}

注：同步是一种高开销的操作，因此应该尽量减少同步的内容。 
通常没有必要同步整个方法，使用synchronized代码块同步关键代码即可。
```

3.使用特殊域变量(volatile)实现线程同步

```
a.volatile关键字为域变量的访问提供了一种免锁机制， 
b.使用volatile修饰域相当于告诉虚拟机该域可能会被其他线程更新， 
c.因此每次使用该域就要重新计算，而不是使用寄存器中的值 
d.volatile不会提供任何原子操作，它也不能用来修饰final类型的变量 

注：volatile 只能保证可见性和有序，无法保证原子性操作
```

4.使用重入锁实现线程同步

```
在JavaSE5.0中新增了一个java.util.concurrent包来支持同步。 
ReentrantLock类是可重入、互斥、实现了Lock接口的锁， 
它与使用synchronized方法和快具有相同的基本行为和语义，并且扩展了其能力

ReenreantLock类的常用方法有：

    ReentrantLock() : 创建一个ReentrantLock实例 
    lock() : 获得锁 
    unlock() : 释放锁 
注：ReentrantLock()还有一个可以创建公平锁的构造方法，但由于能大幅度降低程序运行效率，不推荐使用
```

注：关于Lock对象和synchronized关键字的选择： a.最好两个都不用，使用一种java.util.concurrent包提供的机制， 能够帮助用户处理所有与锁相关的代码。 b.如果synchronized关键字能满足用户的需求，就用synchronized，因为它能简化代码 c.如果需要更高级的功能，就用ReentrantLock类，此时要注意及时释放锁，否则会出现死锁，通常在finally代码释放锁

5.使用局部变量实现线程同步 如果使用ThreadLocal管理变量，则每一个使用该变量的线程都获得该变量的副本， 副本之间相互独立，这样每一个线程都可以随意修改自己的变量副本，而不会对其他线程产生影响。

```
ThreadLocal 类的常用方法

ThreadLocal() : 创建一个线程本地变量 
get() : 返回此线程局部变量的当前线程副本中的值 
initialValue() : 返回此线程局部变量的当前线程的"初始值" 
set(T value) : 将此线程局部变量的当前线程副本中的值设置为value
```

注：ThreadLocal与同步机制 a.ThreadLocal与同步机制都是为了解决多线程中相同变量的访问冲突问题。 b.前者采用以”空间换时间”的方法，后者采用以”时间换空间”的方式

## Java 中的异常处理

### Java异常类层次结构图

[![Java异常类层次结构图](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-2/Exception.png)](https://my-blog-to-use.oss-cn-beijing.aliyuncs.com/2019-2/Exception.png)
在 Java 中，所有的异常都有一个共同的祖先java.lang包中的 **Throwable类**。Throwable： 有两个重要的子类：**Exception（异常）** 和 **Error（错误）** ，二者都是 Java 异常处理的重要子类，各自都包含大量子类。

**Error（错误）:是程序无法处理的错误**，表示运行应用程序中较严重问题。大多数错误与代码编写者执行的操作无关，而表示代码运行时 JVM（Java 虚拟机）出现的问题。例如，Java虚拟机运行错误（Virtual MachineError），当 JVM 不再有继续执行操作所需的内存资源时，将出现 OutOfMemoryError。这些异常发生时，Java虚拟机（JVM）一般会选择线程终止。

这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，如Java虚拟机运行错误（Virtual MachineError）、类定义错误（NoClassDefFoundError）等。这些错误是不可查的，因为它们在应用程序的控制和处理能力之 外，而且绝大多数是程序运行时不允许出现的状况。对于设计合理的应用程序来说，即使确实发生了错误，本质上也不应该试图去处理它所引起的异常状况。在 Java中，错误通过Error的子类描述。

**Exception（异常）:是程序本身可以处理的异常**。Exception 类有一个重要的子类 **RuntimeException**。RuntimeException 异常由Java虚拟机抛出。**NullPointerException**（要访问的变量没有引用任何对象时，抛出该异常）、**ArithmeticException**（算术运算异常，一个整数除以0时，抛出该异常）和 **ArrayIndexOutOfBoundsException** （下标越界异常）。

**注意：异常和错误的区别：异常能被程序本身可以处理，错误是无法处理。**

### Throwable类常用方法

- **public string getMessage()**:返回异常发生时的详细信息
- **public string toString()**:返回异常发生时的简要描述
- **public string getLocalizedMessage()**:返回异常对象的本地化信息。使用Throwable的子类覆盖这个方法，可以声称本地化信息。如果子类没有覆盖该方法，则该方法返回的信息与getMessage（）返回的结果相同
- **public void printStackTrace()**:在控制台上打印Throwable对象封装的异常信息

### 异常处理总结

- **try 块：**用于捕获异常。其后可接零个或多个catch块，如果没有catch块，则必须跟一个finally块。
- **catch 块：**用于处理try捕获到的异常。
- **finally 块：**无论是否捕获或处理异常，finally块里的语句都会被执行。当在try块或catch块中遇到return语句时，finally语句块将在方法返回之前被执行。

**在以下4种特殊情况下，finally块不会被执行：**

1. 在finally语句块第一行发生了异常。 因为在其他行，finally块还是会得到执行
2. 在前面的代码中用了System.exit(int)已退出程序。 exit是带参函数 ；若该语句在异常语句之后，finally会执行
3. 程序所在的线程死亡。
4. 关闭CPU。

下面这部分内容来自issue:<https://github.com/Snailclimb/JavaGuide/issues/190>。

**关于返回值：**

如果try语句里有return，返回的是try语句块中变量值。
详细执行过程如下：

1. 如果有返回值，就把返回值保存到局部变量中；
2. 执行jsr指令跳到finally语句里执行；
3. 执行完finally语句后，返回之前保存在局部变量表里的值。
4. 如果try，finally语句里均有return，忽略try的return，而使用finally的return.

## Java序列化中如果有些字段不想进行序列化 怎么办

对于不想进行序列化的变量，使用transient关键字修饰。

transient关键字的作用是：阻止实例中那些用此关键字修饰的的变量序列化；当对象被反序列化时，被transient修饰的变量值不会被持久化和恢复。transient只能修饰变量，不能修饰类和方法。

## 获取用键盘输入常用的的两种方法

方法1：通过 Scanner

```
Scanner input = new Scanner(System.in);
String s  = input.nextLine();
input.close();
```

方法2：通过 BufferedReader

```
BufferedReader input = new BufferedReader(new InputStreamReader(System.in)); 
String s = input.readLine();
```

## 参考

- <https://stackoverflow.com/questions/1906445/what-is-the-difference-between-jdk-and-jre>
- <https://www.educba.com/oracle-vs-openjdk/>
- <https://stackoverflow.com/questions/22358071/differences-between-oracle-jdk-and-openjdk?answertab=active#tab-top>