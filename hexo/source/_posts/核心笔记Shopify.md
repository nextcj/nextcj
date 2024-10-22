---
title: Shopify核心笔记
date: 2024-10-22 09:14:12
categories: [ 'Shopify' ]
---

| Shopify主题架构 |

- Shopify Online Store 2.0 主题，每个模板可以包含多达20个部分，每个部分都具有特定的功能，如标题、文本、单个图像、图像拼贴或链接。除礼品卡和结账页面外，可使用部分自定义或向在线商店添加页面。通过 sections 和 blocks ，可以在不需要编辑代码的情况下灵活排列和设计商店内容。如果会编程，可以自己编辑主题代码修改设置或选项。

| Shopify主题架构版本 |

- Shopify管理后台>在线商店>主题>自定义>顶部的下拉菜单>选择产品>默认产品>如果是 Online Store 2.0 主题，在部分列表下方就会有一个添加分区的按钮。
- Shopify管理后台进入在线商店>主题>操作>编辑代码>如果是分段主题：可以看到代码目录存在 sections 文件夹且内部有具体代码文件。否则是非分段主题。

## Shopify 主题开发 >

- 利用Liquid模板语言和前端技术如HTML、CSS、JavaScript以及JSON，您可以创建出既美观又响应迅速的定制主题。随着技术的不断进步，使用Shopify Theme Kit等工具可以大大简化开发流程。
- Shopify 官方提供了 Shopify CLI 以及 Theme Kit 两种方式，Theme Kit 是比较旧的开发工具而 Shopify CLI 则是新版的开发工具。
- 如果开发的是 Online Store 2.0 的主題，一定得使用 Shopify CLI。

｜Shopify 主题设计的核心要素原则｜

- 理解Shopify主题的结构和组件。包括模板（用于定义页面的结构）、样式表（用于控制主题的外观）、脚本文件（用于增加动态功能）等。
- 应用响应式Web设计。在不同设备上提供一致的用户体验。在主题开发中采用流体网格、灵活的图片和媒体查询等技术，可以使布局和内容自动适应屏幕大小。
- UX设计和店铺视觉。用户体验（UX）设计，直观、易于导航和美观的界面能够显著提高用户满意度和转化率。简洁性（避免过度设计），一致性（样式，配色），可用性（购物便捷）。
- html 构建页面结构。css 组织样式代码，css 预处理器 Sass Less，样式代码的复用性可维护性。javascript 页面的交互，动态窗口。json 配置主题和传递数据。
- 使用媒体查询实现响应式布局，设备尺寸适配。或者用响应式设计框架，如Bootstrap或Foundation，可以快速实现响应式布局。压缩 css 文件， css sprite 技术减少 http 的请求次数、关键 css 内联在 html 中加快首评加载速度。
- javascript AJAX 实现无刷新页面更新，如实时搜索结果显示、无刷新添加商品到购物车等，提高用户体验。
- shopify ajax api 与 json 配合，从服务器获取数据并动态更新页面内容，无需重新加载页面。

| Shopify页面速度优化的技巧 |

1. 减少HTTP请求：通过合并CSS和JavaScript文件，减少服务器的HTTP请求次数。每个额外的请求都会增加页面的加载时间。
2. 使用CDN：利用内容分发网络（CDN）存储你的静态资源，如图片和样式表。CDN通过将内容存储在全球多个位置，来确保访问者从最近的服务器获取数据，从而加快加载速度。
3. 浏览器缓存优化：通过设置合理的缓存策略，使得返回访问者可以加载已缓存的资源，减少数据的重复下载。
   Shopify主题商店的发布与管理
   当你完成Shopify主题开发后，下一步就是将其发布到Shopify主题商店，这不仅能让你的作品被全球的Shopify用户看到，还能为你带来潜在的收入。以下是主题提交、审查流程、维护更新以及如何收集用户反馈和进行持续改进的详细步骤。

| 主题提交和审查流程概述 |

