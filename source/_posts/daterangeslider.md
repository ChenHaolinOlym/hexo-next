---
title: Properties of Bokeh Daterangeslider that Helps Develop
date: 2019-08-10 18:23:51
tags: [python, bokeh, daterangeslider]
categories: [article, python, bokeh]
---
## Introduction
This article is about two special property of Daterangeslider in bokeh, which can help develop your bokeh app.

My bokeh version is 1.3.1.

## Body
According to the [official documentation](https://bokeh.pydata.org/en/latest/docs/reference/models/widgets.sliders.html), Bokeh Daterangeslider has two property method: `value_as_date` and `value_as_datetime`.

Normally, when you called the on_change callback function, bokeh will return you a tuple of Unix timestamp in miliseconds. It's very inconvinient to change the format of the datetime.

So you can call `daterangeslider.value_as_date` or `daterangeslider.value_as_datetime` (remember this is property not method) in your callback function. Both will return you a tuple of datetime.date object, which can be conveniently turned into any format of datetime via its own strftime method.

Yet anothor way of using property method doesn't work.

You can't simply pass in `value_as_date` or `value_as_datetime` in the on_change method. 

e.g. `daterangeslider.on_change("value_as_date", on_change)`

This will raise an error