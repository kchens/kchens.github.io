#Service Objects: Keeping Controllers Skinny & Models "Businessy"

A production Rails application has monstrous controllers. It makes sense:  You want to implement new services from Instagram to Stripe. As time goes on, code builds on top of code and soon you can't even seem to recognize what's going on inside a controller.

While you could extract that code into a model, the model should be strictly "business logic" associated with the name of the model. So, a `User` model should only have responsibilities that an actual person has. 

That's where **Service Objects** come in. Service objects *implement the user's interactions with the application.* So, you can create an `InstagramService` and `StripeService`. 

To see how to set a Service Object up, let's walk through an example. 

###Example: A *Monstrous* Controller

Here we have a messy, bloated controller. 

`/app/controllers/stock_controller.rb`
<script src="https://gist.github.com/kchens/49e8ada9cb98ed1bcaae.js"></script>

####A slight aside into `private` methods
Before we begin creating a Service Object, let's first get on the same page:  `#update_stocks` should be `private`.

(1) As you might imagine, the user can and will interface with some of these methods in the controller (through the appropriate routes). However, the user will probably never touch `#update_stocks`. 

(2) We don't want anyone besides the controller to touch `#update_stocks`.

(3) `#update_stocks` is used internally by the controller. See the `#index` and `#endpoint` actions.

####Back to Service Objects:  Tell-tale signs for refactoring

Like with most important things, it comes down to art. However, in this controller, we can see that the private method `#load_user` is just ugly. Similarly, `#update_stocks` is way too much logic for the controller.

The `#load_user` doesn't just (1)load the user, but (2) loads the user with stocks. So much for the single-responsibility principle.

The bigger issue though is that why are we loading a user if we're inside the StockService controller..? We should only be concerned with stocks. If we want to deal with a user, then we should (dependency) inject the user as a parameter.

Ultimately, it's this `#load_user` and the logic-ful `#update_stocks` method that we'll want to extract out into a Service Object.


###What A Service Object Looks Like
In the above code, the `#load_users` method does two things. First, the method initializes the user and a few states. Second, it updates each user's stocks. The `#update_stocks` method does a third thing -- updates the stocks container with the relevant information (symbol, name, trade price).

So, our Service Object will serve these purposes. 

<script src="https://gist.github.com/kchens/a6c0baee2fd69f9b43b7.js"></script>

Here, we (1) initialized the `StockService` with a user and a few states. (2) We update the user's stocks. (3) We update the stocks with the right information.

###Finished:  A Better Controller
Now, we can create a "skinnier" and more maintainable controller.

Privately, we'll instantiate the new `StockService` and call the `StockService` methods. 

<script src="https://gist.github.com/kchens/c3e5b1497c71a31a776a.js"></script>

(I also cleared up some the `respond_to` format to be more concise.)

###
For more help, check out these links from [netguru](https://netguru.co/blog/service-objects-in-rails-will-help) and [Engine Yard](https://blog.engineyard.com/2014/keeping-your-rails-controllers-dry-with-services).

