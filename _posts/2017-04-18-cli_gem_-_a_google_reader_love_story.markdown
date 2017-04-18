---
layout: post
title:  "CLI gem - A Google Reader Love Story"
date:   2017-04-18 23:17:43 +0000
---

In 8th grade, I found Google Reader while browsing the web and immediately fell in love. It was perfect. It was a period of time before facebook news was a thing, and when people paid for newspapers. Google reader aggregated information from almost every source I cared about and brought them all to a interface. I viewed the world through that tiny portal. 

When the service was discontinued in 2013, that form of information consumption didn't die with it. RSS and RSS readers, on which Google Reader was essentially, continued to thrive. I myself migrated to inoreader, which recreated the entire google reader experience that I continue to use today.

When given the challenge of creating a CLI gem, I immediately thought about the experience that I had with Google Reader and how it provides content access like no other. Although most websites out there generates official RSS feed for users, when one does not exist, people create unofficial pipes that generated RSS for them through scraping the websites.

In this CLI gem I went though the process of scraping CBC news's trending page, and present it to the user in CLI at the user's request. Each article is stored as an object with attributes. Although a CSS/XML file was not generated. with the information scraped and stored as objects it should be very easy to recreate.

Through this project I realized the hardest part of coding a small project like this is not making it function but staying organized and following proper OOP best practices. It is often tempting to put functionalities where they are not best placed (eg. scraping functionality within the Article class), and may make adding functionalities in the future, troubleshooting or maintanance troublesome.

In the future, it is probably a much better idea to plan the structure out fully in advance (which I did not), because I definitely had to rewrite alot of code after realizing lapses in logic. It will also most likely significantly decrease code refractoring time.

The gem is hosted [here](https://github.com/bryanhou1/canada-news-cli-app).


Any feedback is welcome!
