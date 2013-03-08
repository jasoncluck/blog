---
layout: post
title: "Ruby: Using splats with functions"
date: 2013-03-08 01:05
comments: true
categories: Ruby Rails Splats
---

Splats in Ruby can make your life easier.  The first example of this is to use a splat (asterisk in Ruby) to pass in an entire list to a function. Keep in mind that in Ruby a list can be pretty much anything.

``` ruby asteriskExample.rb
def convert_to_list(*list)
	puts list.inspect
	#output["1", "a", "2", "b", ["foo", "bar", "1"], "alice", "bob"]
end
convert_to_list('1', 'a', '2', 'b', ['foo', 'bar', '1'], 'alice', 'bob')
```


<!--more-->


This can also be paired with Rails methods, such as extract_options!, to make some interesting functions.  This one takes in a list and extracts the last hash that's passed in.  Othewise an empty hash is returned.  This could be utilized when passing params from the view to the controller. Notice the bang indicates that we are removing the hash entry from the passed in list.  This example also shows a splat splits up the remaining list arguments if there is some parameter before it such as first_num in this case.

``` ruby hashExample.rb
def get_options(first_num, *args)
	puts first_num.inspect 	# => "1"
	args.extract_options!	# => {:a=>:x}
end
get_options('1', 'a', '2', :a => :x, :b => :y)
```

If we were to switch out the ordering of first_num and *args we could replicate the behavior of extract_options.  Splats can also be used to call a function with each item in a list.

``` ruby splatArgument.rb
animals = ["cats", "dogs", "werewolves"]
my_function(*animals)
```

Lastly, a double splat (**) can be used to capture every keyword argument.  From what I've seen in Ruby 2.0.0 these are used for the last argument to capture all of the keywords if a default is not specified.  I'll talk more about this is later posts since I just upgraded to 2.0.0 myself.