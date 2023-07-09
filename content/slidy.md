---
permalink: "/slidy/"
layout: page
date: '2018-07-21T14:00:00+03:00'
lang: en
title: Slidy / Responsive jQuery Wordpress Slider
ref: slidy
---

Slidy is a reponsive jQuery slider that uses [slick carousel by Ken Wheeler](http://kenwheeler.github.io/slick/) and it's fully integrated into WordPress, so it's possible to add and administer slides via the Dashboard. Slides can be categorized and in this way you can have different sliders on your website. With the functionalities slick carousel brings, it is possible to create sliders in different ways, such as having multiple items unlike many sliders. Also, with the wide range of settings, you can customize your slider in various ways such as inifinite looping, mouse dragging, swiping, arrow key navigation etc. You can also add links to the individual slides via Add/Edit Slide interface. The slides are posts at the same time so you can use them as contents but you may have to edit your theme to view slide images. Note that this version doesn't cover all functionalities slick carousel provided but the present functionalities are very sufficent for you to create awesome sliders.

### How to use Slidy

Find the example below for inserting it directly into the template

```php
$args = array(
    'category' => 'home-page',
    'autoplay' => 'true',
    'autoplaySpeed' => '500',
    'dots' => 'true',
    'slidesToShow' => '3',
    'slidesToScroll' => '1'
);

if( function_exists( 'slidy_create' ) ){ slidy_create( $args ); }
```

Find the example below for inserting it using shortcode

    [slidy category="" title="false" autoplay="true" autoplaySpeed="500" dots="true" slideToShow="3" slideToScroll="1"]

### Options you can set for the template insert / shortcode

* category (none) - category of the slides (must be slug)
* number (5) - number of sliders to be shown
* title (true) - title of the slides
* autoplay (true) - autoplay of the slides
* autoplaySpeed (3000) - speed of the autoplay
* arrows (true) - navigation arrows
* dots (true) - navigation dots
* draggable (true) - desktop mouse dragging
* fade (false) - fade transition (only possible when slidesToShow is 1)
* infinite (true) - infinite looping of the slides
* pauseOnHover (true) - pause when hover the slides
* pauseOnDotsHover (false) - pause when hover the navigation dots
* slidesToShow (1) - number of slides to show in one time
* slidesToScroll (1) - number of slides to scroll in one time
* speed (300) - speed of the scrolling
* swipe (true) - swiping
* touchMove (true) - touch move
* touchThreshold (5) - threshold of the touch move
* useCSS (true) - CSS transitions

The plugin is written in English and has been translated into Turkish by myself. You're welcomed if you want to translate it into your language. Use translations.pot, rename it as slidy-LANGCODE.po (e.g. slidy-tr_TR) and open it in Poedit. Translate and save. There should be a MO file created by Poedit. Send PO and MO files to me, then I will add them in the next release.

Click here to visit [Slidy's Wordpress plugin page](https://wordpress.org/plugins/slidy/)!
