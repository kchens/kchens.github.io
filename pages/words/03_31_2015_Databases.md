#3 Important Databases To Know:  PostgreSQL, MongoDB, Redis

#PostgreSQL
As a relational database store, it comes built-in with sequences, table inheritance, and subselects. It also has plug-ins for multidimensional indexing, geographic queries, custom datatypes, and more.

Unlike MySQL, PostgreSQL can handle multiple indices (adding new indices without locking up the database for huge amounts of time). It also has more detailed error messages. 

It's fast, scalable, and reliable. It can handle *terabytes* of data. It supports advanced features and works with many different languages. (MySQL is generally really good for the LAMP stack)

Learn more [here](http://stackoverflow.com/questions/110927/would-you-recommend-postgresql-over-mysql).
#MongoDB
Released in 2009, MongoDB is a 'hu*mongo*us' player in the NoSQL world. Designed as a scalable database, MongoDB is a (disk-based) document-based database. That means it allows data to persist in a nested state, ***and*** query that data in an ad hoc fashion. 

With no schema, the documents can contain fields or types that no other document in the collection contains. Essentially, it's a JSON document -- imagine a big JSON object. 

#Redis
Also released in 2009 as "REmote Dictionary Service", Redis is a no-sql, key-value store. Reads are fast, and writes are even faster. It trades durability for raw speed. 

Redis is fast because the data is held in-memory. The data is cached. With ***built-in persistence to the disk***, Redis can be used as a real database instead of just a cache. 

Also referred to as a 'data structure server', Redis can handle complex data types; but not to the degree of a document-based object (like MongoDB). It handles set-based operations; but not to the degree of a relational database (PostgreSQL).

Redis can handle advanced data types like:  key-value pairs (stored as strings), Hashes, Lists, Sets, or Sorted Sets.

Overall, Redis is more like a toolkit of useful data structure algorithms and processes than a member of any specific database genre.

Said best on [StackOverflow](http://stackoverflow.com/questions/7888880/what-is-redis-and-what-do-i-use-it-for): *Redis is a fantastic choice if you want a highly scalable data store shared by multiple processes, multiple applications, or multiple servers. As just an inter-process communication mechanism it is tough to beat. The fact that you can communicate cross-platform, cross-server, or cross-application just as easily makes it a pretty great choice for many many use cases. Its speed also makes it great as a caching layer.*

#####Sources
Many thanks to the book <a href="http://www.amazon.com/gp/product/1934356921/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1934356921&linkCode=as2&tag=techs024-20&linkId=KDB7LBD2W5HZLVM6">Seven Databases in Seven Weeks: A Guide to Modern Databases and the NoSQL Movement</a><img src="http://ir-na.amazon-adsystem.com/e/ir?t=techs024-20&l=as2&o=1&a=1934356921" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
