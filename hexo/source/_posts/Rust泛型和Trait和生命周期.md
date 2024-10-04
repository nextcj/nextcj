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




