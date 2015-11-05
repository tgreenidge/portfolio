---
layout: post
title:  "Protecting Your Twitter API Keys Using Environmental Variables"
date:   2015-11-05 19:28:51
categories: blog
featured: true
comments: true
excerpt: "Protecting Twitter API keys using environmental variables"
---

In a [previous post](http://www.tgreenidge.com/blog/hide-api-keys/), I showed you how to protect your twitter keys from being published online when pushing your project to Github. Should you need to deploy your project, however, you will need to create environment (configuration) variables as well, so that your keys can be access both locally and your online server. In this post, I will show you how to modify your code to use environmental variables and how to store those variables if deploying with Heroku.

### Heroku Configuration
When you create an app on Heroku, you can change the settings for your app, such as setting up your domains, changing the name of the app, and changing your config variables. To change your config variables, click "Reveal Config Vars" tab that is found under "Settings" on your app's dashboard. You can then add the information for your API keys here. The picture below shows an example oh how this is done. You may also review the [documentation that heroku provides](https://devcenter.heroku.com/articles/config-vars), which includes information for using the command line to set up environmental variables.

{:center} 
![heroku config variables img](/../../img/heroku-config.png)

### Node.js Configuration
Now we will be modifying the code that was posted in my [previous post](http://www.tgreenidge.com/blog/hide-api-keys/). Since we want to have access to the API keys on both our local and deployed server, we need to point to both variables, since they have been set up differently. 

In Node.js, prepending environment variables with "process.env." allows your server to access parameters from the environment the app is running on. For example, since the twitter consumer key variable was set up as "TWITTER_CONSUMER_KEY" on heroku, to access when deployed, twitter.consumer_key will be mapped to process.env.TWITTER_CONSUMER_KEY. If running on our local server, the consumer key may be accessed using keys.consumer_keys as explained before. 

As you may recall, "||" is the "OR" operator in javascript. Hence, for each property of the twitter instantiation below, you tell the server - "Get me the variables that were set up on Heroku, if running on Heroku, or the ones that were set up for local server, if running on the local machine."

{% highlight javascript %}

var twitter = new twitter({
    consumer_key: process.env.TWITTER_CONSUMER_KEY || keys.consumer_key, 
    consumer_secret: process.env.TWITTER_CONSUMER_SECRET || keys.consumer_secret,
    access_token: process.env.TWITTER_ACCESS_TOKEN || keys.access_token,
    access_token_secret: process.env.TWITTER_TOKEN_SECRET || keys.access_token_secret
});

{% endhighlight %}

### Conclusion
Although my posts only focused on protecting your twitter API keys, environment variables may be used to set up other server configurations, for example, ports, and database configurations.


