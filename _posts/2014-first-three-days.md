#Sunday - 10/5

#####Personally...
I'm ambivalent about the whole DBC experience. Had I gone to DBC from the start of my education, I think the DBC experience would be worth the time and effort. However, now that I've spent almost a year teaching myself (since Jan. 2014) and now that I feel comfortable with self-teaching myself, I think I could teach myself all I need to know to get a job.

So why am I still going through with DBC? Because I have little time to waste, which means that I still don't have complete faith in my abilities. 

In 9 weeks, I am guaranteed some level of competency. Even if 50% of the material is repetitive for me, I figure I still can learn something. 

Whereas, if I spend 9 weeks by myself, it's doubtful I'll learn *exactly* what I need to know to get a job as a full-stack engineer. 



#Monday - 10/6
#Encoding, Decoding, and Pairing

Today's Highlight:  Multiple Pairings in A Day

Today, we paired. A LOT. In three hours, we rotated through three different pairing partners. It was frustrating because it wasn't enough time to acclimate and actually learn the answer to *any* of the coding challenges.

Our teacher, Sherif, says coding wasn't the point. Instead, we needed to focus on the experience.

I can see how people really like DBC. The instructors really are uplifting and do believe in the DBC philosophy of teaching people to become "Olympic learners". Apparently, programming is easy; learning ruby is an afterthought. Our teacher, Sherif says DBC is not about programming, it's an afterthought of what we do. What we're supposed to be doing is become Olympic Learners. So their job is to push us to the limits of what we thought possible.

We learned that to support us, we'll have access to supportive coaches, meetings, yoga, and life coaching.

#####**Reservations**
These are all great. But for me, after four months of hell. Not just caulking, grouting, and landscaping the house in silence for up to 8 hours in the blazing, humid Virginia summer, but also *learning how to caulk, grout, and landscape.* Suffice it to say, I've already passed the initial shock of anything "surprising" in Life.

At times, I like to remind myself:  I have a date with eternity. And so, if I am already living in an endless experience - what's there to stress about? Eternity is here and now? And, eternity could end any moment.

If I already understand this, then what's the point of going through DBC? I don't have *that* much stress to manage. If I'm already interested in learning how to learn and am optimizing on that, then programming for me is already an afterthought.

I'm still not sure if I like Dev Bootcamp, but I know that I'm still going to stick through. Unfortunately, to gain something, I recognize I have to undergo pain. After this summer, I've decided that I would take on pain. It may be painful to stay at Dev Bootcamp, but I hope to at least get a "good"" grounding in practical programming.


#Tuesday - 10/7
#Encoding, Sorting, and Searching

Today's Highlight: Pairing with One Person All Day

#####Personally...
I emailed the Mixpanel recruiter from two months ago. Just realized that I hadn't actually sent him a reply. In any case, I'm kind of fed up. So far, we've been coding up Ruby challenges that I find repetitive. By no means are they easy, but they're challenges that I could've figured out by myself, searching StackOverflow and GitHub.

Moreover, there are so many activities embedded within DBC -- lectures, yoga, empathy sessions -- that I think detract from getting really good. 

1. I already have friends that I can ask for help. They're not as readily available as DBC coaches, but they sure cost A LOT less.
2. I already do Tai Chi, which is personally more fulfilling than Yoga. Though I do like Yoga once in a blue moon, it detracts from my road to mastering Tai Chi.
3. Empathy sessions are important, but like things worthy of learning:  They can't be taught in a several lectures or meetings. People have to care deeply and be willing to get hurt for some greater purpose.

#Wednesday - 10/8
#Data Structures

Today's Highlight:  First Solo Wednesday

I'm surprised at the pace and the energy of DBC. I still have reservations about the program. While they like to say that DBC invites people to take responsibility for their education, I have to say that this is only a consequence (or confluence) of *personal* situations:  People come to DBC with a more fully fleshed out purpose than do kids attending college.

I would argue that the quality of the instruction and the lectures themselves aren't that deep or theory based. Not that they should be; DBC is a technical school. However, I would think that $12k would pay for a higher standard of understanding.

That said, after our first solo day today, I guess it is worth paying $12k for some quality control on my DBC peers. Working with fellow peers (no matter their level of their programming experience) so far is great - surprising. Despite coding in complete focus for 10+ hours a day (not counting lecture time). I'm not as tired as I figured I would be. 

Perhaps it's that I'm more mature after going through 4 months of family troubles. But perhaps its because I am feeding off the nervous and excited energy of the other students. 

On another note, I took a call from a recruiter at Mixpanel. Apparently, listing myself as "Web Developer" despite not having any polished programming projects does work. Moreover, I seems to illustrate that the level of competency needed to get an (support) engineering job is very low; that or going to Brown did help in getting a job. Probably a bit of both. 

I wonder if I instead spent 9 weeks learning what I wanted to learn, I could get the same job coming out of DBC. A couple of the coaches are and had worked as a support or solutions engineer before moving onward.

In any case, I'm not going to quit. Spent way too much money already. Opposite the theory of economics, I'm going the zen approach:  I said I would do it, so I just have to really **fucking** do it. I have to push myself much more -- I'm going to get an engineering-focused engineering job.

To that end, I'm toying with the idea of working with Tim on the weekends. I can't wait to touch a real product and learn some Backbone.js.

###Data Structures Notes

-	**Stack**:  Is like a stack of plates. Data goes on top of each other. To get the data off, you have to take from the top of the plate pile. In essence, that means you `#push` values and `#pop` values from the array
-	**Queue**:  Is basically a waiting line -- literally a line that you wait in. People come into the line, and the *first ones in* are the are also the *first ones out*. In an array queue, that means you `#unshift` data into the queue and `#pop` that data out.
-	**Linked Lists**:  Is like people waiting in line, but with invisible strings attached to each other. When the second person is placed into the line, he is automatically attached to the first person; the second person can't help but follow the first person. It is through these invisible ties or *links* that a link list is created. Linked lists can be arrays (`[val, [val,[val,nil]]]`), hashes (``), etc. (I don't know what the etc. might be.)

**In working with hashes, remember a few things:**

1.	As of Ruby v2.0, hashes are unordered. To access and retrieve information from a hash, you have to convert the hash to an array (`#to_a`).
2.	When turning an array into a hash, try to find a the nested array that will be the hash keys. Then, define the rest of the nested array as hash values. From there, you can `keys.zip(values)`. 

