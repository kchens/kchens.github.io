#When to use Rails or Sinatra?

#Rails
...is 100,000 lines of code. As you might imagine, Rails comes with lots of boilerplate code (different gems, testings units, and more). Moreover, Rails comes with generators to help create related files when making specific actions (like creating a model or controller). With so much built-in, Rails hopes to solve problems that a typical programmer building out a ***large*** application might run into. It deals with endpoints of 15-20.

#Sinatra
...is 2,000 lines of code. As such, Sinatra doesn't come with a lot built-in -- and that's a plus. Being lightweight, Sinatra runs fast. It's great for applications that need to hit or provide API endpoints. 

However, there are some cons. Sinatra doesn't have any default way to handle data -- and store it into a database. It's great for working with 5-10 endpoints, but, afterward, you might want to switch over to Rails.

#One Way To Put It.
Use Rails for model-driven applications. Use Sinatra for dealing with HTTP from the server-side.


See more: http://www.sitepoint.com/rails-or-sinatra-the-best-of-both-worlds/