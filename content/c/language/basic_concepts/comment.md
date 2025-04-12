+++
title = "注释"
date = 2025-04-11T19:34:57+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/comment](https://zh.cppreference.com/w/c/comment)

​	注释的作用是一套代码内文档。插入注释到程序中时，编译器直接忽略它们；它们只是有意地被人类用作读取源码的笔记。

## 语法

`/*注释*/` （1）

`//注释`      （2）（C99起）

1）通称为“ C 风格”或“多行”注释。

2）通称为“ C++ 风格”或“单行”注释。

​	在[翻译阶段 3](https://zh.cppreference.com/w/c/language/translation_phases)，通过把每段注释替换为单个空白字符，将所有注释从程序中移除。

## C 风格

​	C 风格注释通常用于注释大块文本或小片代码；不过亦可用它们注释单行。只需以 `/*` 和 `*/` 环绕文本，即可将文本作为 C 风格注释插入。C 风格注释告诉编译器忽略 `/*` 和 `*/` 间的所有内容。尽管不是 C 标准的一部分，`/**` 和 `*/` 常用于指示文档块；这是合法的，因为第二个星号仅仅被当做注释的一部分。

​	若非处于[字符常量](https://zh.cppreference.com/w/c/language/character_constant)、[字符串字面量](https://zh.cppreference.com/w/c/language/string_literal)或注释之内，字符 `/*` 即引入一段注释。检验这种注释的内容时，仅鉴别各个多字节字符并寻找终止注释的 `*/`。C 风格注释不能嵌套。

> **C++ 风格**
>
> ​	C++ 风格注释通常用于注释单行文本或代码；不过亦可将它们放在一起组成多行注释。只需将 `//` 置于文本前并在文本后跟随换行符，即将文本作为 C++ 风格注释插入。C++ 风格注释告诉编译器忽略 `//` 和换行符间的所有内容。
>
> ​	若非处于[字符常量](https://zh.cppreference.com/w/c/language/character_constant)、[字符串字面量](https://zh.cppreference.com/w/c/language/string_literal)或注释之内，字符 `//` 即引入一段注释，它包含所有多字节字符，直至但不包含下个换行符。检验这种注释的内容时，仅鉴别各个多字节字符并寻找终止注释的换行符。C++ 风格注释能嵌套：
>
> ```c++
> //  y = f(x);   // 调用算法
> ```
>
> ​	C 风格注释可出现在 C++ 风格注释内：
>
> ```c++
> //  y = f(x);   /* 调用算法 */
> ```
>
> ​	C++ 风格注释可出现在 C 风格注释内；这是一种排除一小块源代码的机制：
>
> ```c++
> /*
>     y = f(x);   // 调用算法
>     z = g(x);
> */
> ```



## 注意

​	由于注释在预处理器阶段前[已被移除](https://zh.cppreference.com/w/c/language/translation_phases)，故宏不能用于组成注释，且不终止的 C 风格注释不会从被 #include 的文件中漏出。

```c
/* 试图用宏组成注释。 */
/* 但空格替换了字符 "//"。 */
#ifndef DEBUG
    #define PRINTF //
#else
    #define PRINTF printf
#endif
...  
PRINTF("Error in file %s at line %i\n", __FILE__, __LINE__);
```

​	除了注释掉，用于排除源码的其他机制还有：

```c
#if 0
    puts("this will not be compiled");
    /* 与 C 风格注释不冲突 */
    // 与 C++ 风格注释不冲突
#endif
```

​	和

```c
if(0) {
    puts("this will be compiled but not be executed");
    /* 与 C 风格注释不冲突 */
    // 与 C++ 风格注释不冲突
}
```

​	C99 中引入 `//` 注释，在一些罕有场合是破坏性更改：

```c
a = b //*除数：*/ c
+ d; /* C89 编译为 a = b / c + d;
        C99 编译为 a = b + d; */
```

## 示例

GCC 13.1(C23)

```c
#include <stdio.h>
/*
C 风格注释
能含有多行。
*/
 
/* 或仅一行。 */
 
// C++ 风格注释能注释一行。
 
// 或者，能将
// 它们串在一起。
 
int main(void)
{
  // 将不运行下方代码
  // puts("Hello");
 
  // 将运行下方代码
  puts("World");
 
  // 有关反斜杠+换行的注解：
  // 尽管属于翻译阶段 2（而非注释的阶段 3），
  // '\' 仍会决定哪部分源代码
  // 会被当做 '注释':
  // 此条注释会连上下一行 \
  puts("Won't be run"); // 可能引发 "多行注释" 警告
  puts("Hello, again");
}
```

Compiler messages:

```
main.cpp: In function 'main':
main.cpp:26:3: warning: multi-line comment [-Wcomment]
   26 |   // 此条注释会连上下一行 \
```

​	输出：

```
World
Hello, again
```

## 引用

 C17 标准（ISO/IEC 9899:2018）：   6.4.9 Comments （第 54 页）     

C11 标准（ISO/IEC 9899:2011）：   6.4.9 Comments （第 75 页）    

 C99 标准（ISO/IEC 9899:1999）：   6.4.9 Comments （第 66 页）     

C89/C90 标准（ISO/IEC 9899:1990）：3.1.9 Comments

## 参阅

**注释**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/comments)**