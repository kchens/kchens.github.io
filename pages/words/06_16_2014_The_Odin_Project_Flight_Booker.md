*The Odin Project entices programmers to learn by copying popular, real-world start-ups. In this case, I learned to build a [**flight search**](http://www.theodinproject.com/ruby-on-rails/building-advanced-forms) company like Priceline, Orbitz, or Google Flights.*

Now that I've begun programming after a two-month hiatus, I must say:  I forget how difficult learning a new, hard skill is. 

Nonetheless, I'm pleased to say that I've remember almost all of what I learned. From using GitHub to navigating Rails's MVC framework, I feel like I've finally internalized what programming entails.

Of course, maintenance is not the name of the game. Completing this project has showed me how difficult it is to improve my skills.

####1. Creating a Search Form
In the first part of building Flight Booker, I had to mimic the usual search form you might find at one of your regular search sights.

![Kevin_Chen_Odin_Flight_Search](http://kchens.github.io/images/Odin_Flight_Search_Final.png)

######Setting up associations between the Airport and Flight models
First off, you need to create your Airport and Flight model -- and the relevant associations. As Airports are the hubs where an airplane flies to and from, I think it's apt to say that `Airport` `has_many` `arriving_flights` and `departing_flights`.

To ensure that the Airport model properly calls the Flight model and can access the flights' relevant attributes (`duration`, `departure_date`, etc.), we'll need to assign correct `class_name: "Flight"`. Likewise, the Flight model will need to access the Airport model with the help of `class_name`.

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

Inside this file, you'll need to first clear out the database -- just to make sure there aren't   any lingering database objects. To do that, type `[model name].delete_all`.

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

	def index
      @airports = Airport.pluck(:code, :id)
      @dates = Flight.flight_dates
      @passengers = (1..4).map { |x| [x, x]}
	end 
    #formatted_date is a model function that shows the date as MM/DD/YY

Whether I'm using `pluck`, a model method, or `map`, the gist here is the same:  I'm creating an array of arrays for customers to choose from. This way, we can display an airport's code like "SFO", but ask the `Airport` model for the correct `id`. The customer can see this if I place use the `options_for_select` correctly like so:
    
    <%= form_tag(root_path, :method => "get") do %>
      <%= select_tag :from, options_for_select(@airports), prompt: "From" %>
      <%= select_tag :to, options_for_select(@airports), prompt: "To" %>
      <%= select_tag :date, options_for_select(@dates), prompt: "Date" %>
      <%= select_tag :passenger, options_for_select(@passengers), prompt: "Passengers" %>
	<%= submit_tag "Search Flights", name: nil %> 

####2. Search queries
When the customer searches in the above code, I am taking the params (which includes the :from, :to, and :date selections) and sendint it into the controller like so:

	def index
    	.
        .
        @flights = Flight.search(params)
	end
The controller then sends the data to the model. In the following model method, `self.search(params)` breaks up the parameters, then calls the `Flight` database to see if any objects match those parameters: 

	def self.search(params)
      if params
		Flight.on_date(params[:date].to_date)
              .where('from_airport_id = ? AND to_airport_id = ?', params[:from], params[:to])
      else
        Flight.none
      end
	end

With this, `@flights` in `Flight#index` now contains an array of flights that match the customer's query. Now, you can build a form using `form_tag` to display the flight search results to the user (I won't detail this here).

######An aside on dates

In the above code, the `on_date` (a user-created) method is used -- and with good reason. When the flights were seeded, the date attribute was recorded in this format:  `2014-06-28 02:25:56 -0400` or something similar. 

However, when the dates were displayed to the user, the date format changed to MM/DD/YYY.

So, to match that the original date format, the `on_date` method calls all objects whose dates are between `2014-06-28 00:00:00` and `2014-06-28 23:59:59`:

	def self.on_date(date_param)
    	where(date: date_param.beginning_of_day..date_param.end_of_day)
	end

####Creating Tickets, Bookings, and Passenger Information
######More models
Once a passegner selects their preferred flight, we have to save that *booking* information somewhere. So, let's create a Booking model. There are two ways that you can think about how to set this up. 

(1) You can look at the associations from the passenger's perspective. In this case, a passenger takes many flights. And, in order to take those flights, they have to have many reservations or bookings. That means:

	class Passenger < ActiveRecord::Base
    	has_many :flights, through: :bookings
        has_many :bookings
        
        #If you are looking to issue tickets...
        has_many :bookings, through: :tickets
        has_many :tickets, foreigh_key: :passenger_id
    end

(2) Take the perspective of the flight. On a flight, there are many passengers. And, you know these passengers by the passenger's bookings.

	class Flight < ActiveRecord::Base
    	has_many :passengers, through: :bookings
    	has_many :bookings, foreign_key: :flight_id
    end

Here, I added a `foreign_key` to the booking model. Otherwise, how would the flight know how to query for the flight information?

Now, it should be relatively easy to set-up the Booking model. First, generate the Booking model with just one attribute, the foreign key:  `rails g Booking flight_id:integer`. 

Next, let's think about associations. A booking has only *one* flight -- because, currently, the app only allows you to fly one way. However, a booking has many passengers because the app allows more than one person to be on the same booking.

	class Booking < ActiveRecord::Base
    	belongs_to :flight
        has_many :passengers
        
        accepts_nested_attributes_for :passengers
        
        #If you are issuing tickets..
        has_many :passengers, through: :tickets
        has_many :tickets, foreign_key: :booking_id
    end

As a side note, you want to make sure that a Booking has access to the passenger's information. For this, we will use the `accepts_nested_attributes_for`. That way, the booking modle has access to the passenger's attributes (Say, when you type `Booking.first.passengers.first` into the `rails console`).
######Setting up the Booking view
At last, we can finally help the passengers input their booking information.

Setting up the `new.html.erb`, let's use a `form_for` so you can input the passenger information into the Booking model's database. We type:  `<%= form_for(@booking) do |b| %>`

As you want the booking model to be able to access the flight model, a `hidden_field` is necessary to send the booking the `flight_id`.	(To be extra sure that the value is saved you could type `<%= b.hidden_field :flight_id, value: @flight.id %>`)

For now, the form should look like:

	<%= form_for(@booking) do |b| %>
	  <%= b.hidden_field :flight_id %>    
      ..
      <%= b.submit "Book Flight" %>
	<% end %>  
    
To enter the passenger's information, I'll need to use a `fields_for`. One way to think about it is that the app will be writing to the Passenger model, through the Booking. As a result, the passenger information is *nested* inside the Booking model. You can get a better sense of this by looking at the whole form:

	<%= form_for(@booking) do |b| %>
    <%= b.hidden_field :flight_id %>    
      <%= b.fields_for :passengers do |passenger_fields| %>
        Name: <%= passenger_fields.text_field :name %>
        Email: <%= passenger_fields.text_field :email %>
        <br>
      <% end %>
    <%= b.submit "Book Flight" %>
	<% end %>
######Creating the right # of passenger fields

In the above code, you want to make sure that there are enough passenger fields. Because if the customer is making a booking for 4 passegners, you want your app to show 4 passenger fields. The view's form is already prompted to display blank passenger fields, but this also needs to be done in the controller; the controller needs to create blank passenger instances.

You can do this by using `.build`. This adds an object to the model, and also renders an empty record in the view. (In Rails 4, `.new` seems to do the same thing. See [here](http://stackoverflow.com/questions/17831812/build-vs-new-in-rails-4).)

	class BookingsController < ApplicationController
  	def new			  				
        params[:passengers].to_i.times { @booking.passengers.build }
	  end
    end

The above code, takes the number of passengers from the params hash, and then builds the multiple empty records for display in the view.
####Tidbits
When using `belongs_to`, the following model should always be in the singular:

*	`belongs_to :from_airport`

	Client.where("orders_count = ? AND locked = ?", params[:orders], false)
    

`Datetime` format is `"YYYY-MM-DD HH:MM:SS"` or `"2014-06-14 08:16:49"`

http://en.wikibooks.org/wiki/Ruby_on_Rails/ActionView/Forms