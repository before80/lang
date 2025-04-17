+++
title = "C 属性： fallthrough (C23 起)"
date = 2025-04-13T11:20:31+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/fallthrough](https://zh.cppreference.com/w/c/language/attributes/fallthrough)

​	指示从前一标号直落是有意的，而在发生直落时给出警告的编译器不应诊断它。

## 语法

| `[[` `fallthrough` `]]` `[[` `__fallthrough__` `]]` |      |      |
| --------------------------------------------------- | ---- | ---- |

## 解释

​	仅可用于[属性声明]({{< ref "/c/language/declarations" >}})以创建*直落声明*（`[[fallthrough]];`）。

​	直落声明仅可用于 [`switch`](https://zh.cppreference.com/w/cpp/language/switch) 语句中，其中要遇到的下个块项（语句、声明或标号）是该 `switch` 语句的带 `case` 或 `default` 标号的语句。

​	指示从前一标号直落是有意的，而在发生直落时给出警告的编译器不应诊断它。

## 示例

```c
#include <stdbool.h>
 
void g(void) {}
void h(void) {}
void i(void) {}
 
void f(int n) {
  switch (n) {
    case 1:
    case 2:
      g();
     [[fallthrough]];
    case 3: // 直落时不警告
      h();
    case 4: // 编译器可在发生直落时警告
      if(n < 3) {
          i();
          [[fallthrough]]; // OK
      }
      else {
          return;
      }
    case 5:
      while (false) {
        [[fallthrough]]; // 谬构：下一语句不是同一迭代的一部分
      }
    case 6:
      [[fallthrough]]; // 谬构：下一语句不是同一迭代的一部分
  }
}
 
int main(void) {}
```

## 参阅

fallthrough 的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/fallthrough)
