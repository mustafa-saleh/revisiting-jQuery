# jQuery W3School

## Introduction

- jQuery is a light weight, "write less, do more" JS library
- jQuery makes it easier to use javascript in your website
- It takes common tasks that requore many JS lines to accomplisjh and wraps them into methods that you can call in single line of code
- It also simplifies Ajax call and Dom manipulation
- jQuery contains the following featuires:
  - Html/Dom manipulation
  - Css manipulation
  - Html event methods
  - Effects and animation
  - AJAX
  - Utilities
- jQuery runs exactly the same on all major browsers

## JavaScript in head or body

- Scripts can be placed in the body, or in the head section of an HTML page, or in both.
- Placing scripts at the bottom of the body element improves the display speed, because script interpretation slows down the display.

## Script Tag attributes

- async: script is downloaded in parallel to page parsing and executed as soon as its available (before parsing complete) (only for external scripts)
- defer: script is downloaded in parallel to page parsing and executed after page has finished parsign (only for external scripts)

## Getting Started

- To use jQuery, either:

  - download the library and reference it
  - or use the cDN

  ```html
  <head>
    <script src="jquery-3.5.1.min.js"></script>
    <!--or-->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
  </head>
  ```

- Using hosted jQuery from Google has advantages such as:
  - Many users already downloaded jQuery when visiting other sites and it'll be loaded from cache when they vist your site => faster loading time
  - Most of CDNs serve files from the nearset location to user => faster loading time

## jQuery Syntax

- basic syntax `$(selector).action()`
- jQuery uses CSS selectors to query elements
- Its good practice to put jQuery code inside ready event (document finished loading)

```javascript
$(documnet).ready(function () {
  //jQuery code
});
// or shorter version of document ready
$(function () {});
```

## jQuery Selectors

- based on CSS selectors and has some selectors of its own
- Select all elements`$("*")`
- Select the current HTML elemnt `$(this)`

## jQuery Event Methods

- Most of Dom events have equivilant jQuery methods

```javascript
$("p").click(function () {});
```

- Commonly used jQuery event methods: ready, click, dblclick, mouseenter, mouseleave, mousedown, mouseup, hover, focus, blur

- The 'on' method is used to attach on or more events to an element

```javascript
$("p").on({
  mouseenter: function () {
    $(this).css("background-color", "lightgray");
  },
  mouseleave: function () {
    $(this).css("background-color", "lightblue");
  },
});
```

```javascript
$("p").on("click", function () {
  //code
});
```

## jQuery Effects

- Show or hide elements by using `show(speed, cb)` or `hide()` methods
- `toggle()` to toggle between show and hide
- you can fade elements in and out with `fadeIn(speed, cb) fadeOut() fadeToggle() fadeTo(speed, opacity, cb)`
- fadeTo fades elements to a given opacity
- speed could be 'slow', 'fast' or milliseconds
- To create slide effect use, `slideUp(speed, cb) slideDown() slideToggle()`
- To create animation, use `animate({params}, speed, cb)`
- If you create mmultiple animations with `animate()` jQuery creates an internal queue for these calls, then runs them one by one
- jQuery methods can be chained to run multiple methods on the same element

## jQuery HTML

### Dom manipulation

- jQuery has methods for dom manipulation such as:
  - `text() html()` for getting or setting element text or html
  - `val()` get or set value of form field
- the `attr()` method is used to get attribute values

### Add HTML Elements

- methods to add new content `append() prepend() after() before()` to add content at end, begining, after and before respectively
- To remove content:
  - `remove()` removes element and its children
  - `empty()` remove child elements

### CSS manipulation

- `addClass() removeClass() toggleClass() css()`
- when adding classes, you can select multiple elements and add multiple classes
  `$("h1, h2, p").addClass("blue legend");`
- `css()` is used to get or set the value of one or more style properties

```javascript
$("p").css("background-color"); //get
$("p").css("background-color", "blue"); //set
$("p").css({ "background-color": "yellow", "font-size": "200%" });
```

### jQuery Element & Window Dimentions

- `width() height() innerWidth() innerHeight() outerWidth() outerHeight()`

## jQuery Traversing

- select html elements based on their relation to other elements
- With jQuery traversing, you can move through DOM tree and select the ancestors, descendants or siblings of an element
- jQuery provide a variety of methods to traverse the DOM

### Ancestors

- `parent()` return direct parent of an element
- `parents()` return all ancestors of an element to the document root element `<html>`, pass an optional parameter to filter the result, for example to select all ancestors that are `<div>` elements `parents("div")`
- `parentsUntil()` return all ancestors between two given arguments

### Descendants

- `children()` return all direct children of an element, pass an optional parameterr to filter result `children('.last')` return all direct children with class last
- `find()` return all descendants down to the last `find('div')` to return all div descendants of the selected element

### Siblings

- `siblings()` returns all siblings of the selected element
- `next()` returns the next sibling of the selected element
- `nextAll()` returns all next siblings
- `nextUntil()` returns all next siblings between two given arguments
- `prev() prevAll() prevUntil()` works similar to the next methods

### Filtering

- `first() last() eq()` methods allow you to select an element based on its position within a group of elememnts

```javascript
$(document).ready(function () {
  $("p").first();
  $("p").eq(1); // p with index number 1 (second p)
});
```

- `filter() not()` to select an element that match or donot match a certain criteria

## AJAX

- Ajax is used to exchange data with server and updating parts of the web page without reloading it
- jQuery provide several methods for ajax functionality
- with jQuery, you can request html, xml, text or json from a server using a get or post request

### Load

- `load()` method loads the data from server to the selected element `$(selector).load(URL, data, cb)`
  - URL: URL to load
  - data: data to send along with request
  - cb: callback to execute after load is finished, it can have the following parameters:
    - responseTxt: contains resulting content if success
    - statusTxt: status of call
    - xhr: XMLHttpRequest Object

### Get and Post

- request data from sevre with an http request

```javascript
$.get(URL, function(data, status))
$.post(URL, data, function(data, status))
```

- The noConflict method `$.noConflict()` is used to avoid any conflicts with other frameworks that use the '$' sign. You can use jQuery by writing the full name instead of the shortcut

```javascript
$.noConflict()
jQuery(document).ready(function(){
 //...
})
//or
var jq = $.noConflict();
jq(document)...
```
