---
title: Update Bokeh Figure's X/Y Range
tags:
  - python
  - bokeh
  - figure
  - range
categories:
  - note
  - python
date: 2019-08-12 12:05:30
---
To update bokeh figure's x_range/y_range, you should use:
```
"plotname".x_range.start = xxx
"plotname".x_range.end = xxx
"plotname".y_range.start = xxx
"plotname".y_range.end = xxx
```