---
layout: post
title:  "How to disable the startup sound of your Mac?"
date:   2015-12-12 20:09:25 +0800
categories: MacOS
---

There were thounds of answers of this question offering the following command:

``` bash
# doesn't work for me
sudo nvram SystemAudioVolume=%80
```
Unfortunately, the command doesn't work for me at all. However, when i changed the parameter %80 to **%01**, it worked perfectly fine.

``` bash
# works perfectly fine
sudo nvram SystemAudioVolume=%01
```
