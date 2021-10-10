# Introduction 简介
This chapter describes the object file format, called ELF (Executable and Linking Format). There are three main types of object files.

本篇我们大致描述介绍ELF文件。总体来说，ELF文件可以细分为三类。
* A relocatable file holds code and data suitable for linking with other object files to create an executable or a shared object file.
  
  **可重定位文件**。可重定位文件中包含链接器需要的代码和数据信息，链接器根据这些信息将多个可重定位文件通过链接过程生成可执行文件或者生成共享库。
* An executable file holds a program suitable for execution; the file specifies how exec(BA_OS) creates a program's process image.
  
  **可执行文件**。顾名思义，可执行文件中包含最后需要执行的程序。它的信息用于指导操作系统如何生成最后的进程映像。
* A shared object file holds code and data suitable for linking in two contexts. First, the link editor [see ld(BA_OS)] processes the shared object file with other relocatable and shared object files to create another object file. Second, the dynamic linker combines it with an executable file and other shared objects to create a process image.
  
  **共享库**。共享库中的代码和数据主要有两个用途。第一，静态链接器（例如GNU ld）利用共享库和可重定位文件生成最终的目标文件（可以是可执行文件，也可以是生成新的共享库）。第二，动态链接器（例如GNU ld-linux.so）利用共享库和可执行文件来生成最终的进程映像。
  
Created by the assembler and link editor, object files are binary representations of programs intended to be executed directly on a processor. Programs that require other abstract machines, such as shell scripts, are excluded.

经过编译器和链接器一系列处理后的目标文件（可执行文件或者共享库）就是程序最终的二进制表现形式，这些二进制是处理器可以识别的指令序列。注意，某些程序的执行必须通过解释器的帮助才能执行（例如大家熟知的shell脚本），它们不在我们的讨论范畴。

After the introductory material, this chapter focuses on the file format and how it pertains to building programs. Chapter 5 also describes parts of the object file, concentrating on the information necessary to execute a program.

接下来分两部分讨论ELF文件。第一部分，介绍ELF的文件格式，着重介绍有利于帮助生成最终可执行文件的信息。第二部分，同样是介绍ELF的文件格式，不过着重于程序最终执行的信息。
***

# File Format 文件格式
Object files participate in program linking (building a program) and program execution (running a program). For convenience and efficiency, the object file format provides parallel views of a file's contents, reflecting the differing needs of those activities. Figure 4-1 shows an object file's organization.

在生成最终程序的链接阶段和程序最终在操作系统中运行这两个过程中都是需要目标文件参与其中的。因此为了方便与高效，目标文件根据这两个过程分别包含不同的信息，以适应每个过程的需要。图1-1是从两个不同的视角来看目标文件的内容，一个是链接时视角，一个是运行时视角。
![object file's organization](https://img-blog.csdn.net/20160526170240099)



