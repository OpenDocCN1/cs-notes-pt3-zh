
## VERSION CONTROL

- APT (Advanced Package Tools)
  - apt-get: *command-line tool*
    - **update**      e.g. >apt-get update
    - **install**     e.g. >apt-get install htop
    - **remove**      e.g. >apt-get remove htop
    - **upgrade**     e.g. >apt-get upgrade htop
  - apt-cache: *cache manipulator*
    - **search**      e.g. >apt-cache search htop
    - **showpkg**     e.g. >apt-cache showpkg htop

## VERSION CONTROL

- APT (Advanced Package Tools)
  - example: *install vim*

  - >su
    root user
  - >apt-get update
    update apt list
  - >apt-cache search vim
    search in cache
  - >apt-get install vim
    install vim
  - >man vim
    manual of vim

```
$ apt-cache search vim
...
vim - Vi IMproved - enhanced vi editor
vim-doc - Vi IMproved - HTML documentation
...
```

Pre-requisite

SVN

Toolchain

## VERSION CONTROL

- SVN (SubVersioN)
  - Maintain current and historical versions of files

## VERSION CONTROL

- SVN (SubVersioN)
  - Install on Debian
    - Update e.g. >apt-get update
    - Search e.g. >apt-cache search svn
    - Install e.g. >apt-get install subversion
    - Uninstall e.g. >apt-get remove subversion

## VERSION CONTROL

- SVN (SubVersioN)
  - Client Command
    - checkout
      e.g. >svn co svn://10.132.143.1/truck truck
      --username=rong
    - update      e.g. >svn update
    - commit      e.g. >svn ci a.c -message=".."
    - add file e.g. >svn add b.c
      >svn ci b.c -message=".."
    - del file e.g. >svn del b.c
      >svn ci b.c -message=".."

## VERSION CONTROL

- SVN (SubVersioN)
  - Client Command
    - show status
      e.g. >svn status -q
    - diff file
      e.g. >svn diff b.txt
    - resolve conflict
      e.g. >vi a.c  //manually remove conflict
      >svn resolved a.c

*svn resource link: http://subversion.tigris.org/

Pre-requisite

SVN

Toolchain

C Language

Compiling, Gcc

Make

## To C or Not to C

- Why we choose C?

> " The limits of my language are the limits of my world "
> 
> Tranctatus Logico-
> Philosophicus 5.6 1918

Our Requirements

- Realize Computer
- More Control Program
- Implement not Large but Practical Software
- Good Support in Multi-fields

Best Choice

Assembler C Java Shell Script Lisp

## HISTORY

- Birth of C Language
  - Thompson & Ritchie, 1969 ~ 1971
  - Based on B language
    (BCPL, Basic Common Programming language)
  - Rewrite Unix in C, 1973
- ANSI (American National Standards Institute)
  - C89 and C99
- BOOK: The C Programming Language
  http://www.china-pub.com/computers/common/info.asp?id=14975

Pre-requisite

SVN

Toolchain

C Language

Compiling, Gcc

Make

## GNU

- What is GNU?
  - GNU is Not Unix, 1983
    - Richard M. Stallman (culture legend)
  - Goal: absolutely FREE operating system
  - The GNU Manifesto, 1985
  - Free Software Foundation (FSF)
    - Emacs, GCC, tar, ...
  - GPL, General Public License
    - Virus infectivity

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1341_0.png)

![](img/b3f8b91675c485f1e811aa092ebbf3d4_1341_1.png)

## COMPILER

- **GNU Compiler Collection**
  - Preprocessor, Assembler, Linker, Loader, ...
  - Support : C, C++, Java, Fortran, Ada, ...
  - Install on Debian
    - `e.g. >apt-get remove build-essential`

## COMPILING

- C Files Compilation Example
  - C Files: test.h test.c
  - e.g.
    - `>gcc -E test.c > test-pp.c      (test-pp.c)`
    - `>gcc -S test.c                  (test.s)`
    - `>gcc -c test.c                  (test.o)`
    - `>gcc -o test test.c             (test)`

# Pre-requisite

SVN

Toolchain

C Language

Compiling, Gcc

Make
