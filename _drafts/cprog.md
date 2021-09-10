---
title: 'C Programming'
date: 2021-10-02
tags:
  - problem-solving
---

# Setup

Note that [UNIX is an IDE](https://blog.sanctum.geek.nz/series/unix-as-ide/), therefore, we will just need the following tools along with a terminal emulator to create C programs:

| Purpose | Program | Linux package name | 
|---------| ------- | ------------ |
| Text editor within Terminal with syntax highlighting| [Vim](https://www.vim.org/) | `vim` | 
| Compiler and code coverage [`gcov`](https://gcc.gnu.org/onlinedocs/gcc/Gcov.html) | [GNU Compiler Collection (GCC)](https://gcc.gnu.org/) | `gcc`|
| Build-automation utility | [GNU Make](https://www.gnu.org/software/make/) | `make` | `make` |
| Debugger | [GNU Project Debugger (GDB)](https://www.gnu.org/software/gdb/) | `gdb` |
| Memory error detector | [Valgrind Memcheck](https://valgrind.org/docs/manual/quick-start.html) | `valgrind` |
<!----
| Source code package portability | [GNU Autotools](https://developer.fedoraproject.org/tech/languages/c/autotools.html) | `autoconf` and `automake`|
---->
Now we can illustrate all the steps involved using the following example:


## Step 1: Write the source code

````c
#io
````
## Step 2: Create Makefile to automate the compiling and linking process

https://web.stanford.edu/class/archive/cs/cs107/cs107.1174/guide_make.html

## Step 3: Compile and run the program

## Step 4: Debug the program

https://cs.baylor.edu/~donahoo/tools/gdb/tutorial.html
