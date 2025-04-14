---
title: Java学习笔记
published: 2024-09-01
description: ''
image: ''
tags: [ Java ]
category: 学习笔记
draft: false
---

## Java 基础

### JVM vs JDK vs JRE

#### JVM

Java 虚拟机（JVM）是运行 Java 字节码的虚拟机。JVM 有针对不同系统的特定实现（Windows，Linux，macOS），目的是使用相同的字节码，它们都会给出相同的结果。字节码和不同系统的
JVM 实现是 Java 语言“一次编译，随处可以运行”的关键所在。

**JVM 并不是只有一种！只要满足 JVM 规范，每个公司、组织或者个人都可以开发自己的专属 JVM。** 也就是说我们平时接触到的 HotSpot
VM 仅仅是是 JVM 规范的一种实现而已。

除了我们平时最常用的 HotSpot VM 外，还有 J9 VM、Zing VM、JRockit VM 等 JVM 。维基百科上就有常见 JVM
的对比：[Comparison of Java virtual machines](https://en.wikipedia.org/wiki/Comparison_of_Java_virtual_machines)
。在 [Java SE Specifications](https://docs.oracle.com/javase/specs/index.html) 上找到各个版本的 JDK 对应的 JVM 规范。

#### JDK

JDK 是 Java Development Kit 缩写，它是功能齐全的 Java SDK。它拥有 JRE 所拥有的一切，还有编译器（javac）和工具（如 javadoc 和
jdb）。它能够创建和编译程序。

#### JRE

JRE 是 Java 运行时环境。它是运行已编译 Java 程序所需的所有内容的集合，包括 Java 虚拟机（JVM），Java 类库，java
命令和其他的一些基础构件。但是，它不能用于创建新程序。

如果只是为了运行 Java 程序，只需要安装 JRE 。如果需要进行 Java 编程方面的工作，就需要安装 JDK 。但是，这不是绝对的。有时，即使不在计算机上进行任何
Java 开发，仍然需要安装 JDK。例如，如果要使用 JSP 部署 Web 应用程序，应用程序服务器会将 JSP 转换为 Java servlet，需要使用 JDK
来编译 servlet。

### 什么是字节码?采用字节码的好处是什么?

在 Java 中，JVM 可以理解的代码就叫做字节码（即扩展名为 `.class` 的文件），它不面向任何特定的处理器，只面向虚拟机。Java
语言通过字节码的方式，在一定程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言可移植的特点。所以， Java
程序运行时相对来说还是高效的（不过，和 C++，Rust，Go 等语言还是有一定差距的），而且，由于字节码并不针对一种特定的机器，因此，Java
程序无须重新编译便可在多种不同操作系统的计算机上运行。

### Java Annotation（注解）

用于为代码元素（类、方法、字段等）添加额外说明信息。

这些信息本身不影响程序执行，但可通过编译工具或反射机制在编译时、运行时被解析，实现特定功能。