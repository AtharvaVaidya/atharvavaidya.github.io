---
layout: post
title: Optionals
---

What are they?

Optionals are variables that can have to 2 states: No value and some value.

This is from the documentation: "The type Optional<Wrapped> is an enumeration with two cases, None and Some(Wrapped), which are used to represent values that may or may not be present. Any type can be explicitly declared to be (or implicitly converted to) an optional type. If you don’t provide an initial value when you declare an optional variable or property, its value automatically defaults to nil."

Here's an example:

{%highlight swift%}
var someVariable: Int?
{%end highlight%}

That '?' is equivalent to saying:

{%highlight swift%}
var someVariable: Optional<Int>
{%end highlight%}

Notice something about the above type declaration? It means that the variable is an optional *of* type Int. So you have to 'unwrap' them to get their actual value.

How do you 'unwrap' an Optional value? By doing this:

{%highlight swift%}
someVariable!
{%end highlight%}

The '!' is functionally equivalent to casting the Optional<T> to T.

###Implicitly Unwrapped Optional

They are variables that can never be nil once you use them. Their value by default if none is assigned is nil. So once you use them you don't have to unwrap them with '!'.

Example:
{%highlight swift%}
var i: Int!
{%end highlight%}

##If let, Guard and Defer

When working with optionals, your code can become error-prone. Conside this example from the documentation:

{%highlight swift%}
class Person {
    var residence: Residence?
}
 
class Residence {
    var numberOfRooms = 1
}
{%end highlight%}

If you create a new Person instance, its residence property is default initialized to nil, by virtue of being optional. In the code below, john has a residence property value of nil:

{%highlight swift%}
let john = Person()
{%end highlight%}

If you try to access the numberOfRooms property of this person’s residence, by placing an exclamation mark after residence to force the unwrapping of its value, you trigger a runtime error, because there is no residence value to unwrap:

{%highlight swift%}
let roomCount = john.residence!.numberOfRooms // Gives you a runtime error because John's residence is nil.
{%end highlight%}

Here's where if let comes in.
###if let

Say you don't want the above example to crash. What do you do? Well, you want to check 'if' the residence is not nil, if true then do something otherwise do something else that doesn't crash because residence is nil.
{%highlight swift%}

if john.residence != nil {
  let roomCount = john.residence!.numberOfRooms
}
{%end highlight%}

The if-let statement lets you do this in a much more compact way:

{%highlight swift%}
if let roomCount = john.residence.numberOfRooms {
  //Do Something
}
else {
  let roomCount = 0
  ///Do something
}
{%end highlight%}

Wanna make this even more compact? Use the nil coalescing operator'??' operator and the code above becomes equivalent to this:

{%highlight swift%}
let roomCount = john.residence?.numberOfRooms ?? 0
{%end highlight%}

Notice that now we didn't have to force unwrap john.residence.

A problem with the if-let statement is that you cannot use that the scope of roomCount is limited to the if statement. What do you do if you want to use it outside the if statement? This is where the guard statement comes in.

###guard

The guard statement is used to exit out of a scope if a certain cond
