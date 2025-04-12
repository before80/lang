+++
title = "生存期"
date = 2025-04-11T20:22:45+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/lifetime](https://zh.cppreference.com/w/c/language/lifetime)

​	C 中每个[对象](https://zh.cppreference.com/w/c/language/object)存在、拥有常地址、保有其最近一次存储值（除非其值不确定），对于 VLA 还有保有其大小(C99 起)的程序执行部分，被称作该对象的*生存期*。

​	对于声明有自动、静态及线程存储期的对象，生存期等于其[存储期](https://zh.cppreference.com/w/c/language/storage_duration)（注意非 VLA 和 VLA 自动存储期的区别）。

​	对于拥有分配存储期的对象，其生存期始于分配函数的返回（包含从 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 返回），终于 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 或解分配函数的调用。注意因为分配的对象没有[声明类型](https://zh.cppreference.com/w/c/language/object)，首次访问该对象所用的左值表达式类型会成为其[有效类型](https://zh.cppreference.com/w/c/language/object)。

​	在生存期外访问对象是未定义行为。

```c
int* foo(void) {
    int a = 17; // a 拥有自动存储期
    return &a;
}  // a 的生存期结束
int main(void) {
    int* p = foo(); // p 指向生存期结束后的对象（“悬垂指针”）
    int n = *p; // 未定义行为
}
```

​	指向生存期结束的对象（或该对象后一位置）的指针拥有不确定值。

## 临时生存期

​	[非左值表达式](https://zh.cppreference.com/w/c/language/value_category)所指代的拥有数组成员的结构体和联合体对象（直接为其成员或为嵌套的结构体/联合体成员）拥有*临时生存期*。临时生存期始于求值指代该对象的表达式，终于下一个[序列点](https://zh.cppreference.com/w/c/language/eval_order)(C11 前)包含它的完整表达式或完整声明器结束(C11 起)。

​	任何修改临时生存期对象的尝试会导致未定义行为。

```
struct T { double a[4]; };
struct T f(void) { return (struct T){3.15}; }
double g1(double* x) { return *x; }
void g2(double* x) { *x = 1.0; }
int main(void)
{
    double d = g1(f().a); // C99：对 g1 中的 a[0] 的访问为 UB
                          //      其生存期结束于 g1 开头的序列点
                          // C11：OK，d 为 3.15
    g2(f().a); // C99：修改生存期结束于序列点的 a[0] 为 UB
               // C11：试图修改临时对象为 UB
}
```