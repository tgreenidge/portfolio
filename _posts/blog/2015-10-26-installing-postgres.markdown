---
layout: post
title:  "Reinstalling PostgresSQL on Mac"
date:   2015-10-26
categories: blog
featured: true
comments: true
excerpt: "Instructions for reinstalling Postgres on Mac"
---

I recently had issues connecting to a PostgreSQL (Postgres) database on my local server, and had to perform quite a few steps to get it working properly. The following commands should be run in the terminal. Since I had a version that was installed on my machine a couple of years ago, I had to remove my previous version by performing the first step below. 

**Remove previous versions of Postgres**

````
brew uninstall --force postgresql and rm -rf /usr/local/var/postgres
````


**Install Postgres with Homebrew**

````
brew install postgresql -v
````


**Since it is your first time running Postgres after installation, you will need to run the following to initialize the Postgres database**

````
initdb /usr/local/var/postgres
````

It may look like you received an error, but don't worry, this is not the last step.

{% highlight bash %}
initdb: directory "/usr/local/var/postgres" exists but is not empty
If you want to create a new database system, either remove or empty
the directory "/usr/local/var/postgres" or run initdb
with an argument other than "/usr/local/var/postgres".
{% endhighlight %}

**Remove old database files**

````
rm -r /usr/local/var/postgres
````

**Run the initdb command again**

````
initdb /usr/local/var/postgres
````


You should now receive a message of success! 

**Start the Postgres database server**

````
postgres -D /usr/local/var/postgres
````

###Username and password
Note that your username for your local Postgres database is shown in the following, which is part of the success message on installation.

{% highlight bash %}
The files belonging to this database system will be owned by user "this_is_your_username".
This user must also own the server process.
{% endhighlight %}

Your password by default is "postgres" 