**In working with regular expressions:**

-	To substitute several parts of an expression, bunch the Regex with parentheses `()` and use a `#gsub`; second argument should have a `\1` up to the last number `\n`. So, to ensure that the following SSN have a dash in-between
	
	SSN: 480.01.4430, 480014430, 480-01-4430
	string.gsub(/(\d{3})[\D]?(\d{2})[\s\W]?(\d{4})/, '\1-\2-\3')

-	For optional Regex values, use a `?` after the value.
-	For either or Regex values, use `[]`. Hence, the above code looks for `\s` OR `\W`.

#Thursday - 10/9:  
#Part 1: Test-Driven Development:  An Example

Today's Highlight:  Slow Down and Program Faster with TDD

Great code doesn't come from omniscient programmers -- ones who seem to be able to code programs in 1-10 lines that's fully extensible to all use cases. Great code comes from keeping things simple. From simplicity comes great code. 

Today, Dev Bootcamp teacher Miles talked to us about the importance of designing (architecting?) a program. Each method and variable must be properly named -- essentially, you ***want*** to spend significant upfront energy and time (probably 60% of your coding time) to get to the philosophical underpinnings of what you're coding.

For example, to create a method that will calculate change for a dollar, we want something pithy like `make_change`.

	def make_change(cents)
		change = {}	
	end	

Moreover, we know that we will want to return the `change`. And, we want to be able to return the change and have it readable by calling for : `:quarters`, `:dimes`, `:nickels`, and `:pennies`. 

Next, in writing the `make_change` method's inner operations, we want to make sure we're actually writing usable code. That's why we need to use tests.
	
	def test(expected, actual)
	  passed = actual == expected
	  unless passed
	    p expected
	    p actual
	    raise "Test failed"
	  end
	end
	
	test({}, make_change(0)) 
	test({:pennies => 1}, make_change(1))

In trying to make the first test pass, what code would you write? All you need to do is return an empty hash. 

What code would make the second test pass?

	def make_change(cents)
	  change = {}
	  if cents >= 1
	    change[:pennies] = cents      
	  end
	  change
	end

Next, our test ask for:

	test({:nickels => 1}, make_change(5))
	test({:nickels => 1, :pennies => 1}, make_change(6))

Our code thus becomes:

	def make_change(cents)
	  change = {}
	  if cents >= 5
	    change[:nickels] = cents % 5
	    cents = cents % 5
	  end
	  if cents >= 1
	    change[:pennies] = cents   
	  end
	  change
	end

As we can see, we more or less the same loop. If we were to extend the code to handle cases for `:quarters` and `:dimes`, the same four lines would occur again and again. Just write it out to see. 

Seriously, write it out.

***Only after all your tests pass can you refactor the code. Refactoring code that doesn't pass all the tests is to refactor broken code.*** Finally, we arrive at the "genius-level" code:

	def make_change(cents)
	COIN_VALUES = {:quarter => 25, :dimes => 10, :nickels => 5, :pennies => 1}  
	change = {}
	  COIN_VALUES.each do |coin, value|
	    if cents >= value
	      change[coin] = cents / value
	      cents = cents % value
	    end
	  end
	  change
	end	

#Personally...
I'm warming up to Dev Bootcamp.

#Thursday - 10/8:  
#Part 2: When To Make Variables `private`

Today's Highlight:  Instance Variables are *Automatically* private to a Class.

If, say, a `BankAccount` class were a circle, how would other classes (or actual people) access information (move back and forth through the circle boundaries) and possibly manipulate information inside that `BankAccount`? Well, that's what accessor methods are for. Think `attr_reader`, `attr_writer`, `attr_accessor`.

However, what happens if you want to make the information ***inaccessible*** to any object outside of the class? You could declare `private` like so:

	class BankAccount
	private
	attr_reader :acct_number  ### see here
	
	public
	attr_accessor :type, :customer_name

	  
	  def initialize(customer_name, type, acct_number)
	    @customer_name = customer_name
	    @type = type
	    @acct_number = acct_number
	  end

	   ...
	end

However, this is unnecessary and tedious for most programs. Generally, you can leave the `attr_reader :acct_number` out entirely. Instead, use the instance variable denoted with `@` so that the instance methods can access the variable within the class.

	class BankAccount
	  attr_accessor :type, :customer_name

	  def initialize(customer_name, type, acct_number)
	    @customer_name = customer_name
	    @type = type
	    @acct_number = acct_number
	  end

	  def to_s
	    "My account information is #{@customer_name}: #{@type} #{masked_account}"
	  end

	  def masked_account
	    ### see here 
	    @acct_number.gsub(/(\d{3}\W?\d{2})(\d)\W?(\d+)/, '*****\2\3')
	  end
	end

**Thanks to Brick Thorton who taught Yash and me this.**

#Personally...

I'm liking Dev Bootcamp more and more. 


#Friday - 10/8
#Programming Sudoku (with Sudocode)

Today, my pair Kiope and I doubled down on *going slow* with Pseudocode and Test-Driven Development. 

It took us almost two hours to write a full draft of Pseudocode with properly named methods and variables, but pseudo-coding was a huge boon to communication. We still had hiccups - points where we weren't on the same page, but, overall we were. And we moved a lot faster through coding than had we not pseudo-coded.

Moreover, TDD made it feel like we were in control. Instead of coding up a monster method, TDD forced us to breakdown our method into the smallest component parts. Not only were the methods then easier to debug, but TDD helped us get into a state of *flow* -- and avoid a state of frustration.

#Friday - 10/8:  
#Recursion
Today's Highlight:  Recursion is a like a Escher Staircase -- just with a "Stop Sign"

Usually, when recursion is taught, math and/or code is used. Today, Sherif showed us the best visual image for what recursion is. But before we get to that, let's look at some code.

	def do_it(counter)
	  puts "on the way down, #{counter += 1}"
	  return counter if counter > 3              # you can return from the base case
	  counter = do_it(counter) - 1               # and use that value
	  puts "on the way up at level #{counter}"
	  counter                                    # but line 151 now expects a return value!
	end

