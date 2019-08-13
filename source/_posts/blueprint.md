---
title: Template and Static Folder Setting in Flask Blueprint
date: 2019-08-12 16:50:39
tags: [python, flask, blueprint, template, static]
categories: article
---

## Settings
```
bp = Blueprint(xxxxxxx, template_folder='templates', static_folder='static')
```

## How to Use
Flask treat them differently:

### Template Folder
For template folder, when you register your blueprint, flask will add the address of blueprint template folder into its config.

All contents under all blueprint/original template folder will be treated as if they are in a same big folder "template".

If there are templates of the same name, Flask will search the original template folder first and then the blueprint folders.

The solution is to create a folder with the same name in the blueprint's template folder, so you can use it like your static folder.

### Static Folder
For static folder, the blueprint's static folder address will be register to the blueprint.

So you can reference it wherever in your Flask app by: `"blueprintName".static`