1. 准备提交：确保你的主题符合Shopify的质量标准和要求。这包括设计的创新性、代码的清晰性、响应式设计的实现、以及对多语言支持的考虑。
2. 提交主题：登录到你的Shopify合作伙伴账户，导航到“主题”部分，并点击“提交主题”。上传你的主题文件，并填写所有必要的信息，包括主题描述、特色和预览图像。
3. 等待审查：提交后，你的主题将进入审查队列。Shopify的主题审查团队将根据一系列标准评估你的主题，这个过程可能需要几周时间。
4. 处理反馈：如果主题被退回，不要气馁。审查团队会提供具体的反馈，指出需要改进的地方。根据反馈调整你的主题，然后重新提交。

| 遵循最佳安全实践保护用户数据 |

1. 使用HTTPS：确保你的Shopify商店启用了SSL证书，这样可以通过加密连接保护所有传输到服务器和从服务器传回的数据。
2. 访问控制：严格限制对后台管理界面的访问。只有必要的工作人员才能获得访问权限，并且要定期更改密码。
3. 数据处理：在处理用户数据（如地址、支付信息）时，遵循最佳实践，确保数据在传输和存储过程中都得到妥善保护。

| 防止XSS和CSRF攻击的策略 |

1. XSS（跨站脚本攻击）：确保所有用户输入都经过适当的清理和转义，避免恶意脚本注入。使用Shopify Liquid的`html_escape`过滤器自动对输出进行编码。
2. CSRF（跨站请求伪造）：确保你的表单使用了Shopify提供的authenticity token，这样可以验证请求是从你的网站发起的，而不是第三方网站。

## Shopify Theme 文件夹结构

```html
└── theme
    ├── assets目录 - 包含主题中使用的所有资源文件，包括图像、CSS和JavaScript文件。
    ├── config目录 - 包含主题的配置文件。 配置文件在主题编辑器的主题设置区域中定义设置，并存储它们的值。
    ├── layout目录 - 包含主题的布局文件，模板文件通过这些文件呈现。
    ├── locales目录 - 包含主题的locale文件，这些文件用于提供翻译后的内容。 Locale文件允许您在主题编辑器中提供翻译体验，为在线商店提供翻译，并允许商家在在线商店中定制文本。
    ├── sections目录 - 包含一个主题的sections。放置自定义的 Liquid 区块文件，区块可以复用在页面上。
    ├── snippets目录 - 包含较小的可重用代码片段的Liquid文件。 您可以使用Liquid render标记在整个主题中引用这些片段。
    └── templates目录 - 每一个json文件是一个模板，每一个模板对应着一个页面。
        └── customers目录
```

## Shopify 开发工具 >

* Shopify CLI: 即命令行界面工具，允许您直接从本地环境创建、测试和部署主题。
* Liquid: Shopify的模板语言，用于将数据注入网页。
* Dawn: Shopify的参考主题，可以作为自定义创建的起点。
* Theme Kit: 一种旧的用于主题开发的工具，在某些情况下仍然有用，尽管Shopify鼓励新项目使用CLI。
* GitHub集成: 可以在主题项目上实现版本控制和协作。

## Shopify CLI 安装 >

```shell
hf@BENZCAR ~ % npm install -g @shopify/cli@latest

added 5 packages in 11s
hf@BENZCAR ~ % shopify help
A CLI tool to build for the Shopify platform

VERSION
  @shopify/cli/3.69.0 darwin-x64 node-v22.3.0

USAGE
  $ shopify [COMMAND]

TOPICS
  app       Build Shopify apps.
  auth      Auth operations.
  config    CLI configuration options.
  hydrogen  Build Hydrogen storefronts.
  theme     Build Liquid themes.

COMMANDS
  commands  list all the commands
  help      Display help for Shopify CLI
  search    Starts a search on shopify.dev.
  upgrade   Shows details on how to upgrade Shopify CLI.
  version   Shopify CLI version currently installed.

hf@BENZCAR ~ % shopify version
3.69.0
hf@BENZCAR ~ % 
```

|| 参考文章 ||

https://www.zzbaimaozi.com/%E7%B2%BE%E9%80%9Ashopify%E4%B8%BB%E9%A2%98%E5%BC%80%E5%8F%91/
https://inbound.technology/shopify-theme-develop/
https://www.hulkapps.com/zh-hans/blogs/shopify-20/zhang-wo-shopifyzhu-ti-kai-fa-zhu-bu-zhi-nan-da-zao-zi-ji-de-shang-dian