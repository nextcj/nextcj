---
title: 技术选型调研 - FinClip / UniSDK
date: 2024-07-06 17:28:53
categories: [ '技术选型' ]
tags: [ '多端','FinClip','UniSDK' ]
---

开发微信小程序 → 将微信小程序迁移到自有 App 中 → 某些应用小程序暂时不上架微信，但也需要具备统一的语法与框架，学习与迁移成本不应太高。

微信、百度、阿里这些大厂的小程序容器技术要么不公开，要么太重会接管底层，都不是很合适，市面上能实现 App 跑小程序的也就 FinClip 和 uniapp 比较成熟。

## <font color=#A3CAEB># FinClip</font>

### <font color=#A3CAEB>## FinClip 核心</font>

FinClip 的核心是提供一个小程序容器技术，让 App 拥有运行小程序的能力，从而实现跨平台：

1、使用 FinClip，可以在自己的 App 中打造与微信小程序类似的生态，FinClip 提供了小程序容器技术，就够将小程序运行环境集成到 App，从而让 App 具备小程序运行的能力。

2、使用 FinClip，可以进行模块化开发，真正实现敏捷迭代，把 App 中的业务模块都拆成单独的小程序，各个业务模块之间互相不影响，均可独立更新与发布。

3、极大的优化了工作效率和产品迭代的效率，多系统、多框架的支持为公司大大节约了跨平台开发的成本。

### <font color=#A3CAEB>## FinClip 技术平台</font>

FinClip 提供多系统框架、多系统支持与开发管理的能力：

1、FinClip 小程序 SDK 支持纯 WXML 微信小程序运行，也支持包括 uniapp、Taro、kbone 第三方框架集成的小程序。

2、FinClip 小程序 SDK 同时提供 HarmonyOS、Android、iOS、Flutter、ReactNative、Windows 等多种环境。

3、拥有完善的管理平台，小程序开发、测试、上下架、App 集成与联调等流程。

FinClip SDK 是一个能运行小程序的安全沙箱，通过嵌入 SDK 的形态让移动端软件、PC 端软件与物联网设备软件的宿主环境集成小程序容器。
FinClip 管理后台可以理解成一个应用商店，提供应用的发现（陈列、搜索与推荐）机制、上下架与灰度发布的管理后台。
使用 FinClip IDE 完成代码编写，使用 FinClip App 完成小程序预览。
即使开发者不在应用商店中对 App 进行发版更新，仍然可以更新小程序资源，只要用户安装并打开了 App，就可以根据规则库的配置实现小程序 “千人千面” 的功能。

总之，FinClip 将 “小程序运行时” 实现成一个可私有化部署的 HarmonyOS、iOS 和 Android 的 SDK，可以被第三方集成。任何 APP 嵌入 FinClip SDK 即可获得运行小程序的能力。
FinClip SDK 采用多进程机制实现，每个小程序运行在独立的进程中，即一个小程序对应一个进程。

https://www.zhihu.com/search?type=content&q=Finclip%20%E4%B8%8E%20uniapp%20%E7%9A%84%E5%8C%BA%E5%88%AB

https://www.finclip.com/landpage-common/

https://www.finclip.com/landpage-car/

https://www.finclip.com/solutions/car/

https://www.163.com/dy/article/J393B6UN0511B8LM.html

https://www.baidu.com/s?ie=utf-8&f=8&rsv_bp=1&rsv_idx=1&tn=baidu&wd=FinClip%20%E5%BC%80%E5%8F%91%E7%9A%84%E5%85%AC%E5%8F%B8%E6%9C%89%E5%93%AA%E4%BA%9B&fenlei=256&oq=Fin%2526lt%253Blip&rsv_pq=ae9adb190005e6ee&rsv_t=f9f0RqKlS0VbcWzMgYHsd%2Fpfo6X1gJiuGrXBaW%2F%2F1qB8866d5wLi3q7FUr0&rqlang=cn&rsv_enter=1&rsv_dl=tb&rsv_btype=t&inputT=19451&rsv_sug3=43&rsv_sug1=36&rsv_sug7=100&rsv_sug2=0&rsv_sug4=20729

## <font color=#A3CAEB># UniSDK</font>

UniSDK 也是小程序 SDK，是为原生 App 打造的可运行基于 uni-app 开发的小程序前端项目的框架，从而帮助原生 App 快速获取小程序的能力。
uni 小程序 SDK 是原生 SDK，提供 Android 版本和 iOS 版本，需要在原生工程中集成，然后即可运行 uni-app 框架开发的小程序前端项目。

UniSDK 和 FinClip 类似，提供小程序 SDK 供 App 集成，宿主 App 集成其 SDK 之后就拥有了运用 uni-app 开发的小程序的能力，但是 uni 小程序 SDK 这里没有提供管理端，只提供了 SDK。




