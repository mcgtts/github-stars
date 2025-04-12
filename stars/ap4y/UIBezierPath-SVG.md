---
project: UIBezierPath-SVG
stars: 179
description: |-
    NS/UIBezierPath from SVG string
url: https://github.com/ap4y/UIBezierPath-SVG
---

SKUBezierPath+SVG
=============

`SKUBezierPath` is a `UIBezierPath`/`NSBezeierPath` class category with SVG parser. This project was previously called `UIBezierPath+SVG`, it was renamed to `SKUBezierPath+SVG` with introduction of `NSBezierPath` support, see [#5](https://github.com/ap4y/UIBezierPath-SVG/pull/5).

[<img src="https://raw.github.com/ap4y/UIBezierPath-SVG/master/photo.png" width="420px"></img>](https://raw.github.com/ap4y/UIBezierPath-SVG/master/photo.png)

[<img src="https://raw.github.com/mredig/UIBezierPath-SVG/master/macSS.png"></img>](https://raw.github.com/ap4y/UIBezierPath-SVG/master/macSS.png)

## Usage ##

    + (SKUBezierPath *)bezierPathWithSVGString:(NSString*)svgString;

Example project included with sample SVG icons (from Raphael free icons collection).

Contributors
-------

`ARC` and `NSBezierPath` support was implemented by [@mredig](https://github.com/mredig).

Alternative Projects
-------

Check [IJSVG](https://github.com/curthard89/IJSVG) (`NSBezierPath` only) if you need support for transfortmations, elements, etc.

Reference
-------

- [SVG 1.1 (Second Edition)](http://www.w3.org/TR/SVG/paths.html#PathData)
- [Raphael.js free icons](http://raphaeljs.com/icons/)

License
-------
(The MIT License)

