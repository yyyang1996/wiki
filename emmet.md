---
title: Emmet
date: '2020-12-14T18:28:43.000Z'
icon: icon-emmet
background: bg-green-400
tags:
  - snippets
  - coding
  - html
  - css
  - abbr
categories:
  - Toolkit
intro: >
  [Emmet](https://emmet.io/) is a web-developer’s toolkit for boosting HTML &
  CSS code writing, which allows you to write large HTML code blocks at speed of
  light using well-known CSS selectors.
---

# emmet

## Syntax

### Getting started

Let us start to improve your development to the speed of light.

* [Emmet in Visual Studio Code](https://code.visualstudio.com/docs/editor/emmet) _\(code.visualstudio.com\)_
* [Emmet 2 for Sublime Text](https://github.com/emmetio/sublime-text-plugin) _\(github.com\)_
* [Emmet for Coda](https://emmet.io/download/coda/) _\(emmet.io\)_
* [Emmet for Atom](https://github.com/emmetio/emmet-atom#readme) _\(github.com\)_

### Multiplication: \*

ul&gt;li\*5

```markup
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

### Child: &gt;

`nav>ul>li`

```markup
<nav>
    <ul>
        <li></li>
    </ul>
</nav>
```

### Custom attributes

p\[title="Hello world"\]

```markup
<p title="Hello world"></p>
```

td\[rowspan=2 colspan=3 title\]

```markup
<td rowspan="2" colspan="3" title=""></td>
```

\[a='value1' b="value2"\]

```markup
<div a="value1" b="value2"></div>
```

### Text: {}

a{Click me}

```markup
<a href="">Click me</a>
```

p&gt;{Click }+a{here}+{ to continue}

\`\`\`html {.wrap}

Click [here](emmet.md) to continue

```text
### ID and CLASS attributes

`#header`

```html
<div id="header"></div>
```

.title

```markup
<div class="title"></div>
```

form\#search.wide

```markup
<form id="search" class="wide"></form>
```

p.class1.class2.class3

```markup
<p class="class1 class2 class3"></p>
```

### Implicit tag names

.class

```markup
<div class="class"></div>
```

em&gt;.class

```markup
<em><span class="class"></span></em>
```

ul&gt;.class

```markup
<ul>
    <li class="class"></li>
</ul>
```

table&gt;.row&gt;.col

```markup
<table>
    <tr class="row">
        <td class="col"></td>
    </tr>
</table>
```

### Sibling: +

div+p+bq

```markup
<div></div>
<p></p>
<blockquote></blockquote>
```

### Climb-up: ^

div+div&gt;p&gt;span+em^bq

```markup
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>
```

div+div&gt;p&gt;span+em^^bq

```markup
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>
```

### Grouping: \(\)

div&gt;\(header&gt;ul&gt;li\*2&gt;a\)+footer&gt;p

```markup
<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

\(div&gt;dl&gt;\(dt+dd\)\*4\)+footer&gt;p

```markup
<div>
    <dl>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
        <dt></dt>
        <dd></dd>
    </dl>
</div>
<footer>
    <p></p>
</footer>
```

### $

ul&gt;li.item$\*3

```markup
<ul>
    <li class="item1"></li>
    <li class="item2"></li>
    <li class="item3"></li>
</ul>
```

h$\[title=item$\]{Header $}\*3

```markup
<h1 title="item1">Header 1</h1>
<h2 title="item2">Header 2</h2>
<h3 title="item3">Header 3</h3>
```

ul&gt;li.item$$$\*3

```markup
<ul>
    <li class="item001"></li>
    <li class="item002"></li>
    <li class="item003"></li>
</ul>
```

ul&gt;li.item$@-\*3

```markup
<ul>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>
```

ul&gt;li.item$@2\*3

```markup
<ul>
    <li class="item2"></li>
    <li class="item3"></li>
    <li class="item4"></li>
</ul>
```

## Also see

* [Emmet Cheat sheet](https://docs.emmet.io/cheat-sheet/) _\(docs.emmet.io\)_

