+++
title = "未定义行为"
date = 2025-04-11T23:31:01+08:00
weight = 140
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/behavior](https://zh.cppreference.com/w/c/language/behavior)

​	C 语言标准精确指定了 C 语言程序的[可观察行为](https://zh.cppreference.com/w/c/language/as_if)，除了下列分类之一：

- *未定义行为* - 程序的该行为没有限制。未定义行为的例子是越过数组边界的访问、有符号整数溢出、空指针解引用、在表达式中[超过一次](https://zh.cppreference.com/w/c/language/eval_order)修改标量而其中无顺序点、通过不同类型的指针访问对象，等等。编译器不要求诊断未定义行为（尽管多数简单情形是得到诊断的），且编译后的程序不要求做任何有意义的事。

- *未指定行为* - 容许二种或多种行为，且不要求实现规范每种行为。例如，[求值顺序](https://zh.cppreference.com/w/c/language/eval_order)、同样的[字符串字面量](https://zh.cppreference.com/w/c/language/string_literal)是否有别，等。每个未指定行为导致一组合法结果之一，并且可以在同一程序中重复时产生不同结果。

- *实现定义行为* - 在未指定行为之上，实现规范了如何选择。例如，字节中的位数，或有符号整数右移是算术还是逻辑。

- *本地环境限定行为* - 依赖于[当前选择的本地环境](https://zh.cppreference.com/w/c/locale/setlocale)的实现定义行为。例如， [islower](https://zh.cppreference.com/w/c/string/byte/islower) 对任何 26 个小写拉丁字母外的字符是否返回 true。

（注意：[严格遵从](https://zh.cppreference.com/w/c/language/conformance)的程序不依赖任何未指定、未定义或实现定义行为）

​	要求编译器对违背任何 C 语法规则或语义约束的任何程序发布诊断消息（错误或警告），即使其行为被指定为未定义或实现定义，或者编译器可提供语言扩展以允许此种程序被接受。另外，不要求对未定义行为诊断。

## UB 与优化

因为正确的 C 程序是没有未定义行为的，编译器可以在启用优化的条件下编译确实有 UB 的程序时，生成不期待的结果：

例如，

### 有符号溢出

```c
int foo(int x) {
    return x+1 > x; // 真或为有符号溢出导致的 UB
}
```

可以编译成（[演示](https://godbolt.org/z/9dh7b71TK)）

```txt
foo:
        mov     eax, 1
        ret
```

### 越界访问

```c
int table[4] = {0};
int exists_in_table(int v)
{
    // 在最初的 4 次迭代中返回真或因为越界访问 UB
    for (int i = 0; i <= 4; i++) {
        if (table[i] == v) return 1;
    }
    return 0;
}
```

可以编译成（[演示](https://godbolt.org/z/48bn19Tsb)）

```txt
exists_in_table:
        mov     eax, 1
        ret
```

### 未初始化标量

```c
_Bool p; // 未初始化局部变量
if(p) // 访问未初始化标量是 UB
    puts("p is true");
if(!p) // 访问未初始化标量是 UB
    puts("p is false");
```

可能产生下列输出（可在一个旧版本 gcc 观察到）：

```txt
p is true
p is false
```



```c
size_t f(int x)
{
    size_t a;
    if (x) // x 为非零或 UB
        a = 42;
    return a; 
}
```

可以编译成（[演示](https://godbolt.org/z/9nz6EMPTG)）

```
f:
        mov     eax, 42
        ret
```

### 非法标量

```c
int f(void) {
  _Bool b = 0;
  unsigned char* p =(unsigned char*)&b;
  *p = 10;
  // 从 b 读取现在是 UB
  return b == 0;
}
```

可编译成（[演示](https://godbolt.org/z/rjx77bjoh)）

```txt
f:
        mov     eax, 11
        ret
```

### 空指针解引用

```c
int foo(int* p)
{
    int x = *p;
    if (!p)
        return x; // 为上述 UB，或绝不采用此分支
    else
        return 0;
}
int bar() {
    int* p = NULL;
    return *p;       // 无条件 UB
}
```

可以编译成（[演示](https://godbolt.org/z/8jnjMjcPz)）

```txt
foo:
        xor     eax, eax
        ret
bar:
        ret
```

### 访问传递给 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 的指针

​	选择 Clang 以观察示出的输出

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *p = (int*)malloc(sizeof(int));
    int *q = (int*)realloc(p, sizeof(int));
    *p = 1; // 访问传递给 realloc 的指针是 UB
    *q = 2;
    if (p == q) // 访问传递给 realloc 的指针是 UB
        printf("%d%d\n", *p, *q);
}
```

可能的输出：

```txt
12
```

### 无副作用的无限循环

​	选择 Clang 以观察示出的输出

```c
#include <stdio.h>
 
int fermat()
{
  const int MAX = 1000;
  // 无副效应的无限循环是 UB
    for (int a = 1, b = 1, c = 1; 1;)
    {
        if (((a * a * a) == ((b * b * b) + (c * c * c))))
            return 1;
        ++a;
        if (a > MAX)
        {
            a = 1;
            ++b;
        }
        if (b > MAX)
        {
            b = 1;
            ++c;
        }
        if (c > MAX)
            c = 1;
    }
    return 0;
}
 
int main(void)
{
  if (fermat())
    puts("Fermat's Last Theorem has been disproved.");
  else
    puts("Fermat's Last Theorem has not been disproved.");
}
```

可能的输出：

```txt
Fermat's Last Theorem has been disproved.
```