
# Comparison of 3-layered Architecture and 3-tiered client/server architecture

# 三层架构与三层客户端-服务器软件体系结构的区别

+   > **三层架构**（包括显示层，应用层与永久数据保持层）中的层指的是**逻辑意义上的层**。这些层，可以部署在同一台计算机上，当然也可以部署在不同的计算机上。
+   > **三层客户端-服务器架构**里面所涉及的层指的是**物理意义上的层**。
+   > **客户端**运行在PC上；
+   > **应用层**被部署与运行在应用服务器上；
+   > **数据层**包含数据库与数据库管理系统软件，被部署与运行在数据库服务器上。

# 三层架构与三层客户端-服务器软件体系结构的区别

![](img/95717dc23f76db2057b9aa0c49790307_802_0.png)

# 三层架构与三层客户端-服务器架构

# 三层客户端-服务器架构

Browser/
Beans/
ActiveX

Application
Services
Business logic

Databse, DBMS,
Legacy & other
Resource Managers

# 三层架构与三层客户端-服务器软件体系结构的区别

+   - **例子：**

+   - 假如我们要利用三层客户端-服务器架构设计一个运行于 Web 上的简单的网上运动会管理系统。则我们可能将软件系统设计为如下图所示的系统。

# 2. Evolution of client-server architecture

Client Tier

GUI

PC

Presentation Layer

Business logic Layer

DB Access Layer

运动会业务逻辑

Application Server

Database Tire

数据库与 DBMS

DB Server

An example design of a 3-tire client/server program

# 2. Evolution of client-server architecture

+   - 注意到，在本设计中，对于三层的客户端-服务器架构的应用层部分，设计为一个通常意义下的三层的层次架构。
+   - 该架构包含显示层，用于生成用户图形界面，具体地说，图形界面生成代码被部署在服务层，但是生成的界面被显示在客户端PC上。
+   - 应用层包含所有的业务逻辑核心代码，永久数据保持层包含所有的数据库访问代码，例如JDBC代码。
+   - 实际上，层次架构里面的所谓的三个层都被部署在应用服务器上。因此，本设计可以被认为是应用了三层的客户端-服务器架构，其中在应用层中，包含了通常意义下的一个三层架构的程序。

# 2. Evolution of client-server architecture

+   - 不要以为所有的程序都允许在互联网上
+   - 在现实的软件开发中，除了运行在互联网上的程序外，还有很多程序不运行在互联网上，例如
+     - Matlab软件，就是运行在桌面的软件；Matlab提供了强大的计算、仿真、绘图等功能因此，通常意义下的层次架构也具有广泛的用途
+     - 智能无人机控制软件
+     - 制造业软件

# JaveEE Architecture

# Summary

+   - **3-Tier most popular architecture**: scalable, flexible, clear separation of application areas, network efficient; expensive, difficult to implement
+   - **2-Tier more traditional**: convenient for small user base, easy to implement; not very scalable, db vendor lock-in, not very flexible
+   - **JavaEE architecture:** a special kind of 3-tire client server architecture, is the most suitable architecture for developing high quality web applications

# Question for Students

+   - **Question**: What is the main difference between a 3-layer layered architecture and a 3-tire client/server architecture?
+   - **Incomplete Answer:**
+     - A 3-layer layered architecture organizes the program into logical layers, all the layers can run in one computer
+     - A 3-tire client/server architecture also design the program into layered fashion: client tire runs on the client machine, business logic layer runs on the application server and DB and DBMS runs on the DB server

# Lecture 7. Strategy Pattern Behavioral

策略模式

# Professor:

Yushan (Michael) Sun

Fall 2016

# # Contents of this lecture

+   1. Introduction to the strategy pattern through Design of a sorting program
+   2. Theory of the strategy pattern
+   3. Example of design using the strategy pattern
+   4. Further discussion of the strategy pattern

# Introduction to the strategy pattern through
Design of a sorting program

# Introduction to the strategy pattern through
Design of a sorting program

# 【例1】 Design of a sorting program

Requirement: design a program to sort integers by using

+   - Bubble Sort
+   - Heap Sort
+   - Insertion Sort
+   - Quick Sort

respectively.

# Introduction to the strategy pattern through Design of a sorting program

+   • Design 1: use a single class named sorting to implement all the sorting algorithms

| Sorting |
|--------|
|+main(String[ ] args ) : int[ ]|
|+bubbleSort (int[ ] nums) : int[ ]|
|+heapSort (int[ ] nums) : int[ ]|
|+insertionSort (int[ ] nums) : int[ ]|
|+quickSort (int[ ] nums) : int[ ]|

# Introduction to the strategy pattern through Design of a sorting program

The code may look like this

```
Public class Sorting {
    public static void main(String[] args) {
        int choice;
        if (choice ==1) { bubbleSort (nums); }
        else if (choice ==2) { quickSort (nums); }
        //...
    }
    public int[] bubbleSort (int[] nums) {// code}
    public int[] heapSort (int[] nums) {// code}
    public int[] insertionSort (int[] nums) {// code}
    public int[] quickSort (int[] nums) {// code }
} //the code works, but it has some problems
```