As described in the [Little Bastard's Book of Ruby](ruby.bastardsbook.com/chapters/recursion/), for recursion to work, we need a (1) a procedure and (2) a base case.

While it can be difficult to wrap your head around recursion, here's what you need to know:  Have the program do the same thing until the base case says "STOP."

As the sample output illustrates, recursion is like going down a set of stairs.

	# on the way down, 1
	# on the way down, 2
	# on the way down, 3
	# on the way down, 4
	# on the way up at level 3
	# on the way up at level 2
	# on the way up at level 1

You do one thing on the way down four times. Then, you hit the base case which tells the procedure to STOP. Next, we run the rest of the procedure (if any other code exists); in this case, we go back on the way up.

INSERT IMAGE

#####Personally...
After the first week, is Dev Bootcamp worth $12k? 

I'm still not sure. But, the value of Dev Bootcamp is up there. While the teachers don't seem to help *that much* during the coding challenges. It's not like they should. All of us students must figure out coding for ourselves and with each other (through pairing). I think the teachers do just enough and come in at just the right points to make sure that we are learning and not just refactoring or reading random blogs.

Moreover, I think Dev Bootcamp has done a fairly good job with coordination -- making sure fellow students are driven to be here.

The verdict is still out on Dev Bootcamp is out. My guess is that it's worth it, but I'll have to wait and see to believe.


#Monday - 10/13:  
#Part 1:  Inheritance vs. Composition

Today's Highlight: Composition over Inheritance?

Chances are you've heard of Inheritance, but what of Composition? What is it? Why do programmers often say "composition over inheritance"? (Dev Bootcamp makes no opinion on one or the other.)

To put it simply:
1) Composition is used when you can say an object "has-a" relationship. 

Take for example, that you want to build a mountain bike. You think about it real hard, and you realize you can use Composition. So, the only classes you create are `Bicycle` and `Parts`. And to build the mountain bike, we'll build `mountain_parts`. Then, call the `mountain_parts` into a new instance of `Bicycle` called ``mountain_bike`. For more information, the driver test code might look like this:

	mountain_parts = Parts.new({wheel_size:29, tire_type:"Big", rear_sus: "lots"})
	mountain_bike= Bicycle.new(15, mtnbikeparts)

Inheritance is used when you can say an object "is-a" relationship. With inheritance, we might create a `MountainParts` and `MountainBike` class that `<` from their relative superclasses `Parts` and `Bicycle`, respectively.

However, if we were to do that, then every time we changed the `Bicycle` class, we might have to change the inside code of `MountainBike`. Using composition, we can ensure that `mountain_bike` always has features that are up-to-date with `Bicycle`.

#####Personally...
I don't recommend taking the weekend off or working on side projects during Dev Bootcamp. Everyone is there for a reason, and taking, probably, more than a day off is too long -- my newfound knowledge will probably fade away. I need to keep the momentum moving throughout these 9 weeks.

More than that, I need time to recharge.

Dev Bootcamp is what I make of it. So, I need to put in more hours to stretch myself.

#Monday - 10/13:  
#Part 2:  Reading/Writing Files

Today's Highlight:  Reading/Writing Files with a "Castle"

Dev Bootcamp Coach Alex gave me an almost perfect example of how to decode the little letters like `r`, `r+`, `w`, `w+`, `a`, `a+`...

You might find this code in lines like this:
	File.open("some_file.csv", "w+") do |file|
	   file.write(some_file.to_yaml)
	end

Think for a second that you're an Army captain. Today, you want to *add a few soldiers* (or "write") to the castle's infantry ("the file"). 

Unfortunately, you're a low-level captain (`r`). So, you can only list off the names of the soldiers already inside the castle. And, you have to start at the beginning of the morning drill line.

Now, you're an `r+` captain. So, you can add a new soldier and *even* change (write over) any soldier's name at will. The only thing is you're still an `r`, so you have to start from the beginning of the line -- even if you just want to add the new soldier to the end of the line.

(A few more important ones..)

As a `w+` captain, you can change the name of any soldier. But, if the physical castle doesn't exist, you first create the castle (the file), *then* put your soldiers inside, and *then* start changing names.

As a `a+` captain, you start *at the end of the file*. If the castle doesn't exist, you create it. Then, you can start adding soldiers to the end of the line.

#Tuesday - 10/14:  
#MegaMoths

Today's Highlight:  Paring Down MegaMoths

Simply put, any method that seems to go on *forever*; like, if it has 10+ lines of code with array indices or hash calls, then you probably want to simply the method into many methods.

If you still want the methods to run seamlessly, well, there's no hurt in creating an `#execute` method that calls all the method you want to run at once.

Today's Highlight:  MetaProgramming

Until today, I didn't understand why Ruby is *better* in some ways to other languages, like Java.

The short answer (from our teacher Sherif) is that you can *metaprogramming*.

Take for example this situation. You want to create cookies and then be able to batch the cookies into different groups. You could write the classes with Inheritance or Composition. However, there's a far simpler way to do this.

First, we can just create a `Cookie` class and initialize any cookie to be any type with `instance_variable_set` like so:

	class Cookie
	   def initialize(cookies_param = {})
		cookies_param.each do |k, v|
			instance_variable_set("@#{k}", v)
		end
	   end
	end

Don't believe me? Just run this code yourself:

	ingredients = %i[sugar flour eggs milk]
	flavors = %i[peanuts chocolate sprinkles]

	cookies = Array.new(10) do
	  Cookie.new(ingredients: ingredients, flavors: flavors.sample(1), cooking_time: rand(10..20))
	end
That's great and all. But, one thing we would like is to batch our cookies into different flavors. Y'know, some people have peanut allergies, so let's separate them.

Now, I could create a `#batch_cookies` method, but that's inflexible. With `#method_missing`, we can automatically batch the cookies without writing out the full method.

	class Cookie
	  ...
	  def method_missing(args)
	    flavors = args[0..-2].to_sym #:milk
	    @flavors.include? flavors
	  end
	  
	cookies.select(&:peanuts?)
	#=> [#<Cookie:0x007fabe3118190 @ingredients=[:sugar, :flour, :eggs, :milk], @flavors=[:peanuts], @cooking_time=13>, 
	#<Cookie:0x007fabe390bf50 @ingredients=[:sugar, :flour, :eggs, :milk], @flavors=[:peanuts], @cooking_time=16>, 
	#<Cookie:0x007fabe390b410 @ingredients=[:sugar, :flour, :eggs, :milk], @flavors=[:peanuts], @cooking_time=18>]

