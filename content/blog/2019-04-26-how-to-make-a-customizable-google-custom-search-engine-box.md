---
author: Güngör Budak
date: '2019-04-26T18:00:00+03:00'
slug: how-to-make-a-customizable-google-custom-search-engine-box
tags:
- google custom search engine
- google custom search
- search box
- customization
title: How to Make a Customizable Google Custom Search Engine Box
year: '2019'
---

Google Custom Search Engine (CSE) is a great service when you need to implement a search functionality to a website and do not spend too much time. However, the default way of implementing it restricting us to have a certain search box design that might not blend well to our website. In this post, I'll show how I found a workaround solution and actually implement on this very blog.

To see the solution in action, feel free to search anything on the search box at the top of the right sidebar. :)

[![Customized Google CSE Box](/public/images/customized-google-cse-box.png)](/public/images/customized-google-cse-box.png)
*Customized Google CSE Box*


[![Customized Google CSE Results](/public/images/customized-google-cse-results.png)](/public/images/customized-google-cse-box.png)
*Customized Google CSE Results for "django" search*


Google recently (2019) changed CSE in a way that now it is more powerful and allows to send queries directly with a search string (i.e. `?q=search-text` at the end of the URL); however, for this to work you need to create a new search engine. The old ones have to use hash string (i.e. `#qsc.q=search-text` at the end of the URL). I updated the search engine in my website for search string version as it is cleaner and I'm primarily explaining that one but I'll share the methods for hash version at the end. Only difference is the hash string version requires JavaScript.

**1\. Get Google CSE code and make a results page**

I'll skip how to go and create a Google Custom Search Engine for your website. Use [the official Custom Search Engine guide here](https://support.google.com/customsearch/answer/4513751?hl=en) to do it. Briefly go to [Google CSE website](https://cse.google.com/cse/all), hit create new button, put your website URL, and you're done. All other customizations are up to you and depend on how you want to show your search results. What you need is to get the HTML code for placing search results to a page from Google Custom Search Engine service, say it's `example.com/search.html` for you. It will look something like this;

```html
<script async src="https://cse.google.com/cse.js?cx=YOUR_CSE_ID"></script>
<div class="gcse-searchresults-only"></div>
```

**2\. Place the search box form to any page you want**

Below find a minimal `input` tag in a `form`, I'm also putting a `button` but typing search query and hitting `Enter` will work fine.

```html
<!-- minimal & customizable Google CSE search box form -->
<form method="get" action="/search.html">
    <input type="text" name="q">
    <button type="submit">Search</button>
</form>
```

You can add styles, classes, a placeholder, anything. Below are the minimal requirements:

- `action="/search.html"` on `form` so browser will redirect user to correct place for search results, use your search results page if it is different
- `name="q"` on `input` so Google CSE (default is `q`, it is configurable but keep it as `q` if you don't have to) knows what you are searching for

**Optional JavaScript code for showing searched text in the search box**

If you want to keep the searched text at the search box while showing search results (just a feedback for user) such as in my website you may use below code.

```javascript
// check if there is any text in the search string
if (window.location.search.length > 0) {
  // retrieve the "q" keyed search string value
  var q = window.location.search.substring(1).split('&').filter(function(x) {
    return x.substring(0, 2) === 'q=';
  })[0].substring(2);
  // put the value to the search box if it is not empty
  if (q.length > 0) {
    document.querySelector('input[name="q"]').value = q;
  }
}
```

**Hash version changes**

The HTML part now includes a class name and doesn't have `get` and `action` as now we do not rely on the browser redirection and JavaScript will redirect.

```html
<!-- minimal & customizable Google CSE search box form -->
<form class="search-form">
    <input type="text" name="q">
    <button type="submit">Search</button>
</form>
```

The JavaScript code with must part is responsible for opening the search results page.

```javascript
  // JavaScript code that should follow the search box code
  
  // (must part)
  
  // add a listener for form submission, i.e. when user hits Enter or
  // clicks to any submit button form has
  document.querySelector('.search-form').addEventListener('submit', function(e) {
    // do not actually submit the form, we'll do something else :)
    e.preventDefault();
    // read the search query for input tag, i.e. user searches
    // for "django" let's say
    var q = document.querySelector('input[name="q"]').value;
    // just proceed if user has typed something
    if (q.length > 0) {
      // go to search results page which is search.html here
      // but can be anything you like with "gsc.q" hash parameter
      // equal to search query
      window.open('/search.html#gsc.q=' + q, '_self');
    }
  });

  // (optional part)
  // below is only used if you also want to put the search box
  // on the search results page it's useful when the user wants
  // to search something else directly and let user know
  // what she is searching for at that moment
  
  // check if any hash parameter exists on the URL
  if (window.location.hash.length > 0) {
    // read the search query value among hash parameters
    // with key "gsc.q="
    var q = window.location.hash.substring(1).split('&').filter(function(v) {
      return v.substring(0, 6) === 'gsc.q=';
    })[0].substring(6);
    // if there is actually a search query
    if (q.length > 0) {
      // put it as the input tag's value
      document.querySelector('input[name="q"]').value = q;
    }
  }

```

Note that:

- `/search.html` is assumed for this guide. You should change the code accordingly. For example it's `/blog/search/` for my website
- This JavaScript code should be put anywhere the search box form is placed. Also, place the JavaScript code below the form so it is loaded beforehand

That's it. Now, you have a minimal search box that works and you can customize it in any ways.
