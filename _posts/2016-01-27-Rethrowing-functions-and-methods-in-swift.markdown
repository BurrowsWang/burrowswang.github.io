---
layout: post
title:  "Rethrowing functions and methods in Swift"
date:   2016-01-27 06:31:19 +0800
categories: Swift
---

As described in [official documentation](https://developer.apple.com/library/prerelease/ios/documentation/Swift/Conceptual/Swift_Programming_Language/Declarations.html#//apple_ref/doc/uid/TP40014097-CH34-ID531):

> A function or method can be declared with the `rethrows` keyword to indicate that it throws an error only if one of its function parameters throws an error. These functions and methods are known as *rethrowing functions* and *rethrowing methods*. Rethrowing functions and methods must have at least one throwing function parameter.

For example: 

```swift
enum SomeError: ErrorType {
    case SomeCase
}

class SomeClass {
    func someFunction(someParameter: () throws -> Int ) rethrows {
        try someParameter()
        
        //throw SomeError.SomeCase
    }
}
```

In the example above, if the function *someFunction* itself does not throw an Error, we can easily mark *someFunction* with `rethrows`, also we can declare it with `throws`. But if any Error was thrown inside *someFunction*, we can only declare it with `throws`. 

Since *someFunction* can be declared with `rethrows` as well as `throws`, what's the difference and what's the advantage of using `rethrows`? Let's look at another snippet:

```swift
class AnotherClass {
    func anotherFunction() {
        let someInstance = SomeClass()
        
        // we are passing a function of type [() -> Int] instead of [() throws -> Int]
        someInstance.someFunction {() -> Int in
            return 0
        }
    }
}
```

Here we demonstrated how to call a *rethrowing* function. In this example, we are passing a parameter of type `() -> Int` which is a subtype of `() throws -> Int`. Because no Error will be thrown in *anotherFunction* and we have declared *someFunction* as `rethrows`, no `Error Handing` code is needed here. But if we declared *someFunction* as `throws`, we have to write `try!` in front of `anotherFunction` which is obviously an extra burden.
