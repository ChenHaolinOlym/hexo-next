---
title: 'CS50 Beyond Python, Flask, OOP and AI'
tags:
  - CS50
  - beyond
  - python
  - flask
  - oop
  - ai
categories:
  - note
  - CS50 Beyond
date: 2019-08-19 11:07:08
---

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102776514&page=7" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102776153&page=5" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

## Flask Session

We will use a flask extension called "flask_session"

```en
from flask import Flask, render_template, session
from flask_session import Session
from tempfile import mkdtemp

app = Flask(__name__)

app.config["SESSION_FILE_DIR"] = mkdtemp()
app.config["SESSION_PERMANENT"] = False
app.config["SESSION_TYPE"] = "filesystem"
Session(app)

@app.route('/')
def index():
    return session
```

"session" is a dict that differ for every session. Store your temporary app data in it.
