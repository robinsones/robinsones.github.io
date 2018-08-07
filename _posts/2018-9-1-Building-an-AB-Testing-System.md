Points

I recently wrote a post on 12 guidelines for A/B testing. In this post, I want to discuss specifically if you're working on building an A/B testing system. That's what I've been doing at DataCamp over the past five months. While there are still best practices, you take less things for granted. Cavaet: I cannot comment on outsourcing A/B testing and using something like Optimizely, not something I've done. I also won't talk about the engineering side of setting up. I can share that DataCamp uses [splitrb](https://github.com/splitrb/split)
- Take a look at my other post (12 guidelines). All those points apply. 
- have a health check system and build it out separately from your "regular system" 
  - check all the things. We've had it where people were in the experiment who never saw the page, a huge spike in experiment starts halfway through the test, domain ids with no other events besides the experiment start, missing domain user ids. 
- make it easy to have a prioritize projects
- deliniate between different types 
  - traditional A/B tests onsite
  - new feature launch where you want to see how many people sign up (and maybe make sure doesn't hurt anything). This can be good when you do an MVP and decide if it's worth doing a full implementation (either expanding to the rest of the site or fixing the engineering behind it) 
  - email tests
- set a cadence for doing test discussion/speccing/analysis
- beware the lingering test. Set end dates
- if you're the analyst, make other people do some of the upfront work. Important - what is the audience for the test? 
- When should you start experimenting? It's a catch-22 - experiments can be a great way to grow your traffic, but you need traffic for your A/B tests to matter. 
- Not everything needs to be A/B tested. There is a cost to the analysis and set-up component. Two reactions - paralyzed and skeptical. https://twitter.com/robinson_es/status/1020082299029815296

