---
title: Rust程序笔记
date: 2024-09-25 09:10:12
categories: [ 'Rust' ]
---

## Cargo >

可以使用 cargo new 创建项目。
可以使用 cargo build 构建项目。
可以使用 cargo run 一步构建并运行项目。
可以使用 cargo check 在不生成二进制文件的情况下构建项目来检查错误。
有别于将构建结果放在与源码相同的目录，Cargo 会将其放到 target/debug 目录。

cargo build --release 在 target/release 而不是 target/debug 下生成可执行文件。

```
// 要在任何已存在的项目上工作时，可以使用如下命令
// 通过 Git 检出代码，移动到该项目目录并构建：
$ git clone example.org/someproject
$ cd someproject
$ cargo build
```

## 了解 Rust 的第一个程序 >

```rust
use rand::Rng;
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```


## 变量和常量 >

let / let mut
我们不能改变变量的类型
mut 与隐藏的区别是，当再次使用 let 时，实际上创建了一个新变量，我们可以改变值的类型，并且复用这个名字。隐藏有作用域。

声明常量使用 const 关键字而不是 let，并且 必须 注明值的类型。
常量可以在任何作用域中声明，包括全局作用域，这在一个值需要被很多部分的代码用到时很有用。
最后一个区别是，常量只能被设置为常量表达式，而不可以是其他任何只能在运行时计算出的值。

`const THREE_HOURS_IN_SECONDS: u32 = 60 * 60 * 3;`

## 数据类型 >

**Rust 是 静态类型（statically typed）语言。** 也就是说在编译时就必须知道所有变量的类型。

在 Rust 中，每一个值都属于某一个 数据类型（data type），这告诉 Rust 它被指定为何种数据，以便明确数据处理方式。
两类数据类型子集：标量（scalar）和复合（compound）。

#### 标量类型 >