As you can see, we're looking for cookies return `true` for `#peanuts?`. But instead of actually creating the `#peanuts?` method, we ask `#method_missing` to find any missing methods and run the block of code shown. Here, the `#include?` statement essentially acts as the `#peanuts?`.

#####Personally...
I'm really tired. Maybe I'm sick. I'm not getting enough sleep. But, more than anything else, I feel like I'm behind. That I should be farther in the challenges and in my learning.

Once again, there's nothing I can do besides continuing to work on the process:  Manage my sleeping, what I eat, who I spend my time with. I have no more time anymore and to grasp the opportunities at Dev Bootcamp I need to optimize my learning. That means reading books and redoing the *important* challenges.

Of course, I shouldn't push myself too hard. Everyone comes to DBC with similar feelings.

In Engineering Empathy, we learned to deal with our Super Egos -- the part of your brain that seemingly criticizes every action you make. Or, in other words, it's that nagging voice in your head that you are too old, too young, too fat, too stupid, and too whatever to be great at anything and everything.

At first, this all seems like pretty simple stuff. Learn to deal with yourself. However, when you're in a competitive atmosphere like Dev Bootcamp, the reality is that you can't help but compare. For example, to say that you are behind is to acknowledge that there is a comparison going on. 

However, it's often the simplest things that are hardest to overcome.

When we finally connected to each other today, I learned that more than one person I thought was "smart" felt like they were 'too slow'. It's small bit of solace, but it's solace nonetheless. Now, I can take whatever energy was boxed up worrying and put it towards becoming better.

I can't wait for the weekend to get some rest/extra work done. I really need a break.

Talking with Sefora, the Dev Bootcamp Life Coach, was helpful. After telling her my whole story for the past year, I came to my own realization that I need a break for myself. Since my dad passed away in April, I've had little time to really think about anything except execution:  Fix the lawn, Call my dad's retirement accounts, Teach mom how to manage her finances, Remodel the bathrooms, and now Learn programming. So many tactical...tasks...really does burn one's energy. It leaves no time for big thought, revelations. 


Questions:  What is Duck Typing?

#Wednesday - 10/15:  
#MVC

Today's Highlight:  MVC is Simpler Than You Think

Don't you hate it when you have a 200-300 line program, all running in the same ruby file? Don't you *especially* hate mega-classes that seem to do everything -- from interacting with the database, structuring and modifying the data, and presenting that data in a readable format in terminal?

All in all, it's a lot to manage. And because it is so complex, there's a likelihood that things will break in the future. Whether you need to add a new method to splice the data or just want to print out a new message to the console, relying on 250 lines of code to work perfectly as a whole is a bad idea.

With MVC, we can *separate the concerns* into:
1) Models:  Or, the Classes that interact with and store the information from the Databases
2) Views:  Or, the `puts` and `print` statements that the user can physically see and interact with.
3) Controller:  Or, the "middle manager" methods that take commands from the Views and sends it to the Models, and vice versa.

As the Model is essentially the guts of the program that I'm sure you're familiar with, I'll only show the View and Controller.

Here's the View:

	class View

	  def self.display(list)
	    puts "------CURRENT LIST--------"
	    list.flatten.each_with_index do |task, index|
	      puts "#{index+1}. " + task.to_s
	    end
	  end

	  def self.appended(new_task)
	    puts "Appended #{new_task} to your TODOs..."
	  end

	  def self.deleted(new_task)
	    puts "Deleted #{new_task} to your TODOs..."
	  end

	  def self.completed(new_task)
	    puts "Completed #{new_task} to your TODOs..."
	  end
	end
	
In the view, you get what you can see - literally. It may interact with the `List` model like in `#self.display`, but the key here is that the View actually doesn't need to know anything about the model. `list` (lowercase) is just a parameter. Looking below at the controller, the View should make more sense.

	class ListManager

	  def initialize
	    @my_list = List.new
	  end

	  def run
	    View.display(@my_list.task_list)
	    command = ARGV[0]
	    new_task = ARGV[1..-1].join(" ")
	    task_id = ARGV[1].to_i
	    case command
	    when "list"
	      View.display(@my_list.task_list)
	    when "add"
	      View.appended(new_task)
	      @my_list.add_task(new_task)
	      @my_list.display_all
	    when "delete"
	      View.deleted(new_task)
	      @my_list.delete_task(task_id)
	      View.display(@my_list.task_list)
	    when "completed"
	      View.completed(new_task)
	      @my_list.completed_task(task_id)
	      View.display(@my_list.task_list)
	    end
	  end
	end
	
Now, I admit that the variable and method names are not well-defined. So, it's probably hard to read this code. But if you stick it out, you'll notice that you call the View using class methods (hence the `self.` names in the View). 

More importantly, the `ListManager` controller illustrates an important point. Since it is the thing that calls creates an instance of a model `@my_list`, the controller is also the class that calls all the methods of the model. (Read that again)

By separating the concerns of the program into MVC, we have simplified the our program execution to two lines:

	my_manager = ListManager.new
	my_manager.run
	
#####Personally...
I'm proud of myself today. As Wednesdays are "solo days", I decided to test myself by creating this program on my own. At first, I thought I'd probably give up and work with someone else (I even asked two people ahead of time). But, I didn't need to. More importantly, at no point was I panicking. All thanks to focusing on the Test-Driven Development process.

Instead of trying to build the whole ToDo list program out of my head. I instead try to build upon small wins. First, I wrote down the methods as if I were to execute them. Then, I would run the method -- even before typing anything inside of them. 

By *purposely* failing first, I felt a sense of accomplishment which helped me forge onward as I wrote the method, tested it again, and failed until I succeeded. I want ***you*** to understand this:  <u>The philosophy of programming is to succeed by failing a lot and in little places.</u>

While I started out slow, I found myself not at all behind. I had plenty of time to help my other cohort mates.


#Thursday - 10/16:  
#Databases

Today's Highlight:  One Table to Rule The World

My pair Tom and I were given the problem to model the database for a family tree. Here were the requirements:

1. 	People have a first name, middle name, birth (last) name, legal (last) name, gender, and birth date

