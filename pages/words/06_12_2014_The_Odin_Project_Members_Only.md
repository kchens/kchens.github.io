####The Easy
To check if user submit the proper password, use the `#authenticate` in the `SessionsController#create`:

	if user && user.authenticate(params[:session][:password])
    .
    .
    end
####The Hard
######Creating cookies with `remember_token`
First, add `remember_token` attribute to the *Users* table.

	rails g migration add_remember_token_to_users

Second -- now in the `User.rb` file -- create a remember token with a randomized string:
	
    def User.new_remember_token
		SecureRandom.urlsafe_base64
	end

Third, encrypt the token in a hash:

	def User.hash(token)
		Digest::SHA1.hexdigest(token.to_s)
	end

Finally, use a `before_create` callback in the User model to `private`-ly create the remember token.

	private

	def create_remember_token
    	self.remember_token = User.hash(User.new_remember_token)
	end

######Setting Current User
Given the following, what does the `current_user=` method do?

	def sign_in(user)
    	.
    	.
	    self.current_user = user
    end
	
	def current_user
	    #pulls token from browser, then hashes it
    	remember_token = User.hash(cookies[:remember_token])
		@current_user ||= User.find_by(remember_token: remember_token)
    end	
    
    def current_user=(user)
    	@current_user = user
	end
	
Essentially, `self.current_user =` is actually calling the `current_user=` method. I'm not sure, but I think it's a way to simply break up the two methods (so that `sign_in` doesn't encroach on `current_user=` territory).
####Tidbits
######`has_secure_password` & `password_digest`
To use the [`has_secure_password`](http://apidock.com/rails/ActiveModel/SecurePassword/ClassMethods/has_secure_password) validation method, the `user` model (`User.rb`) must also have the `password_digest` attribute. This can be done by the following:

	rails g model User username:string password_digest:string

As a result, the User now has a `password` and `password_confirmation` attribute. So, when creating a user, these attributes must match:

	user = User.new(name: 'david', password: 'matching', password_confirmation: 'matching')

If you forget to add `password_digest`, you can create a migration. Submitting the following code should create the relevant column in the `users` table (notice the plural):

	rails generate migration add_password_digest_to_users password_digest:string
    
######Tidbitty-Tidbits
To find a user based on an attribute, you can use `find_by` to access the `params` hash. Below is an example (downcase is used because email is a string): 

* 	`user = User.find_by(email: params[:session][:email].downcase)`
    
To create a link in a view -- one with the appropriate HTTP request -- `rake routes` to see the correct path:

*	`<%= link_to "Sign out", signout_path, method: "delete" %>`

To set a post's foreign key to that of the author's (user_id):

	@post = Post.new(post_params)
	@post.user_id = current_user.id`