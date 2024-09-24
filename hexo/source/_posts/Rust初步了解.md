---
title: Rust初步了解
date: 2024-09-23 09:10:12
categories: [ 'Rust' ]
---

## 开发环境

Rustup 是 Rust 安装器和版本管理工具。官方网站 https://www.rust-lang.org

windows 安装 rustup 提示

`Rust Visual C++ prerequisites
Rust requires a linker and Windows API libraries but they don't seem to be
available.
These components can be acquired through a Visual Studio installer.`

因为在 Windows 上，Rust 需要某些 C++ 生成工具。
怎么解决：安装 [Visual Studio C++ Build tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)

安装教程微软：[在 Windows 上针对 Rust 设置开发环境](https://learn.microsoft.com/zh-cn/windows/dev-environment/rust/setup)

安装完 VSC++ Build tools 再安装 rustup-init.exe

`Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:C:\Users\90986\.rustup
This can be modified with the RUSTUP_HOME environment variable.`

`The Cargo home directory is located at:C:\Users\90986\.cargo
This can be modified with the CARGO_HOME environment variable.`

`The cargo, rustc, rustup and other commands will be added to
Cargo's bin directory, located at:C:\Users\90986\.cargo\bin
This path will then be added to your PATH environment variable by
modifying the HKEY_CURRENT_USER/Environment/PATH registry key.`

Current installation options:
default host triple: x86_64-pc-windows-msvc
default toolchain: stable (default)
profile: default
modify PATH variable: yes

stable-x86_64-pc-windows-msvc installed - rustc 1.81.0 (eeb90cda1 2024-09-04)

安装成功：

```plaintext
PS C:\Users\90986> rustc --version
rustc 1.81.0 (eeb90cda1 2024-09-04)
PS C:\Users\90986> cargo --version
cargo 1.81.0 (2dbb1af80 2024-08-20)
```

cargo new hello_rust 生成一个基本的Rust项目结构：

```plaintext
.git
src
.gitignore > main.rs
Cargo.toml
```

## Rust 语言特点

1. 可以编译可靠且高效的系统软件
2. 可替代C/C++系统软件语言，且保证了内存安全
3. 没有大型运行时或垃圾回收器
4. 在性能、安全性和实现表达式之间达到了独特的平衡
5. Rust 函数不支持可变数量的参数，而宏可以接受任意数量的参数

#### 宏

1. 可变长度的参数：Rust 的函数不支持可变数量的参数（varargs），而宏可以接受任意数量的参数。
2. 编译时字符串检查：宏在编译时展开，这允许进行格式字符串的分析，包括检查提供的参数数量是否正确以及参数类型是否与格式说明符相匹配。
3. 性能优化：由于宏会在编译时被展开，编译器能够对结果代码进行优化。相比于运行时构建字符串并打印的函数，使用宏能够带来更好的性能。
4. 类型安全性：宏在编译时进行类型检查，而不是在运行时。这保证了类型安全，增加了灵活性，有助于预防一些安全风险，比如格式化字符串攻击。
5. 参数传递引用：宏传递的参数是引用，不会因为实际上没有执行而导致性能损失。
6. Rust 中使用宏实现打印语句是因为宏在编译时能提供灵活性、类型安全与性能的独特结合，这样的特质很难通过普通函数调用来实现。
7. Rust 标准库在许多其他地方也广泛地使用宏。

#### 内存安全：

Rust 所有权系统和借用检查器确保了程序在编译时就能够捕获大多数内存错误。
所有权系统是Rust最独特和最重要的特性之一。它允许Rust在不需要垃圾收集的情况下保证内存安全。理解所有权对于掌握Rust至关重要。

所有权规则：

1. Rust每一个值都有一个被称为其所有者的变量。
2. 值在任一时刻有且仅有一个所有者。
3. 当所有者（变量）离开作用域，这个值将被丢弃。

#### 并发无忧：

Rust 类型系统和线程模型消除了数据竞争，使并发编程变得更加安全。

#### 零成本抽象：

Rust 允许你使用高级抽象，而不牺牲运行时性能。

#### 跨平台：

Rust 可以编译到多种目标平台，包括嵌入式系统。

参考文章：

[Rust | 秒懂 println! 的超实用格式化技巧](https://www.cnblogs.com/RioTian/p/18145045)


