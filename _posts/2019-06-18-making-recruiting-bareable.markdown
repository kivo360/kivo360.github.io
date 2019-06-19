---
layout: post
title:  "Making Recruiting Bearable Using Financial and Data Science Theories!"
date:   2019-06-18 19:57:43 -0400
categories: recruiting financial
---

# Recruiters Have A Difficult Job

I recently ventured into the jaws of the Detroit Startup week. Throughout the entire day I had the chance to speak to various individuals (both developers and recruiters) about breaking through information asymmetry inside of the recruiting industry. Generally, you want to do this when you have to do recruiting for highly leveraged roles because the amount of money paid for the role will be high, while the impact done will also be high. Imagine paying a team of engineers 1 million dollars throughout the year, only to realize that they destroyed some designs for your infrastructure because they couldn't come to a consensus of what needed to be done. That 1 million dollars could end up wasted and the damage could be done. 

The major problem faced is that there's really no way to tell who knows what inside of the space. Topping that problem, it's awfully difficult to determine exactly what you need for a role. The more novel and new the role is, the more difficult it is to understand what needs to be added into the company and what you should hire for. You don't want to hire the wrong person, nor do you want to hire for the wrong skill set. Generally speaking recruiters try to avoid making the wrong decsions using **signalling theory** and by copying what other companies do. Some tricks recruiters use to have certainty in an uncertain world:

* They'll use other company's tech  because the stack they use works for the other company, meaning they instantly know what they should hire for. (this is signalling)  
* They'll run highly complex interviews that originated from other companies. It may or may not be an accurate representative of the work that would be done at the company. (this is signalling)
* They look for brand name companies on people's resume. The idea goes if the person was good enough to be accepted at a great company, then they must be good enough to be accepted at their company as well. (this is signalling)
* They state senior roles on job boards with extremely high requirements, when realistically the requirements don't have to be met for the job. (this is signalling)
* They'll look for people that have posted a blog or library that's recently receieved a major amount of attention in the industry. The logic that runs here is that if attention is scarce, and the developer is good enough to capture it, the developer must be very good. (this is signalling)
* Introducing high pay for a role to scare people that don't deserve the amount paid. (this is signalling)


In case you're wondering what signalling is, the Wikipedia economics explaination explains it best:

> *"One party (termed the agent) credibly conveys some information about itself to another party (the principal). For example, in Michael Spence's job-market signalling model, (potential) employees send a signal about their ability level to the employer by acquiring education credentials. The informational value of the credential comes from the fact that the employer believes the credential is positively correlated with having greater ability and difficult for low ability employees to obtain. Thus the credential enables the employer to reliably distinguish low ability workers from high ability workers."*

***Signalling*** is about revealling some information required to make a solid decision for the case you have when you can't possibly have all of the information. 100% of the methods I explained are forms of signalling. However, *there's a major trade-off that's made*. If recruiters all demand a certain kind of credential out of the belief that the signal has a high correlation to proficiency, eventually agents (job seekers), will go through the efforts of exploiting that credential given it doesn't have too high of a cost. The issue is that as more people get the signals you demand (involuntarily), the weaker those signals will be over time. The signals will eventually become noise, and the job of the recruiter will become exponentially harder. Making matters worse, if the barrier to entry is too high, you end up leaving major positions unfilled. 


This is the main problem when it comes to recruiting for tech companies in the modern age. The result is a *talent shortage*. The shortages don't necessarily exist, however, to beat the competition a company generally has to play a game of **moneyball**. By having a set of theories that allow any company to both explore new possible candidates and exploit discovered positions, positions will generally be better filled. At the end of the article I will give 10 ideas for using hackathons and open source to do such a thing.


## Explore-exploit Trade-off

The explore exploit trade-off is very common and obvious inside of the Hollywood industry. So we'll start with them to showcase what it looks like:

> *Your small movie production business has had a few hits over the years and you’re trying to work out what your next project should be. You know that if you did a sequel of an old classic it would have mediocre returns. Alternatively, you could try a hot new idea which is highly unpredictable: it could nosedive, meaning you don’t recover what it cost you to make it, or it could be the next Harry Potter series.*


