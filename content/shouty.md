---
permalink: "/shouty/"
layout: page
date: '2018-07-21T14:00:00+03:00'
lang: en
title: Shouty / Wordpress Shoutbox Plugin
ref: shouty
---

Shouty (shoutbox) is a Wordpress plugin for you to receive messages from your users. It creates a custom post type called "shout" which will allow you to administer shouts from the Dashboard as you do for the default post types. You can add Shouty in a post, page or a widget using its shortcode. The shortcode has certain options for you to customize the look and function of the Shouty. Shouty also creates a custom category option which can be used to create multiple shoutboxes on your website. To do that, you should first create a category, then set it in the shortcode. Shouty shares messages using AJAX and protects your blog using Honeypot spam protection technique. Users must log in to share shouts. It doesn't accept any HTML but http and https links are converted to a tags when the shout is shared. You don't have to worry about unclickable links.

### How to use Shouty

Insert the shortcode below into any post/page or widget.

    [shouty category="home-page" look="widget" user="hide" form="hide" messages_number="5" messages_title="hide" messages_users_avatar_size="60" show_more_button="hide"]

### Options you can set for the shortcode

* category (category-slug, default: empty; Filters shouts to a category)
* look (post, widget; default: post; Switches looks - widget look is more compact)
* user (show, hide; default: show; Displays user information at the top of the form)
* user_avatar_size (in px; default: 64; Changes size of the user avatar in user information)
* form (show, hide; default: show; Displays Shouty form and the share button)
* messages_title (show, hide; default: show; Displays a title at the tops of the shouts)
* messages (show, hide; default: show; Displays shouts)
* messages_number (a number; default: 10; The number of shouts to be viewed in one time)
* messages_users_avatar_size (in px; default: 32; Changes size of the user avatar on the left of the each shout)
* show_more_button (show, hide; default: show; default: 32; Displays show more button at the end of the shouts)

The plugin is written in English and has been translated into Turkish by myself. German (by [Pascal Jordin](http://www.jordin.eu/)) and Serbian (by [Ogi Djuraskovic](http://firstsiteguide.com)) translations are also available. You're welcomed if you want to translate it into your language. Use translations.pot, rename it as shouty-LANGCODE.po (e.g. shouty-tr_TR) and open it in Poedit. Translate and save. There should be a MO file created by Poedit. Send PO and MO files to me, then I will add them in the next release.

Find more information and download link on [Shouty Wordpress.org page](https://wordpress.org/plugins/shouty/)!