2. 	Come up with a way to relate people. You should be storing the data in a way that permits constructing a family tree, and also answering questions about a family tree, e.g., "Who is this person's parents?", "Who are Steve's paternal ancestors?", "Who are Dora's descendants?", "Who are Steve's cousins?", "Who are Lila's granddaughters?", etc.

The answer? It's just one table called `Persons`. A person has all the usual attributes `name`, `birthday`, and so on. But, the person also has a mom and a dad. So...the person should have a `mom_id` and `dad_id` that map to a different person on the list.

To get the mom and dad of a particular person, you would query something *like* (not 100% sure here): 

	SELECT *
	FROM persons
	WHERE mom_id = id and dad_id = id
	
That's it!

#####Personally...
Sherif tries to make Thursday a day of decompression. And, boy was a breather needed. I woke up late today. To compound that stress, all the tension in my body from sitting and even standing while coding is going straight to my stomach. Maybe it's because my back and shoulders are so tight that now the stress is working it's way to my stomach.

It's days like today that I appreciate that Dev Bootcamp provides free yoga. It was as if the instructor was reading my mind -- we stretched our psoas and massaged our backs with a cushy, rubber ball. 

Moreover, I appreciate that Sherif planned out this Thursday as more of a talking day. Tom and I designed databases on a white board. We actually only spent about an hour or so coding up a database -- just enough to get a practical understanding of the topic.

#Friday - 10/16:  
#MVC w/Groups

Today's Highlight:  Working With Groups is Tough

Technically, there wasn't much to deal with today. We built a flashcards game in the command line in an MVC type format.


#####Personally...
I think we should have stubbed the whole project. Had we given each person something to work on, rather than worrying about pairing on different parts (so 4 groups of 1, rather than 2 groups of 2), we would have finished a lot quicker.

However, that was impossible because communication was crucial. While we spent the time needed to (1) talk about the problem, (2) pseudocode by figuring out our (2a) nouns or classes and (2b) our verbs or methods, failed to be EXPLICITLY clear about the input and output. 

Of course, we said, we want to return a value. However, had we simply wrote out exactly what we were looking to output - be that as hash of keys or and array of objects (ex: `{term: "yolo", definition: "you only live once"}`), then our brainstorming session and pairing would have been much smoother.

In short, also *write out* what the (A) input and the (B) output will look like before moving onto (C) how to design the program.

#Monday - 10/20:  
#Object Relational Mapping 

Today's Highlight:  ActiveRecord Isn't Magic with ActiveRecord 'JR'

INPUT IMAGE:  SQL-RUBY-MODEL

`ActiveRecord` is the Rails Object Relational Mapper. But, let's slow down first -- what is an ORM?

It simply *maps* the Ruby classes and *objects* to *relations* in the Database. 

More explicitly, Ruby classes are database tables. Instances of the class are table rows. And instance variables are table columns.

INPUT IMAGE:  ANIMATED-ORM

Whether your database is SQLite3 or PostgreSQL or something else, `ActiveRecord` is a way to *translate* the Ruby code into SQL commands. Once those SQL commands are done CRUD-ing the data, the data gets pushed back to Ruby through the model (see image). After converting that data into Ruby objects, you can do whatever you want. Perhaps even create the next Facebook.


#####Personally...
I really feel in my element now. As I've been playing around with Rails apps for several months, the concepts behind the challenges are finally solidifying. Dev Bootcamp is helping me fill in all the holes in my Rails logic. 

Today, we also had a mock assessment for the end of Phase 1. We were given three problem -- five minutes each -- to solve. Under those time constraints, I was happy to say that I was able to maintain my composure and breath through the assessment. Now, I don't have to do the real one with Sherif. 

That said, some of my peers are really stressed that they may be held back. I wish there was something I could do to help. But as we're already required to pair for most of the day, there seems to be no time. I wish Dev Bootcamp had more active coaches or teaching assistants. Sherif is looking for ways to make an auxiliary staff (more available. At the moment, nothing seems like it's going to change soon.

#Tuesday - 10/21:  
#ActiveRecord Overview/Review

Today's Highlight:  Setting Up Databases And Playing With ActiveRecord

Today, we were given a several plug-and-chug exercises. That by no means that it was an easy day. For some, I'm sure their heads were spinning. For me, the challenges were a great way to hone down the basics of what all the files and classes mean in ActiveRecord.

-	`config/environment.rb`: requires the gems and ruby files needed, then it loads the model files and sets up the database connection. Essentially, it set ups the *environment* for the app to run.
-	`Rakefile`: contains domain specific language (DSL) with set tasks to help get our application up and running. Namely, it has all the useful `db:` commands
-	`db/migrate`: contains the all the migration files (or changes to the database). there are multiple migrations so that you can change your database step-by-step as opposed to making it magically appear (or disappear).
-	`Gemfile`: is a list of gems and the gems' specific version needed to run the file 
-	`Gemfile.lock`: is a list of the *exact* environment known to let the your web app work correctly. Hence, you 'lock' or keep this file because -- in the worst case scenario if your gems' versions are off -- others may want to reference the file for future use.


Other tidbits:

-	`ActiveRecord::Associations::CollectionProxy`: is an object that behaves similarly to an array. When you set-up associations and ask a `Dog` for it's `Person` (owner) in `Dog.find(1).owners`, you'll get a *collection* of owners associated with the dog.

#####Personally...

I'm doing well. I talked to Sefora, the Dev Bootcamp life coach, today and I have to say having someone to talk to.

As the end of Phase 1 nears, I had started thinking about what I want to do after Dev Bootcamp. Not because I'm waiting to graduate and find a job, but because I want to keep learning. I applied to Hacker School before Dev Bootcamp, and I still think I'd like to attend. 

While Week 2 and Week 3 so far has been good in honing down the basics of MVC and ActiveRecord, I definitely want to get better at some core computer science-y topics. Moreover, I want to build more command-line centric things before I really start honing into web and mobile apps. At the end of the day, I think since technical knowledge builds upon the basics, I want more practice on just that.

For now though, I think I'll take Sefora's advice. Dev Bootcamp is short -- I should be with it for now. Don't worry about taking a few months off applying to Hacker School. Just get the most out of Dev Bootcamp for now.

#Wednesday - 10/21:  
#More ActiveRecord


Today's Highlight:  Symmetric Migrations