Movie studios generally get caught in a scenario where they have to balance exploring and exploiting new movies for the long-term. During times when cost are tight or when profit is more important, studios go for sequels that are cash cows, other times, they make bets to find the next greatest thing. 

Recruiters face the same exact problem. They go with proven technologies and pre-existing signals to reduce risk, yet they need to sometimes go for new risky paths to find something that will be marginally better for them. The big question now is how to properly balance risk and reward. The way one person suggested was to use a 1 day hackathon as a means to filter candidate's skills. I was queried about what kinds of hackathons could exist out there to do just that. 

I say that hackathons are both a way to explore candidates and explore new tech stacks that can exponentially grow the community the area is apart of. Without further ado, I'm going to give some ideas on what types of hackathons can be done to improve the degree of exploitation of old ideas and exploration of old ones.




## 10 Hackathon Ideas
---
1. Tut-hack - Find existing tutorials and add a special twist on them to have very presentable ideas
2. Build a start-up hackathon - This type of hackathon will showcase people's overall full-stack skills. Over the period of a month, people will create a small easy to build start-up app and present that at the end.
3. Library creation hackathon - Find a simple development problem a developer generally faces, and ask them to build a library to solve it. The beautiful part about this is that you'll also get to see if they even face problems to begin with. This allows you determine what kinds of development experiences people have.
4. Language Learning Week - Find a new programming language that's not heavily explored in the area you're in, then ask for people to learn it and produce something with that language. The beautiful part of this is that you'll be able to see how fast people generally learn. 
5. Design Hack - Take React or Vue.js, get a UI library, and ask people to come up with some set of innovative designs. 
6. Machine Learning Hackathon - Ask people to create machine learning models on Google Colab
7. Open Source Constraints - Want to see if an open source library will improve your processes?
8. Model Integration - Integrate models that you've already deployed.
9. Deploy Model Hackathon - Get models that already exist in the industry (such as GPT-2 from OpenAI), then have people deploy them to a web service. Whoever creates it in the best way possible wins.
10. IoT Hackathon - Get a bunch of raspberry pi's and create a set of possible sensors. This can be combined with machine learning.
11. Big Hack - Create a hackathon where anything can happen. This should happen only once throughout the year and should be a combination of what people have already done. 

## Why use a hackathon?
---



Hackathons are a perfect balance of the explore-exploit trade-off. Assuming you create many small focused hackathons, they're also amazing for balancing risk yet will allow you to find the best set of rewards for the community at large. This is much like how people inside of financial trading rely heavily on bet sizing to operate inside of hedge funds. Inside of finance, even when gains seem sure you want to change bet sizes on each transaction you make. By dynamically modifying bet sizes inside of finance, you can both discover what's going on inside of the market (by seeing how it responds to you), determine and profit more by betting more money when the opprotunity seems most certain. Here's how hackathons relate to bet sizing and risk:

* They're relatively low risk, companies can aggregate funds with each other to diffuse risk of hosting one. You also aren't supplying major funds to hire people into your organization immediately.
* They're low risk ways to explore new technologies. By having hackathons centered around a new technology that not many has seen, somebody can setup and teach everybody else how to use it during the hackathon process. The more focused your hackathon, the fewer degrees of freedom you have, and the more people will optimize inside of a certain space.
* Recruiters can learn about how workable frameworks are for people in a working environment. They can explore many alternatives for the same set of activities and lock in whichever will yield the best results.
* It can produce long-term data about how people go about certain tasks. 
* See if people can learn or generate new processes on the fly.
* Major projects can be built using a combination of smaller hackathons.
* People generally can find new business partners using this methodology.
* You can create a commons of information for people to operate. This is particularly useful for creating new projects inside of the community. 
    * Imagine having forked version of all git repos for start-up code from various hackathons. New people can easily take that code and build their next start-up.
* After kits are made for people to build start-ups (through the hackathons), and participation grows, you can make larger hacks to have people combine the assets that have been generated.



### Using hackathons as a learning and building tool
All good hackathons should be centered around removing **information asymmetry** for everyone in the process and gathering assets. Developers should learn something and have assets generated for themselves, while recruiters and organizers should learn stuff how code works while being developed in short burst. The 10 hackathon ideas are centered around that concept. 