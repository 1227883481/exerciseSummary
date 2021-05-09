# java虚拟机

作为大佬笔记的补充

## 运行时数据内存

运行时数据内存：可以理解为java虚拟机管理的内存。（不重要，他包括的区域划分才重要）

![image-20210503103216426](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210503103216426.png)

## 内存泄漏

什么是内存泄漏（memory leak）？. 指因为疏忽或错误造成程序未能释放已经不再使用的内存的情况。. 内存泄漏并不是指内存在物理上的消失，而是应用程序分配某段内存后，因为设计错误，失去了对该段内存的控制，因而造成了内存的浪费。

## 直接内存的回收

直接内存不能通过垃圾回收释放，之所以垃圾回收之后他也能清理掉，是因为java对象（堆里面的ByteBuffer）被回收，触发了虚引用机制（cleaner），虚引用机制中，虚引用对象关联的实际对象（ByteBuffer）被回收以后，就会调用虚引用对象里面的cleaner方法，执行任务对象，里面有unsafe.freeMemory方法，可以直接内存进行回收。

## 分代垃圾回收-总结

![image-20210507150541597](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210507150541597.png)

## 垃圾回收器

![image-20210507204819250](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210507204819250.png)

## G1的垃圾回收阶段（目前还没有一致的说法）（自己总结记住一种）

## 类文件结构-二进制的字节码文件

![image-20210508133107941](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210508133107941.png)

## 理解一下局部变量槽位和操作数栈

![image-20210508215300995](C:\Users\wang\AppData\Roaming\Typora\typora-user-images\image-20210508215300995.png)

## 类构造器方法<clinit>和实例构造器方法<init>

一个在类初始化的时候执行（针对类中静态的那一套），一个是实例创建的时候调用（非静态的那些变量，方法块，非静态方法里的一系列东西）

类方法，实例方法这两个词语一般也分别指的是静态方法和一般的方法。