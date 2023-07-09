---
author: Güngör Budak
date: '2018-12-12T11:00:00+03:00'
slug: bootstrap-4-search-box-with-search-icon
tags:
- bootstrap 4
- css
- search box
- search icon
title: Bootstrap 4 Search Box with Search Icon
year: '2018'
---

Bootstrap 4 is a very handy library to generate quick web user interfaces for web pages and web applications. Search box is a very fundamental UI element if the web page is providing some content and in this post I'll describe some styles that make a nice text input for search box.

To accomplish this, I'll make use of [the default way of form validations in Bootstrap 3](https://getbootstrap.com/docs/3.3/css/#forms-control-validation) which was removed in Bootstrap 4 because it doesn't support font icons anymore. But the below solution will for work Bootstrap 4. [Check this pen if you're looking for a solution in Bootstrap 3](https://codepen.io/gungorbudak/pen/gPWqRP).

This solution is also using Font Awesome font icons but it can be done with any other font icon.

After you **include Bootstrap 4** and **Font Awesome** CSS files, use below HTML and CSS to display the box as shown in the pen below.

```html
<div class="form-group has-search">
  <span class="fa fa-search form-control-feedback"></span>
  <input type="text" class="form-control" placeholder="Search">
</div>
```

In this HTML code, `.has-search` is something new Bootstrap 4 doesn't have. So here are those class styles:

```css
.has-search .form-control {
  padding-left: 2.375rem;
}

.has-search .form-control-feedback {
  position: absolute;
  z-index: 2;
  display: block;
  width: 2.375rem;
  height: 2.375rem;
  line-height: 2.375rem;
  text-align: center;
  pointer-events: none;
  color: #aaa;
}
```

This way, `.has-search` will place given font icon for search icon correctly left to the search box. Find this search box below, I also have a version with an actual button but this one uses built-in styles.

<pre class="codepen" data-height="300" data-type="result" data-href="ooKNpz" data-user="gungorbudak" data-safe="true"> <code> </code> <a href="https://codepen.io/gungorbudak/pen/ooKNpz">Check out this Pen!</a> </pre>
<script src="https://codepen.io/assets/embed/ei.js"> </script>
