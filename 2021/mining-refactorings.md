---
layout: tud
title: Mining refactorings
---

In this lecture, we will discuss two papers:

* Tsantalis, N., Ketkar, A., & Dig, D. (2020). RefactoringMiner 2.0. IEEE Transactions on Software Engineering.
	* For the more curious, feel free to also see the first paper on RefactoringMiner: Tsantalis, N., Mansouri, M., Eshkevari, L., Mazinanian, D., & Dig, D. (2018, May). Accurate and efficient refactoring detection in commit history. In 2018 IEEE/ACM 40th International Conference on Software Engineering (ICSE) (pp. 483-494). IEEE.
* Danilo Silva, Joao Paulo da Silva, Gustavo Santos, Ricardo Terra, Marco Tulio Valente. RefDiff 2.0: A Multi-language Refactoring Detection Tool. IEEE Transactions on Software Engineering, pages 1-17, 2020.

	
## Comments and Questions
### Nick Dekker

Both papers:

The Rminer paper claims refdiff performs better since they look at the code differently (not AST-wise), which causes it to be better at "extract and move". And it looks like the CST (code structure tree) method is indeed bad (0.66 recall, java) at this refactoring.
Rminer paper: 

9 person-months for manual validation, pretty long. Is it worth it, can /did they opensource their ground truth for other research?
Refdiff paper: 

Renames are matched with similarity of bodies and a relation by matching children. This is an interesting method, but a logical one. It makes me wonder what part of their heuristics are bad and can be optimized the most, for higher recall or precision.
System
	
### Rolf de Vries
RefactoringMiner 2.0:

While it is nice that RefactoringMiner outperforms RefDiff and GumTreeDiff, it can be noted that both RefDiff and GumTreeDiff support more languages than just Java. This only makes RefactoringMiner the go-to choice for Java, while for other languages, it is not even an option. It would be nice to see RefactoringMiner 3.0 focus on supporting more languages.
I like how they differentiate from other tools by only checking the files affected in a commit. I'm surprised that they are unique in this, as logically, you cannot have detect a refactoring in a commit for the files that are not changed in a commit.
While I like that Table 4 shows all refactoring detection rules, it's not very readable.
Overall, I like the performance of the tool. For our project, we're mining refactorings for Java projects too. However, since we're also using JavaScript projects, we chose to use RefDiff (didn't even know about GumTreeDiff as an option at the time) despite RefactoringMiner outperforming it.
RefDiff 2.0:

I like how they acknowledge that RMiner outperforms RefDiff, but that they instead focussed on expanding the available languages, because: "By restricting refactoring research to a single language, we may get a biased understanding of the reality."
Similarly to RMiner, they only consider files changed in the commit, learning from the strategy that RefactoringMiner 2.0 also applied.
After reading both papers, it's somewhat more clear how hard it is to mine revision histories to detect refactorings, which I think becomes even hard when commits contain floss-refactorings rather than pure refactorings.


### Haiyin Zhang

RefactoringMiner 2.0

What doesn't the previous research use AST but use similarity threshold? Why do they use the whole project instead of the changing files? I think using AST and using changing files is the most natural way to detect refactoring....
RefDiff 2.0: A Multi-language Refactoring Detection Tool

In this paper, why doesn't it compare with refactoringminer in the evaluation stage? It will be interesting if it can validate the result of the refactoringminer paper.
	
### Andrzej Westfalewicz

RefactoringMiner 2.0 :

Looking at the syntax tree is a great way to get more information about the change. Sadly, it also makes the tool language specific and hides whitespace changes.
The idea to add a extensions with an overlay over the CR page with refactor information is very interesting. One could even suggest to hide the code that is just an refactoring, but then we are once again encountering the problem of how to make developers trust the tools.
RefDiff 2.0: A Multi-language RefactoringDetection Tool :

So this paper did exactly what I wanted to comment about the previous one, that you can exchange the tree derivation for different languages.
The authors say that because of not representing the syntax exactly they are missing low level refactoring like extract method. I wonder if we could mine architectural refactorings if we push this further and ignore even more details.
System

	
### Andries Reurink

RefactoringMiner

I don't get the novelty of the commit level granularity. Is it just performance for many commits? Other tools can use differt commit versions as input and have the same granularity?
As far as I can tell the related works don't mention machine learning based approaches: I wonder if these just don't compare in terms of performance.
conclusion 4: automatically document refactors, sounds very useful, in context of the previous (or 1 before) where we saw that many refactors are done flossed and not mentioned in commits.
	
### Khalid El Haji
Paper “RefactoringMiner 2.0”:

The paper took an interesting approach when it comes to detecting refactoring. As far as I have been able to understand it, the project employees source code matching (without a threshold, because that has been shown to be difficult to define) to find refactoring occurrences. I am wondering whether a similar approach can be applied to detecting design patterns (we had discussed something similar earlier for our project). 

Furthermore, I am surprised by the really high precision achieved by the project, this indicates that this kind of tooling is “good” enough to be applied in the real world. Nonetheless, this is the first time I have heard for automatic refactoring detection. Why is this not more often applied in the real-world?

Paper “RefDiff4Go”:

This paper has a relatively small evaluation set which brings into questions the generalizability of the method. The previous paper had a much larger evaluation set but did not include as many languages into consideration as this paper.


## Discussion

* Machine learning applied in refactoring detection - by extracting refactoring methods from data set and then labelling them, which makes the ML refactoring detection possible. You can also resample it. It could be a thesis master project.
* Similar approaches of refactoringminer or refdiff - source course matching, could be applied in detecting design patterns. The challenge would be that design patterns can manifest themselves in many different kind of ways and hard to specify.
* Mining refactoring can be done successfully with high precision currently. However, it lacks practical application in the development process. When and how could we utilize the refactoring mining tools? 1) The paper mentions the code review process, which helps readers understand and save time 2)Help annotate refactoring and put them in commit messages 3)tools can help collect and detect some potential malicious code(about trusting refactoring tools)
The current trend of mining tools is to fast their speed while the challenge is to find all refactorings in some large commits. Precision is pretty good now and performance is really important.
* Although these mining tools are designed for Java, these algorithms or design formats could be reused for other languages as well. But it will be a lot of work to implement these algorithms multiple times. So, presenting source code in a unique way for future implementations that work for any language is a possibly good way.
* When doing threshold-based research, there is always a trade-off between precision and question.
* The refactoringminer paper did a lot of manual work to convince us of its tool.
* These papers lack a section that discusses the detection of refactoring combined with other operations.
* MSR mining challenge conference: mining data software related to source code




