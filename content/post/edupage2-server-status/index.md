---
title: "Edupage2 Server Status"
date: 2023-12-18T17:04:28+01:00
draft: false
description: A short summary of the current EduPage2 situation
tags:
  - EduPage2
  - Server
  - Status
image: cover.png
---

## EduPage2 Servers are down
For over two weeks now, the EduPage2 app has been non-functional. This is due to the servers not working as they should. 
In this article, I will explain exactly what is happening and what will be done about it in the future.

## Possible causes
I do not have many theories about why the public servers aren't working and private ones are, but here are a couple.

If you have any other theories or ideas, I'd be glad to hear them. You can join our discord [here](https://discord.gg/zP4xfz2g8U)

### Rate-limiting by Edupage
One posible answer is that the EduPage2 servers are getting rate limited by edupage. But this doesn't quite make sense.
First of all, if it is rate limiting, shouldn't the servers be able to resume normal operation after some period of time?

Second, in schools there are often hundreds of people accessing edupage at once. It is possible that they have some database 
of IP addresses that belong to schools, but I don't really think so.

### Out-dated login method
The current EduPage2 server uses an older method of logging in to edupage. It is possible that edupage has implemented some 
check, to see if the client isn't using a very old version of the app. But again, something doesn't make sense. In this case, 
if the login method is outdated, why do private instances of the server still work?

### EduPage2 servers getting blacklisted
This would also be a valid option, but I don't really see a reason for them to do something like this.

## How I'm planning on fixing this
I'm planning on looking into this issue during the winter break. There are a couple potential fixes, but I have no idea if they will work, 
and if they do, will it really be an ideal fix?

### Update login method
Probably the first thing that I will try is to update the way that the server loggs the user in. This involves some work, monitoring requessts 
made by the official apps, trying to adapt the data to other accounts, etc.

### Get PHPSESSID on client
This would also be an option, it would involve only small modifications to the codebase, and it might be a little more secure, because the end-user's 
login information would never be sent to EduPage2, only the PHPSESSID cookie would. EduPage2 would then be able to access all data as usual using this token.

### Direct access to edupage
This is another option, it would involve rewriting all the server code from golang to dart, and adapting the app to use it instead of a server.
This seems like a good approach, but it also has a couple disadvantages. First of all, directly accessing edupage is slow. 
Edupage sends a lot of 'useless' information, which makes it a lot slower. That is the whole reason why I made EduPage2.
Second a bunch of other smaller features can't work without the server, for example push notifications.

## A short backstory
So around two weeks ago, I noticed that users (including me) were unable to login to the EduPage2 app. 
It was a little wierd and unexpected, as there were no major recent changes to the codebase.

### But it works locally
To try and isolate the issue, I downloaded a local copy of the code, and ran it on my personal computer.
After some testing, it was clear that there was no issue with the server's code. It all worked as expected.
When I tried pointing my phone to the local server, it loaded up and worked as usual.

### Server working for 3 days
So obviously the app and server were working correctly, so what else could be causing this issue?
While trying to answer that, I set up a new server hosted on heroku. When the server had finaly been built and started,
I tested it with the EduPage2 app on my phone and it worked! I was happy to have the issue resolved and I used firebase remote config
to remotely redirect all trafic from the app to the new heroku server. Everything worked, but only for 3 days.

3 days later, when I arrived at school, the app wouldn't load again. I took out my laptop, and tried to directly communicate with the server,
and nothing. Every time I wanted to login, it timed out waiting for a response from edupage. 
### And that is where we are now
None of the public servers are working, but local private instances still work.