---
title: Migrating my Blog Site
---
Renewals came up on my hosting service for my blog site. So I thought it would be a good time to figure out the shortcomings of my hosting service and start shopping around.

The first thing I found that I needed from my hosting service was an affordable option for site encryption. My former hosting service didn't provide one. I loved what I was seeing with LetsEncrypt. It constantly rotates the certificate, and web browsers accepted certificates from LetsEncrypt. Also, it's free!

Unfortunately, my former hosting service did not allow me to have root privileges, which I needed to have in order to install the LetsEncrypt agent. Exhausting all other options to get encryption for my blog site at a reasonable cost, I decided it was time to shop around.

I found a lot of hosting providers provide great deals for new customers, cutting my hosting costs by almost half. Also, some of the hosting providers provided affordable options for encryption. They would allow me to set up encryption with LetsEncrypt for free. Or if I needed a higher level of trust with my certificate, they would provide one for an additional cost. Since this is my personal blog site, free is great!

Now that I have determined a hosting provider that cuts my hosting costs, has great reviews from customers, and does site encryption for free, I paid my hosting fee. Now time to start exporting my blog from one host to another.

Exporting the data from my former hosting service was not that painful. I quickly found my inexperience with the software hosting providers use for multi-tenanted hosting when I was trying to import my data. I spent about 3 hours one day trying to import my MySQL backup into the portal of my new hosting provider with no luck.

I finally stumbled across a blog post that gave me the information I was looking for. It is a simple point and click to get the backup into MySQL. I realized that I was trying to use my operations experience to do this work. I tried to get access to the database through logging into the host, and uploading the backup into the database. It just did not work. Hosting providers want common and easy tooling for their users. PHP and phpMyAdmin are common and easy for web developers.  Figuring out about the single point and click option in the portal was a game changer.

At the command line, it kept saying I didn't have root privileges, even though the credentials I created were supposed to be root. I was trying to use my systems experience, which is not applicable for blog hosting providers.  For a number of reasons, it held me up from bringing my site up for nearly a year. Frustration and life got the best of me.

What I took away from this experience is sometimes you need to think outside of the box. Also, relate the tool to the common user that is expected to use it.  With my experiences coming from working in operations, that is how I approached my problem of loading in a backup of my MySQL database. But the hosting provider has to deal with a different set of users. The customer wants GUI's. They want things "point and click". They want it easy.

