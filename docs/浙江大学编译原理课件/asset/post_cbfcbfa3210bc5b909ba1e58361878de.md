

# Compile Principle and Technology

## Chapter 1 introduction

### Outline

- Course Organization
  - General course information
  - Homework
- Introduction to Compilers
  - Why do we need compilers?
  - What are compilers?
  - General compiler structure

### Reference book

- Compilers -- Principles, Techniques and Tools,(Dragon Book), by Aho, Sethi and Ullman (1986)
- Modern Compiler Implementation in Java(C,ML), by Andrew Appel (2002)
- 程序设计语言编译原理（第3版），国防工业出版社,陈火旺等
- Compiler Design in C. Prentice Hall, Allen I. Holub
- 编译原理与技术,浙江大学出版社,冯雁等编著

### Work Distribution

- Homeworks = 15%
- Class Quizzes = 20%
- Final Exams = 65%

## Chapter 1 introduction

### Why Take This Course?

#### understand compilers/languages:

- Understand the code structure
- Understand the language semantics
- Understand the relation between source code and generated machine code
- Become a better programmer

### Why Take This Course? (ctd.)

nice balance of theory and practice:

#### Theory:

- Lots of mathematical models: regular expressions,
- automata, grammars, graphs, lattices
- Lots of algorithms that use these models

#### Practice:

- Apply theoretical notions to build a real compiler
- Better understand why “theory and practice are the same in theory; in practice they are different”

### Why Take This Course? (ctd.)

#### Programming experience

- Write a large program that manipulates complex data structures
- Learn how to be a better programmer in groups
- Learn more about c/c++ and Intel x86 architecture and assembly language

## 1.1 A brief history of compiler

- in the late 1940s, programs were written in machine language , c7 06 0000 0002
- assembly language : numeric codes were replaced symbolic forms. Mov x, 2
- assembler : translate the symbolic codes and memory location of assembly language into the corresponding numeric codes.
- Defects of the assembly language : difficult to read , write and understanding , dependent on the particular machine

## 1.1 A brief history of compiler

- FORTRAN language and its compiler: between 1954 and 1957 , developed by the team at IBM , John Backus.
  - The structure of natural language studied by Noam Chomsky,
  - The classification of languages according to the complexity of their grammars and the power of the algorithms needed to recognize them.
  - Four levels of grammars: type 0 、 type 1、 type2 and type3 grammars

## 1.2 Programs related to compilers

- Interpreters
  - A language translator. It executes the source program immediately.
- Assemblers
  - A translator translates assembly language into object code
- Linkers
  - Collects code separately compiled or assembled in different object files into a file.
  - Connects the code for standard library functions.
  - Connects resources supplied by the operating system of the computer.

## 1.2 Programs related to compilers

- Loaders
  - Loaders resolve all relocatable address relative to the starting address.
- Preprocessors
  - delete comments, include other files, perform macro substitutions.
- Editors
  - Produce a standard file ( structure based editors)
- Debuggers
  - Determine execution errors in a compiled program.

