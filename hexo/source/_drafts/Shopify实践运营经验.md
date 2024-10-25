---
title: Shopify实践运营经验
date: 2024-10-23 17:49:07
categories: [ 'Shopify' ]
tags: [ 'Liquid','Shopify运营' ]
---

> ->
> [问题：Shopify变体链接如何关联在一起，点击一个颜色或样式时如何跳转到另外一个链接的内容。比如服装，手机壳]()
> ->
> 回答：关联多款 Shopify 产品实现组合 Listing，无需 Shopify Plus 即可突破变体数量 100 的限制。
> 只需要设置产品Tags 即可将商品关联起来，当前商品始终会显示在第一位，不需要手动对每一款产品进行排序设置。
> 也不依赖于元字段，不需要在店铺后台分别为不同的变体选项上传特定命名格式的 Swatch 图片(因为自动获取产品图进行显示)。
> ->
> 操作：
> 1、将展示产品的网址链接里的 handle 复制下来，handle 就是 products/后面的部分，比如 red-pants, white-pants, black-pants。
> 2、回到后台产品目录：搜索要关联的产品各个颜色 pants，分别打开他们的编辑界面，设置标签 Tags。
> 3、设置 Tags >
> 在需要关联的各个商品上添加相同的 Tags ：编辑界面右下角的标签输入框，粘贴所有关联的 handle，也就是每款产品设置相同的 Tags，而不是设置单独的某个 Tag。Tag 跟产品的 handle 保持一致。
> 比如输入用英文逗号隔开比如 `red-pants,white-pants,black-pants`，添加。
> 4、修改Shopify 2.0代码：
> `编辑代码` > `目录 Snippets` > `文件 product-variant-picker.liquid` > `搜索代码片段：elsif picker_type == 'button'`
> 在搜索到的代码片段下方添加代码：
```html
{% liquid
    assign is_color = false
    assign color_option_index = 0
    assign swatch_trigger = "color"
    assign color_option_index = forloop.index0
    assign downcased_option = option.name | downcase
    if downcased_option contains swatch_trigger
        assign is_color = true
    elsif downcased_option contains "colour"
        assign is_color = true
    endif
%}
{% if is_color %}
    {% render 'binding-products', product: product, option: option, block: block, is_color: is_color, color_option_index: color_option_index %}
{% else %}
```
在`</fieldset>`下方添加：` {% endif %}`

`目录 Snippet` > 创建新文件 `binding-products.liquid`




























