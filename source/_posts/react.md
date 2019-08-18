---
title: CS50 Beyond React
date: 2019-08-17 14:05:49
tags: [CS50, beyond, react]
categories: [note, CS50 Beyond, React]
---

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102776522&page=8" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102776867&page=9" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102760014&page=12" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

## Declarative

Write code to tell the computer the way we want the web application to look like.

## JSX

An extension of JavaScript.

In JSX we can treat HTML elements as values of their own.

## Packages

- React(The React library)
- ReactDOM(Insert React components into webpage)
- Babel(Translate JSX into JS)

Scripts CDN:

```en
React:
<script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
ReactDOM:
<script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
Babel:
<script src="https://cdn.staticfile.org/babel-standalone/6.26.0/babel.min.js"></script>
```

<script src="https://cdn.staticfile.org/react/16.4.0/umd/react.development.js"></script>
<script src="https://cdn.staticfile.org/react-dom/16.4.0/umd/react-dom.development.js"></script>
<script src="https://cdn.staticfile.org/babel-standalone/6.26.0/babel.min.js"></script>

## Components

### Basic Structure

```en
class Hello extends React.Component {

}
```

The Hello class is a React component.

Each component need something to determine what should show up on the page, so each component needs a render function.

```en
class Hello extends React.Component {
    render() {
    return <p>Hello!</p>;
    }
}
```

So now all Hello class does is display a p tag.

### Example1

```en
<div id="codeexample1"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is render by React!
                </p>
            );
        }
    }
    ReactDOM.render(<Hello />, document.querySelector("#codeexample1"));
</script>
```

<div id="codeexample1"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is render by React!
                </p>
            );
        }
    }
    ReactDOM.render(<Hello />, document.querySelector("#codeexample1"));
</script>

### Example2

```en
<div id="codeexample2"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is render by React!
                </p>
            );
        }
    }
    class App extends React.Component {
        render() {
            return (
                <div>
                <Hello/>
                <p>Above and below are two Hello class.</p>
                <Hello/>
                </div>
            )
        }
    }
    ReactDOM.render(<App />, document.querySelector("#codeexample2"));
</script>
```

<div id="codeexample2"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is render by React!
                </p>
            );
        }
    }
    class App extends React.Component {
        render() {
            return (
                <div>
                <Hello/>
                <p>Above and below are two Hello class.</p>
                <Hello/>
                </div>
            )
        }
    }
    ReactDOM.render(<App />, document.querySelector("#codeexample2"));
</script>

### Properties

Some arguments that attached to a class.

### Example3

```en
<div id="codeexample3"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is {this.props.count} {this.props.name}
                </p>
            );
        }
    }
    class App extends React.Component {
        render() {
            return (
                <div>
                <Hello count="Number1" name="Hello Class"/>
                <Hello count="Number2" name="Hello Class"/>
                <Hello count="Number3" name="Hello Class"/>
                </div>
            )
        }
    }
    ReactDOM.render(<App />, document.querySelector("#codeexample3"));
</script>
```

<div id="codeexample3"></div>
<script type="text/babel">
    class Hello extends React.Component {
        render() {
            return (
                <p>
                    This is {this.props.count} {this.props.name}
                </p>
            );
        }
    }
    class App extends React.Component {
        render() {
            return (
                <div>
                <Hello count="Number1" name="Hello Class"/>
                <Hello count="Number2" name="Hello Class"/>
                <Hello count="Number3" name="Hello Class"/>
                </div>
            )
        }
    }
    ReactDOM.render(<App />, document.querySelector("#codeexample3"));
</script>

**Set the default value:**

Change `This is {this.props.name}` to `This is {this.props.name || "Hello Class"}`

So now you can use the Hello class without "name": `<Hello count="Number3"/>`

## State

In React, if you change the state of the application, the view of the application is going to change based on that.
So if you want to update the page, just change the state of the application, no need to refresh the whole page.

### Example4

A counter class.


