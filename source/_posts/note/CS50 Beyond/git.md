---
title: CS50 Beyond Git and Github
tags:
  - CS50
  - beyond
  - git
  - github
categories:
  - note
  - CS50 Beyond
date: 2019-08-15 14:01:15
---

<iframe src="//player.bilibili.com/player.html?aid=58975882&cid=102766022&page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" width="100%" height="500px"> </iframe>

## Git Commands

command | usage
:-: | :-:
`git clone <url>` | Clone the repository to local
`git init` | initiallize a repository locally
`git add <filename>` | add the file to the workspace
`git commit -m "message"` | commit the change in the workspace
`git status` | Show the status of your files
`git push` | push to remote repository
`git pull` | pull from remote repository
`git commit -am "message"` | add every untracked file into workspace then commit
`git log` | show the log of git change
`git reset --hard <commit>` | go back for one version
`git branch` | show the branches that currently have
`git checkout -b <branch name>` | create a new branch
`git checkout <branch name>` | switch to an existed branch
`git merge <branch name>` | merge current branch with that branch
`git branch -D <branch name>` | delete the branch

## Pull Request

In industry, they don't let everyone to modify the code base, instead, you should make change on different branch and then summit a pull request so that someone else can do a review and comment and then merge the branches.

So pull request is a request to merge your branch into the master branch. And it is widely used in the inductry.

## Sass

Sass is an extension of CSS that allows you to use variable and nesting.

### Link a seperate CSS file

```en
<link rel="stylesheet" href="address of the css file">
```

### Variable

For Sass file, file extension is `.css`

`$` as the mark of variable, `$variable_name` is a complete variable

```en
$color: red;

ul {
    color=$color;
}
```

Above is a complete SASS file.

### Compile

SASS file can't be directly linked to the HTML file.

Download the SASS program then run it, it will convert SASS file to CSS file for you.

Use the command `sass xxx.scss xxx.css`

### Nesting

```en
div {
    xxxxxx

    p {
        xxxxx
    }

    ul {
        xxxxx
    }
}
```

You can use the above code to directly apply CSS to that structure in Sass.

### Inheritence

Inheritence in Sass use the `%` sign.

```en
%extend {
    xxx
    xxx
}

#id {
    @extend %extend;
    xxx
    xxx
}
```

Properties in %extend will also effect in #id
