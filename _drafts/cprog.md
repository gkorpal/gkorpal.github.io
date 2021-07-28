---
title: 'C Programming'
date: 2021-10-02
tags:
  - problem-solving
---

# Setup

Note that [UNIX is an IDE](https://daveparillo.github.io/intermediate-cpp/back-matter/app-a/toctree.html), therefore, we will just need the following tools along with a terminal emulator to create C programs:

| Purpose | Program | dnf package name | 
|---------| ------- | ------------ |
| Text editor within Terminal with syntax highlighting| [Vim](https://fedoraproject.org/wiki/Vim) | `vim` | 
| Compiler | [GNU Compiler Collection (GCC)](https://developer.fedoraproject.org/tech/languages/c/c_installation.html) | `gcc`|
| Build-automation utility | [GNU Make](https://www.gnu.org/software/make/) | `make` | `make` |
| Source code package portability | [GNU Autotools](https://developer.fedoraproject.org/tech/languages/c/autotools.html) | `autoconf` and `automake`|
| Debugger | [GNU Project Debugger (GDB)](https://www.gnu.org/software/gdb/) | [`gdb`](https://src.fedoraproject.org/rpms/gdb) |
| Memory error detector | [Valgrind Memcheck](https://valgrind.org/docs/manual/quick-start.html) | [`valgrind`](https://src.fedoraproject.org/rpms/valgrind)

Now we can illustrate all the steps involved using the following example:

gcov: https://gcc.gnu.org/onlinedocs/gcc/Gcov.html

## Step 1: Write the source code

````c
#io
````
## Step 2: Create Makefile to automate the compiling and linking process

https://web.stanford.edu/class/archive/cs/cs107/cs107.1174/guide_make.html

## Step 3: Compile and run the program

## Step 4: Debug the program

https://cs.baylor.edu/~donahoo/tools/gdb/tutorial.html
