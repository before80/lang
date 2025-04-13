+++
title = "C 属性： maybe_unused (C23 起)"
date = 2025-04-13T11:24:16+08:00
weight = 40
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/maybe_unused](https://zh.cppreference.com/w/c/language/attributes/maybe_unused)

​	抑制对未使用实体的警告。

## 语法

| `[[` `maybe_unused` `]]`<br /> `[[` `__maybe_unused__` `]]` |      |      |
| ----------------------------------------------------------- | ---- | ---- |

## 解释

​	此属性能出现在下列实体的声明中：

- [结构体](https://zh.cppreference.com/w/c/language/struct)/[联合体](https://zh.cppreference.com/w/c/language/union)： `struct [[maybe_unused]] S;` ，
- [typedef 名](https://zh.cppreference.com/w/c/language/typedef)： `[[maybe_unused]] typedef S* PS;` ，
- 对象： `[[maybe_unused]] int x;` ，
- 结构体/联合体成员： `union U { [[maybe_unused]] int n; };` ，
- [函数](https://zh.cppreference.com/w/c/language/function_definition)： `[[maybe_unused]] void f(void);` ，
- [枚举](https://zh.cppreference.com/w/c/language/enum)： `enum [[maybe_unused]] E {};` ，
- 枚举项： `enum { A [[maybe_unused]], B [[maybe_unused]] = 42 };` 。

​	若编译器对未使用实体发布警告，则对任何声明为 `maybe_unused` 的实体抑制该警告。

## 示例

```c
#include <assert.h>
 
[[maybe_unused]] void f([[maybe_unused]] _Bool cond1, [[maybe_unused]] _Bool cond2)
{
   [[maybe_unused]] _Bool b = cond1 && cond2;
   assert(b); // 发布模式中， assert 被编译掉，而 b 不被使用
              // 无警告，因为它声明为 [[maybe_unused]]
} // 参数 cond1 与 cond2 不被使用，无警告
 
int main(void)
{
    f(1, 1);
}
```

## 参阅

maybe_unused 的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/maybe_unused)