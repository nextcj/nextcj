---
title: Solana核心笔记
date: 2024-10-01 09:14:12
categories: [ 'Solana' ]
---

> Solana 通过代币账户来保存代币，相比的以太坊智能合约的账本型合约有着本质的不同。
> 非同质化代币在 Solana 中的定义：精度为0的代币都属于非同质化的代币。

> 在 Solana 中，Everything is An Account. 类似于Linux中把所有资源都抽象成“文件”。
> Solana 所有信息都存储在 Account 对象中，如合约 OnChain Program

> Solana 有三类账户：
> 数据账户，用来存储数据。分为 "系统所有账户" 和 "程序派生账户 PDA"
> 程序账户，用来存储可执行程序
> 原生账户，指Solana上的原生程序，例如 System, Stake, Vote 等

