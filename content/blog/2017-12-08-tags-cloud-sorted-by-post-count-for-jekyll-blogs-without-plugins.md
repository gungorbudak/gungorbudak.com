---
author: Güngör Budak
date: '2017-12-08T12:42:00+03:00'
slug: tags-cloud-sorted-by-post-count-for-jekyll-blogs-without-plugins
tags:
- tags
- cloud
- tags cloud
- jekyll
- blog
title: Tags Cloud Sorted by Post Count for Jekyll Blogs without Plugins
year: '2017'
---

Recently, I have been trying to transfer my old posts in a Blogger blog to my new Jekyll blog since I really liked this way of blogging. But there were some features that I like in Blogger and wasn't supported in Jekyll by default. I did some research and found a very nice way of generating tags cloud the my blog.

Although I build my blog locally and then push to GitHub pages, I still try not to use a custom plugin. So this solution is not using any custom plugin and it should work for GitHub pages.

The idea comes from on [this SO answer](https://stackoverflow.com/a/24744306/1597907) by Christian Specht. Briefly, he's putting the counts of the tags in front of the tag name and then sorts, which at the end sorts the list. Of course, he needed to add some large value to the counts as string sorting doesn't recognize numbers. But his solution wasn't working for the tags with spaces (issue 1) and also although the ordering was correct for numbers and the tags were not alphabetically ordered (they were reverse ordered, issue 2).

So in the solution below, I fix these two issues with his approach.

First, I make the list of tags but with their counts prepended by `count + (-10000)` (solves issue 2 by giving negative ordering with `-10000`) and appended by the actual count. I also replace spaces in the tag names with `##` which will help me work on tags with spaces (solves issue 1). These three data are joined by `###` which is unusual enough for a separator.

Then, I convert this captured string into an array with `| split = ' '` and then sort the array. Finally, I just split the tag name and post count, replace spaces back and output the tags in the correct order with their post counts.

There is also one additional thing here `size` in the code below which is used to style the tags. What I do is to add class `tag-size-{{ size }}` to each tag for showing them in different font sizes according to the their number of posts. I also put the CSS down below. 

```liquid
{% raw %}{% capture tags %}
  {% for tag in site.tags %}
    {{ tag[1].size | plus: -10000 }}###{{ tag[0] | replace: ' ', '##' }}###{{ tag[1].size }}
  {% endfor %}
{% endcapture %}
{% assign sorted_tags = tags | split: ' ' | sort %}
{% for sorted_tag in sorted_tags %}
    {% assign items = sorted_tag | split: '###' %}
    {% assign tag = items[1] | replace: '##', ' ' %}
    {% assign count = items[2] | plus: 0 %}
    {% if count > 5 %}
        {% assign size = 5 %}
    {% else %}
        {% assign size = count %}
    {% endif %}
    <span class="tag-size-{{ size }}">
        <a class="tag-link" href="/blog/tag/{{ tag | slugify }}" rel="tag">{{ tag }}</a> ({{ count }})
    </span>
{% endfor %}{% endraw %}
```

Styles for the tags:

```css
.tag-size-5 {
    font-size: 1.25rem;
}

.tag-size-4 {
    font-size: 1.10rem;
}

.tag-size-3 {
    font-size: 0.95rem;
}

.tag-size-2 {
    font-size: 0.80rem;
}

.tag-size-1 {
    font-size: 0.65rem;
}
```

Have a look at the tags cloud on the right for the live example!
