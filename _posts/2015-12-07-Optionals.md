---
layout: post
title: Optionals
date: 2015-12-07 23:50:00
tags: swift
---

What are they?

Optionals are variables that can have 2 states: No value and some value.

Here's an example:

{%highlight swift%}
var someVariable: Int?
{%endhighlight%}

That '?' is equivalent to saying:

{%highlight swift%}
var someVariable: Optional<Int>
{%endhighlight%}

Notice something about the above type declaration? It means that the variable is an optional *of* type `Int`. So you have to 'unwrap' them to get their actual value.

How do you 'unwrap' an Optional value? By doing this:

{%highlight swift%}
someVariable!
{%endhighlight%}

The '!' is functionally equivalent to casting the Optional<T> to T.

###Implicitly Unwrapped Optional

They are variables that can never be nil once you use them. Their value by default if none is assigned is nil. So once you use them you don't have to unwrap them with '!'.

Example:
{%highlight swift%}
var i: Int!
{%endhighlight%}

##If let, Guard and Defer

When working with optionals, your code can become error-prone. Conside this example from the documentation:

{%highlight swift%}
class Person {
    var residence: Residence?
}
 
class Residence {
    var numberOfRooms = 1
}
{%endhighlight%}

If you create a new Person instance, its residence property is default initialized to nil, by virtue of being optional. In the code below, john has a residence property value of nil:

{%highlight swift%}
let john = Person()
{%endhighlight%}

If you try to access the `numberOfRooms` property of this person’s residence, by placing an exclamation mark after residence to force the unwrapping of its value, you trigger a runtime error, because there is no residence value to unwrap:

{%highlight swift%}
let roomCount = john.residence!.numberOfRooms // Gives you a runtime error because John's residence is nil.
{%endhighlight%}

Here's where if let comes in.

###if let

Say you don't want the above example to crash. What do you do? Well, you want to check 'if' the residence is not nil, if true then do something otherwise do something else that doesn't crash because residence is nil.
{%highlight swift%}

if john.residence != nil {
  let roomCount = john.residence!.numberOfRooms
}
{%endhighlight%}

The if-let statement lets you do this in a much more compact way:

{%highlight swift%}
if let roomCount = john.residence.numberOfRooms {
  //Do Something
}
else {
  let roomCount = 0
  ///Do something
}
{%endhighlight%}

Wanna make this even more compact? Use the *nil coalescing operator* '??' and the code above becomes equivalent to this:

{%highlight swift%}
let roomCount = john.residence?.numberOfRooms ?? 0
{%endhighlight%}

Notice that now we didn't have to force unwrap john.residence.

A problem with the if-let statement is that you cannot use that the scope of `roomCount` is limited to the if statement. What do you do if you want to use it outside the if statement? This is where the guard statement comes in.

###guard

The guard statement is used to exit out of a scope if a certain condition is met which means that the code inside the guard statement is only executed if a certain condition is *not* met. Here's an example:

{%highlight swift%}
func someFunction() {

  guard let roomCount = john.residence.numberOfRooms else {return}

}
{%endhighlight%}
