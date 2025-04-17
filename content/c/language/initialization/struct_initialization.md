+++
title = "结构体与联合体初始化"
date = 2025-04-13T10:01:21+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/struct_initialization](https://zh.cppreference.com/w/c/language/struct_initialization)

​	[初始化]({{< ref "/c/language/initialization" >}})[结构体]({{< ref "/c/language/declarations/struct" >}})或[联合体]({{< ref "/c/language/declarations/union" >}})类型的对象时，初始化式必须是成员初始化式的非空、(C23 前)花括号环绕、逗号分隔的列表：

| `=` `{` *表达式* `,` `...` `}`                | (1)  | (C99 前) |
| --------------------------------------------- | ---- | -------- |
| `=` `{` *指派符*(可选) *表达式* `,` `...` `}` | (2)  | (C99 起) |
| `=` `{` `}`                                   | (3)  | (C23 起) |

​	其中 *指派符* 是一序列（空白符分隔或相邻的）`.` *成员* 形式的单独成员指派符，和 `[` *索引* `]` 形式的[数组指派符]({{< ref "/c/language/initialization/array_initialization" >}})。

​	[隐式地初始化]({{< ref "/c/language/initialization#.E9.9A.90.E5.BC.8F.E5.88.9D.E5.A7.8B.E5.8C.96" >}})所有未显式初始化的成员均被[零初始化]({{< ref "/c/language/initialization#.E9.9B.B6.E5.88.9D.E5.A7.8B.E5.8C.96" >}})。

## 解释

​	初始化[联合体]({{< ref "/c/language/declarations/union" >}})时，初始化式列表必须只有一个成员，它初始化联合体的首个成员，除非使用指派初始化式(C99 起)。

```c
union { int x; char c[4]; }
  u = {1},           // 令 u.x 活跃，拥有值 1
 u2 = { .c={'\1'} }; // 令 u2.c 活跃，拥有值 {'\1','\0','\0','\0'}
```

​	初始化[结构体]({{< ref "/c/language/declarations/struct" >}})时，列表中的首个初始化式初始化首个被声明成员（除非指定了指派符）(C99 起)，而所有后继的无指派符(C99 起)初始化式，初始化先前表达式所初始化者之后的结构体成员。

```c
struct point {double x,y,z;} p = {1.2, 1.3}; // p.x=1.2, p.y=1.3, p.z=0.0
div_t answer = {.quot = 2, .rem = -1 };      // div_t 中的成员顺序可以不同
```

​	指派符导致后随的初始化式初始化该指派符所描述的结构体成员。然后初始化继续按声明顺序向前，从指派符所描述成员的下个成员开始。(C99 起)

```c
struct {int sec,min,hour,day,mon,year;} z
   = {.day=31,12,2014,.sec=30,15,17}; // 初始化 z 为 {30,15,17,31,12,2014}
```

​	提供多于成员的初始化式是错误。

## 嵌套初始化

​	若结构体或联合体的成员是数组、结构体或联合体，则初始化式的花括号环绕列表中的对应初始化式，是对这些成员合法的任何初始化式，除了可以以下列方式省略其括号：

​	若嵌套初始化式以左花括号开始，则直到其右花括号为止的整个嵌套初始化式，初始化对应的成员对象。每个左开花括号建立一个新的*当前对象*。当前对象的成员以其自然顺序初始化，除非使用指派符(C99 起)：数组以下标顺序、结构体成员以声明顺序、仅初始化任何联合体的首个被声明成员。[空初始化]({{< ref "/c/language/initialization#.E7.A9.BA.E5.88.9D.E5.A7.8B.E5.8C.96" >}})当前对象内未由闭花括号显式初始化的子对象。

```c
struct example {
    struct addr_t {
       uint32_t port;
    } addr;
    union {
       uint8_t a8[4];
       uint16_t a16[2];
    } in_u;
};
struct example ex = { // struct example 的初始化式列表开始
                     { // ex.addr 的初始化式列表开始
                        80 // 初始化 struct addr_t 的唯一成员
                     }, // ex.addr 的初始化式列表结束
                     { // ex.in_u 的初始化式列表开始
                        {127,0,0,1} // 初始化 union in_u 的首个成员
                     } };
```

​	若嵌套初始化式不以左花括号开始，则仅从列表采用足够的初始化式，以用于该成员数组、结构体或联合体的元素或成员；任何剩下的初始化式留待初始化下个结构体成员：

```c
struct example ex = {80, 127, 0, 0, 1}; // 80 初始化 ex.addr.port
                                        // 127 初始化 ex.in_u.a8[0]
                                        // 0 初始化 ex.in_u.a8[1]
                                        // 0 初始化 ex.in_u.a8[2]
                                        // 1 初始化 ex.in_u.a8[3]
```

| `struct example ex2 = { // 当前对象为 ex2，指派符属于 struct example 的成员                       .in_u.a8[0]=127, 0, 0, 1, .addr=80};  struct example ex3 = {80, .in_u={ // 更改当前对象为联合体 ex.in_u                           127,                           .a8[2]=1 // 此指派符指代 union in_u 的成员                      } };`若显式初始化任何子对象二次（在使用指派符时可能发生），则使用的初始化式，是较后出现于列表中的初始化式（可能不求值较早的初始化式）：`struct {int n;} s = {printf("a\n"), // 可能打印或跳过它                     .n=printf("b\n")}; // 始终打印`尽管任何未初始化的子对象都被隐式初始化，若子对象的显式初始化在初始化式列表中出现较早，则同一子对象的隐式初始化决不会覆盖显式初始化（选择 clang 以观察正确的输出）：运行此代码`#include <stdio.h> typedef struct { int k; int l; int a[2]; } T; typedef struct { int i;  T t; } S; T x = {.l = 43, .k = 42, .a[1] = 19, .a[0] = 18 }; // 初始化 x 为 {42, 43, {18, 19} } int main(void) {    S l = { 1,          // 初始化 l.i 为 1           .t = x,      // 初始化 l.t 为 {42, 43, {18, 19} }           .t.l = 41,   // 更改 l.t 为 {42, 41, {18, 19} }           .t.a[1] = 17 // 更改 l.t 为 {42, 41, {18, 17} }          };    printf("l.t.k is %d\n", l.t.k); // .t = x 显式设置 l.t.k 为 42                                    // .t.l = 41 会隐式清零 l.t.k }`输出：`l.t.k is 42`然而，当初始化式以左开花括号开始时，会完全重初始化其*当前对象*，并忽略其任何子对象的先前的显式初始化式：`struct fred { char s[4]; int n; }; struct fred x[ ] = { { { "abc" }, 1 }, // 初始化 x[0] 为 { {'a','b','c','\0'}, 1 }                      [0].s[0] = 'q'   // 更改 x[0] 为 { {'q','b','c','\0'}, 1 }                   }; struct fred y[ ] = { { { "abc" }, 1 }, // 初始化 y[0] 为 { {'a','b','c','\0'}, 1 }                     [0] = { // 当前对象现在是整个 y[0] 对象                             .s[0] = 'q'                             } // 以 { {'q','\0','\0','\0'}, 0 } 替换 y[0]                    };` | (C99 起) |
| ------------------------------------------------------------ | -------- |
|                                                              |          |

​	嵌套指派符时，成员的指派符后随外围结构体/联合体/数组的指派符。在任何嵌套的方括号初始化式列表中，最外层指派符指代*当前对象*，而且只在*当前对象*中选择要初始化的子对象。(C99 起)

```c
struct example ex2 = { // 当前对象为 ex2，指派符属于 struct example 的成员
                       .in_u.a8[0]=127, 0, 0, 1, .addr=80}; 
struct example ex3 = {80, .in_u={ // 更改当前对象为联合体 ex.in_u
                           127,
                           .a8[2]=1 // 此指派符指代 union in_u 的成员
                      } };
```



​	若显式初始化任何子对象二次（在使用指派符时可能发生），则使用的初始化式，是较后出现于列表中的初始化式（可能不求值较早的初始化式）：(C99 起)

```c
struct {int n;} s = {printf("a\n"), // 可能打印或跳过它
                     .n=printf("b\n")}; // 始终打印
```



​	尽管任何未初始化的子对象都被隐式初始化，若子对象的显式初始化在初始化式列表中出现较早，则同一子对象的隐式初始化决不会覆盖显式初始化（选择 clang 以观察正确的输出）：(C99 起)

```c
#include <stdio.h>
typedef struct { int k; int l; int a[2]; } T;
typedef struct { int i;  T t; } S;
T x = {.l = 43, .k = 42, .a[1] = 19, .a[0] = 18 };
 // 初始化 x 为 {42, 43, {18, 19} }
int main(void)
{
    S l = { 1,          // 初始化 l.i 为 1
           .t = x,      // 初始化 l.t 为 {42, 43, {18, 19} }
           .t.l = 41,   // 更改 l.t 为 {42, 41, {18, 19} }
           .t.a[1] = 17 // 更改 l.t 为 {42, 41, {18, 17} }
          };
    printf("l.t.k is %d\n", l.t.k); // .t = x 显式设置 l.t.k 为 42
                                    // .t.l = 41 会隐式清零 l.t.k
}
```

输出：

```txt
l.t.k is 42
```

​	然而，当初始化式以左开花括号开始时，会完全重初始化其*当前对象*，并忽略其任何子对象的先前的显式初始化式：(C99 起)

```c
struct fred { char s[4]; int n; };
struct fred x[ ] = { { { "abc" }, 1 }, // 初始化 x[0] 为 { {'a','b','c','\0'}, 1 }
                      [0].s[0] = 'q'   // 更改 x[0] 为 { {'q','b','c','\0'}, 1 }
                   };
struct fred y[ ] = { { { "abc" }, 1 }, // 初始化 y[0] 为 { {'a','b','c','\0'}, 1 }
                     [0] = { // 当前对象现在是整个 y[0] 对象
                             .s[0] = 'q' 
                            } // 以 { {'q','\0','\0','\0'}, 0 } 替换 y[0]
                    };
```



## 注解

​	初始化式列表可拥有尾随的逗号，它被忽略。

```c
struct {double x,y;} p = {1.0,
                          2.0, // 尾随逗号 OK
                          };
```

​	C 中，初始化器的花括号列表不能为空（注意 C++ 允许空列表，并且注意 C 中[结构体]({{< ref "/c/language/declarations/struct" >}})不能为空）：(C23 前)

​	与 C++ 相同，C 中初始化式列表可为空：(C23 起)

```c
struct {int n;} s = {0}; // OK
struct {int n;} s = {}; // C23 前错误：初始化式列表不能为空
                        // C23 起 OK：初始化 s.n 为 0
struct {} s = {}; // 错误：结构体不能为空
```

​	在初始化任何存储期的聚合体时，初始化式列表中的每个表达式必须都是[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})。(C99 前)

