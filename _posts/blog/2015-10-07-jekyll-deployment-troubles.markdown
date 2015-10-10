---
layout: post
title:  "Jekyll Site Deployment With Google Domains"
date:   2015-10-07
categories: blog
featured: true
comments: true
---

For the first couple of days at Hack Reactor, we have been focusing on polishing our resumes. That coupled with the fact that I listed my domain on my Greenfield Group Project site, is driving me to get my site up and running. I something that I want to show to the world, and I am using Github Pages as my platform. 

### Google.com Domain
Did you know that Google now sells domains? I purchased my domain from Google after learning that GoDaddy would charge me $103, because I previously had a domain through them that expired. I am no longer eligible for their awesome discounts - ughh. My domain purchased through Google only cost me around $12 per year, with the following features as extracted from [Google Domains Help page](https://support.google.com/domains/answer/6010092?hl=en):

  >Features included at no additional cost

  >Whois privacy

  >Domain forwarding and subdomain forwarding

  >Email forwarding (forwarding of email aliases @<your domain>)

  >Google nameservers with 10 million DNS resolutions per year

  >Support via help center, email, chat, or phone. 

While I may not have use for email fowarding just yet, it is a nice to have. However, the Whois privacy is an amazing (FREE) feature that allows me to hide and protect my personal information that is associated wirh my domain since I am the owner of the domain. When queried, all my personal info, with the exception of my name, points to a third party company in New Zealand. 

### Github hosting
To use Github pages to host my site, I had to create a branch called gh-pages and push to that branch. There is some setting up involved, so I will give you an overview. 

Github has some documentation for setting up custom domains with Github Pages [here](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/). According to the instructions, I had to create a file called CNAME (no additional file extensions like '.txt' required) in my root directory. The only information that this file contained was the name of my site like below:

{:.centered}
![cname img](/../../img/cname-img.png)

I then had to [configure an A record](https://help.github.com/articles/tips-for-configuring-an-a-record-with-your-dns-provider/) with Google, my DNS provider. Below is a snapshot of how I entered this information in my DNS configuration settings on my admin page on Google Domains.

{:.centered}
![google settings img](/../../img/google-settings.png)


I made the mistake of leaving the baseurl as the name of my repo for this site on github, and was horrified to see that all my styles were stripped from my custom domain. 

{:.centered}
![config-settings img](/../../img/domain-img.png)

If you previously used gh-pages as your domain, be sure to change the baseurl and url in your _config.yml file, so that all your images, css and sass can be displayed.

{:.centered}
![config-settings img](/../../img/config-settings.png)

Once I made the correction, all was well again with the world!

{:.centered}
![config-settings img](/../../img/gh-pages-img.png) 

