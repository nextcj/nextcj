---
title: Shopify店铺装修实践记录
date: 2024-10-25 00:37:12
categories:
tags:
---

How To Remove Collection Title In Shopify

`admin > ... > 编辑代码 > base.css > 添加：`

```css
h1.collection-hero__title {
  display: none;
}

```

remove the buy it now button from my product page

`admin > ... > 编辑代码 > assets > theme.css > 添加：`

```css
.shopify-payment-button {
    display: none !important;
}
```

多列 block 标题居中
theme.liquid

```html
    <style>
      .multicolumn [class^='title'] {
        align-items: center !important;
        justify-content: center !important;
        display: flex !important;
        text-align: center !important;
      }
    </style>
```

隐藏页尾语言菜单
theme.liquid

```html
    <style>
      .footer__column.footer__localization.isolate {
          display: none !important;
      }
    </style>
```