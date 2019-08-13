---
title: Some Escape for Jinja, Hexo and HTML
date: 2019-08-12 17:22:10
tags: [python, flask, jinja, hexo, template]
categories: note
---

Jinja takes "{% raw %}{{{% endraw %}", "{% raw %}}}{% endraw %}", "{% raw %}{%{% endraw %}", "{% raw %}%}{% endraw %}" as symbols for statements/expressions.

So if you want to use these symbols in your text of a Jinja Templated HTML file, put them in
```
{% raw %}
    your content
{% endraw %}
```

Hexo seems to use something like Jinja, so that also works when you are writing markdown file of hexo.
Or Hexo will raise an "unexpected token" template render error.

For some special symbol in HTML, like `&lt;`("<"), `&gt;`(">")

Change `&` to `&amp;`