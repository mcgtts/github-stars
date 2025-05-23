---
project: Sketch-Find-And-Replace
stars: 712
description: |-
    Sketch plugin to do a find and replace on text within layers
url: https://github.com/thierryc/Sketch-Find-And-Replace
---

# [Find and Replace](https://github.com/thierryc/Sketch-Find-And-Replace/) V2 for Sketch


![Find and Replace (text) for Sketch](https://raw.githubusercontent.com/thierryc/Sketch-Find-And-Replace/master/_crea/visual-v2.jpg)


[Folow me on twitter](https://twitter.com/@Autre_planete) to be posted.


##  sketch 62 and >. (version: 2.6.0)

New Shortcut : "cmd option shift f"

## How to

**Remembers your settings** - Remembers your settings for next time you do a find/replace (doesn't remember find/replace/scope as these will change each time)

## Regex new feature

Get the Regex Power ! ⚡️

### "John Smith" to "Smith John"

Find
```
(\w+)\s+(\w+)
```

Replace with
```
$2 $1
```

Result: Smith John.


#### Replace all double spaces

Find
```
\s{2,}

```

Replace with
```
(one space)

```

Follow me on twitter for more tips.

https://twitter.com/Autre_planete


## Issues or ideas

If you have any problems, or ideas, please open an issue!

### Credits and Thanks

V1 Created by [Martin Steven - @mscodemonkey](https://github.com/mscodemonkey) - Thank you Martin.

V2 Created by [Thierry Charbonnel - @thierryc](https://anotherplanet.io).

V2 Maintained and improved by [Thierry Charbonnel - @thierryc](https://anotherplanet.io).

Thanks to [Aby Nimbalkar - @abynim](https://github.com/abynim) - for the SketchPlugin-Remember code to save user settings.

Thanks to [Autre Planete - @thierryc](https://github.com/thierryc) - for writing the code to change text within symbol overrides.

Thanks to [Vincenzo Petito - @vincenzopetito](https://github.com/vincenzopetito) - for code within [Shapr](https://github.com/vincenzopetito/Shapr) showing how to focus the text field on start and tabbing between input fields found within the dialog.

Thanks to [Sean Dellis - @seandellis](https://github.com/seandellis) - for his help, test sketch doc and issues review.

Thanks to [@iconmaster](https://github.com/iconmaster) - for his test.

### Disclaimer

I take no responsibility for what you find and replace, or for any changes made unintentionally due to this software erroring. I do test it before I release it so the chances of bugs are minimised, but still, use wisely and completely at your own risk. Remember, cmd-z is your saviour.*

