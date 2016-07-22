---
layout: post
title:  "First parameter in Swift"
date:   2016-07-22 19:35:02 +0800
categories: Swift
---

### Why external name of the first parameter is omitted before Swift 3.0?
Here is the explanation: [Understanding the strange grammar of parameters in Swift?](http://burrows.wang/swift/2015/12/05/understanding-strange-parameter-grammar-of-swift.html)

``` swift
// will be declared as foo(_:b:c:) before Swift 3.0
func foo(a: T, b: U, c: V)
```

### Why parameter naming rules is unified since Swift 3.0?
Here is the explanation: [Establish consistent label behavior across all parameters including first labels](https://github.com/apple/swift-evolution/blob/master/proposals/0046-first-label.md)

``` swift
// will be declared as foo(a:b:c:) since Swift 3.0
func foo(a: T, b: U, c: V)
```
