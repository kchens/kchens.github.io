---
layout: post
title: switching to jekyll
---

{{ page.title }}
================

<p class="meta">10 October 2014 - San Francisco, CA</p>

In creating my own blog, the most upsetting thing for me was that I had to start the css from scratch. Moreover, I wouldn't be able to save my content separate from the HTML file. Now, with Jekyll I can do that and much more.

I first came across Jekyll four months ago, but opted to use the Ghost blogging platform because I would have online access to a markdown editor. It was a great choice at the time -- Ghost got me addicted to writing in markdown. 

In starting to blog for Dev Bootcamp, the thing I found most frustrating was that I had to specify dates, titles, and css multiple times over different HTML files (like specifying the date on the `index.html` and `post.html`). What a massive waste of time.

With Jekyll, I now have the benefits of ruby inside the HTML to save time. Currently, this markdown file `post.md` has the following head:

	---
	layout: post
	title: switching to jekyll
	---
	
	{{ page.title }}
	================

	<p class="meta">10 October 2014 - San Francisco, CA</p>

Now, if I want to the title to display across within the post and the homepage, I specify it in the `title: (POST TITLE HERE)`. Then, it gets displayed in `{{ page.title }}`.

Likewise, given the way that the Jekyll files are set-up, the date is similarly displayed when entered here: `<p class="meta"> (DATE HERE) </p>`

This is just one level of separation. Jekyll also has folders so that we can create different HTML layouts - hence the above `layout: post` for the post layout - and CSS.

There are many more features to be excited about, but, for now, let's get back to blogging.