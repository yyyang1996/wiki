---
title: Sass
date: '2020-12-20T22:15:43.000Z'
icon: icon-sass
background: bg-pink-500
tags:
  - css
categories:
  - Programming
intro: >
  This is a quick reference cheat sheet that lists the most useful features of
  [SASS](https://sass-lang.com).
---

# sass

## Basics

### Introduction

* [Documentation](https://sass-lang.com/documentation) _(sass-lang.com)_
* [Learn X in Y minutes](https://learnxinyminutes.com/docs/sass/) _(learnxinyminutes.com)_

### Variables

```css
$defaultLinkColor: #46EAC2;

a {
  color: $defaultLinkColor;
}
```

### String interpolation

```css
$wk: -webkit-;

.rounded-box {
  #{$wk}border-radius: 4px;
}
```

### Comments

```css
/*
 Block comments
 Block comments
 Block comments
*/

// Line comments
```

### Mixins

```css
@mixin heading-font {
    font-family: sans-serif;
    font-weight: bold;
}
h1 {
    @include heading-font;
}
```

See: [Mixins](sass.md#mixins-2)

### Nesting

```css
.markdown-body {
    a {
      color: blue;
      &:hover {
        color: red;
      }
    }
}
```

#### to properties

```css
text: {
    // like text-align: center
    align: center;          
    // like text-transform: uppercase
    transform: uppercase; 
}
```

### Extend

```css
.button {
    ···
}
```

```css
.push-button {
    @extend .button;
}
```

### @import

```css
@import './other_sass_file';
@import '/code', 'lists';

// Plain CSS @imports
@import "theme.css";
@import url(theme);
```

The `.sass` or `.sass` extension is optional.

## Mixins

### Parameters

```css
@mixin font-size($n) {
    font-size: $n * 1.2em;
}
```

```css
body {
    @include font-size(2);
}
```

### Default values

```css
@mixin pad($n: 10px) {
    padding: $n;
}
```

```css
body {
    @include pad(15px);
}
```

### Default variable

```css
$default-padding: 10px;

@mixin pad($n: $default-padding) {
    padding: $n;
}

body {
    @include pad(15px);
}
```

## Color functions

### rgba

```css
rgb(100, 120, 140)
rgba(100, 120, 140, .5)
rgba($color, .5)
```

### Mixing

```css
mix($a, $b, 10%)   // 10% a, 90% b
```

### Modifying HSLA

```css
darken($color, 5%)
lighten($color, 5%)
```

```css
saturate($color, 5%)
desaturate($color, 5%)
grayscale($color)
```

```css
adjust-hue($color, 15deg)
complement($color)    // like adjust-hue(_, 180deg)
invert($color)
```

```css
fade-in($color, .5)   // aka opacify()
fade-out($color, .5)  // aka transparentize()
rgba($color, .5)      // sets alpha to .5
```

### Getting individual values

#### HSLA

```css
hue($color)         // 0deg..360deg
saturation($color)  // 0%..100%
lightness($color)   // 0%..100%
alpha($color)       // 0..1 (aka opacity())
```

#### RGB

```css
red($color)         // 0..255
green($color)
blue($color)
```

See: [hue()](http://sass-lang.com/documentation/Sass/Script/Functions.html#hue-instance\_method), [red()](http://sass-lang.com/documentation/Sass/Script/Functions.html#red-instance\_method)

### Adjustments

```css
// Changes by fixed amounts
adjust-color($color, $blue: 5)
adjust-color($color, $lightness: -30%) // darken(_, 30%)
adjust-color($color, $alpha: -0.4)     // fade-out(_, .4)
adjust-color($color, $hue: 30deg)      // adjust-hue(_, 15deg)
```

```css
// Changes via percentage
scale-color($color, $lightness: 50%)
```

```css
// Changes one property completely
change-color($color, $hue: 180deg)
change-color($color, $blue: 250)
```

Supported: `$red`, `$green`, `$blue`, `$hue`, `$saturation`, `$lightness`, `$alpha`

## Other functions

### Strings

```css
unquote('hello')
quote(hello)
```

```css
to-upper-case(hello)
to-lower-case(hello)
```

```css
str-length(hello world)
str-slice(hello, 2, 5)     // "ello" - it's 1-based, not 0-based
str-insert("abcd", "X", 1) // "Xabcd"
```

### Units

```css
unit(3em)        // 'em'
unitless(100px)  // false
```

### Numbers

```css
floor(3.5)
ceil(3.5)
round(3.5)
abs(3.5)
```

```css
min(1, 2, 3)
max(1, 2, 3)
```

```css
percentage(.5)   // 50%
random(3)        // 0..3
```

### Misc

```css
variable-exists(red)    // checks for $red
mixin-exists(red-text)  // checks for @mixin red-text
function-exists(redify)
```

```css
global-variable-exists(red)
```

```css
selector-append('.menu', 'li', 'a')   // .menu li a
selector-nest('.menu', '&:hover li')  // .menu:hover li
selector-extend(...)
selector-parse(...)
selector-replace(...)
selector-unify(...)
```

## Feature checks

### Feature check

```css
feature-exists(global-variable-shadowing)
```

### Features

* global-variable-shadowing
* extend-selector-pseudoclass
* units-level-3
* at-error

## Loops

### For loops

```css
@for $i from 1 through 4 {
    .item-#{$i} { left: 20px * $i; }
}
```

### Each loops (simple)

```css
$menu-items: home about contact;

@each $item in $menu-items {
    .photo-#{$item} {
      background: url('#{$item}.jpg');
    }
}
```

### Each loops (nested)

```css
$backgrounds: (home, 'home.jpg'),
              (about, 'about.jpg');

@each $id, $image in $backgrounds {
    .photo-#{$id} {
      background: url($image);
    }
}
```

### While loops

```css
$i: 6;
@while $i > 0 {
    .item-#{$i} { width: 2em * $i; }
    $i: $i - 2;
}
```

## Other features

### Conditionals

```css
@if $position == 'left' {
     position: absolute;
     left: 0;
}
@else if $position == 'right' {
     position: absolute;
     right: 0;
}
@else {
     position: static;
}
```

### Interpolation

```css
.#{$klass} { ... }      // Class
call($function-name)    // Functions

@media #{$tablet}
font: #{$size}/#{$line-height}
url("#{$background}.jpg")
```

### Lists

```css
$list: (a b c);

nth($list, 1)  // starts with 1
length($list)

@each $item in $list { ... }
```

### Maps

```css
$map: (key1: value1, key2: value2, key3: value3);

map-get($map, key1)
```
