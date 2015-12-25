---
layout: post
title:  "How to make Sublime Text open new files in new tab?"
date:   2015-12-25 18:25:20 +0800
categories: MacOS
---

Open up `Sublime Text 3 > Preferences > Settings - User` or press <kbd>&#8984;</kbd> + <kbd>,</kbd> , then append the following snippet into Settings file

``` bash
# don't forget to add a comma at the end of the line above
"open_files_in_new_window": false
```
Restart Sublime Text and have a try.
