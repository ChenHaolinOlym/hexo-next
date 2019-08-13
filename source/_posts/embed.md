---
title: Embed Bokeh Application in Flask
date: 2019-08-10 17:57:14
tags: [python, flask, bokeh]
categories: article
---
This article is based on the [official document](https://bokeh.pydata.org/en/latest/docs/user_guide/embed.html) of Bokeh and is about embed bokeh application in flask using app sessions.

What you need to do is to pull a session from a bokeh server, turn it into script and insert it into your template.

So you need to set up a bokeh server first.

`bokeh serve --show "your bokeh file address"`

Keep it open.

Due to Bokeh's safety settings, you need to set `allow web-socket origin` to avoid errors when you are setting up your bokeh server.

```
bokeh serve --show "your bokeh file address"
--allow-websocket-origin=localhost:5006  (This is bokeh server's default port, if you reset the port, change it to the port you set)
--allow-websocket-origin="your web page address that you want to embed your bokeh app"
```

Then you need to complete your route function:

```
def bkapp_page():
    with pull_session(url="http://localhost:5006/{your bokeh file name}") as session:
        script = server_session(session_id=session.id, url='http://localhost:5006/{your bokeh file name}') (As the above, change the port if you reset it yourself)
        return render_template("your template", script=script, template="Flask")
```

Don't forget to import the functions you need

```
from bokeh.client import pull_session
from bokeh.embed import server_session
```

Finally, put the script into your template.

In the body part of the template:

Put in: `{% raw %}{{{% endraw %}script|indent(n)|safe{% raw %}}}{% endraw %}`

"{% raw %}{{}}{% endraw %}" is the jinja representation of code
script is the script that you put in the render_template function
indent(n) means the number of spaces of where you put your script (Just for beautify your code)
safe means that Jinja won't take care of some illegal symbol for you(like "<>", which normally will be turned into "&lt;" and "&gt;")

So now you complete embed your bokeh app in your flask app. Run your app.py for a test!

