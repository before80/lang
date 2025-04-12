+++
title = "查找与命名空间"
date = 2025-04-11T20:24:38+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/name_space](https://zh.cppreference.com/w/c/language/name_space)

​	在 C 程序中遇到[标识符](https://zh.cppreference.com/w/c/language/identifier)时，会查找定位引入该标识符的，并且在当前[作用域内](https://zh.cppreference.com/w/c/language/scope)的[声明](https://zh.cppreference.com/w/c/language/declarations)。若同一标识符的多个声明属于不同种被称作“命名空间”的类别，则 C 允许它们同时存在于作用域内：

1) 标号命名空间：所有声明为[标号](https://zh.cppreference.com/w/c/language/statements#.E6.A0.87.E5.8F.B7)的标识符。
2) 标签名：所有声明为[结构体](https://zh.cppreference.com/w/c/language/struct)、[联合体](https://zh.cppreference.com/w/c/language/union)及[枚举类型](https://zh.cppreference.com/w/c/language/enum)名称的标识符。注意所有这三种标签共享同一命名空间。
3) 成员名：所有声明为[结构体](https://zh.cppreference.com/w/c/language/struct)或[联合体](https://zh.cppreference.com/w/c/language/union)之一的成员的标识符。每个结构体和联合体引入它自己的这种命名空间。
4) 全局属性命名空间：标准定义的[属性记号](https://zh.cppreference.com/w/c/language/attributes)或实现定义的属性前缀。(C23 起)
5)  非标准属性名：属性前缀之后的属性名。每个属性前缀均拥有它所引入的实现定义属性所在的分离的命名空间。(C23 起)

6) 所有其他标识符，称之为“通常标识符”以别于 (1-5)（函数名、对象名、typedef 名、枚举常量）。

​	在查找点，根据使用方式确定标识符所属的命名空间：

1) 作为 [goto 语句](https://zh.cppreference.com/w/c/language/goto)操作数出现的标识符，会在标号命名空间中查找。
2) 关键词 `struct`、`union` 或 `enum` 之后的标识符，会在标签命名空间中查找。
3) [成员访问](https://zh.cppreference.com/w/c/language/operator_member_access)或通过指针的成员访问运算符之后的标识符，会在类型成员命名空间中查找，该类型由成员访问运算符的左操作数确定。
4) 直接出现于属性说明符（`[[...]]`）中的标识符，会在全局属性命名空间中查找。(C23 起)
5) 后随属性前缀之后的 `::` 记号的标识符，会在属性前缀所引入命名空间中查找。(C23 起)

6) 所有其他标识符，会在通常命名空间中查找。

## 注解

​	[宏](https://zh.cppreference.com/w/c/preprocessor/replace)名不是任何命名空间的一部分，因为语义分析前，预处理器会替换它们。

​	一个常见举措是将结构体/联合体/枚举的名称注入通常命名空间，以 [typedef](https://zh.cppreference.com/w/c/language/typedef) 声明：

```c
struct A { };       // 于标签命名空间中引入名称A
typedef struct A A; // 首先，对 "struct" 后A的查找找到标签命名空间的一个
                    // 然后将名称A引入通常命名空间
struct A* p;        // OK，此A于标签命名空间中查找
A* q;               // OK，此A于通常命名空间中查找
```

​	众所周知的一个同一标识符横跨两个命名空间使用的示例，是 POSIX 头文件 `sys/stat.h` 中的标识符 stat。它用作通常标识符时[指名一个函数](http://pubs.opengroup.org/onlinepubs/9699919799/)，而在用作标签时[指代一个结构体](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/sys_stat.h.html)。

​	不同于 C++ 中，枚举常量不是结构体成员，而且其命名空间是通常标识符的命名空间，故而 C 中无结构体作用域，其作用域是出现结构体声明的作用域：

```c
struct tagged_union {
   enum {INT, FLOAT, STRING} type;
   union {
      int integer;
      float floating_point;
      char *string;
   };
} tu;
 
tu.type = INT; // C 中 OK，C++ 中错误
```

> ​	若不支持某个标准属性、属性前缀或非标准属性名，则忽略非法的属性自身而不导致错误。(C23 起)

## 示例

```c
void foo (void) { return; } // 通常命名空间，文件作用域
struct foo {      // 标签命名空间，文件作用域
    int foo;      // 此 struct foo 的成员命名空间，文件作用域
    enum bar {    // 标签命名空间，文件作用域
        RED       // 通常命名空间，文件作用域
    } bar;        // 此 struct foo 的成员命名空间，文件作用域
    struct foo* p; // OK：使用标签/文件作用域名称 "foo"
};
enum bar x; // OK：使用标签/文件作用域 "bar"
// int foo; // 错误：通常命名空间已有 foo
//union foo { int a, b; }; // 错误：标签命名空间已有 foo 在作用域中
 
int main(void)
{
    goto foo; // OK 从标号命名空间/函数作用域使用 "foo"
 
    struct foo { // 标签命名空间，块作用域（于文件作用域中隐藏）
       enum bar x; // OK，从标签命名空间/文件作用域使用 "bar"
    };
    typedef struct foo foo; // OK：从标签命名空间/块作用域使用 foo
                            // 定义块作用域通常命名空间的 foo（隐藏于文件作用域）
    (foo){.x=RED}; // 使用通常命名空间/块作用域 foo 和通常命名空间/文件作用域 RED
 
foo:; // 标号命名空间，函数作用域
}
```

## 参阅

**名字查找**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/lookup)**