When writing a migration, typically ActiveRecord (and Rails) simply uses the `change` method, like below:

	class ExampleMigration < ActiveRecord::Migration
	  def change
	    create_table :products do |t|
	      t.references :category
	    end 
	  end
	end

So, when you call `rake db:rollback` or migrate to a previous version of the database, ActiveRecord can call its implicit `down` method to undo any changes that you may have put `up`.

However, sometimes you may run into problems. For example, you may want to create a `name` from a student's `first_name` and `last_name`. So, you'll actually have to write a bit of ruby to create the `name` attribute in your database.

	class AddColumnName < ActiveRecord::Migration
	  def up
	    add_column :students, :name, :string
	    add_column :students, :address, :string
	    Student.all.each do |student|
	      student.update_attributes! :name => student.first_name + " " + student.last_name
	    end
	    remove_column :students, :first_name
	    remove_column :students, :last_name
	  end

Here, we add the new column, and delete the old attributes `first_name` and `last_name`. 

A few years pass, and now the principal wants back the `first_name` and `last_name` attributes. Unfortunately, you can simply rollback to an old version. You don't have the `change` method -- so you have to explicitly create your own `down` method to drop the table:

	   def down
		add_column :students, :first_name, :string
		add_column :students, :last_name, :string

		Student.all.each do |student|
		  student.update_attributes! :first_name => student.name.split(" ")[0]
		  student.update_attributes! :last_name => student.name.split(" ")[1]
		end

		remove_column :students, :address
		remove_column :students, :name
	   end

#####Personally...
I'm just tired physically. Mentally, I think I can be pushed more. I've been learning a few cool tidbits here and there this week, but not sure if it makes up for all the other stuff.


#Thursday - 10/21:  
#More ActiveRecord 

Today's Highlight:  Really Understanding The Difference Between `.build` and `<<`

Say, you're a teacher in kindergarten. As such, you have lots of students. And, given the nature of moving families, you may get new students half-way through the year. You need a way to associate a `teacher` and new `students` in the database. (You must have already set-up the association in the model.)

To create the association in ActiveRecord, ask for the teacher's *association collection* with something similar to `teacher.students`. This should return all the students with the same teacher id *in an array*.

Because the association collection returns an array, you can perform array-like operations on the collection. Namely, you can use the shovel operator `teacher.students << Student.new(...)`. The shovel operator instantly fires *update* on SQL without a `.save` or `.update` on the parent object.

###`.build`

While in previous Rails versions, many took `.build` and `.new` to do similar things. I think `.build` is closer to `<<`. 

`teacher.students.new` would create new student. However, it's neither *added* or *saved* the the `student` collection.

`teacher.students.build` would create the new student, *and* place the student in the teacher's `student` collection. However, the new student would *not* be saved. So, you have to save the student manually.

#####Personally...
I'm just okay. Normally, I'd be fed up. But, it's normal that at some point I'd be working with someone who is a little behind. I was paired with someone who seems like she'll be repeating Phase 1. 

So while it was good to dig deep and be forced to explain every little thing that was happening, I was pissed that I didn't get to drive faster and harder at the problem. 

I want to go deeper into my studies, while Dev Bootcamp keeps asking that we go for breadth. I think I already have that.

#Friday - 10/21:  
#Phase 1:  Group Projects

Today's Highlight:  Messing Around with Twilio API

The Twilio API is pretty simple. To get started all you need to type is `require 'twilio-ruby`, and then `bundle install` the gem. From there, you simply copy and paste your `accountsid` and `auth_token` from your Twilio account.

From there, you instantiate a new Twilio client object with:
`client = Twilio::REST::Client.new account_sid, auth_token`

