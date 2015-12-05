---
layout: post
title: Map, Filter and Reduce
---


#Map, Filter and Reduce

What are they? They are functions that take functions as an argument. 

###Map

Map is used to transform the elements in an array or set. Say you want to multiply each element in an array by 2. How would you do this using a for-loop?

{% highlight swift%}  
for i in array  { i *= 2 }
{% endhighlight %}

This is how you would do the same using a map function on the array:

{% highlight swift%}  
array.map({\$0 * 2})
{% endhighlight %}

Now, what's the big difference here? Map evaluates the statement inside those curly braces and assigns that value to the corresponding element in the array.

###Filter

Say you want to remove all numbers below 100 from an array. How would you do this using a for loop?

{% highlight swift%}
var filteredArray: [Int] = []

for i in array {

if i >= 100 { filteredArray.append(i) }

}

{% endhighlight %}

This is how it is done using filter:

{% highlight swift%}  

array.filter({\$0 >= 100})

{% endhighlight %}

Boom! Just one line of code and done.

###Reduce


Say you want to get the mean of all elements in an array. You know how you would do it with a for loop, so I'll skip to the reduce implementation.

{%highglight swift%}

let array = [2.2, 1.2, 2.4, 5.5, 7.8]

let mean = array.reduce(0, +) / Double(array.count)

{% endhighlight %}

The first argument in the funtion is the initial element and the second argument is a function that specifies how to combine two elements. Since + is a funtion in swift we don't even need to write {% highlight swift%}  {\$0 + \$1}. {%unhighlight%}

