---
author: Güngör Budak
date: '2015-09-16T14:09:00.002+03:00'
slug: generating-2d-svg-images-of-mol-files
tags:
- rdkit
- transparent background
- mol to svg
- svg
title: Generating 2D SVG Images of MOL Files using RDKit Transparent Background
year: '2015'
---

The latest release of RDKit (2015-03) can generate SVG images with several lines of codes but by default the generated SVG image has a white background. The investigations on sources didn't solve my problem as I couldn't find any option for setting background to transparent background.

![RDKit Logo](/public/images/rdkit-logo.png)

An example of SVG image generation can be found on <a href="http://rdkit.blogspot.com.tr/2015/02/new-drawing-code.html" target="_blank">RDKit blog post called New Drawing Code</a>.

In [3] shows the SVG image generation and it returns the SVG file content in XML. When you open this file in a text editor, you'll see there is a rect element with a style attribute having fill `#ffffff` which is white. If you make this none, the whole SVG background becomes transparent.

So, if you obtain the SVG file content as XML from using moltosvg function in the blog post, just use the following function to make its background transparent.

```python
import xml.etree.ElementTree as ET


def transparentsvg(svg):
    # Make the white background transparent
    tree = ET.fromstring(svg)
    rect = tree.find('rect')
    rect.set('style', rect.get('style').replace('#ffffff', 'none'))
    # Recover some missing attributes for correct browser rendering
    tree.set('version', '1.1')
    tree.set('xmlns', 'http://www.w3.org/2000/svg')
    tree.set('xmlns:rdkit', 'http://www.rdkit.org/xml')
    tree.set('xmlns:xlink', 'http://www.w3.org/1999/xlink')
    return '<?xml version="1.0" encoding="UTF-8"?>' + ET.tostring(tree).strip()
```

You can write this to an SVG file easily;

```python
svg = transparentsvg(svg)
with open('path/to/svg/file', 'w') as f:
    f.write(svg)
```