Now, to send texts to all your friends, create a hash with their phone number. (Don't forget to verify their phone numbers on Twilio.)

	from = "+14159998888" # Your Twilio number
	 
	friends = {
	"+14153334444" => "Curious George",
	"+14155557775" => "Boots",
	"+14155551234" => "Virgil"
	}

Finally, just loop through your friends, and send them each a message.

	friends.each do |key, value|
	  client.account.messages.create(
	    :from => from,
	    :to => key,
	    :body => "Hey #{value}, Monkey party at 6PM. Bring Bananas!"
	  )
	  puts "Sent message to #{value}"
	end

Pretty simple.


#####Personally...

We didn't do much of anything again today. Dev Bootcamp had graduation day (which happens every 3 weeks). That combined with the fact that our cohort is super chill, we didn't do much of anything. One group actually just hung out all day on the couch.

I'm kind of disappointed that we weren't really programming, pushing my boundaries today. But we all need a rest. Moreover, it was good to dive deeper into the Dev Bootcamp culture.

A student, Ruskin said it best. Most of the lectures are just okay. However, what Dev Bootcamp really adds is the cultural on boarding -- making sure all the students abide by a set of rules so that the place is safe to explore. 

Unfortunately for many of us, Dev Bootcamp focuses a bit much on beginners. And with the lack of teachers and coaches, it feels like some of us are simply teaching other students.

Next week, starts Phase 2, a dive into front-end technologies. It's exciting, however there are also ~10 people repeating Phase 2. Meaning, our cohort just grew from 30 to 40. 40 people, just one or two teachers.

#Monday - 11/3:  
#Phase 2:  Javascripting the DOM

Today's Highlight:  Building a Browser-based Racer Game

This was the first day that I've used pure Javascript to handle elements in the DOM. Before, I had only used jQuery...and I have to say I much prefer the latter.

In any case, here are a few quick things I picked up from today:

-	You can nest functions within `addEventListener`:

It doesn't matter if you understand this code or not. The most important thing you need to understand is that the `addEventListener`	passes an event object to `on_key_press`. The latter function accepts this event object as `e` in our case (but it can be anything - like `banana`).  

	function on_key_press(e) {
	  if (e.keyCode === 90) {
	    update_player_position('#player1_strip');
	  } else if (e.keyCode === 77) {
	    update_player_position('#player2_strip');
	  }
	}
	window.onload = function() {
	  document.addEventListener('keydown', on_key_press, false);
	}

-	`document.querySelectorAll()` returns an array of all elements that match its arguments. 

		var newGame = function() {
		  var track = document.querySelectorAll("tr td");
		  console.log(track);
		  for (var i = 0; i < track.length ; i++) {
		    track[i].className = "";
		  }
		}
		
The above code will return `[td, td, td, td, td, td, td.active, td, td, td, td.active, td, td, td, item: function]`, which is long to say the least. All you need to know is that you can traverse this array and manipulate it.

- Javascript can create HTML for you with `createElement()` and `appendChild()`

Here, we create a row in a table, then we append it to the table. We do something similar for the table data elements (`td`).

		var createTrack = function(track_len, player) {
		  var table_element = document.querySelector(".racer_table");
		  var new_table_row = document.createElement("tr");
		  table_element.appendChild(new_table_row);
		  new_table_row.id = "player" + player + "_strip";
		  for (var p = 0; p < track_len; p++) {
		    var new_table_data = document.createElement("td");
		    new_table_row.appendChild(new_table_data);
		  }
		}
		
#Tuesday - 11/4:  
#Phase 2:  Javascripting the DOM 2

Today's Highlight:  Manipulating Objects in the DOM

Just like the back-end, your front-end code can also be placed into a Model-View-Controller format. We saw that today when creating orange trees that can (1) age and (2) grow oranges.

In this context, the **model** contained data-related properties and methods. That is, it contains *just* the data. No references to HTML, CSS, or to the DOM.

Meanwhile, the **view** contains all UI-related properties and methods. The view can contain HTML, CSS, and DOM references. It represents the user interface, as well as event bindings related to the UI.

As usual, the controller has can reference both the model and the view.

Other tidbits I learned were:

1.  	When using EventListeners, you can `console.log(event.target)` to get a list of all the target's parents, siblings, nodes, etc. That way you can quickly discover the objects you are looking to manipulate.

2.  	Functions *of* constructor functions can be written two ways. Our instructor says that the second way runs more efficiently than the former.:

		// Like this...
		function Tree() {
		  this.dropOrange = function() {
		  	return (this.orangeCount -= 1)
			}
		// or like this..
		Tree.prototype.dropOrange = function() {
		  return (this.orangeCount -= 1);
			}
			
3. A Javascript can accept an infinite number of arguments. When you see `function()` defined, it is actually still passing an argument -- even though it looks like it isn't; All Javascript functions pass an `arguments` array.

		function yolo() {
			console.log(arguments[0]);

Again, it looks like the `yolo()` function isn't accepting any arguments. But when we print out the the first index in the `arguments` array, we get whatever we pass into `yolo()`.

	yolo(5);
	==> 5
	
	yolo("YAY");
	==> "YAY"
	
#Wednesday - 11/5:  
#Phase 2:  AJAX & jQuery

Today's Highlight:  6 Steps to A Proper AJAX Request

AJAX is complicated because of all the routing, database calls, and DOM tempting that is involved. However, you can encapsulate all this knowledge into six, simple steps below.

1.	Bind an event listener to a DOM element. (typically 'click')
2.	Prevent the default action of the event listener.
3.	Create the AJAX request with jQuery (or JS). Make sure it is properly routed to the post route. (the route already contains the params[:id])
4. 	Update the server/database.
5. 	Make sure the server response includes all the information needed to update the DOM. (put information into JSON format)
6. 	Update the DOM with the new information.

...said again in code...

	  // $.ajax takes a hashmap of options as an argument.
	  var ajaxRequest = $.ajax({
	    // these two attributes determine which route in your controller will be called.
	    url: "/foo",
	    type: 'POST',
	    // the 'data' attribute determines what data is sent to the server.
	    // The server will be able to access these values using the params hash.
	    // If the server only needs to know information passed in the URL, this attribute is not necessary.
	    data: { bar: 'baz' }
	  })

	  // the .done function takes a callback, which will only be fired if the server responds
	  // with a success status code. the callback will receive arguments corresponding to the
	  // request object, status, and data sent from the server.
	  ajaxRequest.done(someCallbackFunction)

	  // like the .done function, the .fail function will fire off a callback if the server responds
	  // with an error status code.
	  ajaxRequest.fail(someOtherCallbackFunction)
	  
**Note:  When testing AJAX, it's helpful to print message inside the `.done` and `.fail` to make sure things are (or are not) working properly.

#######Recreating Hacker News Votes

Here's the code we wrote today to make upvotes work without refreshing the whole page.

	$(document).ready(function() {

	(document).ready()
		  // 1
		  $(".vote-button").click(function(event){ 
		  // 2
		    event.preventDefault();
		    var newThis = $(this);
		    var postID = $(this).parent().attr("id");
		    var postUrl = $(this).attr('href');
		  // 3
		    var ajaxRequest = $.ajax({
		      url: postUrl,
		      type: 'POST'
		      //no data attribute needed b/c we're not sending anything
		    });
		    ajaxRequest.done(function(response){
		      var points = $("#"+postID).find("span.points");
			      $(points).html(response);
			    });
			  });
			});
			
Here, we (1) bound the event listener to the `.vote-button` class. Then, we (2) prevented the default routing action (refreshing the page to refresh the vote count).

After grabbing the relevant href post route with a few jQuery selectors, we're finally able to make a AJAX call. (3) We can see that the AJAX call requires that post rout (`postURL`). Moreover, it requires a certain type `POST` -- because we're posting, creating information in the database. 

That brings us to step (4) updating the database. We can do all this work within the Sinatra route:

	post '/posts/:id/vote' do
	  post = Post.find(params[:id])
	  post.votes.create(value: 1)
	    if request.xhr?
	      post.votes.count.to_json
	    else
	      redirect '/posts'
	    end
	end

As mentioned, the jQuery selectors automatically held the `:id` of each post -- through the `postUrl`. That's why the app was able to properly route; that's also why we're able to find the `post` by the `params[:id]`. 

Once the record is created in the Votes database, we're ready to (5) pass the server information back to Javascript. All we need to do is make sure it is in the JSON (Javascript Object Notation) format. 

(The control flow with `request.xhr?` simply validates that the request passed to this route was a XML HTTP Request -- basically something done by a computer and not a human.)

At last, we go back to our JS file:

		    ajaxRequest.done(function(response){
		      var points = $("#"+postID).find("span.points");
			      $(points).html(response);
			    });
			  });
			});
			
