---
title: Solana核心笔记
date: 2024-10-01 09:14:12
categories: [ 'Solana' ]
---

> Solana 相关温故知新常看站点 >
> - [Solana 中文大全 - https://www.solana-cn.com](https://www.solana-cn.com)
> - [Solana 程序库 - Solana Program Library/](https://www.solana-cn.com/SolanaProgramLibrary/home.html)
> - [Solana 中文文档 - Solana Documentation/](https://www.solana-cn.com/SolanaDocumention/home.html)
> - [Solana 验证器文档 - Solana Validator/](https://www.solana-cn.com/SolanaValidatorDocumentation/home.html)
> - [Solana Labs Docs - https://docs.solanalabs.com](https://docs.solanalabs.com)

> Solana 工具资源 >
> - [Solana CLI 工具套件下载镜像 - sourceforge.net](https://sourceforge.net/projects/solana.mirror/)

> Solana 核心概念 >
> - 交易：区块链执行指令的集合。
> - 账户：Solana 中数据和状态存储的机制。
> - 程序：区块链上执行操作的代码。
> - 跨程序调用：Solana 上可组合性的核心，程序如何调用彼此。

> Solana 常见术语 >
> - 账户：一条 Solana 账本记录，可以持有数据或作为一个可执行程序。可以持有资金 Lamport，就像是 Linux 中的文件，可以通过一个键来寻址（公钥/PubKey）。
> - 键：1、一个 ed25519 公钥；2、一个程序派生账户地址（32字节值，从 ed25519 曲线中推导出来）；3、一个 ed25519 公钥的哈希，附加 32 字符的字符串。
> - 账户拥有者：拥有账户的程序的地址，只有拥有者的程序才能修改账户。
> - 应用程序：与 Solana 集群交互的前端应用程序。
> - 银行状态：给定 `tick 高度` 下解释账本上所有程序的结果。至少包括持有非 0 原生代币的所有账户集合。
> - 区块：由一个 `投票` 覆盖的账本中的连续 `条目` 集。一个 `领导者` 一个 `插槽` 最多生产一个区块。
> - 区块哈希：标识记录（区块）的唯一值（ `哈希` ）。Solana 从区块的最后一个 `条目 ID` 计算一个区块哈希。
> - 区块高度：当前区块下方的 `区块` 数量，紧随 `创世区块` 之后的区块高度之一。
> - 哈希：字节序列的数字指纹。
> - 条目：账本中的一个条目，可以是一个 tick 条目或一个交易条目。
> - tick 条目：估算时钟持续时间的账本条目。
> - tick 高度：账本中的第 N 个 tick 条目。
> - 交易条目：可以并行执行的一组交易。
> - 条目 ID：一个对条目最终内容的抗御，像攻击哈希，作为条目的全局唯一标识符。哈希作为以下内容的证据：条目是在一段时间后生成的。包含的交易是条目中的那些交易。条目相对于账本中其他条目的位置。
> - 历史证明：PoH，一个证明堆栈，每个证明都证明在创建前存在一些数据，并且在上一个证明之前经过了精确的时间。
> - 引导验证者：生成区块链创世（第一个）区块的验证者。
> - 创世区块：链中的第一个区块。
> - 创世配置：为创世区块准备账本的配置文件。
> - BPF加载器：Solana 程序负责拥有和加载 BPF 链上程序，使程序能够与运行时接口。
> - 客户端：访问 Solana 服务器网络集群的计算机程序。
> - 承诺：对区块的网络确认的度量。
> - 集群：维护单一账本的一组验证者。
> - 节点：参与集群的计算机。
> - 节点数量：参与集群的验证者数量。
> - 计算预算：每笔交易消耗的最大计算单位数。
> - 计算单位：区块链计算资源消耗的最小测量单位。
> - 确认时间：从领导者创建一个 tick 条目到创建一个确认区块的时钟持续时间。
> - 确认区块：已收到账本投票超级多数票的区块。
> - 超级多数：集群的2/3。
> - 账本投票：在给定tick高度上验证者状态的哈希。它包含验证者对已收到的区块的验证确认，以及在特定时间段锁定期分叉的承诺。
> - 控制平面：连接集群所有节点的 gossip 网络。
> - 数据平面：用于高效验证条目并达成共识的多播网络。
> - gossip 网络：P2P 网络核心技术，Gossip 协议
> - 冷却期：在质押被停用后的若干周期，期间逐渐变得可以提取。在此期间，质押被认为是正在停用。
> - 锁定期：验证者无法对另一个分叉进行投票的时间段。
> - 质押：如果能够证明验证者的恶意行为，则这些代币将被没收给集群。
> - 周期：有效的领导者计划的时间，即插槽数。（纪元）
> - 投票信用：对验证者的奖励统计。当验证者达到一个根时，投票信用会被奖励到其投票账户。
> - 跨程序调用 CPI：从一个链上程序调用另一个。（ = 内部指令 = 程序间调用 ）
> - 指令：处理程序的调用。指定要读取或修改的账户，以及作为辅助输入提供的附加数据。客户端必须在交易中包含至少一个指令，所有指令必须完成，交易才能被视为成功。
> - 指令处理程序：处理交易中指令的程序函数。（指令处理程序可以包含一个或多个跨程序调用）。
> - 无人机：作为用户私钥托管人的链外服务。通常用于验证和签署交易。
> - 纪元：有效的领导者计划的时间，即插槽数。
> - 领导者计划：将验证者的公钥映射到插槽的序列。集群使用领导者计划来确定任何时刻的领导者。
> - 插槽：每个领导者吸收交易并生成区块的时间段。插槽集合创建一个逻辑时钟，插槽按顺序排列，且不重叠，大致相当于实际世界的时间。
> - 费用账户：将交易包括在账本中的费用。这是交易中的第一个账户。由于支付交易费用会减少账户余额，因此该账户必须在交易中声明为可读写。
> - 最终性：当代表 2/3 质押的节点有一个共同的根。
> - 分支：从共同条目派生但是随后分叉的账本。
> - 账本：包含由客户端签名的交易的条目列表。
> - 通货膨胀：随着时间的推移，代币供应量的增加用于资助验证奖励和 Solana 的持续开发。
> - 密钥对：访问账户所需的公钥和对应的私钥。
> - 程序 ID：包含程序的账户的公钥。
> - Lamport：价值 0.000000001 SOL 的原生代币的分量单位。（在计算预算中，微 Lamports 用于计算优先费用）
> - 优先费用：用户可以在计算预算指令中指定的额外费用，以优先处理他们的交易。优先费用通过将请求的最大计算单位数乘以计算单位价格（以每计算单位0.000001 lamports为增量指定）并四舍五入到最接近的lamport来计算。
> - 交易应请求执行所需的最小计算单位数以最小化费用。
> - 领导者：当验证者将条目附加到账本时候的角色。
> - 验证者：在 solana 网络集群中生成新区块的完整参与者。验证者验证添加到账本中的交易。
> - 轻客户端：一种可以验证其指向有效集群的客户端。它执行的账本验证比薄客户端多，比验证者少。
> - 薄客户端：一种客户端，它相信自己正在与一个有效的集群进行通信。
> - 加载器：能够解释其他链上程序二进制编码的程序。
> - 原生代币：用于追踪集群中节点完成工作的代币。 sol 是 Solana 集群的原生代币。
> - Solana 程序库 SPL：如 spl-token，便于创建和使用代币等任务。
> - 链上程序 OnChain Program：Solana 区块链上可执行的代码，解释每个交易中发送的指令，读取并修改其控制的账户。这些程序在其他区块链上通常被称为 “智能合约”。
> - 点数：奖励机制中的加权信用。
> - 程序派生地址：签名权限为程序的账户，因此不像其他账户那样受私钥控制。
> - 租金：由账户和程序支付的在区块链上存储数据的费用，当账户余额不足以支付租金的时候，账户可能会被垃圾回收。
> - 运行时：负责执行程序的验证者组件。
> - 分片：一个区块的一部分，在验证者之间传递的最小单位。
> - 质押：如果能够证明验证者的恶意行为，则这些代币将被没收给集群。
> - 系统变量：系统账户。系统变量提供集群状态信息，如当前 tick 高度、奖励点数值。程序可以通过系统变量账户（公钥）或通过系统调用访问系统变量。
> - 代币：一种数字可转移的资产。
> - 代币程序：提供代币转账、冻结和铸造的基本功能。
> - TPS：每秒交易数量。
> - 交易：由一个或多个客户端使用一个或多个密钥对签名的一个或多个指令，原子性地执行，只有两种可能结果：成功或失败。
> - 钱包：管理资金的一组密钥对。
> - 预热期：在质押被委派后若干周期，期间质押逐渐生效。在此期间，质押被认为是“正在激活”。

> 权益证明区块链工作原理的底层架构 >
> - 验证者：作为网络骨干的单个节点。
> - 集群：达成共识的验证者集合。

> Solana 通过代币账户来保存代币，相比的以太坊智能合约的账本型合约有着本质的不同。
> 非同质化代币在 Solana 中的定义：精度为0的代币都属于非同质化的代币。

> 在 Solana 中，Everything is An Account. 类似于Linux中把所有资源都抽象成“文件”。
> Solana 所有信息都存储在 Account 对象中，如合约 OnChain Program

> Solana 有三类账户 >
> 数据账户，用来存储数据。分为 "系统所有账户" 和 "程序派生账户 PDA"
> 程序账户，用来存储可执行程序
> 原生账户，指Solana上的原生程序，例如 System, Stake, Vote 等

> 验证者是一台帮助运行 Solana 网络的计算机。
> 每个验证者都会执行一个程序来跟踪 Solana 集群上的所有账户，并验证添加到网络的交易。
> 没有验证者，Solana 将无法运行。

> 客户端 DApp 和链上程序的粘合剂是 Solana JSON RPC API 。
> 客户端向 Solana 网络发送 RPC 请求，与链上程序进行交互。与前端和后端之间的正常开发非常相似。 与在 Solana 上工作的主要区别在于后端是一个全局无需许可的区块链。

> 参考网址 >
> https://solana.stackexchange.com/questions/16241/avm-install-latest-fails
> https://www.anchor-lang.com/docs/installation#anchor
> https://github.com/coral-xyz/anchor/releases

> Validator 创建验证者密钥 >

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

> 创建 Vote 账户 >

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

> 报错 RPC request error: .... >
> 什么是 RPC 
> Remote Procedure Call Protocol，远程过程调用协议。
> RPC 是一种思想。客户端在不知道调用细节的情况下，调用存在于远程计算机上的某个对象，就像调用本地应用程序中的对象一样。
> 通过网络从远程计算机程序上请求服务，不需要了解底层网络的协议。传输层用的是 TCP UDP HTTP 不需要关心。
> RPC 可以用任何协议来实现：HTTP ProtocolBuf JSON 等。














