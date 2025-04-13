+++
title = "外部及试探性定义"
date = 2025-04-13T11:07:51+08:00
weight = 130
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/extern](https://zh.cppreference.com/w/c/language/extern)

​	在[翻译单元](https://zh.cppreference.com/w/c/language/translation_phases)的顶层（及在预处理器后拥有所有 #include 的源文件），每个 C 程序都是[声明](https://zh.cppreference.com/w/c/language/declarations)的序列，它们声明拥有[外部或内部链接](https://zh.cppreference.com/w/c/language/storage_duration)的函数和对象。这些声明被称作*外部声明*，因为它们出现于任何函数之外。

```c
extern int n; // 外部声明拥有外部链接
int b = 1;    // 外部定义拥有外部链接
static const char *c = "abc"; // 外部定义拥有内部链接
int f(void)    // 外部定义拥有外部链接
{
    int a = 1; // 非外部
    return b; 
}
static void x(void) // 外部定义拥有内部链接
{
}
```

​	声明为拥有外部声明的对象拥有静态[存储期](https://zh.cppreference.com/w/c/language/storage_duration)，从而不能使用 auto 或 register 说明符[Template:rev inc](https://zh.cppreference.com/mwiki/index.php?title=Template:rev_inc&action=edit&redlink=1)。这些由外部声明引入的标识符拥有[文件作用域](https://zh.cppreference.com/w/c/language/scope)。

## 试探性定义

​	*试探性定义*是没有初始化器的外部声明，且要么没有[存储类说明符](https://zh.cppreference.com/w/c/language/storage_duration)要么带有说明符 static。

​	*试探性定义*是可能或可能不表现为定义的声明。若在同一翻译单元的前方或后方能找到实际的外部定义，则试探性定义仅表现为声明。

```c
int i1 = 1;     // 定义，外部链接
int i1;         // 试探性定义，表现为声明，因为 i1 已定义
extern int i1;  // 声明，引用前面的定义
 
extern int i2 = 3; // 定义，外部链接
int i2;            // 试探性定义，表现为声明，因为 i2 已定义
extern int i2;     // 声明，引用到前面的外部链接定义
```

​	若在同一翻译单元中无定义，则试探性定义表现为将对象[空初始化](https://zh.cppreference.com/w/c/language/initialization#.E7.A9.BA.E5.88.9D.E5.A7.8B.E5.8C.96)的实际定义。

```c
int i3;        // 试探性定义，外部链接
int i3;        // 试探性定义，外部链接
extern int i3; // 声明，外部链接
// 在此翻译单元中，如同以“ int i3 = 0; ”方式定义 i3
```

​	不同于 [extern](https://zh.cppreference.com/w/c/language/storage_duration) 声明（如果前一声明已建立标识符链接， extern 声明不更改链接），试探性定义可以与同一标识符另一声明的链接不一致。若同一标识符的二个声明均在作用域内且拥有不同链接，则行为未定义：

```c
static int i4 = 2; // 定义，内部链接
int i4;            // 未定义行为：链接与前一行不一致
extern int i4;     // 声明，引用到内部链接定义
 
static int i5; // 试探性定义，内部链接
int i5;        // 未定义行为：链接与前一行不一致
extern int i5; // 引用到前者，其链接为内部
```

​	拥有内部链接的试探性定义必须拥有完整类型。

```c
static int i[]; // 错误：试探性 static 声明中的不完整类型
int i[]; // OK：等价于 int i[1] = {0}; 除非在此文件之后重声明
```

### 唯一定义规则

​	每个翻译单元可以拥有每个具有[内部链接](https://zh.cppreference.com/w/c/language/storage_duration)（static 全局名称）的零或一个外部定义。

​	若一个具有内部链接的标识符被用于任何异于非 VLA 的(C99 起) [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 、[`_Alignof`](https://zh.cppreference.com/w/c/language/_Alignof)(C11 起)(C23 前)、[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 或 [`typeof`](https://zh.cppreference.com/w/c/language/typeof)(C23 起) 的表达式，则在该翻译单元中必须有且只有一个该标识符的外部定义。

​	整个程序可以拥有每个具有[外部链接](https://zh.cppreference.com/w/c/language/storage_duration)的标识符的零或一个外部定义。

​	若一个具有外部链接的标识符被用于任何异于非 VLA 的(C99 起) [`sizeof`](https://zh.cppreference.com/w/c/language/sizeof) 、[`_Alignof`](https://zh.cppreference.com/w/c/language/_Alignof)(C11 起)(C23 前)、[`alignof`](https://zh.cppreference.com/w/c/language/alignof)(C23 起) 或 [`typeof`](https://zh.cppreference.com/w/c/language/typeof)(C23 起) 的表达式，则在整个程序中必须有且只有一个该标识符的外部定义。

## 注解

​	不同翻译单元中的内联定义不受一个定义规则约束。内联函数定义的细节见 [`inline`](https://zh.cppreference.com/w/c/language/inline)。(C99 起)

​	关键词 extern 与文件作用域中声明在一起的含义，见[存储期及链接](https://zh.cppreference.com/w/c/language/storage_duration)。

​	声明与定义间的区别见[定义](https://zh.cppreference.com/w/c/language/declarations#.E5.AE.9A.E4.B9.89)。

​	发明试探性定义是为了标准化各种 C89 前的前置声明具有内部链接标识符的手段。

​	