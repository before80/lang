+++
title = "作用域"
date = 2025-04-11T20:18:56+08:00
weight = 60
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/scope](https://zh.cppreference.com/w/c/language/scope)

​	C 程序中出现的每个[标识符]({{< ref "/c/language/basic_concepts/identifier" >}})都仅在一些可能不连续的部分*可见*（即可使用），这些部分被称为其*作用域*。

​	在作用域内，标识符仅若在不同[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})中，才可以指代多于一个实体。

​	C 拥有四种作用域：

- 块作用域
- 文件作用域
- 函数作用域
- 函数原型作用域

## 嵌套作用域

若相同标识符所命名的两个不同实体在同一时刻都在作用域中，且它们属于同一[命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})，则作用域被嵌套（不允许其他形式的作用域重叠），而内层作用域中的声明隐藏外层作用域中的声明：

```
// 此处的命名空间为通常标识符。
 
int a;   // 名称 a 的文件作用域始于此
 
void f(void)
{
    int a = 1; // 名称 a 的块作用域始于此；隐藏文件作用域的 a
    {
      int a = 2;         // 内层 a 的作用域始于此，隐藏外层 a 
      printf("%d\n", a); // 内层 a 在作用域中，打印 2
    }                    // 内层 a 的块作用域终于此
    printf("%d\n", a);   // 外层 a 在作用域中，打印 1
}                        // 外层 a 的作用域终于此
 
void g(int a);   // 名称 a 拥有函数原型作用域；隐藏文件作用域的 a
```

## 块作用域

任何在[复合语句]({{< ref "/c/language/statements#.E5.A4.8D.E5.90.88.E8.AF.AD.E5.8F.A5" >}})，包含函数体或出现于 [if]({{< ref "/c/language/statements/if" >}})、[switch]({{< ref "/c/language/statements/switch" >}})、[for]({{< ref "/c/language/statements/for" >}})、[while]({{< ref "/c/language/statements/while" >}}) 或 [do-while]({{< ref "/c/language/statements/do" >}}) 语句中的任何表达式、声明或语句(C99 起)，或在[函数定义]({{< ref "/c/language/functions/function_definition" >}})内的参数列表中声明的标识符的作用域，在声明点开始，在声明于其中的块或语句的结尾结束。

```c
void f(int n)  // 函数参数 'n' 的作用域开始
{         // 函数体开始
   ++n;   // 'n' 在作用域中并指代函数参数
// int n = 2; // 错误：不能在同一作用域重声明标识符
   for(int n = 0; n<10; ++n) { // 循环局域的 'n' 的作用域开始
       printf("%d\n", n); // 打印 0 1 2 3 4 5 6 7 8 9
   } // 循环局域的 'n' 的作用域结束
     // 函数参数 'n' 回到作用域
   printf("%d\n", n); // 打印参数的值
} // 函数参数 'n' 的作用域结束
int a = n; // 错误：名称 'n' 不在作用域中
```

> ​	C99 前，选择和迭代语句不建立其自身的块作用域（尽管若在语句中使用复合语句，则它拥有其通常的块作用域）：(C99 起)
>
> ```c
> enum {a, b};
> int different(void)
> {
>     if (sizeof(enum {b, a}) != sizeof(int))
>         return a; // a == 1
>     return b; // C89 中 b == 0，C99 中 b == 1
> }
> ```

​	块作用域变量默认[无链接]({{< ref "/c/language/declarations/storage_duration" >}})并拥有[自动存储期]({{< ref "/c/language/declarations/storage_duration" >}})。注意非 VLA 局部变量的存储期在进入块时开始，但在见到声明前，该变量不在作用域中且不能访问。

## 文件作用域

在任何块或形参列表外声明的任何标识符的作用域，在声明点开始，翻译单元尾结束。

```c
int i; // i 的作用域开始
static int g(int a) { return a; } // g 的作用域开始（注意 "a" 拥有块作用域）
int main(void)
{
    i = g(2); // i 和 g 在作用域中
}
```

文件作用域的标识符默认拥有[外部链接]({{< ref "/c/language/declarations/storage_duration" >}})和[静态存储期]({{< ref "/c/language/declarations/storage_duration" >}})。

