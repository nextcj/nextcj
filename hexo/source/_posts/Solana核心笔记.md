---
title: Solana核心笔记
date: 2024-10-01 09:14:12
categories: [ 'Solana' ]
---

> Solana 相关温故知新常看站点：
> - [Solana 中文大全 - https://www.solana-cn.com](https://www.solana-cn.com)
> - [Solana 程序库 - Solana Program Library/](https://www.solana-cn.com/SolanaProgramLibrary/home.html)
> - [Solana 中文文档 - Solana Documentation/](https://www.solana-cn.com/SolanaDocumention/home.html)
> - [Solana 验证器文档 - Solana Validator/](https://www.solana-cn.com/SolanaValidatorDocumentation/home.html)
> - [Solana Labs Docs - https://docs.solanalabs.com](https://docs.solanalabs.com)

> Solana 资源网站：
> - [Solana CLI 工具套件下载镜像 - sourceforge.net](https://sourceforge.net/projects/solana.mirror/)

> 验证者是一台帮助运行 Solana 网络的计算机。
> 每个验证者都会执行一个程序来跟踪 Solana 集群上的所有账户，并验证添加到网络的交易。
> 没有验证者，Solana 将无法运行。

> Solana 通过代币账户来保存代币，相比的以太坊智能合约的账本型合约有着本质的不同。
> 非同质化代币在 Solana 中的定义：精度为0的代币都属于非同质化的代币。

> 在 Solana 中，Everything is An Account. 类似于Linux中把所有资源都抽象成“文件”。
> Solana 所有信息都存储在 Account 对象中，如合约 OnChain Program

> Solana 有三类账户：
> 数据账户，用来存储数据。分为 "系统所有账户" 和 "程序派生账户 PDA"
> 程序账户，用来存储可执行程序
> 原生账户，指Solana上的原生程序，例如 System, Stake, Vote 等

> Installed by Homebrew package manager on Mac

```shell

```
