---
layout: post
title:  "Displaying Code Blocks in Jekyll"
date:   2015-10-25
categories: blog
featured: true
comments: true
excerpt: "Instructions for displaying code blocks in Jekyll"
---

Until recently, posting blocks of javascript code has been such a challenge. I followed the directions of so many markdown "cheatsheets" online, to enclose code with tick marks and the stipulated language. The result, as shown below, is inline and did not preserve indentation of code. You may have noticed that with the exception of my last post, I had been posting screen shots for code that spanned more than one line as a work around. Since images take up more space than text, I needed to find a solution fast, as I plan to include code in the majority of my posts.

``` javascript
var name = "Alice";
var function = alertMessage(){
  alert("Hello, " + name);
  var name = "Bob";
};
alertMessage();
```

### The Solution
So here's how you do it - simply wrap your code with liquid "highlight" tags as shown below.
{% highlight liquid %}
{%  raw %}
{% highlight language %}

var name = "Alice";
var function = alertMessage(){
  alert("Hello, " + name);
  var name = "Bob";
};
alertMessage();

{% endhighlight %}
{% endraw  %}
{% endhighlight %}


I replaced the word "language" with "javascript", and look at the difference in appearance when I wrapped the same code in the liquid tags! The block of code displayed with the indentation exactly as I intended.

{% highlight javascript %}
var name = "Alice";
var function = alertMessage(){
  alert("Hello, " + name);
  var name = "Bob";
};
alertMessage();
{% endhighlight %}

### Showing liquid tags on Jekyll
Of course I then had problems getting my liquid tags to show up on this jekyll post (they were invisible on the page), so I had to spend extra time trying to figure it out. Fortunately, I came across a very detailed [blog post](http://fatpixels.me/programming/displaying-liquid-tags-in-jekyll/) by Krishanashish Gogoi, which helped me help you! I srongly encourage you to check it out.