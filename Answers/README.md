# 答案总集

　　Q1:谈谈你对Java垃圾回收机制的理解？

　　答：Java GC 主要针对的是JVM中的堆区和方法区中无用的对象，对其进行回收释放内存。回收时采用的是分代划分，分代收集的方式。它把JVM的堆内存分成了新生代，老生代。新生代又分为Eden,survivor1,survivor2;新生代采取拷贝的方式,每次都是Eden拷到survivor,Eden+survivor拷到另一个survivor,拷贝完后清空原来的无用的对象（Minor GC）.对象存在一定次数转入老生代,老生代采取Mark-Compact（标记-整理）算法。先对内存中存活的对象进行标记，然后把标记的对象都向一端移动，整理成一整块内存区域，再将垃圾对象清除。（Full GC）

　　Q2:接口和抽象类有什么区别？

　　答：首先定义的方式不一样，一个是 abstract class，一个是 interface 。使用的方式不同，抽象类使用extends被继承且，只能继承一个，接口使用implements实现，可以实现多个接口。 抽象类作为类的一种，可以拥有普通方法，成员变量，构造器方法，静态代码块以及静态方法等。而接口只能是public abstract 方法，变量只能是public static final。从概念上讲，接口是一种协议与规范，抽象类则是对一种事物的抽象。

　　Q3：组合与继承有什么区别？

　　答：在概念上，继承是一种是什么的关系。比如A继承B，说明A是B的一种。而组合是一种有什么的关系。比如A组合成B，说明A是B的一部风。在使用上继承易于对父类方法进行重写扩展，但这样也使得父类和子类耦合性更强，破坏了封装性。而组合则不破坏封装，整体类与局部类之间松耦合，彼此相对独立，具有较好的扩展性。而在运行时，动态组合使整体对象可以选择不同类型的局部对象。而在设计原则上则倡导多用组合少用继承，这样实现的系统相对来说拓展性更强，易于修改维护。

　　Q4：线程的实现方式有几种？

　　答：继承Thred类，重写run方法。实现Runnable接口，实现接口的run（）方法。而在Java 1.5 后也可以实现Callable接口，重写call（）方法来实现线程。实现Runnable接口的run方法是无法返回结果值或者抛出异常。而实现Callable接口的call方法可以返回结果值或抛出异常。实现Runnable接口与继承Thread类相比，可以避免java中的单继承的限制，且更适合实现多个相同的程序代码的线程去共享同一个资源。

　　Q5：数据库事务特征有哪些？ 

　　答：事务具有四个特征：原子性、一致性、隔离性和持久性。

　　Q6：Java异常关键字有哪些，作用是什么？

　　答：相关的关键字有throw、throws、try...catch、finally。throws 用在方法签名上, 以便抛出的异常可以被调用者处理。throw 在方法内部通过throw抛出异常。try 用于检测包住的语句块, 若有异常, catch子句捕获并执行catch块。finally不管有没有异常都要处理。当try和catch中有return时，finally仍然会执行，finally是在return后面的表达式运算后执行的。finally不执行的几种情况：程序提前终止如调用了System.exit, 病毒，断电。finally代码块主要用来释放资源，比如：I/O缓冲区，数据库连接。

　　Q7：异常体系是怎么样的，有哪些类型，常见的有那些？

　　![异常继承关系.jpg](https://github.com/suinichange/JavaQuestions100/blob/master/Answers/%E5%BC%82%E5%B8%B8%E7%BB%A7%E6%89%BF%E5%85%B3%E7%B3%BB.jpg)

　　粉红色的是**受检查的异常**(checked exceptions),其必须被try...catch语句块所捕获, 或者在方法签名里通过throws子句声明。受检查的异常必须在编译时被捕捉处理。

　　绿色的异常是**运行时异常**(runtime exceptions), 需要程序员自己分析代码决定是否捕获和处理,比如空指针,被0除...

　　而声明为Error的，则属于严重错误，如系统崩溃、虚拟机错误、动态链接失败等，这些错误无法恢复或者不可能捕捉，将导致应用程序中断，Error不需要捕获。

　　 常见的几种runtime exceptions：

- NullPointerException（空指针引用异常）
- ClassCastException（类型强制转换异常）
- IllegalArgumentException（传递非法参数异常）
- ArithmeticException（算术运算异常）
- IndexOutOfBoundsException（下标越界异常）
- NumberFormatException（数字格式异常）

　　Q8：
