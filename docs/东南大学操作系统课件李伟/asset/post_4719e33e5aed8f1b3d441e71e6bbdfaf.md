
# 操作系统原理及应用

李 伟

xchlw@seu.edu.cn

计算机科学与工程学院、软件学院

江苏省网络与信息安全重点实验室

## 课程定位与目的

- 软件工程专业基础课程之一
- 考研内容之一——计算机专业基础（学校自主命题）
  - 数据结构（45分）
  - 操作系统（60分）
  - 计算机组成原理（45分）
- 掌握操作系统的基本概念和原理，能够熟练使用和维护常用操作系统（如Windows、Linux等），具备研发基于Linux的嵌入式操作系统的能力，为从事软件项目的研发打下扎实的基础。

## 教学内容与要求（1/2）

| Introduction | 掌握操作系统的一般概念，复习和回顾与操作系统相关的硬件知识，了解操作系统的发展和分类 |
| Operating system Structures | 介绍操作系统的组成，树立操作系统的整体概念 |
| Process | 牢固掌握进程相关概念，能够编写并发程序 |
| Threads | 掌握创建和管理线程的方法，熟练使用多线程技术编程 |
| CPU Scheduling | 理解相关算法，能编写一个进程调度程序 |
| Process Synchronization | 理解同步概念，掌握同步的编程方法 |
| Deadlocks | 理解死锁现象，掌握预防、避免、检测、解除死锁的方法 |

## 教学内容与要求（2/2）

| Memory Management | 掌握固定分区、可变分区、段式、页式存储管理的原理与算法 |
| Virtual Memory | 正确理解虚拟内存的概念，熟练掌握请求页式的地址转换过程以及常用的页面置换算法 |
| File Systems | 掌握文件系统的基本概念，熟练使用文件系统的操作方法 |
| Mass-Storage Structure | 了解磁盘结构，及几种磁盘调度算法 |
| I/O Systems | 掌握I/O系统的基本概念，理解设备驱动程序。弄清从用户请求到设备完成用户请求的全过程 |

## 考核方式

- 闭卷考试（全英文试卷）
- 成绩评定：由下述三部分组成
  - 期末考试成绩（60%）
  - 实验、期中考试成绩（30%）
  - 平时成绩（作业、出勤、讨论等）（10%）

## 参考书目

- 《操作系统概念》
  （第七版 影印版）
  西尔伯莎茨 等编著
  高等教育出版社
  2007年3月

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_7_0.png)

## 参考书目

- 《操作系统概念》
  （第七版 翻译版）
  郑扣根 译
  高等教育出版社
  2010年1月

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_8_0.png)

# 操作系统原理及应用

李 伟

xchlw@seu.edu.cn

计算机科学与工程学院、软件学院

江苏省网络与信息安全重点实验室

# Chapter 1 Introduction

## Outline

- What is Operating System?
- OS-related Hardwares
- Development of Operating System

## Computer System Components

- **Hardware** – provides basic computing resources (CPU, memory, I/O devices, etc).
- **Operating system** – controls and coordinates the use of the hardware among the various programs for the various users.
- **Programs** – (compilers, database, video, games, email systems, QQ, etc) are used to solve user problems.
- **Users** (people, machines, other computers).

## Abstract View of Computer System Components

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_13_0.png)

## User View

- **PC Users**: an operating system is **a program** that provides an easy-to-use interface for using the hardware
- **Mainframe/Minicomputer Users**: an operating system is **a program** that helps maximize the system resource utilization
- **Workstation Users**: an operating system is **a program** designed to compromise between individual usability and resource utilization

## System View

- A *Resource Allocator*: the operating system allocates and reclaims the system hardware resources to and from user programs
- A *Control Program*: the operating system controls the execution of user programs to prevent errors and improper use of the computer

## What is an Operating System?(1/3)

- There is *no* universal definition of what is an operating system.
- A common definition is that the operating system is the one *kernel program* running at all times on the computer. All other programs are systems/application programs.

## What is an Operating System?(2/3)

- An operating system is a set of programs that acts as an intermediary between the user of a computer and the computer hardware.
  - Make the computer system convenient to use.
  - Execute user programs and make solving user problems easier.
  - Manage the computer hardware.

## What is an Operating System?(3/3)

- General View
  - A resource allocator, a control program, a kernel program
- The Goals of Operating System
  - Primary Goal: efficient operation of the computer system.

The matter of what constitutes an operating system has become increasingly important.

## Outline

- What is Operating System?
- OS-related Hardwares
- Development of Operating System

## Computer-System Architecture

![](img/0f9477f9dd9e571abf0b2ce4550a9e88_20_0.png)

- How does the OS get into system?
- How do we request for services?
- How does the OS know something has happened?
