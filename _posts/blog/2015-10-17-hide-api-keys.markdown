---
layout: post
title:  "Protecting Your Twitter API Keys in Node.js with gitignore"
date:   2015-10-17 19:28:51
categories: blog
featured: true
comments: true
excerpt: "Protecting Twitter API keys on Github Using Node.js"
---

If you need to push your code to github for a node.js app that uses the Twitter API, here are the steps that you can take to protect your keys, by using gitignore.

* Create a separate file that stores your api keys, let's call it twitterKeys.js

{:.centered}
![twitter credentials img](/../../img/twitter-info.png)


* Require the twitterKeys.js files in the file that you wish to extract data required using the API.

``` javascript
var keys = require('./server/twitterKeys');
```

* Now that you 'required' the file that contains your Twitter API credentials, you can access them as properties of the keys variable you created above.

{:.centered}
![twitter credentials img](/../../img/keys-props.png)



* Be sure to add your file that contains your personal information to the gitignore file, before you push your code to GitHub.


