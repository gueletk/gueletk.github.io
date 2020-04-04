---	
layout: post	
title:  "Thinking about infrastructure"	
date:   2020-04-04 	
categories: infrastructure, cloud, aws	
---

Over the last several weeks, I've had the chance to work more with the DevOps side of things and with that came a growing awareness of some aspects of working with technology that up until now have been abstracted away from me. Since I don't have a more formal background in computer science, my introduction to programming was very web-first and I think if I want to become a better developer, I need to become aware of the different trade offs that are made when making specific design/infrastructure choices. 

Since infrastructure trade offs are an incredibly large topic, I'm going to shrink the question down to something more manageable: 

What needs to be considered when choosing a cloud hosted service on which to run a web server? I'm mostly familiar with AWS, but I think that the questions below are generic enough to apply to Azure, Google Cloud, etc

I'm not going to try and answer any of these questions yet, but I do want to come up with at couple questions that would be useful to ask. 

1. What is this server going to be used for? Is it going to be serving a user-facing app, a user-facing API or will it perform background tasks? 
2. What kind of (if any) database operations will it need to perform? Will it be fetching large amounts of data from a database? Will it be doing extensive calculations that will use a lot of CPU? 
3. Does it need to be accessible to everyone on the internet or do we need to be able to give access (whether full or partial) to a specific set of people? (For example: a paid API, a private QA server, etc) 
3. What kind of traffic do we expect? Do we expect a fairly consistent stream of traffic with occasional spikes or do we expect the majority of our traffic to come in at certain times?
4. How often do we expect to receive identical requests that can be given identical responses? AKA: how much data are we planning to cache? This depends on both the frequency of repeat requests and the frequency of data changes. A live stock market feed is going to use caching very differently from a blog that gets updated a couple of times a month. 
5. What regions of the world do we expect the majority of the users to be in? Do we want to rent servers in Asia or North America? Are there legal requirements that dictate the location of the servers (fintech, etc)?
6. How big (memory wise) is the server that we want to run? Is it going to be a large server (Django, Rails, etc) that handles multiple functions (API, user facing rendering, etc) or do we want to make a bare bones server that  (for example) wraps a machine learning model with a couple of simple routes, handles vector generation and little else?
 
