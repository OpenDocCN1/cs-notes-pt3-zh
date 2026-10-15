
## Why Emulator

- OS Test and Debug
- Increase Utilization

- Just as Why IBM’s Virtualization
  - IBM’s M44/44X, in 1960s

## OPERATING SYSTEM
ARCHITECTURE

## Operating System Design and Implementation

Design and Implementation of OS not “solvable”, but some approaches have proven successful

- Internal structure of different Operating Systems can vary widely
- Start by defining goals and specifications
- Affected by choice of hardware, type of system

> Remember “**Worse is better design**”

## Operating System Design and Implementation

*User* goals and *System* goals

### User goals

operating system should be convenient to use, easy to learn, reliable, safe, and fast

### System goals

operating system should be easy to design, implement, and maintain, as well as flexible, reliable, error-free, and efficient

## Operating System Design and Implementation (Cont.)

Important principle to separate

**Policy:** What will be done?
**Mechanism:** How to do it?

Mechanisms determine how to do something

# Policies decide what will be done

The separation of policy from mechanism is a very important principle

It allows maximum flexibility if policy decisions are to be changed later

## Simple Structure

MS-DOS – written to provide the most functionality in the least space (1981~1994)

Not divided into modules

Although MS-DOS has some structure, its interfaces and levels of functionality are not well separated

![](img/53ee1e3b0eba43505c7d530851f32f6f_149_0.png)

![](img/53ee1e3b0eba43505c7d530851f32f6f_149_1.png)

## MS-DOS Layer Structure

![](img/53ee1e3b0eba43505c7d530851f32f6f_150_0.png)

## Layered Approach

The operating system is divided into a number of layers (levels)

- Each built on top of lower layers.
- The bottom layer (layer 0), is the hardware;
- The highest (layer N) is the user interface.

With modularity, layers are selected such that

- each uses functions (operations) and services of only lower-level layers

## Layered Operating System

![](img/53ee1e3b0eba43505c7d530851f32f6f_152_0.png)

## UNIX

### UNIX – limited by hardware functionality

the original UNIX operating system had limited structuring.

### The UNIX OS consists of two separable parts

- Systems programs
- The kernel

Consists of everything below the system-call interface and above the physical hardware

Provides the file system, CPU scheduling, memory management, and other operating-system functions; a large number of functions for one level

## Microkernel System Structure

Moves as much from the kernel into “user” space

Communication takes place between user modules using message passing

Benefits:
- Easier to extend a microkernel
- Easier to port the operating system to new architectures
- More reliable (less code is running in kernel mode)
- More secure

Detriments:
- Performance overhead of user space to kernel space communication

## Microkernel Structure & Instances

![](img/53ee1e3b0eba43505c7d530851f32f6f_156_0.png)

## Exokernel Structure

### Overview

let the kernel allocate the physical resources of the machine to multiple application programs, and

let each program decide what to do with these resources.

The program can link to an operating system library (libOS) that implements OS abstractions.

## Exokernel & Corey

Exokernel [SOSP’95]
- Kernel classification
- Motivation
- Design and Implementation
- Evaluation

Corey [OSDI’08]
- Multi-core era and scalability problem
- Sharing and Address range
- Summery

## Kernels

Kernel classification (wikipedia)

| Kernel (architecture) | Monolithic | Microkernel | **Exokernel** | hybrid |
|---|---|---|---|---|

### Monolithic kernel

A **monolithic kernel** is an operating system architecture where the entire operating system is working in kernel space and is alone in supervisor mode.

Linux, BSD…
