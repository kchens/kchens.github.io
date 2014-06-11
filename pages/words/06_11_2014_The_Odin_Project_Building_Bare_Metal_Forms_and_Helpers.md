#The Odin Project:  Bare Metal Forms & Helpers
*Note: I started blogging a while after completing this project. This is my attempt to relearn what I learned.*

The Odin Project took a break from "real-world" projects in this lesson. Here's what I learned building forms in three different ways:

##RAILS
####The Easy
When building the `routes.rb` file, specify the `only:` option to specify which controller actions are permitted.

*	`resources :users, only: [:new, :edit, :update, :create]`
####The Hard
This took a while to get. Essentially, the root path (facebook.com/[blank]) is what you see when you visit www.facebook.com. In the case below, I've set the root path to whatever template is called in the index method within `users_controller.rb`.

*	`root 'users#index'`

####Tidbits
*	While the `user.rb` model is singular, the `users_controller.rb` is plural. `rails g controller Users`.

##HTML FORMS
####The Easy

To create `HTML` fields, the `type` is usually `text` (for usernames, emails) or `password` (for '***************').

*	`input type="text" name="[user][email]"`
####The Hard

For `HTML` forms,  the `action` specifies that data will be sent to the `users` route/controller. The `method` is POST because  (1) we are creating a user and (2) `rake routes` notes that the method is POST. 

*	`<form action="/users" method="post" accept-charset='UTF-8'>`

In accessing the `user_params`, one way is something similar to the `rails console`:

*	`@user = User.new(:username => params[:username], :email => params[:email], :password => params[:password])`

To get rid of all the params calls, we can create a `private` `user_params` method. Then , use it like so:

`def create
    @user = User.new(user_params)
end` 
`private`   
`def user_params
	params.require(:user).permit(:username, :email, :password)
end`

####Tidbits

*	The difference between `redirect_to` and `render` are slight. [GitHub](http://stackoverflow.com/questions/7493767/are-redirect-to-and-render-exchangeable) has a great graphic detailing the differences. In general, `render` will send the previous POST request again (possibly creating duplicates in the database); whereas `redirect_to` refreshes the page. For this The Odin Project, it's "simpler": 
>If you successfully save the user, you should **redirect** back to the New User form (which will be blank) and if you don't, it should **render** the :new form again (but it will still have the existing information entered in it). 

##RAILSY FORMS WITH `#form_tag`
####Tidbits
Simply switch the HTML to `form_tag` to create a POST method form.

*	`<%= form_tag('/users') do %>`

Use the appropriate tag:  `text_field_tag`, `password_field_tag`, `submit_tag`.

*	`Email   <%= text_field_tag(:email, "Your email") %>`

The `users_controller.rb` reverts back to the old, "brute force" way of accessing the user_params:

*	`@user = User.new(:username => params[:username], :email => params[:email])`

*Overall, `#form_tags` take care of the authenticity token, but nonetheless it's a lot of code. *

##RAILSY-ER FORMS WITH `#form_for`
####Tidbits
To set up the `form_for`, must first create a corresponding variable (`@users`) in the `user_controller#new`. 

*	`<%= form_for(@user) do |f| %>` uses...
*	...`def new; @user = User.new; end`

From then on, we can do the following under `form_for`


	<%= f.label :email %>
	<%= f.text_field :email, value: 'jack@jack.com' %><br>

	<%= f.submit "Create~!" %>