+++
title = "const 类型限定符"
date = 2025-04-13T10:48:11+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/const](https://zh.cppreference.com/w/c/language/const)

​	C [类型系统]({{< ref "/c/language/basic_concepts/type" >}})中每一个独立的类型，都有该类型的几个*限定*版本，对应 `const`、[`volatile`]({{< ref "/c/language/declarations/volatile" >}}) 及对于指向对象指针的 [`restrict`]({{< ref "/c/language/declarations/restrict" >}}) 限定符中的一个、两个或全部三个。此页面描述 `const` 限定符的效果。

​	编译器可以把[声明]({{< ref "/c/language/declarations" >}})为带 const 限定类型的对象放到只读内存中，并且若程序从来不获取该 const 对象的地址，则可能完全不存储它。

​	对类型被 const 限定的对象的任何修改尝试都导致未定义行为。

```c
const int n = 1; // const 限定类型的对象
int* p = (int*)&n;
*p = 2; // 未定义行为
```

​	`const` 语义仅适用于[左值]({{< ref "/c/language/expressions/value_category" >}})表达式；只要在不要求左值的语境中使用 const 左值表达式，就会丢失其 `const` 限定符（注意不丢失 `volatile` 限定符，若它存在）。

​	指代 const 限定类型对象的左值表达式，和指代拥有至少一个 const 限定类型成员（包含为聚合体或联合体所递归含有的成员）的结构体或联合体的左值表达式，不是*可修改左值*。具体而言，它们不可赋值：

```c
const int n = 1; // const 类型对象
n = 2; // 错误： n 的类型为 const 限定
 
int x = 2; // 未限定类型的对象
const int* p = &x;
*p = 3; // 错误：左值 *p 的类型为 const 限定
 
struct {int a; const int b; } s1 = {.b=1}, s2 = {.b=2};
s1 = s2; // 错误：s1 的类型无限定，但它有 const 成员
```

​	const 限定的结构体或联合体类型的成员，取得它所属类型的限定版本（在用 `.` 运算符或 `->` 运算符访问时）。

```c
struct s { int i; const int ci; } s;
// s.i 的类型为 int，s.ci 的类型为 const int
const struct s cs;
// cs.i 和 cs.ci 的类型都是 const int
```

​	若以 const 类型限定符声明数组类型（通过使用 [typedef]({{< ref "/c/language/declarations/typedef" >}})），则数组类型无 const 限定，但其元素类型有。(C23 前)

​	始终认为数组类型与其元素类型同等地拥有 const 限定。(C23 起)


```c
typedef int A[2][3];
const A a = {{4, 5, 6}, {7, 8, 9}}; // const int 的数组的数组
int* pi = a[0]; // 错误： a[0] 拥有 const int* 类型
void *unqual_ptr = a; // C23 前 OK ； C23 起错误
// 注： clang 即使在 C89-C17 模式也应用 C++/C23 中的规则
```

​	若以 const 类型限定符声明函数类型（通过使用 [typedef]({{< ref "/c/language/declarations/typedef" >}})），则行为未定义。

​	函数声明中，关键词 `const` 可出现在用于声明函数形参的数组类型的方括号内。它限定数组类型所变换到的指针类型。以下两条声明声明相同函数：(C99 起)

```c
void f(double x[const], const double y[const]);
void f(double * const x, const double * const y);
```

​	const 限定的复合字面量不必指代相异的对象；能与恰好拥有重叠表示的其他复合字面量和字符串字面量一同存储它们。(C99 起)

```c
const int* p1 = (const int[]){1, 2, 3};
const int* p2 = (const int[]){2, 3, 4}; // p2 的值可等于 p1+1
_Bool b = "foobar" + 3 == (const char[]){"bar"}; // b 的值可为 1
```

​	指向非 const 类型的指针能隐式转换成指向同一或[兼容](https://zh.cppreference.com/w/c/language/compatible_type)类型的 const 限定版本的指针。需要转型表达式进行逆向转换。

```c
int* p = 0;
const int* cp = p; // OK：添加限定符（int 到 const int）
p = cp; // 错误：舍弃限定符（const int 到 int）
p = (int*)cp; // OK：转型
```

> 注意
>
> ​	指向指向 `T` 指针的指针不可转换为指向指向 `const T` 指针的指针；对于要兼容的二个类型，其限定必须等同。
>
> ```c
> char *p = 0;
> const char cpp = &p; // 错误：char* 与 const char* 不是兼容类型
> char * const *pcp = &p; // OK：添加限定符（char* 到 char *const）
> ```
>

## 关键词

[`const`]({{< ref "/c/language/keyword/const" >}})

## 注解

​	C 从 C++ 接纳了 *const* 限定符，但不同于 C++，C 中 const 限定类型的表达式不是[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})；它们不可用作 [case]({{< ref "/c/language/statements/switch" >}}) 标号，或用于初始化[静态]({{< ref "/c/language/declarations/storage_duration" >}})和[线程]({{< ref "/c/language/declarations/storage_duration" >}})存储期对象，用作[枚举项]({{< ref "/c/language/declarations/enum" >}})，或[位域]({{< ref "/c/language/declarations/bit_field" >}})大小。以之为[数组]({{< ref "/c/language/declarations/array" >}})大小时，产生的数组为 VLA。

## 参阅

cv（`const` 与 `volatile`）类型限定符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/cv)
