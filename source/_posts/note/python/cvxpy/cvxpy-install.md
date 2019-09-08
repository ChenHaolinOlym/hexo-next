---
title: Python Cvxpy Install on Win10
tags:
  - python
  - cvxpy
  - optimization
  - convex optimation
categories:
  - note
  - python
  - cvxpy
date: 2019-09-07 16:06:27
---

1. Upgrade pip first: `python -m pip install --upgrade pip`.
2. Try `pip install cvxpy`, if success, everything is done.
If an error occur:
3. Donwload wheel files from ![https://www.lfd.uci.edu/~gohlke/pythonlibs/](https://www.lfd.uci.edu/~gohlke/pythonlibs/), and use `pip install filename.whl` to install them.
Remember to download the correct version of the wheel file:
"cpxx" is the version of python and what's followed is the operation system's version.
