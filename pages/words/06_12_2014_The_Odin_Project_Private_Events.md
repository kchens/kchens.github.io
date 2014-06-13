*Note: I started blogging a while after completing this project. This is my attempt to relearn what I learned.*

The Odin Project entices programmers to learn by copying popular, real-world start-ups. In this case, **Eventbrite**. 

This project gave me the chance to work on mapping associations (many-to-many relationships), while digging deeper into foreign keys and class names. Here what else I learned:

####The Easy
If you need to recreate a table, be sure to first `drop_table` like so:

	class CreateUsers < ActiveRecord::Migration
	  def change
  		drop_table :users
		  create_table :users do |t|
          .
          .
####The Hard
######Creating Associations between Creators and Events
Creators make events. But, instead of building a creator model, you can use `class_name` to  help specify the model that will be used in place. In `Events.rb`, this is the User model: 
	
    belongs_to :creator, class_name: "User"

Don't forget to add the `foreign_key` to the Events table (`CreateEvents.rb`):
	
	t.integer :creator_id
    
To complete the association, there must be a `creator_id` reference somewhere within the User model:
	
    has_many :events, foreign_key: "creator_id"
    
######Creating Through Tables

A creator makes events. Attendees go to events. And, to save time and headache, we can make Users the creator and the attendee. Above, you saw how a user becomes a creator. Here is how to make a user an attendee:

	class User < ActiveRecord::Base
	has_many :attended_events, through: :event_relationships
    has_many :event_relationships, foreign_key: "attendee_id"


First, you say the user has many `:attended_events` -- in which he is, second, an attendee with an `attendee_id` (we'll get to the `through` table below). Likewise, you do the same for events. First, you say the event has many `:attendees` -- in which it, second, has an `attended_event_id` because people are attending it (make sense?):

	class Event < ActiveRecord::Base
	has_many :attendees, through: :event_relationships
    has_many :event_relationships, foreign_key: "attended_event_id"


Finally, to bring this all together, you have to create an `EventRelationship.rb` `through` table with the corresponding migration (integer attributes: `:attendee_id` and `:attended_event_id`):

	class EventRelationship < ActiveRecord::Base

	belongs_to :attendee, class_name: "User"
	belongs_to :attended_event, class_name: "Event"


######Separating and displaying events in a view

There are four parts to displaying several events -- separated by different dates -- in a view. First, in the `User.rb` model, you must create methods that use SQL methods to query inside Rails:

	def previous
    	attended_events.where('day < ? ', Date.new + 5)
	end
	def upcoming
    	attended_events.where('day >= ? ', Date.new + 5)
	end
  
Second, you call those methods in the `UserController`. This case it will be in the `show` action (you must also specify the user you are calling the method on first):

	def show
	   @user = User.find(params[:id])
	   @prev_events = User.previous
       @upcoming_events = User.upcoming
    end

Third, you display the `@prev_events` contents in the `show.html.erb` view:

	PREVOUSLY ATTENDED EVENTS:
	<%= render @prev_events %>
    UPCOMING EVENTS
	<%= render @upcoming_events %>
    
Finally, the view renders the corresponding (and brief) partial `_prev_event.html.erb`:

	<%= prev_event.description %>
    
######...using scopes instead

In the first step, we could use scopes. Here's how that looks like for the `Event.rb` model:

	scope :past_events, -> { where('day < ? ', Date.new + 5) }
	scope :upcoming_events, -> { where('day >= ? ', Date.new + 5) }
    
Then, in the `EventsController`, you can call the, say, `past_events` method like so:

	def index
	    @past_events = Event.past_events
    	@upcoming_events = Event.upcoming_events
	end

####Tidbits
######`form_for` with 'missing' paths
In Rails, one can type `rake routes` to find the name of the `create` path needed to submit form data into the database. However, sometimes the path is blank. In this case, you can type `url: { action: [action name] })`. This will send the form data to and through the `create` view:

	<%= form_for(:event, url: {action: "create"}) do |f| %> 
######`source`
`source:` tells us that the source of the `:attended_events` array is the set of `attended_event` ids. In this case, you could  leave `source:` out because Rails would singularize the `:attended_events`. 

	has_many :attended_events, through: :event_relationships, source: :attended_event

####Questions/Comments/Reminders
######`:event` vs `@event` for `form_for`
When the `EventsController#new` doesn't create an `@events` variable, `:events` is used instead
`events/new.html.erb`:

	<%= form_for(:event, url: {action: "create"}) do |f| %> 

######There's an [extra credit task](http://www.theodinproject.com/ruby-on-rails/associations).
    