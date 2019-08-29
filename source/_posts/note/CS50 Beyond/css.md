---
title: CS50 Beyond HTML and CSS
tags:
  - CS50
  - beyond
  - html
  - css
categories:
  - note
  - CS50 Beyond
date: 2019-08-15 20:00:52
---

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102768936&page=2" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

## HTML

### HTML5 features

#### Common HTML elements

tag | usage
:-: | :-:
`<h1>, ..., <h6>` | header tag
`<ol>, <ul>` | order list/ unorder list
`<img>` | image tag
`<a>` | anchor tag(often for href)
`<p>` | paragraph tag
`<table>` | paragraph tag
`<th>` | table header
`<tr>` | table row
`<td>` | table data
`<form>` | form tag

#### ID attribute

Insert in any tag.

In `<a>` tag, href="#**the ID of that place**" can create a link to that specific place.
ID can only be used once in the same page.

#### New HTML5 Features

##### contenteditable

contenteditable is an attribute of paragraph

###### Code

```en
<p contenteditable="true">This paragraph is editable</p>
```

###### Effect

<p contenteditable="true">This paragraph is editable</p>

##### datalist

datalist is a tag, it enables auto complete

###### Code

```en
<div>
    <input name="junk" list="some junk" />
    <datalist id="some junk">
        <option value="aa11">
        <option value="ab12">
        <option value="ac13">
        <option value="bc23">
        <option value="ca31">
        <option value="cb32">
    </datalist>
</div>
```

###### Effect

<div>
    <input name="junk" list="some junk" />
    <datalist id="some junk">
        <option value="aa11">
        <option value="ab12">
        <option value="ac13">
        <option value="bc23">
        <option value="ca31">
        <option value="cb32">
    </datalist>
</div>

##### pattern

pattern is an attribute of the input tag
It accept a regular expression

###### Code

```en
<form>
    <input pattern=".*\..*" placeholder="something.something">
    <button type="submit">Submit</button>
</form>
```

**NOTE:** Don't use pattern as the only verification process. Users can modify the source code to bypass that. Never trust your user.

###### Effect

<form>
    <input pattern=".*\..*" placeholder="something.something">
    <button type="submit">Submit</button>
</form>

### Regular Expressions

- Use in string searching algorithms
- Basic Operations
  - Concatenation
  - Alternation
  - Kleene Star

Expression | Matches
:-: | :-:
`hi` | `hi`
`hi{% raw %}|{% endraw %}hello` | `hi` or `hello`
`hi?` | `h` or `hi`
`hi*` | `h/hi/hii/hiii/...` (from 0 to infinite)
`hi+` | `hi/hii/hiii/...` (from 1 to infinite)
`hi{3}` | `hiii`
`.` | anything
`\.`/`\+`/... | `.`/`+`   `\` is the escape character
`\s` | white space
`[a-z]`/`[A-Z]`/`[0-9]` | a to z/A to Z/0 to 9

**NOTE:** Those marks only apply on the one before them

## CSS

### CSS Properties

- color
- text-align
- width, height
- margin, padding
- font-family, font-size, font-weight
- border

### Styling Ways

Inline Styling:

```en
<!DOCTYPE html>
<html>
    <head>
        <title>Style</tile>
    </head>
    <body>
        <h1 style="color:red;">This is red</h1>
    </body>
</html>
```

Use of Selector:

```en
<!DOCTYPE html>
<html>
    <head>
        <title>Style</tile>
        <style>
            h1 {
                color:red;
            }
        </style>
    </head>
    <body>
        <h1>This is red</h1>
    </body>
</html>
```

### Selector

Selector | Example | Description
:-: | :-: | :-:
element | `h1` | Select every `h1` element
`.class` | `.welcome` | Select every element whose class is welcome
`#id` | `#welcome` | Select the element whose id is welcome
element, element | `h1, div` | Select every `h1` and `div` element
element element | `div h1` | Select every `h1` that is inside `div`
element>element | `div>h1` | Select every `h1` that is an **immediate** children of `div`
element+element | `div+h1` | Select every `h1` that is right after `div`
`[attribute=value]` | `[target=1]` | Select every element that has `target=1`
`:hover` | `button:hover` | Acts when a button has the cursor hover over it

### CSS Box Model

All element in the HTML has a border. Outside of the border there is comething called the Margin. Inside the border there is something called Padding.

### Responsive Design

**Viewport:** The visible area of the webpage on the screen

```en
<meta name="viewport" content="width=device-width initial-sacle=1.0">
```

`width=device-width` means that the width of the webpage is equal to the device's width
`initial-scale=1.0` means that at the beginning, do not zoom the webpage

**Media Query:** Let you customize the CSS you use based upon the type of the media of the user that is viewing the page.

Inside the "Style tag"

```en
@media (min-width 500px) {
    Just the same as others
}
```

The above only got to apply when the page is at least 500 pixels wide

```en
@media (max-width 499px) {
    Just the same as others
}
```

The above only got to apply when the page is at most 499 pixels wide

```en
@media print {
    Just the same as others
}
```

The above only got to apply when the page is printed out

**Flex Box:** It is a technology that automatically wrap the page for you.

Inside the "Style" tag

```en
selector {
    display: flex;
    flex-wrap: wrap;
}
```

**Grid Model:** Display like grid

Inside the "Style" tag

```en
selector {
    display: grid;
    flex-wrap: wrap;
    grid-column-gap: xxx; (in pixel)
    grid-row-gap: xxx; (in pixel)
    grid-template-columns: xxx;
}
```
