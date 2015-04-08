#What's the difference between ActiveModel, ActiveRecord, and ActiveResource?

#ActiveModel
Created for Rails 3, the Rails team took all the parts model related parts that did not have a database requirement and moved it into ActiveModel. It includes things like attributes, callbacks, validations, serialization, internationalization, and testing.

It is packaged together as a gem [here](https://rubygems.org/gems/activemodel/versions/4.2.1). 
#ActiveRecord
As you might imagine, ActiveRecord associates a class to a database. This gives the class functionality with the usual suspects of ActiveRecord methods (like `.where`, `.find`, etc.). Still, ActiveRecord inherits a lot from ActiveModel. 

#ActiveResource
If you are *manipulating* data via the web API and don't intend on storing anything on your server, use ActiveResource. It allows you to communicate between multiple Rails applications.

ActiveRecord is used for *retrieving* data and storing it on your web server. 

See more [here](http://stackoverflow.com/questions/12653296/difference-between-active-model-active-record-and-active-resource).