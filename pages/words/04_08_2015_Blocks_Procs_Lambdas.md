#blocks, Procs, and lambdas

This is a post I should've written a year ago. *Should've* because I keep forgetting the differences between blocks, Procs, and lambdas.

#1. Yielding Blocks
`yield` invokes a block. Simply put from [TutorialsPoint](http://www.tutorialspoint.com/ruby/ruby_blocks.htm):

	def test
		yield 5
		puts "You are in the method test"
		yield 10
	end	
	
	test { |num| puts "You are in the block #{num}" }

This will produce: 

	You are in the block 5
	You are in the method test
	You are in the block 100

###Yielding more than one variable

You can create a block to take in two parameters, like so:

	def test
		yield 5, 10
		puts "You are in the method test"		
		yield 100, 200	
	end
	
	test { | a, b | puts "You are in block #{a}-#{b}" }	
This produces:
	
	You are in block 5-10
	You are in method test
	You are in block 100-200

###Yielding with no variables

Of course, you can yield with no variables at all:

	def test
		yield
	end
	
	test { puts "You are in the block" }
	#=> "You are in block"
	
#2. Another Way To Call Blocks
You can pass a block by using `&` as a preceding character:

	def test(&code)
		code.call
	end
	
	test { puts "Hello World"}
	#=> "Hello World"	
	
By using the `&`, you can call the block like this:

	def test(n, &code)
		n + code.call
	end
	
	test(3) { 4 + 5 }
	#=> 12So now, you can write your own enumerables:

	class Array
		def iterate!(&code)
			self.each_with_index do | n, i |
				self[i] = code.call(n)
			end
		end
		
	array = [1,2,3,4]
	array.iterate! { |num| num ** 2 }
		
	#=> array == [1, 4, 9, 16]
#3. Blocks are Procs. Procs do way more.

If you look into what the block actually is, you can see that a block is a Proc! (A Proc is *capitalized* because it is an actual class)

	def what_am_i?(&code)
		code.class
	end
	
	what_am_i? {}
	#=> Proc < Object	
###What are Procs?

Procs are anonymous functions that can (1) be placed inside a variable and (2) as such, they can be passed around and reused. 

	def multiply_2(num, proc)
		proc.call(num)
	end
	
	two = Proc.new { |number| number * 2 }
		
	multiply_2(5, two)
	#=> 10 
	
###Procs: You can use more than one!

Unlike with blocks, you can pass multiple Procs to a method.

	def callbacks(procs)
	  procs[:starting].call
	
	  puts "Still going"

	  procs[:finishing].call
	end

	callbacks(:starting => Proc.new { puts "Starting" },
          :finishing => Proc.new { puts "Finishing" })
          
#4. Lambdas

Lambdas are also Procs. The difference is a lambda checks the number of arguments passed to it, and will throw an *ArgumentError* if necessary.

	def args(code)
	  one, two = 1, 2
	  code.call(one, two)
	end

	args(Proc.new{|a, b, c| puts "Give me a #{a} and a #{b} and a #{c.class}"})

	args(lambda{|a, b, c| puts "Give me a #{a} and a #{b} and a #{c.class}"})


#Thanks!
See more at [Reative.io](http://www.reactive.io/tips/2008/12/21/understanding-ruby-blocks-procs-and-lambdas/).
