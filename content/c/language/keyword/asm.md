+++
title = "内联汇编"
date = 2025-04-12T11:04:13+08:00
weight = 150
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/asm](https://zh.cppreference.com/w/c/language/asm)

​	内联汇编（常由 asm 关键词引入）给予在 C 程序中嵌入汇编语言源代码的能力。

​	不同于 C++ 中，内联汇编在 C 中被当作扩展。它是条件性支持及由实现定义的，意思是它可以不存在，而且即使实现有所提供，它也并不拥有固定的含义。

## 语法

`asm (` *字符串字面量* `)` `;`

> 本节未完成 
>
> 原因：写下关于 GCC 扩展汇编语法的注解，因为现在 Intel、IBM、Sun（自 v12 起）等均支持它

## 解释

​	这种内联汇编语法为 C++ 标准所接受，而在 C++ 中称为*汇编声明*。 *字符串字面量* 通常是以汇编语言编写的短程序，每当执行这条声明时对其执行。不同的 C 编译器拥有差异巨大的汇编声明规则，和与周围的 C 代码之间交互的不同约定。

​	汇编声明可出现于块（函数体或其他复合语句）内，而且同所有其他声明，此声明亦可出现于块外。

## 注解

​	MSVC 在 ARM 与 x64 处理器上不支持内联汇编，而且在 x86 处理器上仅支持由 __asm 引入的形式。

​	以 GCC 或 Clang 用 ISO C 模式编译（例如以选项 -std=c11）时，必须用 __asm__ 代替 asm 。

## 示例

​	演示 GCC 提供的二种内联汇编语法。此程序将只在 x86-64 上的 Linux 下正确工作。注意“标准内联汇编”在 C 标准中亦被当作扩展。

```c
#include <stdio.h>
 
extern int func(void);
// func 的定义以汇编语言书写
__asm__(".globl func\n\t"
        ".type func, @function\n\t"
        "func:\n\t"
        ".cfi_startproc\n\t"
        "movl $7, %eax\n\t"
        "ret\n\t"
        ".cfi_endproc");
 
int main(void)
{
    int n = func();
    // gcc 的扩展内联汇编
    __asm__ ("leal (%0,%0,4),%0"
           : "=r" (n)
           : "0" (n));
    printf("7*5 = %d\n", n);
    fflush(stdout); // 冲刷是有意的
 
    // C++ 中的标准内联汇编
    __asm__ ("movq $60, %rax\n\t" // Linux 上的“退出”的系统调用序号
             "movq $2,  %rdi\n\t" // 此程序返回 2
             "syscall");
}
```

​	输出：

```txt
7*5 = 35
```

## 参阅

**`asm` 声明**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/asm)**

## 外部链接

| 1.   | [GCC 内联汇编 HOWTO](http://www.ibiblio.org/gferg/ldp/GCC-Inline-Assembly-HOWTO.html) |
| ---- | ------------------------------------------------------------ |
| 2.   | [IBM XL C/C++ 内联汇编](https://pic.dhe.ibm.com/infocenter/comphelp/v121v141/topic/com.ibm.xlcpp121.aix.doc/language_ref/asm.html) |
| 3.   | [Intel C++ 内联汇编](https://software.intel.com/en-us/cpp-compiler-developer-guide-and-reference-inline-assembly) |
| 4.   | [Visual Studio 内联汇编器](https://learn.microsoft.com/en-us/cpp/assembler/inline/inline-assembler.aspx) |
| 5.   | [Sun Studio 12 Asm 语句](https://blogs.oracle.com/x86be/entry/gcc_style_asm_inlining_support) |
| 6.   | [基于 Itanium 的 HP-UX 的内联汇编](https://h21007.www2.hp.com/portal/site/dspp/menuitem.863c3e4cbcdc3f3515b49c108973a801?ciid=4308e2f5bde02110e2f5bde02110275d6e10RCRD) |