​	同所有其他初始化，在初始化静态或线程局域(C11 起)[存储期]({{< ref "/c/language/declarations/storage_duration" >}})的聚合体时，初始化式列表中的每个表达式必须为[常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})：(C99 起)

```
static struct {char* p} s = {malloc(1)}; // 错误
```

​	任何初始化式中的子表达式[求值顺序]({{< ref "/c/language/expressions/eval_order" >}})为非确定顺序（但 C++11 起的 C++ 中不同）：(C99 起)

```c
int n = 1;
struct {int x,y;} p = {n++, n++}; // 未指定，但是良定义的行为：
                                  // n 以任意顺序自增二次
                                  // p 等于 {1,2} 和 {2,1} 都是合法的
```

## 示例

> 本节未完成 
>
> 原因：更多实用的示例，最好初始化某些接头结构体

```c
#include <stdio.h>
#include <time.h>
 
int main(void)
{
    char buff[70];
    // 指派初始化式简化成员顺序未指定的结构体的使用
    struct tm my_time = { .tm_year=2012-1900, .tm_mon=9, .tm_mday=9,
                          .tm_hour=8, .tm_min=10, .tm_sec=20 };
    strftime(buff, sizeof buff, "%A %c", &my_time);
    puts(buff);
}
```

可能的输出：

```txt
Sunday Sun Oct  9 08:10:20 2012
```

## 参阅

聚合初始化的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/aggregate_initialization)
