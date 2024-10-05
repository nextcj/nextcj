---
title: Rust泛型、Trait和生命周期
date: 2024-09-30 09:10:12
categories: [ 'Rust' ]
---

## 1.泛型 >

允许我们使用一个可以代表多种类型的占位符来替换特定类型，以减少代码的冗余。
高效处理重复概念的工具。
是具体类型或其他属性的抽象替代。
Optino<T>、 HashMap<K,V>、Vec<T>、Result<T,E>

如果要在函数体中使用参数，就必须在函数签名中声明它的名字，好让编译器知道这个名字指代的是什么。
`fn largest<T>(list: &[T]) -> &T {`
函数 largest 有泛型类型 T。它有个参数 list，其类型是元素为 T 的 slice。largest 函数会返回一个与 T 相同类型的引用。
```
enum Option<T> {
Some(T),
None,
}

enum Result<T, E> {
    Ok(T),
    Err(E),
}

```
编译时将泛型定义替换为具体的定义
单态化过程是 Rust 泛型在运行时极其高效的原因

## 2.Trait >

定义泛型的方法。
定义了某个特定类型拥有可能与其他类型共享的功能。
通过 trait 以一种抽象的方式定义共同行为。
可以与泛型结合，将泛型限制为只接受拥有特定行为的类型，而不是任意类型。
trait 类似于其他语言中的常被称为 接口（interfaces）的功能。

```
pub trait Summary {
fn summarize(&self) -> String;
}

pub struct NewsArticle {
pub headline: String,
pub location: String,
pub author: String,
pub content: String,
}

impl Summary for NewsArticle {
fn summarize(&self) -> String {
format!("{}, by {} ({})", self.headline, self.author, self.location)
}
}
```

## 3.生命周期 lifetimes >

是一类允许我们向编译器提供引用如何相互关联的泛型。
生命周期的功能：允许在很多场景借用值的同时，仍然可以使编译器能够检查这些引用的有效性。

生命周期确保引用在预期内一直有效。
Rust 中的每一个引用都有其 生命周期（lifetime），也就是引用保持有效的作用域。
确保运行时实际使用的引用绝对是有效的。
生命周期的主要目标是避免悬垂引用（dangling references）。

函数返回的引用的生命周期应该与传入参数的生命周期中较短那个保持一致。

生命周期语法是用于将函数的多个参数与其返回值的生命周期进行关联的。一旦它们形成了某种关联，Rust 就有了足够的信息来允许内存安全的操作并阻止会产生悬垂指针亦或是违反内存安全的行为。

函数或方法的参数的生命周期被称为 输入生命周期（input lifetimes），而返回值的生命周期被称为 输出生命周期（output lifetimes）。

每个引用参数都有其自己的生命周期。

静态生命周期 'static 生命周期能够存活于整个程序期间。




