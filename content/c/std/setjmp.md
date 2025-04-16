+++
title = "<setjmp.h>"
date = 2025-04-14T22:34:39+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型








### jmp_buf

原址：[https://zh.cppreference.com/w/c/program/jmp_buf](https://zh.cppreference.com/w/c/program/jmp_buf)

```c
typedef /* 未指明 */ jmp_buf;

```

​	`jmp_buf` 类型是适合于存储并恢复调用环境的数组类型。存储的信息足以恢复程序在当前块的执行和该块的调用。浮点状态标志、打开的文件或其他任何数据不存储于 `jmp_buf` 类型对象中。

## 宏








### setjmp

原址：[https://zh.cppreference.com/w/c/program/setjmp](https://zh.cppreference.com/w/c/program/setjmp)

```c
#define setjmp(env) /* 由实现定义 */

```

​	将当前执行环境保存于 [jmp_buf](https://zh.cppreference.com/w/c/program/jmp_buf) 类型的变量 `env`。此变量可在之后被 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 函数用来恢复当前执行环境。即当调用 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 函数时，执行将从传递给 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 的 [jmp_buf](https://zh.cppreference.com/w/c/program/jmp_buf) 变量所构建的特定调用点继续。该情况下 **setjmp** 返回传递给 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 的值。

​	`setjmp` 的调用必须只出现在下列语境之一中：

1. 选择或迭代语句（[`if`](https://zh.cppreference.com/w/c/language/if)、[`switch`](https://zh.cppreference.com/w/c/language/switch)、[`while`](https://zh.cppreference.com/w/c/language/while)、[`do-while`](https://zh.cppreference.com/w/c/language/do)、[`for`](https://zh.cppreference.com/w/c/language/for)）的完整控制表达式

```c
switch(setjmp(env)) { // ...

```

1. 关系或相等性运算符的一个操作数，其另一操作数为整数常量表达式，产生的表达式为选择或迭代语句的完整控制表达式

```c
if(setjmp(env) > 10) { // ...

```

1. 一元 ! 运算符的操作数，其结果为选择或迭代语句的完整控制表达式

```c
while(!setjmp(env)) { // ...

```

1. [表达式语句](https://zh.cppreference.com/w/c/language/statements#.E8.A1.A8.E8.BE.BE.E5.BC.8F.E8.AF.AD.E5.8F.A5)的完整表达式（可以将其转型到 `void`）。

```c
setjmp(env);

```

​	若 `setjmp` 出现于其他语境中，则行为未定义。

​	一旦返回到 `setjmp` 的作用域:

- 所有可访问对象、浮点状态标志及其他抽象机组件均拥有与在执行 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 时相同的值，
- 但含有 `setjmp` 调用的函数中的非 [`volatile`](https://zh.cppreference.com/w/c/language/volatile) 局部变量，若已在 `setjmp` 调用后有所更改，则其值不确定。

**参数**

| env  | -    | 要保存程序执行状态的变量。 |
| ---- | ---- | -------------------------- |

**返回值**

​	若原初代码调用该宏，则返回 0，并保存执行环境到 `env`。

​	若进行了非局部跳转则可返回非零值。返回值与传递给 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 者相同。

**注解**

​	上述要求禁止在数据流中使用 `setjmp` 的返回值（例如以之初始化或赋值对象）。只能将返回值用于控制流或舍弃。

**示例**

```c
#include <stdio.h>
#include <setjmp.h>
#include <stdnoreturn.h>
 
jmp_buf my_jump_buffer;
 
noreturn void foo(int status) 
{
    printf("foo(%d) called\n", status);
    longjmp(my_jump_buffer, status + 1); // 将从 setjmp 返回 status+1
}
 
int main(void)
{
    volatile int count = 0; // setjmp 作用域内要修改的局部变量必须为 volatile
    if (setjmp(my_jump_buffer) != 5) // 在一个 if 内与常数比较
        foo(++count);
}

```

输出：

```txt
foo(1) called
foo(2) called
foo(3) called
foo(4) called

```

## 函数








### longjmp

原址：[https://zh.cppreference.com/w/c/program/longjmp](https://zh.cppreference.com/w/c/program/longjmp)

```c
void longjmp( jmp_buf env, int status ); // (C11 前)
_Noreturn void longjmp( jmp_buf env, int status ); // (C11 起) (C23 前)
[[noreturn]] void longjmp( jmp_buf env, int status ); // (C23 起)

```

​	载入先前调用 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 保存的执行环境 `env`。此函数不返回。转移控制流到设置 `env` 的宏 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 的调用方。该 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 会返回作为 `status` 传递的值。

​	若调用 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 的函数已退出（通过返回或通过另一到栈上更高处的 `longjmp`），则行为未定义。换言之，只有调用栈间的长跳转是允许的。

​	跨线程跳转（若调用 `setjmp` 的函数被另一线程执行）亦是未定义行为。(C11 起)

​	若在调用 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 时，[VLA](https://zh.cppreference.com/w/c/language/array) 或其他[可变修改类型](https://zh.cppreference.com/w/c/language/declarations)的变量在作用域中，并且控制流离开了该作用域，则 `longjmp` 到该 `setjmp` 将引发未定义行为，即使控制流仍然留在该函数内。

​	在上溯栈的途中，`longjmp` 不会解分配任何 VLA，若其的生存期以此方式终结，则会出现内存泄漏：(C99 起)

```c
void g(int n)
{
    int a[n]; // a 仍为已分配
    h(n); // 不返回
}
void h(int n)
{
    int b[n]; // b 仍为已分配
    longjmp(buf, 2); // 可能因为 h 的 b 和 g 的 a 导致内存泄漏
}

```

**参数**

| env    | -    | 引用 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 所保存的程序执行状态的变量 |
| ------ | ---- | ------------------------------------------------------------ |
| status | -    | 要从 [setjmp](https://zh.cppreference.com/w/c/program/setjmp) 返回的值。若它等于 0，则代之以 1 |

**返回值**

​	（无）

> 注意
>
> ​	`longjmp` 是有意用以处理非预期的错误条件的，该条件下函数无法有意义地返回。这与其他编程语言中的异常处理相似。

**示例**

```c
#include <stdio.h>
#include <setjmp.h>
#include <stdnoreturn.h>
 
jmp_buf my_jump_buffer;
 
noreturn void foo(int status) 
{
    printf("foo(%d) called\n", status);
    longjmp(my_jump_buffer, status + 1); // 将从 setjmp 返回 status+1
}
 
int main(void)
{
    volatile int count = 0; // setjmp 作用域中修改的局部变量必须为 volatile
    if (setjmp(my_jump_buffer) != 5) // 在 if 中与常量比较
        foo(++count);
}

```

输出：

```txt
foo(1) called
foo(2) called
foo(3) called
foo(4) called
```