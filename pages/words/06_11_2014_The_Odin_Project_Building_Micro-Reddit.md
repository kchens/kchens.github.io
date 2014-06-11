#The Odin Project: Building Micro-Reddit

*Note: I started blogging a while after completing this project. This is my attempt to relearn what I learned.*

[The Odin Project](http://www.theodinproject.com/ruby-on-rails/building-with-active-record) entices programmers to learn by copying popular, real-world start-ups. In this case, [Reddit](http://www.reddit.com). Here's what I learned:


####The Easy
Database Modeling:  A User model (User.rb) `has_many` Posts, a Post (Post.rb) `belongs_to` a user. And Comments (Comment.rb) `belongs_to` a User and a Post.

####The Hard

Keeping track of rails console. As the `create_posts.rb` migration references (has an index) the User model, this creates the `**:id** => 1`

*	*Implementation:* `User.create(:username => "jackjohnson", :id => 1)`


However, because Post belongs to a User, the correct way to match the id is `**:user_id** => 1`

*	*Implementation:* `Post.create(:title => "banana pancakes, :user_id => 1)`

####The Tidbits I Shouldn't Forget

When generating a model with, don't forget to add the columns (aka. the information associated with the User).

* *Implementation:* <code>rails g model User **username:string password:string [column_name]:[data type]**</code>

Validations occur within the model file `User.rb`. Start with `validates`, then list then attribute that needs validating.

* *Implementation:* <code>**validates :username**, presence: true, length: { minimum: 6, maximum: 40}</code>


