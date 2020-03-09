---
title: Philosophies & Implementation of a Good Dev Assessment
date: '2020-03-09'
spoiler: Designing a better way to assess developers.
---

If you're a software engineer, there's a solid chance you don't like the interview process. Even outside of bad communication and ghosting, the actual process of interviewing is unpleasant for most people. The algorithms tests bear little resemblance to most software engineering, coding on a whiteboard is literally insane, and none of it evaluates ability to navigate a large codebase. 

To be clear, this process works for some places but that's because it's a signal from an already culled group. Whatever nonsense big tech companies' PR departments say, they predominately recruit at elite universities because it's easier to find fish at an aquarium than it is in the ocean. These companies know that quicksort doesn't show that you can set up a complex system but they take it as a *signal*[^1] that you can - or at least are teachable. Google is very emblematic of this: their final decision making group not only looks at your interview feedback, they look at your resume and transcript as well. They're looking for multiple signals that you'll be good at the job.

There's a few potential issues with just going with the industry default:
## Replication
It's not replicatable everywhere. Google recruits a certain type of person and has advantages that most places do not. Copying the Google method (and, indeed, their disgregard for candidates) won't work everywhere.

## It's jerk-y
It's not nice to candidates to make them go through this process. I don't view that as automatically disqualifying. Companies are looking for efficiency. Not being nice has an obvious tradeoff: a failed candidates[^2] will be less likely to come back, and your organization will become less appealing. This is especially true for those rejected on trivial grounds. Every organization has to navigate this tradeoff. In general, being nice costs resources while being mean costs candidates. 

## False Positives/Negatives
Companies care less about false negatives because rejecting a good candidate is just opportunity cost (losing a good person) while hiring a bad candidate is real cost (salary) and opportunity cost (one less slot for a good person).


# VandyHacks
VandyHacks organizes Vanderbilt's hackathon. To do this, we have to maintain the technical infastructure behind the hackathon which includes our regisration system, [Vaken](https://github.com/VandyHacks/vaken), a well designed [website](https://vandyhacks.org), and a bunch of other stuff. We use Typescript and React for most stuff, and functioning well in a large codebase is crucial. Quicksorting is not.

In the past, our solution to interviwing for dev team has been to interview for it badly. We'd skim GitHubs, have applicants do basic things like explain the difference between pass-by-value and pass-by-reference[^3], and write a couple lines of code to solve a basic problem like the product-sum of an array. This has been very unsuccessful. 

The fact that VandyHacks doesn't pay is extremely relevant to us. It means that we have to rely on people enjoying working on our dev team and/or believing in the mission, instead of pay, to motivate people to put in good work[^4]. This is not a reliable motivation method. Luckily, without having to pay, we can over-hire and rely on the law of large numbers to ensure that some of them will be highly productive. That means that the only cost to a false positive is the human cost to a director who has to manage someone who doesn't want to do work[^5].

## How we approached the dev team this year
We had two main phases to the dev assessment: the online assessment and pair programming. Pair programming is hard work. Each pair programming session took one hour and was mentally taxing. Scaling that to all 37 applicants would have been impractical. We therefore implemented an initial filter of the dev assessment, a take home test of sort that went through typical things that VH developers do. 

### Dev Assessment
You can find the assessments we gave out [here](https://github.com/VandyHacks-Internal/dev-assessment-dayone) and [here](https://github.com/VandyHacks-Internal/dev-assessment-daytwo/). We randomized the inputs for each person. For the purpose of this blog post, you can see sample inputs [here](https://inputs.vandyhacks.org) with username "blogpost1" and "blogpost2" for each day's assessment. 

Each assessment is divided into 3 levels (0 through 2) and are basically equivalent.

- Level 0: We give a JSON with fake hacker info and ask you to filter it in some way. Tests if candidate is familiar with JSON (which means that they've done stuff outside of Vandy classes: none of them cover JSON), the dictionary/hashmap (whatever you want to call it; basic key-val datstructure) knowledge that JSON implies, and basic programming (string parsing, if statements, for loops etc).
- Level 1: We give a CSV with fake hacker info and ask aggreagation questions about it[^6]. In essence, we're asking them to demonstrate their use of MapReduce concepts.
- Level 2: We ask the candidates to call an API with a large list of inputs to the API. We want to see candidate comfort with async requests and, particularly, timing them right because we expect the order of outputs to be the same as the order of inputs.

I think we did a good job reflecting what a VandyHacks developer has to actually do. As a friend put it to me (paraphrased), they have to code, they have to data, and they have to make async requests. 

We were very successful with this approach[^7]. 11 people didn't attempt the assessment despite cloning the repository (so they saw the questions) which is indicative that they self filtered out. 

[^1]: All of interviewing is about finding a signal that you're good and expending minimal resources on doing so. Sometimes this can become silly, like when Triplebyte's interview is trying to find a signal that you're good at traditional interviews with their quiz and interviews. Multiple layers of signal finding there.
[^2]: Most Google engineers failed the Google interview at least once. 
[^3]: It's shocking how many people with 1 year of experience with C++ couldn't answer this.
[^4]: This has some more fun implications too. It means we're heavily incentivized to use new technologies because keeping dev fun increases total work.
[^5]: I don't want to minimize this: it sucks. However, I've been around high-involvement student-led student orgs for 7 years at this point and I'm pretty convinced it's unavoidable. 
[^6]: Basically, we ask for the simplest possible implementation of MapReduce concepts.
[^7]: I want to note a large failure here: only one female-identifying person passed the dev assessment, less than you would predict based on the number of applicants. Indeed, females seemed disproportionately