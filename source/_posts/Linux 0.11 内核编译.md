---
title: Linux 0.11 内核编译
date: 2017-05-30 00:14:00
tags:
---


##  Linux 0.11 内核编译

### 预备

    apt-get install vim cscope exuberant-ctags gcc gdb binutils qemu

### 下载

    git clone https://github.com/tinyclub/linux-0.11-lab.git

### 编译

    cd linux-0.11-lab && make

### 从硬盘启动

    make start-hd

### 调试
打开一个控制台，从硬盘启动并进入 debug 模式：

    make debug-hd

通过 gdb 调试：

```
	gdb images/kernel.sym
	(gdb) target remote :1234
	(gdb) b main
	(gdb) c
```

### 查阅文档
README.md

### 查看帮助

```
    make help
> Usage:
 make --generate a kernel floppy Image with a fs on hda1
 make start -- boot the kernel in qemu
 make start-fd -- boot the kernel with fs in floppy
 make start-hd -- boot the kernel with fs in hard disk
 make debug -- debug the kernel in qemu & gdb at port 1234
 make debug-fd -- debug the kernel with fs in floppy
 make debug-hd -- debug the kernel with fs in hard disk
 make disk  -- generate a kernel Image & copy it to floppy
 make cscope -- genereate the cscope index databases
 make tags -- generate the tag file
 make cg -- generate callgraph of the system architecture
 make clean -- clean the object files
 make distclean -- only keep the source code files
```

### 生成函数调用关系图

```
    make cg
	ls calltree/linux-0.11.jpg
```