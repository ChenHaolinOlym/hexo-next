---
title: Hexo Tips
date: 2019-08-13 21:35:56
tags: [hexo, tips, note]
categories: [note, hexo]
---
This post is aiming at storing some tips of useing hexo.  

## Tabs

### Code

```en
{% tabs tabs_name %}
<!-- tab first tab@heart -->
first
<!-- endtab -->
<!-- tab second tab-->
second
<!-- endtab -->
{% endtabs %}
```

**NOTICE:** tabs must have unique name

### The effect of the code above

{% tabs tabs_name%}
<!-- tab first tab@heart -->
first
<!-- endtab -->
<!-- tab  second tab-->
second
<!-- endtab -->
{% endtabs %}

## Table

### Code

```en
name | 111 | 222 | 333 | 444
:-: | :-: | :-: | :-: | :-:
aaa | bbb | ccc | ddd | eee|
fff | ggg| hhh | iii | 000|
```

### The effect of the code above

name | 111 | 222 | 333 | 444
:-: | :-: | :-: | :-: | :-:
aaa | bbb | ccc | ddd | eee|
fff | ggg| hhh | iii | 000|

## Centered Quote

### Code

```en
{% centerquote %}This is Centered Quote{% endcenterquote %}
```

Or

```en
{% cq %}This is Centered Quote{% endcq %}
```

### The effect of the code above

{% centerquote %}This is Centered Quote{% endcenterquote %}

## Full Image

This tag enables you to exceed the container's width.

### Code

```en
{% fullimage /hexo/hexo.svg, alt, title %}
```

Or

```en
{% fi /hexo/hexo.svg, alt, title %}
```

### The effect of the code above
{% fullimage /hexo/hexo.svg, alt, title %}

## Bootstrap Callout

### Code

```en
{% note class_name %} Content (md partial supported) {% endnote %}
```

class_name is one of the following:

default | primary | success | info | warning | danger  

### The effect of the code above

{% note default %} Bootstrap Callout default {% endnote %}
{% note primary %} Bootstrap Callout primary {% endnote %}
{% note success %} Bootstrap Callout success {% endnote %}
{% note info %} Bootstrap Callout info {% endnote %}
{% note warning %} Bootstrap Callout warning {% endnote %}
{% note danger %} Bootstrap Callout danger {% endnote %}

## Include Raw

### Code

```en
{% include_raw '/404/404.md' %}
```

This tag include any raw content into your posts. Path is relative to your site "source" directory.

### The effect of the code above

{% include_raw '/404/404.md' %}

## Button

### Usage

```en
{% button url, text, icon [class], [title] %}
<!-- Tag Alias -->
{% btn url, text, icon [class], [title] %}

url     : Absolute or relative path to URL.
text    : Button text. Required if no icon specified.
icon    : FontAwesome icon name (without 'fa-' at the begining). Required if no text specified.
[class] : FontAwesome class(es): fa-fw | fa-lg | fa-2x | fa-3x | fa-4x | fa-5x
          Optional parameter.
[title] : Tooltip at mouseover.
          Optional parameter.
```

### Code

```en
{% btn # ,This Page, home fa-2x, Just This Page%}
```

**NOTE:**It's better to put them into the "&lt;div&gt;" tag, this may avoid some bug  

### The effect of the code above

{% btn # ,This Page, home fa-2x, Just This Page%}

## Group Picture

### Usage

```en
{% grouppicture [group]-[layout] %}{% endgrouppicture %}
{% gp [group]-[layout] %}{% endgp %}

[group]  : Total number of pictures to add in the group.
[layout] : Default picture under the group to show.
```

### Code

```
{% gp 6-3%}
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
{% endgp %}
```

### The effect of the code above
{% gp 6-3%}
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
![](hexo/github.png)
{% endgp %}

## Label

### Usage

```
{% label [class]@Text %}

[class] : default | primary | success | info | warning | danger.
          '@Text' can be specified with or without space
          E.g. 'success @text' similar to 'success@text'.
          If not specified, default class will be selected.
```

### Code

```en
{% raw %}{% label default@default %}{% endraw %} {% raw %}{% label primary@primary %}{% endraw %} {% raw %}{% label success@success %}{% endraw %} {% raw %}{% label info@info %}{% endraw %} {% raw %}{% label warning@warning %}{% endraw %} {% raw %}{% label danger@danger %} {% raw %}{% label success@success%}{% endraw %}
```

### The effect of the code above

{% label default@default %} {% label primary@primary %} {% label success@success %} {% label info@info %} {% label warning@warning %} {% label danger@danger %} {% label success@success%}

## Video

### Code

```
{% video url %}
```

## PDF

### Settings

next/_config.yml

```en
pdf:
  enable: true
  # Default height
  height: 500px
```

### Usage

```en
{% pdf url [height] %}

[url]    : Relative path to PDF file.
[height] : Optional. Height of the PDF display element, e.g. 800px.
```

### Code

```en
{% pdf hexo.pdf %}
```

**NOTE:** Unlike images, you don't need to add your post assets folder in front of the address.

### The effect of the code above

{% pdf hexo.pdf %}

## Reference

[https://theme-next.org/docs/tag-plugins/](https://theme-next.org/docs/tag-plugins/)
[http://theme-next.iissnan.com/tag-plugins.html](http://theme-next.iissnan.com/tag-plugins.html)
[Github Flavored Markdown](https://guides.github.com/features/mastering-markdown/)
