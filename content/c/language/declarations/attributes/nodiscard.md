+++
title = "C 属性： nodiscard (C23 起)"
date = 2025-04-13T11:22:38+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/attributes/nodiscard](https://zh.cppreference.com/w/c/language/attributes/nodiscard)

​	若从转型到 void 以外的[弃值表达式]({{< ref "/c/language/expressions" >}})，调用声明为 `nodiscard` 的函数，或调用返回声明 `nodiscard` 的结构体/联合体/枚举的函数，则鼓励编译器发出警告。

## 语法

| `[[` `nodiscard` `]]` <br />`[[` `__nodiscard__` `]]`        | (1)  |      |
| ------------------------------------------------------------ | ---- | ---- |
| `[[` `nodiscard` `(` *字符串字面量* `)` `]]` <br />`[[` `__nodiscard__` `(` *字符串字面量* `)` `]]` | (2)  |      |

| *字符串字面量* | -    | 能用于解释为何不应舍弃结果的原理的文本 |
| -------------- | ---- | -------------------------------------- |

## 解释

​	出现于函数声明、枚举声明或结构体/联合体声明。

​	若从转型到 void 以外的[弃值表达式]({{< ref "/c/language/expressions" >}})，

- 调用声明为 `nodiscard` 的函数，或
- 调用返回声明 `nodiscard` 的结构体/联合体/枚举的函数，

​	则鼓励编译器发出警告。

​	若指定 *字符串字面量* 则通常包含它于警告中。

## 示例

```c
struct [[nodiscard]] error_info { int status; /*...*/ };
struct error_info enable_missile_safety_mode() { /*...*/ return (struct error_info){0}; }
void launch_missiles() { /*...*/ }
void test_missiles() {
   enable_missile_safety_mode(); // 编译器可能在舍弃 nodiscard 值时警告
   launch_missiles();
}
struct error_info* foo() { static struct error_info e; /*...*/ return &e; }
void f1() {
    foo(); // 不以值返回 nodiscard 类型，无警告
}
// nodiscard( 字符串字面量 ):
[[nodiscard("PURE FUN")]] int strategic_value(int x, int y) { return x ^ y; }
 
int main()
{
    strategic_value(4,2); // 编译器可能在舍弃 nodiscard 值时警告
    int z = strategic_value(0,0); // OK: 未丢弃返回值
    return z;
}
```

​	可能的输出：

```txt
game.cpp:5:4: warning: ignoring return value of function declared with 'nodiscard' attribute
game.cpp:17:5: warning: ignoring return value of function declared with 'nodiscard' attribute: PURE FUN
```

## 参阅

**nodiscard** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/attributes/nodiscard)**
