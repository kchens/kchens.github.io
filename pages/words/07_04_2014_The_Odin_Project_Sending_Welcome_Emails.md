In this Odin Project, you learn how to send emails -- be it welcome, thank you, or goodbye ones -- through your app. The steps are fairly simple and go by quickly.

I completed this email lesson using my [Flight Booker](http://www.kevinkchen.com/2014/06/16/the-odin-project-flight-booker/) app.

####Setting up the mailer
Type: `rails generate mailer PassengerMailer`

Completing the above, uses the `ActionMailer` gem. This `mailer` acts like a model and controller rolled into one. 

####Install `letter_opener`
As this is a test app, we aren't actually trying to send the real emails. Using [`letter_opener`](https://github.com/ryanb/letter_opener), you can view your emails in the browser as opposed to sending them.

To set this up, open your GemFile. Type: `gem 'letter_opener', :group => :development`.

Finally, set the delivery method in the `config/environment/development.rb`: 

	config.action_mailer.delivery_method = :letter_opener
    
####Skipping ahead to *sending* the email

Before we make the email, I want to show you how to actually call the email into action. 

As we'll be sending the email *after the each booking that's created*, we'll call the email method -- `thank_you_email` -- inside `Booking#create`:

	class BookingsController < ApplicationController
      def create
    	...
        if @booking.save
          @booking.passengers.each { |p| PassengerMailer.thank_you_email(p).deliver! }
          redirect_to booking_path(@booking)
        else
          ...
        end
      end
    end
    
By chaining the passengers method onto `@booking`, I'm able to call the `PassengerMailer` mailer (`deliver!` is the method that actually sends the email). From, `thank_you_email` is called to display a browser email.

####Creating the `thank_you_email` method

In the `passenger_mailer.rb`, you need to specify (1) who to send the email *from* and (2) who to send the email *to*.

For (1) type: `default from: "kkch3n@gmail.com"`

For (2) we'll need to create the `thankyou_email` method. In it, we'll need to specify the `passenger` and access his email with `passenger.email`. At last, we can place all this information into the `mail(to:)` method.

	class PassengerMailer < ActionMailer::Base
  	default from: "kkch3n@gmail.com"

	  def thankyou_email(passenger)
	    @passenger = passenger        
    	mail(to: @passenger.email, subject: "Thank you for your flight purchase")
        
        ###For use in the html or text email.
        @booking = @passenger.bookings.last
	    @url = "http://localhost:3000/"

	  end
	end
    
####Creating the actual email
At last, we can create the real email. Create *two* new files and -- within the `passegner_mailer` folder -- save them as `thank_you_email.html.erb` and `thank_you_email.text.erb` (This format is essentially the `[mailer_method_name].html.erb`). Two different email formats are needed to bypass SPAM filters.

In the file, you can type whatever you want. Here's what I typed:

	<body>
      <h1>Thank you <%= @passenger.name %> for your flight purchase</h1>
      <p>
        You have successfully booked your flight. Your confirmation # is <%= @booking.id %>
      </p>

      <p>
        Flight #:   <%= @booking.flight.id %>
        From:       <%= @booking.flight.from_airport.code %>
        To:         <%= @booking.flight.to_airport.code %>
        On:         <%= @booking.flight.date.strftime("%m/%d/%Y") %>
        Duration:   <%= @booking.flight.duration %>
      </p>

      <p>
        For passengers:
        <ol>
          <% @booking.passengers.each do |passenger| %>
          <li><%="#{passenger.name} - #{passenger.email}"%></li>
          <% end %>
        </ol>
      </p>

      <p>
        Have a great trip! Whenever you fly, think of <%= link_to "us", @url %>
      </p>
	</body>
    
(To create the `text.erb` version, remove the `HTML` tags.)

That's it! You're good to go. Now, when your customers create new bookings, they'll automatically be sent this thank you email. Go ahead, test it out!