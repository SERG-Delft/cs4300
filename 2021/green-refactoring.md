---
layout: tud
title: Green refactoring
---

In this lecture, we will discuss two papers:

* Morales, R., Saborido, R., Khomh, F., F., Chicano, F., & Antoniol, G, "EARMO: An Energy-Aware Refactoring Approach for Mobile Apps," in IEEE Transactions on Software Engineering, vol. PP, no. 99, pp. 1-1.
* Cruz, L., & Abreu, R. (2019). Catalog of energy patterns for mobile applications. Empirical Software Engineering, 24(4), 2209-2235.

#### Summary

Measuring efficiency and battery consumption
 - it can be very hard to do
 - frameworks can impact battery usage

Experiment: recreating the same app to measure framework 
 - patterns are very hard to see, too many factors that cannot be controlled
 - battery status, age, health, current level can alter the measurements
 - an external power source can be used to monitor usage better

Do non-mobile devices also have this problem?
 - hard to say, desktop-servers probably not so much
 - mobile phones are constantly changing
 - there are still considerations to be made

Android studio has a built in energy monitor, how does this affect Android vs IOS?
 - IOS (xcode) also has this
 - it is hard to say where the differences come from
 - the IOS environment is more strict

How does the battery health of a user affect phone usage and how they care about battery life and optimization
 - this would affect the user experience a lot
 - this also results in a change in usage of the phone

Do we care more about battery life in phones or energy consumption for sustainability?
 - you can not drive change by only looking at sustainability, therefore improving usability is a good thing to trigger changes

Did your focus shift from improving battery life to sustainability?
 - the whole society has shifted their concerns to sustainability since batteries last longer now

Cellular vs WiFi energy consumption
 - cellular towers use a lot of towers as well
 - WiFi is said to be more efficient
 - its hard to say, since the towers are turned on anyway, WiFi also requires personal routers
 - cloud computing also has this problem, you move the energy away from your cost, but the data center still uses it

Cloud server hosts have a hard problem to solve: turning servers off for example
 - x servers at 100% are less efficient than x*2 servers at 50%
 - managing the amount of servers in a server room and cooling it is hard
 - the combination of this can make for a very complicated problem
 - big companies do not care so much about the energy, more so about their profit and image

It is hard to do research in this field, statistical tests are required
 - hard for newcomers
 - hard to please peer reviewers
 - steep learning curve to start doing research

Is there a correlation between security and sustainability?
 - more security -> more code -> less sustainability
 - energy-refactors decrease maintainability, software is harder to 

Will developers budge and implement energy-refactors?
 - some developers pride themselves on their ability to code, its hard to suggest energy patterns too
 - all refactoring are hard to merge into code by means of PRs for example
 - we can try to convince the developer by saying we gain energy-efficiency

Data gathering is hard for energy consumption, L. Cruz used commit messages and PRs for his research
 - methodology is very hard to get right and will affect the meaning of your results
 - ~1500 messages were combed trough to remove false positive
 - ~400 commits / PRs were more thoroughly inspected for thematic analysis
 - AI was not considered, it will still have error, separate research
 - an AI follow-up was not done yet, since it's hard to estimate its effectiveness

Extraction of energy patterns
 - very subjective process
 - L. Cruz et al tried to start with a blank state
 - assessing related work came later
 - labeling of messages came first and extracting patterns from there

Note by Mauricio: make sure you discuss researching methodology about your research in your thesis.

Automatic refactoring suggestions:
 - probably easier to implement and accept these types of changes, it takes less effort
 - if you automate this process, you do not learn about the code and its structure

#### Comments

	
Andrzej Westfalewicz
 - EARMO: An Energy-Aware Refactoring Approach for Mobile Apps:
   - The Blob anti-pattern in some cases is desired since it allows the compiler to optimize code much more efficiently especially in the case of heavy calculations.
   - It would be interesting to see if other implementation mistakes affect power usage or if they are fixed by the compiler. For example, scanning an array multiple times instead of performing many operations in one loop.
 - Catalog of energy patterns for mobile applications:
   - Just like “normal” design pattern some of these patterns may be implemented accidentally while focusing on other things. For example: “dark UI color” is often a stylistic decision, or “race to idle” is implemented just to give the users the best responsiveness. I wonder how much would that change the results if these were also included.
   - I feel like the paper is missing the information on how efficient these patterns are. How much energy is saved compared to mentioned low level changes (e.g. new drivers), or hardware methods like slowing down the CPU clock.

Ching Chi Chuang
 - Catalog of energy patterns for mobile applications:
   - I learn what is Thematic Analysis from this paper. The authors adopt a four-stage process to derive Energy patterns. The process includes carefully reading vast amounts of documents, iteratively refining the labels, filtering out insignificant labels, and finally naming the patterns. These patterns are useful for developers as a guideline when they want to improve the energy efficiency of their apps.
	
