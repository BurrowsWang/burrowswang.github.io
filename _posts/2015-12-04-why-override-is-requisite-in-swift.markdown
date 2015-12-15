---
layout: post
title:  "Why the keyword override is requisite in Swift?"
date:   2015-12-04 21:52:04 +0800
categories: Swift
---

Here is the description in [Apple's document](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Inheritance.html#//apple_ref/doc/uid/TP40014097-CH17-ID196):

> To override a characteristic that would otherwise be inherited, you prefix your overriding definition with the override keyword. Doing so clarifies that you intend to provide an override and have not provided a matching definition by mistake. Overriding by accident can cause unexpected behavior, and any overrides without the override keyword are diagnosed as an error when your code is compiled.
> 
> The override keyword also prompts the Swift compiler to check that your overriding class’s superclass (or one of its parents) has a declaration that matches the one you provided for the override. This check ensures that your overriding definition is correct.
>

As I see, two purpose:

1. Avoid providing a matching definition by mistake.
2. Make sure the method name or property name or other declaration is exactly the same as super class's.
