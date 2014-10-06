---
layout: post
title: recursion
---

{{ page.title }}
================

<p class="meta">05 October 2014 - San Francisco, CA

Recursion is hard. Some call it a <a href="http://ruby.bastardsbook.com/chapters/recursion/">"litmus test that separates decent programmers from terrible ones."</a> Here's what you need to know to get closer to the "decent" end of programming.

####Recursion in Everyday Life</h4>
![](../images/RecursionWindow.jpeg)

If you've ever video chatted, you've probably encountered a screen similar to the one above. Your screen is displayed over and over again. Why?

It comes back to *procedure*. Given that both users are screensharing, your display is simply following that one rule. Share your screen, which shows the video chat window, in which your friend shows the video chat window, in which shows your video chat...

You get the picture? This is infinite recursion.

####Recursion in Programming: Two Principles</h4>
Infinite recursion happens in programming too, but it's of no use. When programming, we're hoping not to only repeat a **(1) procedure that repeats itself**, but to get to an end, a solution, a **(2) base case.**
In working with code, let's look at hat lengths to find the largest hat [(rocks, unfortunately has already been done).](http://ruby.bastardsbook.com/chapters/recursion/)

	hats = 10.times.map{rand(200) + 1}
	*# => [112, 189, 20, 134, 65, 165, 125, 30, 38, 178]*
	big_hat = 0

	hats.each {|hat| big_hat = hat if big_hat < hat }

Recursion doesn't need a loop. Instead, we're going to create a function and call it within itself. To do this, it helps to first think of the pseudocode. Specifically, (a) we want to take an array of values, (b1) if the array has two values or fewer, return the largest value, (b2) if there are more than two values, split the array into two arrays again...

...but then, we'd have to go through the same *procedure*. Eventually, we'll have to split this array in half, again. Should we manually split the array again with a ruby enumerable, then copy and paste the code over and over? That's not necessary. As noted in the beginning, we can call the function within the function.

	def hat_measure(hats)
		if hats.length <= 2  # the base case
			a = hats[0]
			b = hats[-1]
	    else
			a = hat_measure(hats.slice!(0,hats.length/2))
			b = hat_measure(hats)
		end

    	return a > b ? a : b
	end
	
	hat_measure(hats)
	# => 189
 
As the goal of hats_measure was to keep divide the array into smaller and smaller piles, you can see how the base case is when the array is only a length of 2.

Now that we have some clue of what recursion is, here's the thing:  real-world, programming examples are few. Loops can do the same thing as a recursive algorithm. Sometimes, loops can achieve the solution even faster. But, recursion can have its performance merits. You'll just have to test it out.