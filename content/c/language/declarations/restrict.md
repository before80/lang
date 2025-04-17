+++
title = "restrict 类型限定符 (C99 起)"
date = 2025-04-13T10:55:35+08:00
weight = 100
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/restrict](https://zh.cppreference.com/w/c/language/restrict)

​	C [类型系统]({{< ref "/c/language/basic_concepts/type" >}})中每一个独立的类型都有数个该类型的*限定*版本，对应 [`const`]({{< ref "/c/language/declarations/const" >}})、[`volatile`]({{< ref "/c/language/declarations/volatile" >}})，以及对于指向对象指针的 `restrict` 限定符中的一个、两个或全部三个。此页面描述 `restrict` 限定符的效果。

​	仅有指向[对象类型]({{< ref "/c/language/basic_concepts/type" >}})的指针及其（可能多维的）数组(C23 起)可被 restrict 限定；具体而言，以下是*错误*的：

- `int restrict *p`
- `float (* restrict f9)(void)`

​	restrict 语义仅适用于左值表达式；例如到 restrict 限定指针的类型转换，或返回 restrict 限定指针的函数调用不是左值，从而该限定符无效果。

​	在声明了 restrict 指针 `P` 的块的每次执行（典型例子是函数体的执行，其中 `P` 为函数形参）中，若某个可由 `P`（直接或间接）访问的对象会被任何手段修改，则该块中对该对象的所有访问（读或写），都必须经由 `P` 进行，否则行为未定义：

```c
void f(int n, int * restrict p, int * restrict q)
{
    while (n-- > 0)
        *p++ = *q++; // 通过 *p 修改的对象与通过 *q 读取的无一相同
                     // 编译器可以自由地优化、向量化、做页面映射等等。
}
 
void g(void)
{
    extern int d[100];
    f(50, d + 50, d); // OK
    f(50, d + 1, d);  // 未定义行为：f 中的 p 和 q 均可访问 d[1]
}
```

​	若对象决不被修改，则它可以被别名引用，并被异于 restrict 限定的指针访问（注意若对象为别名引用的 restrict 限定指针所指，则别名引用可能抑制优化）。

​	将一个 restrict 指针赋值给另一个是未定义行为，除非将指向外部块的指针赋值给内部块中的指针（包括在调用含 restrict 指针参数的函数时，以 restrict 指针为参数），或从函数返回指针（还有在前一个指针的块已经结束时）：

```c
int* restrict p1 = &a;
int* restrict p2 = &b;
p1 = p2; // 未定义行为
```

​	restrict 指针可以自由地赋值给非 restrict 指针，只要编译器还能优化代码，优化机会还是保留就位的：

```c
void f(int n, float * restrict r, float * restrict s) {
    float * p = r, * q = s; // OK
    while (n-- > 0)
        *p++ = *q++; // 几乎肯定优化成仅如 *r++ = *s++ 一般
}
```

​	若以 restrict 类型限定符声明数组类型（通过使用 [typedef]({{< ref "/c/language/declarations/typedef" >}})），则数组类型无 restrict 限定，但其元素类型有 restrict 限定：(C23 前)

​	始终认为数组类型与其元素类型同等地拥有 restrict 限定：(C23 起)


```c
typedef int *array_t[10];
 
restrict array_t a; // a 的类型是 int *restrict[10] 
// 注：clang 和 icc 以 array_t 不是指针类型为由拒绝
 
void *unqual_ptr = &a; // C23 前 OK ； C23 起错误
// 注：clang 即使在 C89-C17 模式也应用 C++/C23 中的规则
```

​	在函数声明中，关键词 `restrict` 可以出现于方括号内，用以声明函数参数的数组类型。它对数组所转换得的指针类型赋予限定：

```c
void f(int m, int n, float a[restrict m][n], float b[restrict m][n]);
 
void g12(int n, float (*p)[n])
{
   f(10, n, p, p+10); // OK
   f(20, n, p, p+10); // 可能是未定义行为（取决于 f 所为）
}
```

## 注解

​	restrict 限定符（像寄存器存储类）是有意使用以促进优化的。而从所有组成一致程序的预处理翻译单元中，删除所有此限定符的实例不会影响其含义（即可观的行为）。

​	编译器可以忽略任何一个或全部使用 `restrict` 的别名使用暗示。

​	欲避免未定义行为，程序员应该确保 restrict 限定指针所做的别名引用断言不会违规。

许多编译器提供作为 `restrict` 对立面的语言扩展：指示即使指针类型不同，也可以别名使用的属性： [`may_alias` (gcc)](https://gcc.gnu.org/onlinedocs/gcc/Common-Type-Attributes.html#index-g_t_0040code_007bmay_005falias_007d-type-attribute-3667)

## 使用模式

​	restrict 限定指针有几种常用的使用模式：

### 文件作用域

​	文件作用域的 restrict 限定指针必须在程序运行期间指向单个数组的元素。该数组对象不可以通过 restrict 指针和通过其声明名称（若有的话）或另一个 restrict 指针两种方式一同引用。

​	文件作用域 restrict 指针对访问动态分配的全局数组有用；restrict 语义令通过此指针的引用，和通过静态数组的声明名称引用该数组效率相当：

```c
float *restrict a, *restrict b;
float c[100];
 
int init(int n)
{
   float * t = malloc(2*n*sizeof(float));
   a = t;      // a 引用前半
   b = t + n;  // b 引用后半
}
// 编译器可以从 restrict 限定符推断 a、b 和 c 都没有潜在的别名引用
```

### 函数形参

​	最广泛的 restrict 限定指针使用，是用作函数形参。

​	在下例中，编译器可能推断出被修改对象不会有别名引用，从而能更大胆地优化循环。在 `f` 的入口处，必须提供 restrict 指针对关联数组的独占访问。特别是，在 `f` 内 `b` 或 `c` 都不可以指入 `a` 所关联的数组，因为它们都不是以基于 `a` 的指针值赋值的。对于 `b`，因为其声明的 const 限定符这是显然的，但对于 `c`，需要检查 `f` 的函数体：

```c
float x[100];
float *c;
 
void f(int n, float * restrict a, float * const b)
{
    int i;
    for ( i=0; i<n; i++ )
       a[i] = b[i] + c[i];
}
 
void g3(void)
{
    float d[100], e[100];
    c = x; f(100,   d,    e); // OK
           f( 50,   d, d+50); // OK
           f( 99, d+1,    d); // 未定义行为
    c = d; f( 99, d+1,    e); // 未定义行为
           f( 99,   e,  d+1); // OK
}
```

> 注意
>
> ​	将 `c` 指向 `b` 所关联的数组是允许的。还要注意，对于这些目的，关联到通常指针的“数组”，仅表示数组对象的那一部分实际上是由该指针引用的。

> 注意
>
> ​	在上例中，编译器能推断 a 和 b 不会别名使用，因为 b 的常性确保这点不会变得依赖函数体。程序员能等价地写 `void f(int n, float * a, float const * restrict b)`，该情况下编译器理解无法修改通过 b 引用的对象，而以 b 和 a 一同引用的对象也不会被修改。假如程序员要写 `void f(int n, float * restrict a, float * b)`，则编译器不检验函数体就无法推断出 a 和 b 不会别名使用。

​	通常情况下，最好在函数原型中用 restrict 显式标注所有不会别名使用的指针。

### 块作用域

​	一个块作用域的 restrict 限定指针会做一个限于其块内的别名引用断言。它允许局部断言仅应用到重要的块，譬如紧凑循环。它亦使得将使用 restrict 限定指针的函数转换成宏成为可能：

```c
float x[100];
float *c;
#define f3(N, A, B)                                    \
do                                                     \
{   int n = (N);                                       \
    float * restrict a = (A);                          \
    float * const    b = (B);                          \
    int i;                                             \
    for ( i=0; i<n; i++ )                              \
        a[i] = b[i] + c[i];                            \
} while(0)
```

### 结构体成员

​	作为结构体成员的 restrict 限定指针，所做的别名引用断言作用域，是用于访问该结构体的标识符的作用域。

​	即使结构体声明于文件作用域，当用以访问此结构体的标识符拥有块作用域时，结构体中的别名引用断言亦拥有块作用域；别名引用断言仅在块执行或函数调用中生效，具体取决于此结构体类型的对象是如何创造的：

```c
struct t      // restrict 指针断言
{
   int n;     // 成员指向无交集的存储区。
   float * restrict p;
   float * restrict q;
};
 
void ff(struct t r, struct t s)
{
   struct t u;
   // r、s、u 拥有块作用域
   // r.p、r.q、s.p、s.q、u.p、u.q 应该在
   // 每次执行 ff 时全部指向无交集的存储区。
   // ...
}
```

## 关键词

[`restrict`]({{< ref "/c/language/keyword/restrict" >}})

## 示例

​	代码生成样例；以 -S（gcc、clang 等）或 /FA（Visual Studio）参数编译

```c
int foo(int *a, int *b)
{
    *a = 5;
    *b = 6;
    return *a + *b;
}
 
int rfoo(int *restrict a, int *restrict b)
{
    *a = 5;
    *b = 6;
    return *a + *b;
}
```

可能的输出：

```txt
; 所生成的 64 位 Intel 平台的代码：
foo:
    movl    $5, (%rdi)    ; 存储 5 于 *a
    movl    $6, (%rsi)    ; 存储 6 于 *b
    movl    (%rdi), %eax  ; 从 *a 读回值，考虑到前面的存储会修改它
    addl    $6, %eax      ; 将从 *a 读得的值加 6
    ret
 
rfoo:
    movl      $11, %eax   ; 结果是 11，编译时常量
    movl      $5, (%rdi)  ; 存储 5 于 *a
    movl      $6, (%rsi)  ; 存储 6 于 *b
    ret
```
