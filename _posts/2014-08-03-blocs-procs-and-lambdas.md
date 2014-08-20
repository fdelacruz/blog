---
layout: post
title:  "Blocks, Procs and lambdas"
date:   2014-08-03
categories: post
---
Blocks, Procs and lambdas also known as [closures](http://en.wikipedia.org/wiki/Closure_%28computer_science%29) in Computer Science are one of the most powerful aspects of Ruby, and also one of the most misunderstood. I will attempt to explains the similarities and differences.
{{ more }}

##First Up Blocs
A block is just a bit of code between do..end or {}. It's not an object on its own, but it can be passed to methods like .each or .collect.

We've seen this in action.

{% highlight ruby %}

array = [1, 2, 3, 4]
 
array.collect! do |n|
  n ** 2
end
 
puts array.inspect      # => [1, 4, 9, 16]

{% endhighlight %}

Nothing new here.

##Now Procs
A proc is a saved block we can use over and over. Just like you can give a bit of code a name and turn it into a method, you can name a block and turn it into a proc. With procs you write your code once and use it many times. That way keeping your code D.R.Y (Don't Repeat Yourself).

{% highlight ruby %}

cube = Proc.new { |x| x ** 3 }
 
[1, 2, 3].collect!(&cube)    #=>[ 1, 8, 27]
  
[4, 5, 6].map!(&cube)       #=>[64, 125, 216]

{% endhighlight %}

##Last, but not least, Lambdas
Like procs lambdas are objects. With the exception of some syntax differences, procs and lamdas are essentially the same.


{% highlight ruby %}

mbda { puts "Hello!" }
 
 #Is just about the same as
  
Proc.new { puts "Hello!" }

{% endhighlight %}

##Lambdas vs. Procs
Eventhough procs and lambdas sport stricking similarities there are two main differences.

First, lambdas check the number of arguments, while procs do not.

{% highlight ruby %}

lam = lambda { |x| puts x }    # creates a lambda that takes 1 argument
lam.call(2)                    # prints out 2
lam.call                       # ArgumentError: wrong number of arguments (0 for 1)
lam.call(1,2,3)                # ArgumentError: wrong number of arguments (3 for 1)

{% endhighlight %}

In contrast, procs don’t care if they are passed the wrong number of arguments.

{% highlight ruby %}

proc = Proc.new { |x| puts x } # creates a proc that takes 1 argument
proc.call(2)                   # prints out 2
proc.call                      # returns nil
proc.call(1,2,3)               # prints out 1 and forgets about the extra arguments

{% endhighlight %}

Second, Lambdas and procs treat the ‘return’ keyword differently.

‘return’ inside of a lambda triggers the code right outside of the lambda code

{% highlight ruby %}

def lambda_test
  lam = lambda { return }
  lam.call
  puts "Hello world"
end
 
lambda_test  # calling lambda_test prints 'Hello World'

{% endhighlight %}

‘return’ inside of a proc triggers the code outside of the method where the proc is being executed

{% highlight ruby %}

def proc_test
  proc = Proc.new { return }
  proc.call
  puts "Hello world"
end
 
proc_test  # calling proc_test prints nothing

{% endhighlight %}

##Summary Differences

1. Procs are objects, blocks are not
2. A proc is a saved block we can use over and over.
3. A lambda is just like a proc, only it cares about the number of arguments it gets and it returns to its calling method rather than returning immediately.