## 函数作用域

声明于函数内部的[标号（且只有标号）]({{< ref "/c/language/statements#Labels" >}})，在该函数中的所有位置（所有嵌套块中，其自身声明前后）都在作用域内。注意：任何语句前的冒号字符前的标识符，若不用于其他用途，则隐式声明一个标号。

```c
void f()
{
   {   
       goto label; // label 在作用域中，尽管之后才声明
label:;
   }
   goto label; // 标号忽略块作用域
}
 
void g()
{
    goto label; // 错误：g() 中 label 不在作用域中
}
```

## 函数原型作用域

非函数定义的[函数声明]({{< ref "/c/language/functions/function_declaration" >}})的形参列表中引入的名称的作用域，在函数[声明器]({{< ref "/c/language/declarations" >}})的结尾结束。

```c
int f(int n,
      int a[n]); // n 在作用域中并指代第一形参
```

注意，若声明中有多个或嵌套声明器，则作用域在最近的外围函数声明器的结尾结束：

```c
void f ( // 函数名 'f' 在文件作用域
 long double f,            // 标识符 'f' 现在在作用域中，隐藏文件作用域的 'f'
 char (**a)[10 * sizeof f] // 'f' 指代第一形参，它在作用域中
);
 
enum{ n = 3 };
int (*(*g)(int n))[n]; // 函数形参 'n' 的作用域在其函数声明符的结尾结束
                       // 数组声明器中，全局 n 在作用域
// （这声明指向返回 3 个 int 的数组的指针的函数的指针）
```

## 声明点

​	结构体、联合体及枚举标签的作用域，在声明该标签的类型指定符中的标签出现后立即开始。

```c
struct Node {
   struct Node* next; // Node 在作用域中并指代此 struct
};
```

​	枚举常量的作用域，在枚举项列表中其定义枚举项的出现后立即开始。

```c
enum { x = 12 };
{
    enum { x = x + 1, // 新 x 在逗号前不在作用域中，初始化 x 为 13
           y = x + 1  // 新枚举项 x 现在在作用域中，初始化 y 为 14
         };
}
```

​	任何其他标识符的作用域，正好在其声明符结束后和初始化式前开始，若存在初始化式：

```c
int x = 2; // 第一个 'x' 的作用域开始
{
    int x[x]; // 新声明的 x 的作用域在声明符（x[x]）后开始。
              // 在声明符内，外层 'x' 仍在作用域中。
              // 这声明 2 个 int 的 VLA 数组。
}
 
unsigned char y = 32; // 外层 'y' 的作用域开始
{
    unsigned char y = y;
            // 内层 'y' 的作用域在初始化式（ = y ）前开始
            // 这不会以值 32 初始化内层 'y'，
            // 这以其自身的不确定值初始化内层 'y'
}
 
unsigned long factorial(unsigned long n)
// 声明式结束，'factorial' 从此点开始在作用域中
{
   return n < 2 ? 1 : n * factorial(n - 1); // 递归调用
}
```

​	特别的是，省略了名字的 [类型名](https://zh.cppreference.com/w/c/language/types) 的作用域，在如同未省略名字时，作用域的开始位置（即省略的标识符之后）开始。

## 注意

​	C89 前，拥有外部链接的标识符在块中引入时，拥有文件作用域，因此不要求 C89 编译器诊断已离开作用域的 extern 标识符的使用（这种使用是未定义行为）。

​	C 中，循环体内的局部变量，能隐藏声明于 [for]({{< ref "/c/language/statements/for" >}}) 循环的初始化子句中的变量（其作用域为嵌套的），但 C++ 中不能如此。

​	不同于 C++，C 无结构体作用域：声明于 struct/union/enum 声明内的名称在结构体声明所在的相同作用域（除了数据成员在其[成员命名空间]({{< ref "/c/language/basic_concepts/name_space" >}})中）：

```c
struct foo {
    struct baz {};
    enum color {RED, BLUE};
};
struct baz b; // baz 在作用域中
enum color x = RED; // color 和 RED 在作用域中
```
