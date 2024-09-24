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

```

Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

Rustup metadata and toolchains will be installed into the Rustup
home directory, located at:

  C:\Users\90986\.rustup

This can be modified with the RUSTUP_HOME environment variable.

The Cargo home directory is located at:

  C:\Users\90986\.cargo

This can be modified with the CARGO_HOME environment variable.

The cargo, rustc, rustup and other commands will be added to
Cargo's bin directory, located at:

  C:\Users\90986\.cargo\bin

This path will then be added to your PATH environment variable by
modifying the HKEY_CURRENT_USER/Environment/PATH registry key.

You can uninstall at any time with rustup self uninstall and
these changes will be reverted.

Current installation options:


   default host triple: x86_64-pc-windows-msvc
     default toolchain: stable (default)
               profile: default
  modify PATH variable: yes

1) Proceed with standard installation (default - just press enter)
2) Customize installation
3) Cancel installation
>
info: profile set to 'default'
info: default host triple is x86_64-pc-windows-msvc
info: syncing channel updates for 'stable-x86_64-pc-windows-msvc'
info: latest update on 2024-09-05, rust version 1.81.0 (eeb90cda1 2024-09-04)
info: downloading component 'cargo'
info: downloading component 'clippy'
info: downloading component 'rust-docs'
info: downloading component 'rust-std'
info: downloading component 'rustc'
 58.9 MiB /  58.9 MiB (100 %)  18.3 MiB/s in  3s ETA:  0s
info: downloading component 'rustfmt'
info: installing component 'cargo'
info: installing component 'clippy'
info: installing component 'rust-docs'
 16.0 MiB /  16.0 MiB (100 %)   2.2 MiB/s in  7s ETA:  0s
info: installing component 'rust-std'
 20.5 MiB /  20.5 MiB (100 %)   6.8 MiB/s in  3s ETA:  0s
info: installing component 'rustc'
 58.9 MiB /  58.9 MiB (100 %)   9.2 MiB/s in  6s ETA:  0s
info: installing component 'rustfmt'
info: default toolchain set to 'stable-x86_64-pc-windows-msvc'

  stable-x86_64-pc-windows-msvc installed - rustc 1.81.0 (eeb90cda1 2024-09-04)


Rust is installed now. Great!

To get started you may need to restart your current shell.
This would reload its PATH environment variable to include
Cargo's bin directory (%USERPROFILE%\.cargo\bin).

Press the Enter key to continue.

```

安装成功：

`PS C:\Users\90986> rustc --version
rustc 1.81.0 (eeb90cda1 2024-09-04)
PS C:\Users\90986> cargo --version
cargo 1.81.0 (2dbb1af80 2024-08-20)
PS C:\Users\90986>`

cargo new hello_rust 生成一个基本的Rust项目结构：
`
.git
src
.gitignore > main.rs
Cargo.toml
`