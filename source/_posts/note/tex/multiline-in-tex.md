---
title: Multiline Formula in LaTex
tags:
  - tex
  - latex
mathjax: true
categories:
  - note
  - tex
date: 2019-09-08 10:38:25
---

When writing multiline formula with Mathjax in Hexo:

$$\begin{equation}\begin{split} a&=b+c-d\\
&\quad +e-f\\
&=g+h\\
& =i
\end{split}\end{equation}$$

```en
\begin{equation}\begin{split} a&=b+c-d\\
&\quad +e-f\\
&=g+h\\
& =i
\end{split}\end{equation}
```

1. `\begin` and `\end` represent the begin and end of the formula
2. `\\` as the break line symbol
3. `&` for align

Notice: In Hexo, `\\` is an escape for `\`, in order to write double backslash, in Hexo you should write `\\\\`

```en
\begin{equation}\begin{split} a&=b+c-d\\\\
&\quad +e-f\\\\
&=g+h\\\\
& =i
\end{split}\end{equation}
```

$$\begin{equation}\begin{split} a&=b+c-d\\\\
&\quad +e-f\\\\
&=g+h\\\\
& =i
\end{split}\end{equation}$$
