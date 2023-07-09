---
author: Güngör Budak
date: '2013-11-11T16:24:43+03:00'
slug: base-url-for-your-laravel-4-website
tags:
- php
- laravel
- base url
title: Base URL for Your Laravel 4 Website
year: '2013'
---

To get base URL of your website to generate links to your content or assets do following:

Set `$url` in `app/config/app.php` to your base URL:

```php
'url' => 'http://localhost/example',
```

Use it everywhere with `URL::to()`, for example:

```php
echo URL::to('assets/css/general.css');
/* outputs http://localhost/example/assets/css/general.css */
```
