---
layout: post
title:  "Understanding the strange grammar of parameters in Swift?"
date:   2015-12-05 18:33:09 +0800
categories: Swift
---

# Why no external name for the first parameter?

As described in [Apple's document](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Methods.html#//apple_ref/doc/uid/TP40014097-CH15-ID236):

> Swift gives the first parameter name in a method a local parameter name by default, and gives the second and subsequent parameter names both local and external parameter names by default. This convention matches the typical naming and calling convention you will be familiar with from writing Objective-C methods, and makes for expressive method calls without the need to qualify your parameter names.
> 

it's all about *convention*, we define and call methods in Objective-c as follows:

``` objc
// declaration
- (void)registerClass:(Class)cellClass forCellReuseIdentifier:(NSString *)identifier;

// calling
[tableView registerClass:cellClass forCellReuseIdentifier:identifier];
```

So in Swift, in order to inherit this convention and keep the method name unchanged, the first parameter name has been included in method name. Therefore, we don't need to write the first parameter name twice.

``` swift
// declaration
func registerClass(_ cellClass: AnyClass?, forCellReuseIdentifier identifier: String)

// calling
registerClass(cellClass, forCellReuseIdentifier:identifier)

// since we already know that we are registering class, write Class twice is stupid as well as ugly
registerClass(class:cellClass, forCellReuseIdentifier:identifier)
```

# Why every external parameter name is required in initialization method?

In Objective-c, we declare our initialization method as follows:

``` objc
- (instancetype)initWithFahrenheit:(double)fahrenheit;
- (instancetype)initWithKelvin:(double)kelvin;
```

In Swift, as initialization method name is determined, if we don't provide parameter name, which initialization method we are calling would be confusing.

``` swift
init(fahrenheit: Double)
init(kelvin: Double)
```



