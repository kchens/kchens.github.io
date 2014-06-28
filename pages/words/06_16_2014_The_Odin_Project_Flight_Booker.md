*The Odin Project entices programmers to learn by copying popular, real-world start-ups. In this case, I learned to build a [**flight search**](http://www.theodinproject.com/ruby-on-rails/building-advanced-forms) company like Priceline, Orbitz, or Google Flights.*

Now that I've begun programming after a two-month hiatus, I must say:  I forget how difficult learning a new, hard skill is. 

Nonetheless, I'm pleased to say that I've remember almost all of what I learned. From using GitHub to navigating Rails's MVC framework, I feel like I've finally internalized what programming entails.

Of course, maintenance is not the name of the game. Completing this project has showed me how difficult it is to improve my skills.

####1. Creating a Search Form
In the first part of building Flight Booker, I had to mimic the usual search form you might find at one of your regular search sights.

![Kevin_Chen_Odin_Flight_Search](http://kchens.github.io/images/Odin_Flight_Search_Final.png)

######Setting up associations between the Airport and Flight models
First off, you need to create your Airport and Flight model -- and the relevant associations. As Airports are the hubs where an airplane flies to and from, I think it's apt to say that `Airport` `has_many` `arriving_flights` and `departing_flights`.

To ensure that the Airport model properly calls the Flight model and can access the flights relevant attributes (`duration`, `departure_date`, etc.). We'll need to assign correct `class_name: "Flight"`. Likewise, the Flight model will need to access the Airport model with the help of `class_name`.

Finally, we need the correct `foreign_key` -- the right Flight attribute -- so the Airport model knows which `arriving flight` or `departing flight` it is trying to call (along with the flight's other attributes). 

Here is the completed `Airport.rb` 

	class Airport < ActiveRecord::Base
  	has_many :departing_flights, foreign_key: :from_airport_id, class_name: "Flight"
  	has_many :arriving_flights, foreign_key: :to_airport_id, class_name: "Flight"
	end

...and `Flight.rb`:

	class Flight < ActiveRecord::Base
	  belongs_to :from_airport, class_name: "Airport"
	  belongs_to :to_airport, class_name: "Airport"
	end

######Seeding your database
Before we create the view to show the available flights to our customers, you need to create a database of flights. How do you do that? Well, go to your `db/seed.rb`.

Inside this file, you'll need to first clear out to database -- just to make sure there are any lingering database objects. To do that, type `[model name].delete_all`.

Then, you can start creating flights and airports. Here is the full file:

	Airport.delete_all
	Airport.create(:codename => "SFO")
	Airport.create(:codename => "WAS")
	Airport.create(:codename => "BWI")
	Airport.create(:codename => "PVD")

	Flight.delete_all
	Flight.create(from_airport_id: "1", to_airport_id: "2", departure_date: Time.now, duration: "10")
	Flight.create(from_airport_id: "3", to_airport_id: "4", departure_date: Time.now, duration: "5")
	Flight.create(from_airport_id: "2", to_airport_id: "1", departure_date: Time.now+3, duration: "10")
	Flight.create(from_airport_id: "4", to_airport_id: "3", departure_date: Time.now+3, duration: "5")

At last, we need to run `rake db:setup`. That will create the database, load the schema, and intialize the database with the seed data. (For more, see [here](http://stackoverflow.com/questions/10301794/difference-between-rake-dbmigrate-dbreset-and-dbschemaload) and [here](http://edgeguides.rubyonrails.org/active_record_migrations.html)).

######Creating the form
When the customer arrives at the browser, he'll choose the flight he's looking for, then submit it to your database.

In Rails, that means that the customer will access the form in the View (in this case, the `index.html.erb`). You can build a form with the `form_tag` and `get` method to put the flight data into the database.

	<%= form_tag(root_path, :method => "get") do %>

(`form_for` is used to edit/create a model's attributes. Meanwhile, `form_tag` is used for something more generic (when we aren't dealing with a model's attributes)

To create the "From", "To", "Passengers", and "Date" dropdown menus, you'll need to use the `select_tag`. 

Creating different options in the dropdown menu is not as easy. We'll need to use the following tag option:

	options_for_select(container, selected = nil)

Moreover, you'll create that container (in this case, an array) of options. You do this in the corresponding controller action (`#index`):

	@airports = Airport.all.map { |x| x.codename }
    @num_passengers = (1..4).map { |x| x }
    @dates = Flight.all.map {|x| x.formatted_date}
   
Now, the view should be working correctly; the customer should be able to see and select the options for his flight.
    
    <%= form_tag(root_path, :method => "get") do %>

	  From: <%= select_tag :from_airport, options_for_select(@airports, params[:from_airport]) %>
	  To: <%= select_tag :to_airport, options_for_select(@airports, params[:to_airport]) %>
	  Passengers: <%= select_tag :num_passengers, options_for_select(@num_passengers, params[:num_passengers]) %>
	  Date: <%= select_tag :departure_date, options_for_select(@dates, params[:departure_date]) %>

	<%= submit_tag "Search", :name => nil %>
    
####Tidbits
When using `belongs_to`, the following model should always be in the singular:

*	`belongs_to :from_airport`

	Client.where("orders_count = ? AND locked = ?", params[:orders], false)
    

`Datetime` format is `"YYYY-MM-DD HH:MM:SS"` or `"2014-06-14 08:16:49"`

http://en.wikibooks.org/wiki/Ruby_on_Rails/ActionView/Forms