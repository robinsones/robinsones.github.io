A few weeks ago, I [wrote about](https://robinsones.github.io/Giving-Your-First-Data-Science-Talk/) my experience giving my first data science talk. If you're interested, the full talk is available [online](https://www.youtube.com/watch?v=SF-ryGgLOgQ), as well as the [slides](https://github.com/robinsones/AB-Testing-Slides). In this post, I wanted to share some suggestions for managing business challenges that I didn't have time to cover in my talk. 

### Why Business Challenges? 

Why devote a whole post and half a talk to business challenges instead of, say, cutting edge deep learning papers or the shiny new language for handling Big Data<sup>TM</sup>?

While basic technical skills are the table stakes for a data science career, the importance of non-technical skills in a data science career is often overlooked. I think Yonatan Zunger, a former senior Google engineer, covers this very well in the second section of this [post]( https://medium.com/@yonatanzunger/so-about-this-googlers-manifesto-1e3773ed1788). While he's talking about engineering, his points can be equally applied to data science: 
  
> People who haven’t done engineering, or people who have done just the basics, sometimes think that what engineering looks like is sitting at your computer and hyper-optimizing an inner loop, or cleaning up a class API... Engineering is not the art of building devices; it’s the art of fixing problems... Essentially, engineering is all about cooperation, collaboration, and empathy for both your colleagues and your customers.

At Etsy, each of the analysts works with a partner team, including marketing, seller services, retention and loyalty, and finance. What we help them with can vary a lot. I mainly help design and analyze experiments for search, while other analysts create dashboards in Looker, new tables to make data access easier, or models for estimating the lifetime value of a new customer. While we may be especially deeply embedded with partner teams, all data scientists and analysts (or their managers) will have to work with non-analysts<sup>1</sup> sometimes. While I still have a long way to go, I wanted to share some advice and techniques I've found helpful.

Strategies for Managing Business Challenges
======

**Don't Feign Surprise**

To be a successful partner, you need to make sure your team is comfortable asking you questions. One way to almost guarantee that they won't be is to "feign surprise." 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&quot;no feigning surprise&quot; (from the wonderful <a href="https://twitter.com/recurse">@recurse</a> manual: <a href="https://t.co/Zk7ZQZqSbL">https://t.co/Zk7ZQZqSbL</a>) <a href="https://t.co/ZPc07LlFle">pic.twitter.com/ZPc07LlFle</a></p>&mdash; ⚡Julia Evans⚡ (@b0rk) <a href="https://twitter.com/b0rk/status/846864384731365376">March 28, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Many Etsy engineers come from the [Recurse Center](https://www.recurse.com) (formerly known as Hacker School), a free six or twelve week self-directed retreat for programmers. The Recurse Center has a set of social rules (along with a code of conduct) to make the environment productive and supportive for everyone. One of those is no “feigning surprise” when people admit they don’t know something. As they [put it](https://www.recurse.com/manual#sub-sec-social-rules): 

> Feigning surprise has absolutely no social or educational benefit: When people feign surprise, it's usually to make them feel better about themselves and others feel worse. And even when that's not the intention, it's almost always the effect. As you've probably already guessed, this rule is tightly coupled to our belief in the importance of people feeling comfortable saying "I don't know" and "I don't understand."
 
You also shouldn't make assumptions about what your audience knows. Even if you live p-values and confidence intervals day in and day out, they don’t. You should lean on the side of always defining terms, which will also help in the case people think they know what something means but they actually don’t (very common with p-values).

**Develop empathy**

The Microsoft experimentation platform team put it best [when they said](http://notes.stephenholiday.com/Five-Puzzling-Outcomes.pdf): "our job ... is to tell our clients that their new baby is ugly." As they discuss, while teams build new features or products because they believe they'll be useful, most experiments testing those new features reveal they don't have a positive impact. Teams are often emotionally invested in their new feature: they've spent a lot of time working on it, and it was often one of the team members who came up with the idea in the first place. There may also be financial investment if a company has tied bonuses or performance reviews to experiment success. 

Even though I knew this intellectually, it took me time to develop empathy, and it's still something I'm working on. It can be frustrating when you have to correct misinterpretations of seemingly "positive" results from peeking or [slicing data in every possible way](http://www.slate.com/articles/health_and_science/science/2013/07/statistics_and_psychology_multiple_comparisons_give_spurious_results.html). It's useful to remember to take a step back and see that you have the same overarching goal: for your team do well and thus help the company. 

**Invest in Education Efforts**

Think about how you and your team can help non-analysts understand and make data-driven decisions. First, it will save you time. If an engineer knows they'll need to record the listings that are eligible for a new badge in the variant *and* the control, so you can compare clickthrough rates, or the product manager knows how to use experimentcalculator.com and discovers their experiment would take 150 days to be appropriately powered, that's one less question they'll have to ask you. But second, many companies profess they want to have data-driven decision making. This doesn't work if only the analysts can understand data, and so companies are investing in wider data education efforts: 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Data University is our effort to help every person at Airbnb make data informed decisions - come read how!  <a href="https://t.co/2HjZxnkjHK">https://t.co/2HjZxnkjHK</a></p>&mdash; Airbnb Data (@AirbnbData) <a href="https://twitter.com/AirbnbData/status/867514655060615168?ref_src=twsrc%5Etfw">May 24, 2017</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

At Etsy, we’ve been working on a multi-pronged approach to education. The data engineering team developed an experiment hub, where they’ve gathered documentation about our various tools. Evan D'Agostini, another analyst, and I wrote a general guide to experiments at Etsy, and also gave an “Edsy,” an internal talk, on it. I’m now experimenting with offering office hours for people to come with general questions about experimentation. Finally, we have a Slack channel dedicated to experiment questions, monitored not only by data analysts but also by experiment-savvy engineers.

**Develop consistency among the Analyst Team**

Working with partner teams becomes much easier if you have some consistent standards and practices within the analyst team. For examples, here are some differences that can cause problems: 

- If your team thinks you're stricter than other analysts in judging experiment results 
- If analysts are calculating incremental revenue from experiment launches differently 
- If one analyst says you have to run experiments for at least a week, even if you're powered before then, while others say four days is fine

Working to develop consistency is also a great opportunity to learn for each other. For example, some analysts may not be as familiar with the problems of peeking, which may be why they weren't as strict on not doing so. That kind of information-sharing can also help make a smoother transition when a partner team has to change analysts. 

**Lay Out Hypotheses Before A/B Tests**

Lay out hypotheses ahead of time, especially about whether you will launch on a neutral result (when it's inconclusive whether your metric went up or down). People often think they don't need to have specific hypotheses beyond "we'll launch if it's better," because they think results will be really clear. But you’ll be surprised at the sheer combination of results that are possible (e.g. search clicks went down, but mean search purchase went up, and conversion is neutral, but add to cart is slightly down, etc.). Picking one or two key metrics for launch and a few other metrics for monitoring will also help you from having a multiple comparisons problem, where you're [testing so many metrics one of them will be significant](https://en.wikipedia.org/wiki/Multiple_comparisons_problem), even if there really is no change. 

Next Time
======

In my next post, I'll continue sharing what I've learned about business and statistical data science challenges from reading papers on A/B testing in industry. I’m also working with another Evan D’Agostini on a post for Etsy’s engineering blog, Code as Craft, on one of the statistical challenges I covered in my talk, developing a test for differences in Average Converting Browser Value between groups. 

1. I'm using "non-analyst" as a catch-all phrase for anyone who isn't in analytics (e.g. not a data scientist, business analyst, data analyst, etc.). 