MingyuGao
 - Energy Pattern paper:
   - Although I learned about green architecture in last quarter’s SA, I first realize that energy patterns could be one reason for refactoring, which is from a different perspective compared with former discussion.
   - I like section 4 as these energy patterns can help develop your apps. It is the first time that I know dark mode could save energy, I change all my apps into dark mode today.
   - When I first heard about green software, I thought that it may be hard to execute as most enterprises pursue better features and performance rather than energy. The ‘User knows best’ pattern clarifies this confusion for me as mobile applications can offer choices for users.
 - points:
   - I am quite curious about when the energy patterns mined on GitHub are applied. Are these patterns required by companies, consumers, or just developers themselves? Or what is the developers’ perception of energy patterns? As most apps now focus on how to attract users’ attention, I think energy patterns will not be the main requirement during the development process.
   - This paper could be a guide for software engineers to develop. But as a developer, I would like to know the sacrifice or the effort I need to devote to this kind of green software. Maybe it will be better if you add more comparisons about implementing different kinds of energy patterns.
	
Haiyin Zhang

 - Catalog of energy patterns for mobile applications:

   - Researching on energy patterns is special. I never think that dark UI can save energy before but it is good to know now. The research conclusion is very useful for the mobile application developer to check when they need to develop an energy-saving application.
   - I feel like this paper did a lot of work by manual analysis. Is there any automatic tool that can help to conduct such kind of research nowadays?
   - More data analysis on how much energy can be saved after each pattern is used should be interesting.
	
Rolf de Vries
 - Catalog of energy patterns for mobile applications:
   - The authors found that "the Android community is more energy-aware". I wonder if that is because Android is more open, while Apple is more opinionated.
   - While it's obvious that the screen is a major source of power consumption, I did not realize that "dark mode" actually is beneficial to power usage reduction. In fact, for a few of the patterns described in the paper, it's interesting to learn that they reduce power consumption.
 - EARMO: An Energy-Aware Refactoring Approach for Mobile Apps:
   - While getters and setters are normally encouraged by the refactoring community, it is surprising to see that it much more expensive than direct field access, according to the linked Android documentation. I wonder if that also holds for other platforms or operating systems?
   - I like the use of multi-objective search-based algorithms, and the funding that there a different compromise solutions. Perhaps this can be generalized to more than just Android applications, to improve energy use of applications other than mobile.
	
Nick Dekker
 - EARMO:
   - Funny that they basically roast the GLTron developer.
   - The paper contains some interesting information, but is very hard to read, or to extract data from without the expertise about a lot of these energy consumption numbers.
   - I feel like the paper goes through a lot of effort, both in research and applying the refactoring and would like to know how many people think this is worth the hassle (as the development process difficulty increases).
   - Is the goal to reduce energy consumption for the environment, or for extended use of a single charge? It seems to be the latter, how much do we value 29 more minutes of battery life?
 - Energy Paper: 
   - The paper says the Android community is more energy-aware. A part of that may be the profiler in android studio: https://developer.android.com/studio/profile/energy-profiler
   - A lot of these energy reducing patterns will decrease the user-experience quality. I think this research is a good starting point, since I would assume very few developers will give thought to the amount of energy consumed. But there could be a lot of value in a follow up research. Where these patterns are scored based on their actual consumption and appearance rate.
	
DANYAO WANG
 - An Energy-Aware Refactoring Approach for Mobile Apps:
   - It's fascinating to consider both the design quality and energy consumption when refactoring.
   - When they conducted a qualitative study with developers to gather their opinion about the refactoring recommendations of EARMO, 100 percent of them considered refactorings to be useful. Still, only 12 percent said that they perform refactoring frequently. Maybe encourage developers to apply refactorings in practice is also essential besides providing good refactoring recommendations.
 - Catalog of energy patterns for mobile applications:
   - This paper is quite interesting as it studied many features that we encounter when we use mobile phones and provided a good summary and analysis.
   - According to the paper, the prevalence of each energy pattern in the two platforms, Android and iOS, is different. For example, the pattern Dark UI Color is considerably more popular among Android apps than iOS apps. I am curious about the reason behind it.
	
Andries Reurink
 - EARMO:
   - private getters/setters have a "negative impact ofanti-patterns on change-proneness [7], fault-proneness [8],and maintenance effort"? I don't understand this also, I cannot find this in the android guide, maybe it's changed. 
 - Catalog of energy patterns:
   - In threaths to validity you say it yourself: commits ... that contain the words energy,battery,or power. This does not include patterns where the user does not realise it or uses a pattern knowingly but does not include it in the commit. Why do you think this is a minority of cases? Note that that makes sense since the percentage of total apps is so low: but maybe thats just true due to many small projects taken into account
   - Total energy consumption not taken right? Onky battery life: cellular i would expects uses even more power in total
   - All uncited patterns are novel? Thats impressive? Some appear somewhat obvious but i suppose thats a strength
   - I would have expected the dark ui colors in android to be more a cultural thing instead of the screens, but that makes a lot of sense!

Chadha Degachi

 - Catalog of Energy Patterns for Mobile Applications
   - "Further efforts have leveraged domain-specific catalogues of design patterns to meet non-functional requirements such as security (Yskout et al., 2015)." - very interested in reading this paper, the specialisation of patterns for different objectives is not something I had considered before.
   - It would be interesting to further investigate the effects of different design guidelines on different devices re: pattern choices of developers and their development habits. 
   - I noticed a reference to Stackoverflow mining which I feel obliged to point out since we discussed it last lecture. 
   - The paper mentioned automated refactoring towards these patterns, this seems like an important area of research but I can't particularly visualise how this would work at the moment. 

