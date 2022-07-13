---
layout: post
title: Linux Kernel
description: >
    Linux Kernel is a multi-user, multi-tasking, multi-processor operating system. It is the kernel of the Linux operating system.
---

# Linux Kernel


## Compiler

The Linux kernel is written in C programming language, with small amount of assembly language in some places. To Build the kernel, we must use gcc compiler. If you wish to download the compiler and build it yourself, you can download the source code from [here](https://www.gnu.org/software/gcc/download.html).

To find out the version of the compiler, we can use the command.

```bash
gcc --version
```

## Linker

The C compiler, gcc dose not do all of the compiling on its own. It needs to link the object files together to create an executable. The linker is responsible for this. It need an additional set of tools known as `binutils` to do the linking and assembling of source files. The `binutils` package also contains useful utilities that can manipulate the object files. such as to view the contents of a library.

To find out the version of the linker, we can use the command.

```bash
ld -v
```

## Make

`make` is a tool that helps you to compile and link the source files. It is used to automate the compilation and linking of source files.The kernel requires the GNU version of `make`, which can usually be found in the package called `make`. for your distribution.

If you wish to download the `make` package, you can download the source code from [here](https://www.gnu.org/software/make/).

To find out the version of the make, we can use the command.

```bash
make --version
```
