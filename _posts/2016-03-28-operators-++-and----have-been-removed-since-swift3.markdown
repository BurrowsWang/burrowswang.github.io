---
layout: post
title:  "Operators ++ and -- have been removed since Swift 3"
date:   2016-03-28 22:37:21 +0800
categories: Swift
---

When first open our projects in Xcode 7.3, probably we would encounter the following warnings:`'++' is deprecated: it will be removed in Swift 3` or `'--' is deprecated: it will be removed in Swift 3`.

[Here](https://github.com/apple/swift-evolution/blob/master/proposals/0004-remove-pre-post-inc-decrement.md) is the official explanation of why removing the operators.

### Advantages of These Operators

1. The primary advantage of these operators is their expressive capability.  They are shorthand for (e.g.) `x += 1` on a numeric type, or `x.advance()` on an iterator-like value.  When the return value is needed, the Swift `+=` operator cannot be used in-line, since (unlike C) it returns `Void`.
2. The second advantage of Swift supporting this family of operators is continuity with C, and other common languages in the extended C family (C++, Objective-C, Java, C#, Javascript, etc).People coming to Swift from these other languages may reasonably expect these operators to exist.  That said, there are also popular languages which have kept the majority of C operators but dropped these (e.g. Python).

### Disadvantages of These Operators

1. These operators increase the burden to learn Swift as a first programming language - or any other case where you don't already know these operators from a different language.
2. Their expressive advantage is minimal - `x++` is not much shorter than `x += 1`.
3. Swift already deviates from C in that the `=`, `+=` and other assignment-like operations returns `Void` (for a number of reasons).  These operators are inconsistent with that model.
4. Swift has powerful features that eliminate many of the common reasons you'd use `++i` in a C-style for loop in other languages, so these are relatively infrequently used in well-written Swift code.  These features include the `for-in` loop, ranges, `enumerate`, `map`, etc.
5. Code that actually uses the result value of these operators is often confusing and subtle to a reader/maintainer of code. They encourage "overly tricky" code which may be cute, but difficult to understand.
6. While Swift has well defined order of evaluation, any code that depended on it (like `foo(++a, a++)`) would be undesirable even if it was well-defined.
7. These operators are applicable to relatively few types: integer and floating point scalars, and iterator-like concepts. They do not apply to complex numbers, matrices, etc.  

### What we do
1. Just drop these operators entirely, both prefix and postfix.
2. Use `x += 1` or `x -= 1` instead.
3. And take care of the places where we using the return value of `++x` or `--x` carefully.
