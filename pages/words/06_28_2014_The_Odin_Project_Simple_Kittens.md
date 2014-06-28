

####1. Building HTML Application
By this point, buliding an HTML form in Rails shouldn't be a problem. But because I've taken a few months hiatus, let's go through how to set up your controller, views, and partials.

######`index`
Odin asks to display all the kittens created in the `index.html.erb` view. To do so, I need to save all the Kittens to a `@kittens` variable in the controller like so:

	def index
	  @kittens = Kitten.all
    end
    
Now in the view, we can use "erb" tags to access the @kittens variable. However, before I show you the relevant code, let's think about this. What am I trying to do? 

I want to display each kitten's name, age, etc. In that vein, I will need a `.each` loop.

	<tbody>
    <% @kittens.each do |k| %>
      <tr>
        <td><%= k.name %></td> 
        <td><%= k.age %></td> 
        <td><%= k.cuteness %></td> 
        <td><%= k.softness %></td> 
      </tr>
    <% end %>
    </tbody>
    
(You might notice the `tbody`, `tr`, and `td` tags. They're simply to help create a table that helps display the kitten's attributes in a more defined format.)

Great! Finally, I want each person that accesses this page to be able to see more details about each kitten -- that way they can fluffily find the perfect one. 

Doing so within the `.each` is simple. 

	...
    <td><%= k.softness %></td> 
    <td><%= link_to "Details", k %></td>

You can see, the only thing we need is 'k' -- the kitten. Rails will handle the magic to make sure that, once you click, you are routed to each kitten's relevant show path.

######Creating `new` kittens
In the controller, let's call the model to create a new kitten and save it to a variable:

	def new
       @kitten = Kitten.new
	end

Now in the `new.html.erb` view, I could set-up the form to set the attributes for this new kitten. But, let's not. Both this view and the `edit.html.erb` will be using this same form to submit the kitten's `name`, `age`, etc. So instead, let's put the form in a partial and render the partial in the `new.html.erb`.

	<h1>Kittens#new</h1>
    <%= render "form" %>

Then in `_form.html.erb`:   

    <%= form_for(@kitten) do |f| %>
      <%= f.text_field   :name,     placeholder: "Name",    required: true %>
      <%= f.number_field :age,      placeholder: "Age",     required: true %>
      <%= f.number_field :cuteness, placeholder: "Cuteness",required: true %>
      <%= f.number_field :softness, placeholder: "Softness",required: true %>
      <%= f.submit "Enter kitten" %>
	<% end %>
Here, we are using a `form_for` because we're dealing with the model's attributes (as noted in [Flight Booker](http://www.kevinkchen.com/2014/06/16/the-odin-project-flight-booker/)).

Now, because the `form_for` creates a RESTful POST request, I can be assured that the form submission is handled by the `create` action. That's what the routes are for! (`resources :kittens`)

Here's how your `create` action should look:

	def create
    @kitten = Kitten.new(user_params)
      if @kitten.save
        redirect_to @kitten, notice: "Your kitten was purrr-fectly created."
      else
        render 'new'
      end
	end
    
It says, "If the new kitten (with the relevant parameters) can be saved, then I will redirect the user to that kitten's show path".

######Creating a `notice`/`success` message.
In the code above, `notice:` flashes a message at the top of the page: IMAGE

And, the only thing you need to accomplish this is to simply specify the `notice`.

Getting a `flash[:success]` message to work is different. For this, we'll need to open up the `application.html.erb` file and place the following code between the body:

	<div class="container" color="red">
    <% flash.each do |key, value| %>
      <div class="alert alert-<%= key %>"><%= value %></div>
    <% end %>
    <%= yield %>
    </div>

With this code, I will now see the `flash[:success]` message at the top of the view's page. We can see it like so in the `Controller#update`:

	def update
      @kitten = Kitten.find(params[:id])
      if @kitten.update_attributes(user_params)
        flash[:success] = "Kitten was purrr-fectly updated."
        redirect_to @kitten
      else
        render 'edit'
      end
    end

Now, the `update` view should display a similar display message to `notice` above.

######Adding an "Edit" link
Here's's a problem:  What happens if I made an error in my record keeping? Perhaps, I pressed enter one too many times. Maybe I made a typo; the kitten is really only '4' cute, not the max of '5'.

In that case, I need a `delete` link and an `edit` link.

Back in the `index` view, let's add an edit link:

	<% @kittens.each do |k| %>
    .
    .
	<%= link_to "Edit", edit_kitten_path(k) %>
By placing the `k` inside the `edit_kitten_path`, I can be sure that the link takes me to the edit view for the right kitten.

######Adding a "Delete" link

    <td><%= link_to "Delete", k, method: :delete, 
                confirm: "Are you sure?" %></td> 
                
To delete the kitten `k`, I need to specify the method I'm calling. The reason I can't simply use `delete_path(k)` is because there isn't a `delete_path`! `rake routes` and see for yourself.

####2. Making Kittens Available via API
Turning this kittens website into an API is really simple. For data that I want to be available as an API, I render it in JSON.

Here, I want to let developers access all kittens and find details on a specific kitten. We do this with `respond_to` and the corresponding `variable`. For this controller, it's `@kittens`.

	def index
      @kittens = Kitten.all
      respond_to do |format|
        format.html
        format.json { render json: @kittens }
      end
    end

In the show, it's `@kitten`:

	def show
      @kitten = Kitten.find(params[:id])
      respond_to do |format|
        format.html
        format.json { render json: @kitten }
      end
    end
    
That's it! We've created an API.

####Tidbits
######`scaffold` vs. `controller`
You can use `rails g scaffold` to generate a controller with the 7 RESTful routes. However, `scaffold` first generates a model, then controller, routes, views, and test stubs. See [here](http://stackoverflow.com/questions/17734378/difference-between-scaffold-and-model-in-rails) for more.

But the regular `rails g controller` along with `index`, `new`, etc. may be better. Using `controller` (along with `model`) instead of `scaffold` allows for more customization. 