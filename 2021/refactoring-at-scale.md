---
layout: tud
title: Refactoring at Scale
---

In this lecture, we will discuss two chapters of the [_Refactoring at Scale_](https://www.oreilly.com/library/view/refactoring-at-scale/9781492075523/) book, by Maude Lemaire:

* Chapter 1: Refactoring
* Chapter 3: Measuring our starting state

<img src="{{ '/img/books/ras.jpeg' | relative_url }}" class="book-cover">

## Comments and Questions

* Nick Dekker
	* Chapter 1:
	even though implementation is "hidden" from the uses. They might still notice a difference, since the response may be faster.

	* Chapter 1 says:
	"much of the failure of Healthcare.gov was due to failed development practices caught up in bureaucratic federal government policies". 
	Could the failure and huge spending have been prevented when properly designed? Or would it still cost a lot of money, expertise and communication.
	My best guess: it could have been done, with proper care and a lenient deadline or some kind of flexible rollout plan.

	* Chapter 3: 
	Postmortems can provide a nice backlog of incidents. It also brings a new task along. Storing them and making them easily findable, and managable. Often I have similar (or the same) problems, with different causes and I have logged things before. They can stack up quick, if all incidents are logged and require a good standard to make sure anyone can find and benefit from them.

	
* Andries Reurink

	* Chapter 1:
	Refactoring give you more confidence to start building earlier and less over-designed: Does this philosophy also hold for entire teams or management of multiple teams? How so? Seems like a pitfall where quality just suffers

	* Chapter 2:
	Two detail questions: 
	Why does number of unique operands decrease Halstead? Should you be able to simplify your code if you do many different operations on the same data?
	Why is line 1 in example 3-4 a decision point? The declaration of the function.
	Has anyone used these metrics in practice? They might be good for very large scale refactoring projects but for smaller projects relying on intuition seems way more efficient.


* Andrzej Westfalewicz

	* Chapter 1:
	"Shift in Product Requirements" says that if the goals of the system evolve into new ones you can consider to do refactoring so that the code can support both previous and new goals. I would argue that more often it's better to forget about the old tasks and just focus on implementing the new functionality more clearly.
	* Chapter 3:
	“Code Authorship” says about how code with many contributors is usually more messy than code with one author. With my team I once created file with a aprox. 1k lines of code and even thought it was tidy it was following different approaches as we all added what we needed. I decided to convert everything to my style saying that a single way of writing code, even if not perfect, is better than many different ways. Opinions?


* Chadha Degachi

	* Chapter one:
	I appreciated the discussion of the risks of refactoring as I've had some experience with large companies being reticent to change code when it is operation critical regardless of it's state. However in the last point the author suggests avoiding refactoring when 'you do not have time', which made me realise I would have appreciated a little more discussion of the author's opinion of what priority refactoring should have in the development process in relation to new feature introductions, project tweaks, bug fixes etc.

	* Chapter three: 
	This chapter is largely inspiring to formulate some experimental questions and possible development tools, namely: 
	* The author states that in their personal experience they have found increased inline comments to corelate to increased code complexity, this would be in fact very interesting to verify experimentally and could be a new metric for identifying possible refactoring points.
	* The author discusses the possibility of using file change frequency in version control to imply coupling and dependency between parts of the project, this would indeed be interesting to automate and analyse, while I've come across hotspot highlighting based on change frequency in GitHub I've not seen it used in this context.
	* Lastly, the author discusses the NPath complexity metric and its pros and cons which has me wondering if this metric is actually used anywhere in industry, in my experience I've only seen Cyclomatic complexity used in automated tools, I would be interesting to see if there are any examples of tools using NPath instead.

* Niels Bauman

	* Large refactorings with live systems are difficult and need some form of plan.
	* I relate to having trouble setting boundaries while refactoring.

* Rolf de Vries

	* Chapter one:
	The author states that refactoring isn't the time and place to "try new things and stretch our programming muscles", but to focus on providing the smallest change for the biggest positive impact. I argue that the two aren't mutually exclusive. While refactoring should not be your only time and place to experiment somewhat, you should not be afraid to either, because coming up with some small but impactful solution may be difficult but worthwhile.

	* Chapter three:
	I found the author's note on Type Coverage interesting, as I've never heard of it nor considered it, while having working in Python for 3 years now. I wonder how to implement it for Python tests, and will try to add those tests for future Python codebases.

* Wessel van de Brug

	* The text assumes that the application's interface remains consistent. However, it might make sense to change the signature of a public interface function (e.g. for clarity or removal of a redundant parameter) in some cases. Should such a change be considered a refactor (as they do not change the behavior) or not (as they do change the interaction with the system)?
	* As automated changes can often be quite extensive, I was wondering how such automated tools convey the reasoning behind their changes to developers. If developers cannot always grasp the extent of their own changes, I imagine it would also be difficult to understand the changes made by automated tools.
	* Should changes made for the sake of performance be considered refactors? Or would it be better to classify them as "optimizations" in cases where the changes do not improve, or even worsen, the readability and/or maintainability of the code?
	* As I find the process of refactoring rather relaxing, I slightly disagree with the argument that it should not be done for fun. Of course, it shouldn't get in the way of other work. But, its important to relax every once in a while too.


* Haiyin Zhang

	* Chapter 1:
	Since there is risk in refactoring, how can we balance the risk and gain for refactoring in practice?

	* Chapter 3:
	In this chapter, the author introduces some metrics to measure the start state before refactoring. So what are the most popular metrics in practice? I’m always interested in the distance between theory and practice.
	
	* I don’t understand how the halstead metrics’s equation comes...


* Mingyu Gao

	* chapter 1:
	Benefit of refactoring：How do we distinguish the role of refactoring and comment? For me, comments also help us to understand code. And it is the main way I used to understand code. I think refactoring aims at reducing comments in the code. I am also curious about how should we strike a balance between well-commented code and refactoring.

	* chapter 3:
	Test case coverage: As no test can guarantee 100% coverage in large-scale code, should refactoring focus on the uncovered code?


* Wessel van de Brug

	* Test-coverage is not the same as test-quality. This is very important.
	* Documenting a code base can be difficult. Many people overdo it, but even more do not do it at all. I believe that function signatures and class names should be enough to understand what the code does, and that documentation should focus on how and why it does it. What are your opinions on the extensiveness of (formal) code documentation?
	* I personally do not like informal documentation such as chat/e-mail transcripts. It may be beneficial to understanding the reasoning behind a system, but, if that reasoning is of any importance, it should be formally documented in the code (if no other option is available), an external document (prefered), or via the commit/merge history of the version control system (also a good option, as it also represents the history/timeline of the changes).


* Danyao Wang

	* chapter 1: One of the risks of refactoring is unearthing dormant bugs. The author said these bugs are regression that is commonly exposed by restructuring code. But maybe this can be regarded as a good thing as it exposes some potential risks of the system? 

	* chapter 3: The main informal documentation mentioned in this chapter is chat and email transcripts. But whether these documents are public? If we cannot access this information, would this information lose its value? or how can we solve problems related to privacy?

* Ching Chi Chuang

	* I observe an interesting common suggestion and reasoning both in chapter 1 and chapter 3. The author usually tells us that we had better refactor code step by step because of the evolution of codebase familiarity (chapter 1), unnecessary complexity (chapter 1) and downsides of NPath complexity (chapter 3). 
	* For the evolution of codebase familiarity, the author mentioned that “The familiarity will gradually decrease over time as more modules are added and modified”. 
	* For the unnecessary complexity, the author mentioned that ”By taking small, deliberate steps in one direction …..., you’re better able to maintain focus on your ultimate goal.
	* For the downsides of NPath complexity, the author said that “I recommended that you use NPath complexity to measure constrained sections of the code you are seeking to improve”.


* Maurício Aniche


	* I love that she reinforces that refactoring is about identifying a systemic problem and refactor it in a strategic and disciplined way.
	* No one will ever fully understand a software system completely. Therefore, that's why we need to constantly refactor!
	* She suggests mining software repositories as a way to measure quality. She mentions Adam's book. I love the idea. Some companies do it already. Ah, the fancy name for identifying files that change together is called "logical coupling", there are lots of papers on the topic. 
	* She also mention analysis of chats and issues as a way to identify parts of the code to be refactored. This can be a nice project too (or MSc thesis).
	Discussion points:

	* It seems like there's a way to write/refactor your code in such a way that any developer of the team would understand it. What do you think about it? Is there always a way to write code such that 100% of the people will understand it?
	* One of the ideas is to talk to developers and understand what they feel it's not good enough, so that it needs refactoring. However, the devs that work everyday on that system might be biased. Maybe they got so much used to that ugly code that they can simply work with it, even though if the code was better, changes would be faster. How to avoid such bias?
	* Some agilists argue for the "you should always make whatever code you touch, better". In the book, she argues against it! She says that there might be a lot of downsides to it, e.g., the engineer may not really understand why things are that way, and also because of code ownership. What do you think of it?
	* Identifying what pieces of code to refactor is tricky. She discusses "simple metrics" for that. Is that really enough? (See the paper by Tiago Alves et al and their benchmark technique to derive good thresholds.)


* Khalid El Haji

	* Chapter 1:
	The books to my surprise also highlights the risks of refactoring not only showing the positive effects. In particular the author (similar to the previous paper) strongly urges the reader to verify the behaviour stays the same after refactoring, in particular the author recommends using test suites to verify that the behaviour is preserved (too some extend, this obviously is not perfect). How do we then deal with systems that are not tested (or have low testing coverage) but do require refactoring? The natural answer would be to say let’s first write all kinds of test and then refactor, however this increases the cost of refactoring. Alternatively, automated test suite generation tools can also help in generating tests but they won’t guarantee that the code behaviour is in-line with business requirements. 

	* Chapter 3:
	The book mentions good number of metrics can be used for measuring refactoring impact (or places that should be refactored). What I noticed however is that the metrics described do not necessarily reflect what a developer could consider as code that should be refactoring. For example, a piece of code having high Cyclomatic Complexity might intuitively mean that it should refactored be might not actually need a refactoring. Furthermore, it would be interesting to study whether high values on the metric do actually correspond to what an experienced software engineer considers as code that should refactored (this can be by means of an empirical study).


## Discussion

* Refactoring for fun, or stretching the programming muscle. It might be considered a relaxing activity for some developers.
	* This should be avoided if this is the sole or main reason to refactor. But in general it can be part of the reasons to refactor.
	* Is it good for the mind to refactor? Small systems or parts of a system is satisfying to do and can consequently increase productivity of the programmer.

* When is it better to rebuild instead of refactoring? Michael Feathers wrote a book on this. Rebuilds happen more often in programming than in other lines of work. This may be due to cheaper / less intensive labour and cost of material compared to buildings or real-life structures.

* Should changes made for the sake of performance be considered refactors? Or would it be better to classify them as "optimizations" in cases where the changes do not improve, or even worsen, the readability and/or maintainability of the code?

	* This requires a specific mindset and would not necessarily be a refactoring step. 
	* Refactoring _may_ improve performance, but it is about the intention and not about the results.


* point: Setting boundaries while refactoring is hard. If refactoring, do we take unrelated parts of the system along?

	* When refactoring, you lose track of changes, since a lot is moved around, so including unrelated parts will add more confusion. Otherwise we may not come back to it and we forget about the code that should be refactored.
	* Setting the boundaries will make sure the current objective is clear and there is as little as possible chance at introducing bugs.
	* It's hard to change your mindset when creating new code, switching to refactoring hinders productivity.
	* Option: Keep track of todo's (refactors) in a separate file. This will avoid cluttering the code base and the team can come back to the points, to discuss them at any time.


* A difference between types of refactoring can be made:
Low level refactoring: localized, changes on variables (renames, variable introduction).
high level: changing higher level structures or architectural changes.
An option is to always allow low level changes. High level needs some discussion with the product owner (or the team, or both).
During sprint planning, these things can be addressed.

* Large refactorings, one branch will be greatly altered. How do we merge the two branches in the end.
Merge changes on the fly and merge them into the refactor branch. If they are too large, we have to postpone. Merge after and then refactor.
Try to account for it in your planning.

* Stop developing on the other branches. Or: implement with the new interfaces in mind.

	* Try to code modularly, splitting up the code is very much encouraged. That way, at least those parts of the code work in isolation.
	* Try to make a plan before actually branching.
	* Trunk-based development may help

* Domain driven design: anti-corruption layer, where you only call that layer. Facade classes can hide 'ugly' implementations and are more likely to remain valid.

* Try to chop op high/low level refactoring, picking the low hanging fruit (low level refactoring) will give diminishing returns.
Small changes may improve the system's design, but it will never fix the underlying problem.


* Before refactoring we need a lot of evidence, and when you do, a big part of the plan will quickly follow from the evidence.
Multiple points in the system will give different pieces of evidence that link together into one bigger problem. Which gives a nice starting point for the refactoring process.

* The book mentions good number of metrics can be used for measuring refactoring impact (or places that should be refactored). What I noticed however is that the metrics described do not necessarily reflect what a developer could consider as code that should be refactoring. For example, a piece of code having high Cyclomatic Complexity might intuitively mean that it should refactored be might not actually need a refactoring. Furthermore, it would be interesting to study whether high values on the metric do actually correspond to what an experienced software engineer considers as code that should refactored (this can be by means of an empirical study).

* The scope of the metric analysis is important, one file may be more easily analysed than a whole class. False positives might be desirable.
It is important not always to treat the metrics. If the code works and is legible it may be the case that no improvements are necessary. 

* Lecture by Mauricio:
In code, there are some metrics that should *in general* must be adhered to. SIG does this by benchmarking. They measure a lot of classes and plot the distribution. The 70% quantile is taken as well as 80% and 90%. Complexity is measured against classes in these ranges. Meaning if a class is more complex than 90% of the benchmarked classes, it is indicated as a problem.
SIG also gives a system metric, some number of stars. The more 'bad' classes you have, the less stars you get e.g.: < 10%: 5 stars; < 20%: 4 stars; etc..

* Some of the outliers are purposefully made this way and may not indicate problems.

* Automated tool, raw output that is evaluated by the metric-company (a consultant) that outputs the software metrics. 
This is helpful in legacy or unknown systems, the metrics identify key problems.
The scope of the problem area is reduced, even though there may be false positives.

* As mentioned in Ch3, asking developer for input and only looking at multiple metrics, not at one at a time.

* Critical (security) sections of code can't be altered. Software developers can be biased. Questioning developers on this more regularly may be a nice way to survey the system.

* Mining software repositories can be useful. The same way there is business intelligence, this exists for software. You can extract important information about the software from git.
How would you leverage this data to find problematic parts of the system.

* Finding a set of methods or classes. After other metrics score very badly, we can determine, based on git history and how much a class has been altered.
This is churn vs complexity, the amount of edits on a class:
[churn vs complexity image](https://understandlegacycode.com/static/3afb5dcf17b9245eab0a9a0fd2a5610f/11d19/churn-complexity-graph-quadrant-2.png)

* Such maps may output by [codescene](https://www.codescene.com).

* There are many types of coupling that generated a lot of research, one is logical coupling.

* Could the government projects (e.g. Healthcare.gov) that failed, have succeeded (cheaper) when approached differently?
	* Timelines are very strict in the government and the pressure combined with complixity and scale are a recipe for disaster. A lot of private companies may fail too, but they will not be scrutinized as badly since they will keep it private.

