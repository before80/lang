+++
title = "main 函数"
date = 2025-04-11T23:22:30+08:00
weight = 120
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/main_function](https://zh.cppreference.com/w/c/language/main_function)

​	每个要在宿主环境运行的编码 C 程序都含有名为 `main` 的函数定义（非原型），它是程序中所指定的起始点。

`int main (void) { body }`	(1)	

`int main (int argc, char *argv[]) { body }`	(2)	

`/* 其他由实现定义的签名 */ (C99 起)`	(3)	

## 参数

`argc` - 代表程序所运行的环境传递给程序的实参数量。

`argv` - 指向 `argc + 1` 个指针的数组的首元素的指针。数组末元素为空指针，而若前面有元素，则它们指向表示从宿主环境传递给程序的参数的字符串。若 `argv[0]` 不是空指针（或等价地 `argc > 0`），则它指向表示程序名的字符串。若程序名从宿主环境不可用则该字符串为空。

​	名称 `argc` 和 `argv` 表示“argument count 实参计数”和“argument vector 实参向量”，使用它们是一项传统，但也可以为这些形参选用其他名字，也可以为它们的类型选用不同但等价的声明：`int main(int ac, char** av)` 同样合法。

​	`main` 的常见实现定义形式是 `int main(int argc, char *argv[], char *envp[])` ，其中所添加的第三形参类型为 `char**`，指向[指向*执行环境变量*的指针数组](https://pubs.opengroup.org/onlinepubs/9699919799/functions/exec.html)。

## 返回值

若使用返回语句，则返回值会用作隐式调用 [exit()](https://zh.cppreference.com/w/c/program/exit) 的实参（细节见下）。值零和 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status) 指示成功终止，值 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status) 指示不成功终止。

## 解释

​	在程序启动时，初始化所有静态存储期对象后，调用 `main` 函数。它是执行于*宿主*环境（即在操作系统中）的程序的指定入口点。任何*自立*程序（引导程序、操作系统核心等）的入口点的名称和类型是实现定义的。

​	主函数的双形参形式允许从执行环境传递任意的多字节字符串（常称作*命令行参数*）。指针 argv[1] .. argv[argc-1] 指向每个这些字符串的首字符。argv[0]（若其非零）指向代表用于调用程序自身的名称的，空终止多字节字符串的首字符（或者若宿主环境不支持此做法，则保证 argv[0][0] 为零）。

​	若宿主环境不能一同提供大写和小写字母，则转换命令行参数为小写。

​	字符串可修改，而且任何修改会留存到程序终止时，尽管这些修改不会传播回宿主环境：例如能以 [strtok](https://zh.cppreference.com/w/c/string/byte/strtok) 使用它们。

​	`argv` 所指的数组大小至少是 `argc+1`，并保证末元素 `argv[argc]` 为空指针。

​	`main` 函数拥有几个特殊属性：

1) 程序不能提供此函数的原型。
2) 若主函数的返回类型与 int [兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，则从对 `main` 的初次调用（但不是任何后继、递归调用）返回，等价于以主函数返回值为实参执行 [exit](https://zh.cppreference.com/w/c/program/exit) 函数（将调用 [atexit](https://zh.cppreference.com/w/c/program/atexit) 所注册的函数，冲入并关闭所有流，删除 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 所创建的文件，并返还控制给执行环境）。
3) 若 main 函数执行不指定值的 return，或同样地未执行 return 就抵达结尾的 }，则返回给宿主环境的终止状态未定义。(C99 前)  若 main 函数的返回类型与 int 不[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)（如 void main(void)），则返回给宿主环境的值未指定。若返回类型与 int 兼容且控制抵达结尾的 }，则返回给执行环境的值与如同执行 return 0; 的结果相同。(C99 起)

## 示例

​	演示如何告知程序其寻找输入处及写结果处。 调用： ./a.out indatafile outdatafile

```c
#include <stdio.h>
 
int main(int argc, char *argv[])
{
    printf("argc = %d\n", argc);
    for (int ndx = 0; ndx != argc; ++ndx)
        printf("argv[%d] --> %s\n", ndx, argv[ndx]);
    printf("argv[argc] = %p\n", (void*)argv[argc]);
}
```

可能的输出：

```txt
argc = 3
argv[0] --> ./a.out
argv[1] --> indatafile
argv[2] --> outdatafile
argv[argc] = (nil)
```

## 参阅

**主函数**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/main_function)**