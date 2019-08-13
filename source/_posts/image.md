---
title: Insert Image in Hexo Blog
date: 2019-08-13 21:32:44
tags: [markdown, hexo, image]
categories: [article, hexo]
---

## Modify Config

Modify `post_asset_folder` in `_config.yml` to `true`.  

## Install packages

execute `npm install https://github.com/CodeFalling/hexo-asset-image --save` and wait.  

**WARNING**: Some may tell you to install via `npm install hexo-asset-image --save`, don't do that, that package has bug.

## Put in Images

After those steps, when you create a new post, hexo will auto generate a folder under the same folder with the same name of your post.

Put your images into the correct folder

## Use It

{% tabs tabs %}
<!-- tab First Way -->
`{% raw %}{%{% endraw %} asset_img example.jpg examplename {% raw %}%}{% endraw %}`
<!-- endtab -->
<!-- tab Second Way-->
`![description][1]`
`[1]:picture_path "picture_name" ]`
<!-- endtab -->
<!-- tab Third Way-->
`![description][picture_name]`
<!-- endtab -->
{% endtabs %}
