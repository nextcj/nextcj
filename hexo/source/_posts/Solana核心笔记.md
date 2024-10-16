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

> Solana 工具资源：
> - [Solana CLI 工具套件下载镜像 - sourceforge.net](https://sourceforge.net/projects/solana.mirror/)

> Solana 核心概念
> - 交易：区块链执行指令的集合。
> - 账户：Solana 中数据和状态存储的机制。
> - 程序：区块链上执行操作的代码。
> - 跨程序调用：Solana 上可组合性的核心，程序如何调用彼此。

> 权益证明区块链工作原理的底层架构
> - 验证者：作为网络骨干的单个节点。
> - 集群：达成共识的验证者集合。

> Solana 通过代币账户来保存代币，相比的以太坊智能合约的账本型合约有着本质的不同。
> 非同质化代币在 Solana 中的定义：精度为0的代币都属于非同质化的代币。

> 在 Solana 中，Everything is An Account. 类似于Linux中把所有资源都抽象成“文件”。
> Solana 所有信息都存储在 Account 对象中，如合约 OnChain Program

> Solana 有三类账户：
> 数据账户，用来存储数据。分为 "系统所有账户" 和 "程序派生账户 PDA"
> 程序账户，用来存储可执行程序
> 原生账户，指Solana上的原生程序，例如 System, Stake, Vote 等

> 验证者是一台帮助运行 Solana 网络的计算机。
> 每个验证者都会执行一个程序来跟踪 Solana 集群上的所有账户，并验证添加到网络的交易。
> 没有验证者，Solana 将无法运行。

> 参考网址：
> https://solana.stackexchange.com/questions/16241/avm-install-latest-fails
> https://www.anchor-lang.com/docs/installation#anchor
> https://github.com/coral-xyz/anchor/releases

> Validator 创建验证者密钥 

```shell
Last login: Wed Oct 16 01:44:37 on ttys001
hf@BENZCAR ~ % solana --version
solana-cli 1.18.25 (src:30cf4f7a; feat:3241752014, client:SolanaLabs)
hf@BENZCAR ~ % solana config get                                     
Config File: /Users/hf/.config/solana/cli/config.yml
RPC URL: https://api.mainnet-beta.solana.com 
WebSocket URL: wss://api.mainnet-beta.solana.com/ (computed)
Keypair Path: /Users/hf/.config/solana/id.json 
Commitment: confirmed 
hf@BENZCAR ~ % solana config set --url https://api.testnet.solana.com    
Config File: /Users/hf/.config/solana/cli/config.yml
RPC URL: https://api.testnet.solana.com 
WebSocket URL: wss://api.testnet.solana.com/ (computed)
Keypair Path: /Users/hf/.config/solana/id.json 
Commitment: confirmed 
hf@BENZCAR ~ % solana-keygen new -o validator-keypair.json
Generating a new keypair

For added security, enter a BIP39 passphrase

NOTE! This passphrase improves security of the recovery seed phrase NOT the
keypair file itself, which is stored as insecure plain text

BIP39 Passphrase (empty for none): 
Enter same passphrase again: 

Wrote new keypair to validator-keypair.json
==========================================================================
pubkey: BdnK***************************************X
==========================================================================
Save this seed phrase and your BIP39 passphrase to recover your new keypair:
ill reduce mandate cattle lunch stage south young curve trend prize choice
==========================================================================
hf@BENZCAR ~ % solana-keygen new -o vote-account-keypair.json
Generating a new keypair

For added security, enter a BIP39 passphrase

NOTE! This passphrase improves security of the recovery seed phrase NOT the
keypair file itself, which is stored as insecure plain text

BIP39 Passphrase (empty for none): 
Enter same passphrase again: 

Wrote new keypair to vote-account-keypair.json
===================================================================================
pubkey: 2zWw***************************************3
===================================================================================
Save this seed phrase and your BIP39 passphrase to recover your new keypair:
recipe orange rabbit brisk mutual simple crop festival surprise process night media
===================================================================================
hf@BENZCAR ~ % solana-keygen new -o authorized-withdrawer-keypair.json
Generating a new keypair

For added security, enter a BIP39 passphrase

NOTE! This passphrase improves security of the recovery seed phrase NOT the
keypair file itself, which is stored as insecure plain text

BIP39 Passphrase (empty for none): 
Enter same passphrase again: 

Wrote new keypair to authorized-withdrawer-keypair.json
====================================================================================
pubkey: 36ys***************************************m
====================================================================================
Save this seed phrase and your BIP39 passphrase to recover your new keypair:
canyon initial hybrid oxygen pistol hundred differ doll tilt defense evidence almost
====================================================================================
hf@BENZCAR ~ % 

```

> 创建 Vote 账户

```shell
Last login: Wed Oct 16 10:25:26 on ttys001
hf@BENZCAR ~ % solana --version
solana-cli 1.18.25 (src:30cf4f7a; feat:3241752014, client:SolanaLabs)
hf@BENZCAR ~ % solana config set --keypair ./validator-keypair.json
Config File: /Users/hf/.config/solana/cli/config.yml
RPC URL: https://api.testnet.solana.com 
WebSocket URL: wss://api.testnet.solana.com/ (computed)
Keypair Path: ./validator-keypair.json 
Commitment: confirmed 
hf@BENZCAR ~ % 
hf@BENZCAR ~ % solana balance
Error: RPC request error: cluster version query failed: error sending request for url (https://api.testnet.solana.com/): operation timed out
```

> 报错 RPC request error: ....
> 什么是 RPC 
> Remote Procedure Call Protocol，远程过程调用协议。
> RPC 是一种思想。客户端在不知道调用细节的情况下，调用存在于远程计算机上的某个对象，就像调用本地应用程序中的对象一样。
> 通过网络从远程计算机程序上请求服务，不需要了解底层网络的协议。传输层用的是 TCP UDP HTTP 不需要关心。
> RPC 可以用任何协议来实现：HTTP ProtocolBuf JSON 等。














