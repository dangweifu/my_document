相关书籍：
Java虚拟机规范(Java SE 8版)
深入理解Java虚拟机-JVM高级特性与最佳实践(第二版)
深入理解Java虚拟机-JVM高级特性与最佳实践(第三版)
深入理解JVM & G1GC
揭秘Java虚拟机 JVM设计原理与实现
Java虚拟机基础教程
实战Java虚拟机 JVM故障诊断与性能优化
Java虚拟机精讲
码出高效Java开发手册 Easy Coding


JVM规范 -> JVM虚拟机(规范的实现) ，不同厂商有不同的实现，也就是不同版本的JVM

#JVM架构模型
##基于栈的指令集架构
+ 设计呵呵实现更简单，适用于资源受限的系统；
+ 避开了寄存器的分配难题：使用零地址指令方式分配。
+ 指令流中的指令大部分都是零地址指令，其执行过程依赖于操作栈。指令集更小，编译器容易实现。
+ 不需要硬件支持，可移植性更好，更好实现跨平台
##基于寄存器的指令集架构
+ 典型的应用是X86的二进制指令集：比如传统的PC以及Android的Davlik虚拟机
+ 指令集架构则完全依赖硬件，可移植性更差
+ 性能优势和执行更高效
+ 花费更少的指令去完成一项操作
+ 大部分情况下，基于寄存器架构的指令集往往都以一地址指令、二地址指令和三地址指令为主。

#JVM生命周期
##启动
通过引导类加载器创建初始类，初始类由具体的JVM实现指定。
##执行
程序开始执行时它才运行，程序结束时就停止
执行一个Java程序时，真真正正执行的是一个Java进程
##退出
+ 程序正常执行结束
+ 程序异常终止
+ 操作系统错误导致Java虚拟机进程终止
+ 程序调用Runtime的exit或halt方法，并且Java安全管理器也允许这次exit或halt操作
+ JNI(Java Native Interface)规范描述了用JNI Invocation API来加载或卸载 Java虚拟机时，Java虚拟机的退出情况

#JVM发展历程
+ Sun Classic VM
+ Exact VM
+ HotSpot VM  Sun/Oracle JDK (收费)和 OpenJDK(免费) 的默认虚拟机
+ BEA 的 JRockit 世界上最快的JVM (监控、管理和分析应用程序工具：MissionControl)
+ IBM 的 J9(全称：IBM Technology for Java Virtual Machine 简称：IT4J，内部代号：J9)
+ Azul VM(与特定硬件平台绑定，性能更高)
+ BEA Liquid VM(与特定硬件平台绑定，性能更高)
+ TaobaoJVM 基于OpenJDK定制版本AlibabaJDK，过度依赖Intel的CPU
+ Graal VM