

## 版本控制

- APT (Advanced Package Tools)
  - apt-get: *命令行工具*
    - **update**      e.g. >apt-get update
    - **install**     e.g. >apt-get install htop
    - **remove**      e.g. >apt-get remove htop
    - **upgrade**     e.g. >apt-get upgrade htop
  - apt-cache: *缓存操作工具*
    - **search**      e.g. >apt-cache search htop
    - **showpkg**     e.g. >apt-cache showpkg htop

## 版本控制

- APT (Advanced Package Tools)
  - example: *安装 vim*

  - >su
    root 用户
  - >apt-get update
    更新 apt 列表
  - >apt-cache search vim
    在缓存中搜索
  - >apt-get install vim
    安装 vim
  - >man vim
    vim 手册

```
$ apt-cache search vim
...
vim - Vi IMproved - enhanced vi editor
vim-doc - Vi IMproved - HTML documentation
...
```

先决条件

SVN

工具链

## 版本控制

- SVN (SubVersioN)
  - 维护文件当前版本和历史版本

## 版本控制

- SVN (SubVersioN)
  - 在 Debian 上安装
    - 更新 e.g. >apt-get update
    - 搜索 e.g. >apt-cache search svn
    - 安装 e.g. >apt-get install subversion
    - 卸载 e.g. >apt-get remove subversion

## 版本控制

- SVN (SubVersioN)
  - 客户端命令
    - checkout
      e.g. >svn co svn://10.132.143.1/truck truck
      --username=rong
    - update      e.g. >svn update
    - commit      e.g. >svn ci a.c -message=".."
    - add file e.g. >svn add b.c
      >svn ci b.c -message=".."
    - del file e.g. >svn del b.c
      >svn ci b.c -message=".."

## 版本控制

- SVN (SubVersioN)
  - 客户端命令
    - show status
      e.g. >svn status -q
    - diff file
      e.g. >svn diff b.txt
    - resolve conflict
      e.g. >vi a.c  //manually remove conflict
      >svn resolved a.c

*svn 资源链接: http://subversion.tigris.org/

先决条件

SVN

工具链

C 语言

编译, Gcc

Make

## To C or Not to C

- 为什么我们选择 C？

> " The limits of my language are the limits of my world "
> 
> Tranctatus Logico-
> Philosophicus 5.6 1918

我们的需求

- 实现计算机
- 更多控制程序
- 实现不大但实用的软件
- 在多领域有良好支持

最佳选择

Assembler C Java Shell Script Lisp

## 历史

- C 语言的诞生
  - Thompson & Ritchie, 1969 ~ 1971
  - 基于 B 语言
    (BCPL, Basic Common Programming language)
  - 1973 年用 C 重写 Unix
- ANSI (American National Standards Institute)
  - C89 和 C99
- 书籍: The C Programming Language
  http://www.china-pub.com/computers/common/info.asp?id=14975

先决条件

SVN

工具链

C 语言

编译, Gcc

Make

## GNU

- 什么是 GNU？
  - GNU is Not Unix, 1983
    - Richard M. Stallman (文化传奇)
  - 目标：绝对自由的操作系统
  - The GNU Manifesto, 1985
  - Free Software Foundation (FSF)
    - Emacs, GCC, tar, ...
  - GPL, General Public License
    - 病毒式传染性

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1341_0.png)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1341_1.png)

## 编译器

- **GNU Compiler Collection**
  - 预处理器, 汇编器, 链接器, 加载器, ...
  - 支持 : C, C++, Java, Fortran, Ada, ...
  - 在 Debian 上安装
    - `e.g. >apt-get remove build-essential`

## 编译

- C 文件编译示例
  - C 文件: test.h test.c
  - e.g.
    - `>gcc -E test.c > test-pp.c      (test-pp.c)`
    - `>gcc -S test.c                  (test.s)`
    - `>gcc -c test.c                  (test.o)`
    - `>gcc -o test test.c             (test)`

# 先决条件

SVN

工具链

C 语言

编译, Gcc

Make

