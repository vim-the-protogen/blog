---
title: Functional Programming in C#
description: Reflections on functional programming in C#
tags:
    - functional-programming
    - c-sharp
    - reflection
date: 2026-05-17
---

I'm not an expert on programming languages, functional programming, or C#. However, these are some of my reflections on these subjects.

# What is functional programming?
Functional programming is both a classification for a programming language and a _style_ of programming within multi-paradigm languages.

## What is a functional programming language
A programming language can be said to be functional when it has support for first-class and higher-order functions. First-class functions is just a fancy way of saying that functions themselves can be passed around as arguments to other functions. Higher-order functions are functions that operate on other functions.

C# supports both of these, and having first-class functions is necessary for higher-order functions.

## What is a functional style of programming?
The style of functional programming is a difficult to nail down, like most matters of style. However, constructing programs by applying and composing functions together is the barrest essence of it. This is dnoe by creating trees of _expressions_ as opposed to sequences of _statements_.

There is a subset of functional programming (FP) called _purely functional programming_. This is characterized by writing programs using only _pure_ functions. A function is said to be pure when it doesn't have any side effects (modifications of state outside the lexical scope of the function) _AND_ it has the same output when given the same input.

# Why?
There are two major reasons:
- Compared to OOP langs, one can achieve all the expressive power and _more_.
- When using as pure of a style as is reasonably possible, bugs caused by global state are reduced significantly, if not completely. 

In OOP languages, one needs to make use of inheritance, class composition, encapsulation, design patterns, etc. to achieve what functional programming can achieve just by composing functions and passing around functions.

Your programs will become more terse and potentially easier to read because you're dealing with a greater levels of abstraction. Let's not worry about flipping bits, and let's worry about what matters for you and your program. Note: if you flipping bits does matter for your use case, FP may not be the choice for you.

Certain classes of bugs, particularly ones caused by things being or returning `null` can be caught _at compile time_ by using a languages _type system_. God, I wish I could explain how much relying on the type system has helped my programs have fewer bugs by letting the compiler yell at me.

A less important reason is that you can get lazy execution by storing a function in a variable and only calling it when the return value is needed.

# Why not?
- It's not the most common paradigm, though it's gaining in acceptance
- It _can_ be less performant than imperative programs. Note: for most web and desktop applications, the performance hit is _worth it_.
- Existing code bases may not be easily modified to allow for even small portions of FP.
- Your language doesn't support it. (I would say you should switch languages but YMMV)
- It's not a magic bullet

# Tools for FP in C#
Well, C# has had functional programming since C# 2.0, but it's never been as featured as F#. C# does have some handy tools to make dealing with list types more manageable with `IEnumerable<T>` and LINQ.

## Non-microsoft sources for FP in C#
LINQ, Lambadas, `delegate`s, and closures are all very nice, but C# leaves a littel bit on the table when it comes to FP. 

Enter, [C# Functional Programming Language Extensions](https://github.com/louthy/language-ext) by [Paul Louth](https://github.com/louthy). This library has been a _god send_ for me and my team. It's really the reason I'm at all proficient with FP. It adds important features like `Option<T>` (perfect for getting rid of `null` and `nullable` in your code base), `Either<L,R>` (good for conditional execution based on types), the `Bind` family of functions, and `Effect`s!

# Binding
I really want to go into [[monads]] and monadic binding for chaining operations, but I am having trouble thinking of any good examples. Many people have written good articles on the subject already, but most of them are for JavaScript or Haskell. The JavaScript ones will be more intelligible to those new to FP, but the Haskell one's are going to be more in depth and mathematical.

# Examples of my code
Recently, I was in an advanced C# course. I uploaded the labs to Github and an example of returning functions for deferred execution can be found [here](https://github.com/vim-the-protogen/advanced-cs-labs/blob/lab-7-1/Aviation/Commands.cs). In this, I was tasked with writing a little lesson on lambas, delegates, and other functional things. That can be found [here](https://github.com/vim-the-protogen/advanced-cs-labs/blob/lambdas/Lambdas/Program.cs).

# Further reading
- [C# language-ext wiki](https://github.com/louthy/language-ext/wiki)
- [Optional and alternative value monads](https://github.com/louthy/language-ext#optional-and-alternative-value-monads)
- [What are Monads?](https://moonad.net/docs/monads/)(I haven't used `Moonad` and can't recommend it because I haven't used it)