Here, the `response` (which we can name `banana` or anything else we want) is the JSON object. As such, we're able to pass that object back to the correct html element(`.points`). With jQuery's `.html` function, the text inside the `span` is automatically updated. (`.html` is the jQuery equivalent of Javascript's `.innerHTML()`).

That's as far as I'm going to summarize today. However, we follow similar format and syntax to make delete or create database request. I'm sure you can figure it out yourself. =)


#Thursday - 11/5:  
#Phase 2:  Group Projects Part 1

Today's Highlight:  Javascript DOM Games

My three-person team today was tasked with building a connect four game. Working with them, I realize how little I actually know about the MVC model in Javascript.

Ideally, a Controller calls all the Model and View actions. Basically, the Controller is the *transformer*. But it is also the *passer*; After getting the data from the model, the controller passes that information for the View to render.

The View should only manipulate HTML and CSS type tags. It should find which part of the DOM it should place the model's data. 

So, what does the Model do? Ideally, the Model creates and handles all the data. 

It may sound like the Model and Controller have overlapping responsibilities. But all the Controller does is *call* or invoke the Model's methods. 

Very simply, your MVC should look like this:

	function Model = {
		this.variable = 0;
		this.modelFunction = function() {
			this.variable;
	
	function View = {
		this.viewFunction = function(modelData) {
			$('div').html(modelData)
	
	function Controller(model, view) = {
		this.myModel = model
		this.myView = view
		this.ControllerFunction = function() {
			var data = this.myModel.modelFunction();
			this.myView.viewFunction(data);
	


#Friday - 11/6:  
#Phase 2:  Group Project Part 2

Today's Highlight: 


Global SCOPE: -- whole document knows about these

todoName
todoId
todoCompleted

Local SCOPE:

var todoName
var todoId
var todoCompleted

#Monday - 11/10:  
#Phase 2:  Building an API

Building an API is surprisingly easy. All you need to do is change the data into a JSON object and return it through the controller's routes.

#Tuesday - 11/11:  
#Phase 2:  Consuming an API

Today's Highlight:  Poor-ly Documented APIs Suck

Nothing's worse than not understanding a challenge. Even worse is realizing later on that you don't understand something because of how the problem was set-up.

It's like getting a 25% of an exam wrong and later realizing that the Professor had a typo in the question. 

Anyway, accessing an API isn't that difficult. The difficult part is parsing that (JSON) data into a format that your application can use. To better understand how to do that, here are a few tips in implementing an API inside the MVC model:

<u>Model</u>

1.	Make the HTTP request in the model (you can also do so in the controller).
2.	You can parse and manipulate the data into any format you like by writing methods like `get_all_articles` or `get_one_article`.
3.	**Caching:** You can save the API JSON data into your own database -- you just need to create a table with similar columns. **But don't do this!** It may be simple, but it's incredibly inefficient.

<u>Controller</u>

1. 	Can make HTTP request.
2. 	Generally, just passes data to the View.

#####Other TidBits

-	`before_save` is an ActiveRecord callback. Any `before_save` method will only be invoked when creating or updating a database. However, [AR methods](http://api.rubyonrails.org/classes/ActiveRecord/Callbacks.html) like `update_columns` can skip such callbacks.
-	Helper methods like `current_user` are intended to be called within the View. However, the Controller does have access to it.


#Wednesday - 11/19:  
#Phase 3:  Rails Set-up & Testing

Today's Highlight:  Realizing How Much It Sucks to Set-up Your Own Gems & Testing

####Starting A New Rails App

To create a Rails 4 app with postgres database, and without the default testing framework (-T):

	rails new app_name -T -d=postgresql

####Testing Gem Setup

Rspec-rails will provide the usual DSL:

	group :development, :test do
	  gem 'rspec-rails', '~> 3.0'
	end

However, `capybara`, `shoulda-matchers`, and `factory_girl` will go in just testing environment:

	group :test do
	  gem 'shoulda-matchers', require: false
	  gem 'factory_girl_rails'
	  gem 'capybara'
	  gem 'faker'
	  gem 'simplecov', require: false
	end
	
The `faker` gem is always a good one to include. `simplecov` also provides the ability to see how much test coverage your code has.

***Rails automatically requires gems. And, sometimes Rails fails.***

####Using the Testing Gems

##### `shoulda-matchers`
`shoulda-matchers` is surprisingly easy to use. Perhaps common way to use `shoulda-matchers` is on validations:

	describe Question do
	  context "validations" do
	    it { should validate_presence_of :title }
	  end
	end

##### `factory_girl` 

`factory_girl` is the hardest to use in my opinion. However, it's also the useful. Instead of creating object instances before each test (in `let` or `before...do`), `factory_girl` lets you create test objects inside just one folder -- `spec/factories`. The file though might look like this: 

	FactoryGirl.define do
	  factory :f_question, class: Question do
	    title { Faker::Name.title }
	    body { Faker::Lorem.sentence }
	  end
	  
	  factory :f_answer, class: Answer do
	    title { Faker::Name.title }
	    body { Faker::Lorem.sentence }
	    association :question, factory: :f_question
	  end
	end

`factory_girl` knows by convention to create an instance of the Answer model. However, because I want to name this instance `:f_answer`, I have to specify a `class: Answer`. Also, if I want to set_up an association, I'll have to specify the factory method `factory: :f_question`.

Inside the spec, you can create the object like so. (The `let` statement is optional):

	let!(:f_answer) { create :f_answer }

##### `capybara` 
`capybara` allows for testing on the View. Essentially, it loads up a browser in the background and can behave as if it were a real user. In doing so, `capybara` allows us to test links, forms, etc. 

	  it "answers can be UPVOTED" do
	    visit question_path(f_answer.question)
	    click_link("Upvote")
	    within('#question-answer-' + "#{f_answer.id}") do
	      expect(page).to have_content 1
	      puts page.body
	    end
	  end

Here, `capybara` can visit a url path, click a link, and expect content `within` an html id.

####GIT Tidbits
-	If you committed on master, (1) checkout a new branch (2) checkout back to master (3) `git reset --hard HEAD~1` to go back one commit. You can customize the number of commits
-	To delete a remote branch (after committing and merging), `git push origin :<branch name>`. Essentially, we are pushing an empty branch (left side of colon) to the remote branch. This is similar to, in Heroku, `git push production <feature branch>:master` -- which makes the feature branch a master branch.

#Thursday - 11/20:  
#Phase 3:  Rails Routing, APIs, and AJAX

Today's Highlight:  Cool Routing, Simple API, Complicated AJAX
