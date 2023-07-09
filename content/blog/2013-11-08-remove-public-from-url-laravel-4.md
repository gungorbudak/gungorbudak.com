---
author: Güngör Budak
date: '2013-11-08T11:14:57+03:00'
slug: remove-public-from-url-laravel-4
tags:
- php
- laravel
- remove public
title: Remove public from URL Laravel 4
year: '2013'
---

Move all content of (files in) `public/` folder one level above (to the base)

Fix paths in `index.php`:

```php
require __DIR__.'/bootstrap/autoload.php';
$app = require_once __DIR__.'/bootstrap/start.php';
```

Fix path in `bootstrap/paths.php`:

```php
'public' => __DIR__.'/..',
```

Done

[Source](http://creolab.hr/2013/03/removing-the-public-segment-in-a-laravel-4-app/)
