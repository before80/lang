+++
title = "<stddef.h>"
date = 2025-04-14T22:03:04+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 宏

### unreachable <- (C23 起)

```c
#define unreachable() /* 见下文 */ (C23 起)
```

​	仿函数宏 `unreachable` 展开成 void 表达式。执行 unreachable() 导致[未定义行为](https://zh.cppreference.com/w/c/language/behavior)。

​	实现可以用此宏优化掉不可能的代码分支（常于优化构建中），或使之进入陷阱以免后续执行（常于调试构建中）。

**可能的实现**

```c
// 若可能则使用编译器特定的扩展。
#ifdef __GNUC__ // GCC, Clang, ICC
 
#define unreachable() (__builtin_unreachable())
 
#elifdef _MSC_VER // MSVC
 
#define unreachable() (__assume(false))
 
#else
// 即使不使用扩展，空函数体与 noreturn 属性也足以引发未定义行为。
 
// 由于 C 中 inline 函数的规则，unreachable_impl 的外部定义必须发放到分离的翻译单元。
 
[[noreturn]] inline void unreachable_impl() {}
#define unreachable() (unreachable_impl())
 
#endif
```

**示例**

```c
#include <assert.h>
#include <stddef.h>
#include <stdint.h>
#include <stdlib.h>
 
struct Color { uint8_t r, g, b, a; };
struct ColorSpan { struct Color* data; size_t size; };
 
// 假设仅支持受限制的材质容量集合。
struct ColorSpan allocate_texture(size_t xy)
{
    switch (xy)
    {
    case 128: [[fallthrough]];
    case 256: [[fallthrough]];
    case 512:
    {
        /* ... */
        struct ColorSpan result = {
            .data = malloc(xy * xy * sizeof(struct Color)),
            .size = xy * xy
        };
 
        if (!result.data)
            result.size = 0;
 
        return result;
    }
    default:
        unreachable();
    }
}
 
int main(void)
{
    struct ColorSpan tex = allocate_texture(128); // OK
    assert(tex.size == 128 * 128);
 
    struct ColorSpan badtex = allocate_texture(32);  // 未定义行为
 
    free(badtex.data);
    free(tex.data);
}
```

可能的输出：

```txt
Segmentation fault
```

## 函数





