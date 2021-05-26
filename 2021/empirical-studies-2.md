---
layout: tud
title: Empirical studies - II
---

In this lecture, we will discuss two papers:

* M. Kim, D. Cai, and S. Kim, "An empirical investigation into the role of API-level refactorings during software evolution," 33rd International Conference on Software Engineering (ICSE'11), pp. 151–160, 2011.
* Ng, T. H., Shing Chi Cheung, Wing-Kwong Chan, and Yuen-Tak Yu. "Work experience versus refactoring to design patterns: a controlled experiment." In Proceedings of the 14th ACM SIGSOFT international symposium on Foundations of software engineering, pp. 12-22. 2006.

Although not compulsory, I also recommend the following papers:

* Danilo Silva, Nikolaos Tsantalis, and Marco Tulio Valente, "Why We Refactor? Confessions of GitHub Contributors," 24th ACM SIGSOFT International Symposium on the Foundations of Software Engineering (FSE'2016), Seattle, WA, USA, November 13-18, 2016.

# Comments and Questions
### Andries Reurink
The Role of API-LevelRefactorings:
In conclusion four, "API-level refactorings occur more frequently before than after major software releases" I feel the causality might be flipped. Isn't it common practise to release a major version if your API signature has changed? This is what I have learned in other courses atleast. It therefor stands to reason that after API refactorings there is significantly more often a major release, where there might have been a minor release otherwise.

### Khalid El Haji

Paper “An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution”: 
The way the paper approaches refactoring identification is quite clever. Besides employing automated methods for refactoring identifications on specific repositories (which is not guaranteed to find refactorings) the authors also employing manual inspection based on 1000 randomly sampled revision that were found using the automated methods.  In this way, it is ensured that the automatic methods actually do yield reasonably accurate results. Nonetheless, I would have been nice if the authors had exactly specified what exactly an API-Level refactoring means. API-level refactoring for a REST API can have a different impact than library API refactoring.

Paper “Work Experience versus Refactoring to Design Patterns: A Controlled Experiment”:
A first thing to note about the study is that it only focuses on a single project, which brings into question the generalizability of its results. Nonetheless, the authors argue that focusing on just a single project is not a methodological problem as the project is “realistic” enough.

### Ching Chi Chuang

Paper “An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution”:

In Table 2, we can interpret the data from another perspective.  It reveals that programmers are likely to add specific keywords such as bug or fix in logs, comment or bug reports due to fix-revisions. In contrast, programmers are less likely to document specific keywords when they make refactoring revisions.
One of the main ideas in this paper is that  the time taken to fix bugs decreases after refactorings. However, I think there is another reason leading to this result. If we see Table 3 closely, we could see that most of the refactoring revisions and fix revisions are completed by the same author. The author may have already known where the bug is likely to occur. So, the author uses less time to fix the bug after refactoring!

### Rolf de Vries

Work experience versus Refactoring to Design Patterns: A Controlled Experiment:

I like the experiment, where the authors refactored JHotDraw to add design patterns that were not present and useful for their change tasks. However, I hope that this paper does not motivate developers to add a lot of design patterns in their code, just because they might come in handy in the future for change tasks. Instead, when facing a change task like the Direct approach group, it would be best to refactor the code by adding the design pattern that would best fit the task.
An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution:

Interest to read that the reason more bug fixes happen after API-level refactorings is because of the mistakes that happened during the refactoring attempts. Beforehand, I thought it was because while refactoring, developers discovered bugs and went to fix them after refactoring. This result shows that refactoring is very tricky to do perfectly.

	
### Chadha Degachi
Work Experience versus Refactoring to Design Patterns: A Controlled Experiment∗

In general I like the experiment set up its very clear and upfront about possible issues however I have a few points: a. They assume time reported by student is an accurate reflection of time spent as compared to time reported by them vs time spent by them on refactorings b. I would say I understand the need to control this variable but the generalisability is a little compromised by their performing of the refactoring themselves thus providing what I assume to be a correct, complete and appropriate refactoring when this is not always the case in the wild. c. Using your students as experiment subjects seems at least a little mean haha
On the point of appropriate refactoring - they are able to implement the most efficient and helpful refactorings for a given change only because they know what this change is going to be, I would say this is very uncommon in the real world, though your refactoring may be triggered by the need to enable a specific development I don't think you often know such fine grain details about the future s to enable the level efficiency presented here.
An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution

"A fix rate increase is often caused by mistakes in applying refactorings and behaviour modifying edits together." The authors go over a number of possibly reasons the bugs fixes increase post refactoring, but it seems like incorrect floss refactoring was the leading cause among these which is concerning since from our reading it seems to be such a common practice.
"This result is surprising because developers do not avoid refactorings even when they have a pressure to meet deadlines. In conjunction with the fact that many revisions include both refactorings and bug fixes, we speculate that refactorings were done to facilitate bug fixes that needed to be implemented before major releases." - This is interesting reasoning but it seems the authors don't consider that the reason for this maybe that APIs post major releases are explicitly meant to be at least fairly stable, certainly within the first 30 revisions.
"When it comes to fixing bugs introduced near the time of refactorings, the average fix time tends to decrease after refactorings." - I would not attribute this to refactoring in general so much as refactoring specifically for increased ease of debugging, since the issue is known before redesign occurs.


	
### Haiyin Zhang

Paper “An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution”:

For H4, the authors found there are 39.1% more refactoring revisions within 30 revisions before major releases than 30 revisions after the releases, and came to the conclusion that developers do not avoid refactorings even when they have a pressure to meet deadlines. However, is it possible that this is because developers focused on the code quality before the release stage but not implement the new feature? You may also able to come to a conclusion that developers often release a version after the code quality is stable from the observation. 

Paper “Work Experience versus Refactoring to Design Patterns: A Controlled Experiment”:

They seem to control a lot of variables to make the results reliable. And doing the controlled experiment is indeed a good way to verify the usefulness of the design pattern. However, in this experiment, they only use JHotDraw and only investigate the students from HKUST. Some replicate experiments can be conducted in different universities and use different projects to verify the result.
	
### Andrzej Westfalewicz

An Empirical Investigation into the Role of API-Level Refactorings during Software Evolution :

One finding is that bugs take less time to fix after the refactoring compared to prior. However this is not necessarily because the code is new and cleaned up. The time decrease might be caused by the fact that developers spent time with the code.
Work experience versus Refactoring to Design Patterns: A Controlled Experiment :

The paper does a good job in measuring the effect of the refactoring. However to complete the picture it would be great to know how much time the refactoring took.
	
### Niels Bauman

API-level refactorings:

Million dollar question regarding cost-benefit analysis of refactorings is mentioned
"The results also suggest the need of new software engineering tools that detect and correct inconsistent program updates when developers apply refactorings."
	
### DANYAO WANG

An empirical investigation into the role of API-level refactorings during software evolution

This papers focus on API-level refactorings but does not introduce this kind of refactorings in detail. I am curious about other refactorings and whether API-level refactorings are more important than other types of refactorings.
Work experience versus refactoring to design patterns: a controlled experiment.

In my opinion, when we evaluate the time spent on using the refactoring approach, we should include the time spent on the refactoring process. In this paper's experiment, the meantime that group1 spent on Audit using the refactoring approach is 5.86, which should be 11.36 after adding the time of refactoring, 5.5. As a result, the time spent on both approaches is similar. How can this result be explained? Or should we include the refactoring time when evaluating these two approaches?
	
### Nick Dekker

API-level paper:

interesting metrics to see the fixrate go up, though only for small window after the refactor. It could be the developers focus on that piece of code and a bit of maintainance would be expected after making a change. They would be in the "refactor and fix"-mindset. Instead of the "create new feature"-mindset. It is also related to H3 - do refactorings facilitate bugfixes. The paper mentions this briefly at the end of section 4.2.
I think the environment needs to be more controlled, mining Git repos may give a wrong indication of the metrics that are tested. This also is seen in the paper, since they say its hard to find relations between commits and bug fixes and projects with high quality were picked.
The fix rate goes down after some revisions past the refactor to very close to the original level. Seemingily indicating refactoring does help with bug fix speed, but also showing it is very hard to find meaningful results.

# Discussion

### The trade-off between of cost and benefit in refactoring
Refactoring may introduce new bugs. However, refactoring may make it easier to fix bugs which would obviously make it less time. 
Possible bugs after refactoring also prevent developers to fix bugs before applying refactoring because they may worry about reintroducing bugs. This may result in higher bug rate.
The experiment should set a longer window as the benefit of refactoring may show in the long term. 
The refactoring and bug fixing are very much related. 
API-level refactoring facilitate bug fixing. 
### Experiments
In the paper "Work experience versus refactoring to design patterns: a controlled experiment", the authors design the variable-controlled experiments to test the influence of refactoring. The idea of having an intervention and comparing the before and the after is very common in scientific fields like medical science. 

1. Variable-controlled experiments versus Empirical research


|  | Pros | Cons |
| -------- | -------- | -------- |
| Controlled Experiments     | 1）easier to control and evaluate variables  2）have a clear contrast to see the effect of factor 3）apply some fanbulous algorithm(GA) and design 4）results are clear to classify as we know the metrics| 1）hard to set up   2） hard to control variables 3）introduce observer bias 4）less realistic |
| Empirical Experiments | much easier to create similar environment |  hard to determine the quality in mining |

Conclusion: both of them are valuable and we need these two experiments. 

3. Comparison of medical and computer science experiments
Conducting medical experiments is as they need to exert experiments on human. 

Analyzing medical experiments' results is easier because the effect of the drug is clear while the result and effect of techniques in computer science experiments can be unexpected. 

Medical experiments may have more ethical concerns while this impact in computer science experiments is smaller. 

4. The application of double blind in computer science experiments 
It is doable but difficult as more metrics are needed. 

Our refactoring research is quantitative while the double-blind experiments may be effective in qualitative analysis.

The researchers made the experiments as assignments, which blind the participants in a clever way. 

5. Bias Analysis
Metrics in experiments may introduce huge bias. A smaller-scale experiment before conducting the exact experiments will help us to realize some defects in experiment design. 

To check the bias in the experiments, we need to find whether there exists anomalies in data. 


### Refactoring tool
We need some refactoring tools in IDE to notice us the existence of possible refactorings in the future.

A large-scale refactoring will be easier with the help of refactoring tool.


### Design Pattern in Refactoring
Experience is needed to decide when to apply design patterns and which kind of design pattern before refactoring.

The design pattern paper has an academic bullshit as they only mention some patterns' name in other papers instead of explaination for the patterns they used. They should offer some details to reason the selection of design patterns rather than the simple reason - popular.

The design pattern paper did not explain the degree of students' understanding of design patterns. They should give some training of design patterns on participants as well. However, training may introduce object-oriented concepts. In this experiments, they use students as participants which introduce some learning bias to some extent. This kind of bias is not bad but should be reported and discussed in papers. 

### Should more tex money be spent on empirical studies on refactoring
We don't know when the refactoring works exactly.

We should reach more decisive conclusion that can help in a general sense. 

Data could back up when we need to prove something in empirical software analysis.

The API-level paper beautifully reports their findings but they miss a section where they can discuss how these results could be made actionable in practice. 

### Definition of Refactoring
Refactoring unavoidably mixes with performance improvement and adding features. It is hard to determine whether the definition of refactoring include the performance preserving. 

Martjin Flower(https://martinfowler.com/bliki/IsOptimizationRefactoring.html) points out that the goal of refactoring is to make the code more understandable. In our first reading paper, its definition of refactoring is the process of improving readability, maintainability and extensibility. 

Mauricio mentioned two terms - re-engineering(book:Software Re-engineering) and high/low-level refactoring(book:Refactoring to Patterns). 

### Some ideas for further research
It will be interesting to properly use crowd workers in experiments in software engineering. The first study we should do is to analyze how reliable is crowd workers for this type of experience. 

When we reach some results, we should think about how to use the results to develop or improve in software engineering, which could be the recommendation part in papers.
