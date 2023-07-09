---
author: Güngör Budak
date: '2018-06-28T10:00:00+03:00'
slug: capture-full-size-screenshot-on-chrome-without-extension
tags:
- chrome
- screenshot
- full size
- full page screenshot
title: Capture Full Size Screenshot on Chrome without Extension
year: '2018'
---

Chrome's new Developer Tools has a way to capture high quality full size screenshot of the page so you don't have to have an extension for it anymore!

**Update for latest Chrome versions**: Chrome DevTools was slightly changed so here are the new steps (tested in Version 71.0.3578.98 (Official Build) (64-bit) on macOS).

- Open the website that you want to capture
- Use `Ctrl + Shift + J` shortcut on Windows/Linux or `Cmd + Opt + J` on Mac to open Developer Tools.
- By default, device toolbar is not visible, to toggle the device toolbar, use `Ctrl + Shift + M` shortcut on Windows/Linux or `Cmd + Shift + M` on Mac. You will see a screen similar to this:

[![Chrome device toolbar](/public/images/chrome-device-toolbar.png)](/public/images/chrome-device-toolbar.png)

- For me, the pre-selected device was `Galaxy S5` so I need to change it to `Responsive` to set a resolution for the page. Then, use `Ctrl + Shift + P` shortcut on Windows/Linux or `Cmd + Shift + P` to open commands section of DevTools and type `Capture full-size screenshot` and hit Enter when you find the command. This operation will take the screenshot and download it.

[![Full-size screenshot Chrome command](/public/images/full-size-screenshot-chrome-command.png)](/public/images/full-size-screenshot-chrome-command.png)

You will find the screenshot (in PNG format) in your `Downloads` directory.
