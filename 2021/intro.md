---
layout: tud
title: "Introduction to CS4300: Software Refactoring"
---

This is our introductory lecture. We will discuss about the course and how everything works. 

In addition, we will discuss the following paper:

* Mens, T., & Tourwé, T. (2004). A survey of software refactoring. IEEE Transactions on software engineering, 30(2), 126-139.


## Comments and Questions

	
* Nick Dekker

	* when refactoring, pre- and post-conditions have to hold on the method that is refactored, these have to be tested (perhaps automatically by a program like Daikon). It would be useful and maybe even required to have an extensive test suite in place that verifies existance. The paper mentions this and notes this is not always possible and instead method call verification can be used. However, now the original methods are tested, but the newly refactored methods are not tested. Is is important to test these newly refactored and created methods as a unit? why and why not?
	* I think it's interesting that refactoring improves performance. This seems to be mosly concerning conditionals, replaced by polymorphism. But what about a chunk of a method, that is reused. Will compilers optimize this whole method better, or cache it, when called often?

* Rolf de Vries

	* The preservation properties do not seem to be equally useful. While acces and update preservation should always hold after refactoring, call preservation should not. When two methods are combined into a new one, it seems apparent that call preservation would not hold, since the original two methods no longer exist, thus not all methods call are preserved by the refactoring.
	* Boger et al. developed a tool to refactor diagrams, where a user can apply refactorings to diagrams that cannot be easily/naturally expressed in other diagrams or the source code. Since these diagrams are closely linked to the source code, it is unclear to me how one could not express the refactoring of the diagram as a refactoring of the source code.

* Wessel van de Brug

	* Modern IDEs include (automated) tools for invariant detection (through static analysis), code duplication detection (https://www.jetbrains.com/help/idea/analyzing-duplicates.html), and semi-automated refactoring (https://www.jetbrains.com/help/idea/refactoring-source-code.html#popular-refactorings). How do these tools compare to the ones presented in the paper (e.g. Daikon)? And what do we expect from these tools in the future (integration with code quality assessment, artificial intelligence, etc.)?
	* Section 4.4 mentions the use of refactoring tools to improve the performance of functional programs. Would the immutability of functional programming make it easier to perform refactoring (or not)?

* Khalid El Haji

	* The authors state in Section 3.2 that "By definition, a refactoring should not alter the behavior of the software." They further delve in to the topic of behavior preservation in software. However, it's easy to come up with a common refactoring example which does alter the behavior of the program. For example, the removal of a poorly written feature that adds no value to a software system could be considered a form of software refactoring that does change the behavior. Would that then not be considered a refactoring? Why should all refactorings always preserve behavior? 


* Andrzej Westfalewicz

	* I'm wondering how much this document stands up to today's standard. It is after all from 2004. Since then IT has had the Web and the ML revolutions, we've seen the rise of JavaScript, Python and C#. For example the section 4.A “Invariants, pre- and postconditions” would be today called unit and integration tests.
	* I don't agree with 6.F “Language independence”. Code in different languages is written in a different way and some practices that are good in one are bad in another. Some syntax constructions are also unavailable in different languages. Maybe this applies in languages that operate in a similar way, like C# and Java, but not to all of them.

	
* Andries Reurink

	* The paper mentions refactorings may invalidate tests if they rely on program structure. Is this still the case for properly structured tests? If so, is it possible to extend conditions for test structure to avoid this? Or perhaps easier, to have conditions for test structures that allow for automatically refactoring tests along  with the refactored methods

* Niels Bauman

	* My points for the first paper: In section 3.3 they shortly talk about performance. A difficult dilemma for me sometimes is how much I am willing to sacrifice readability for performance. I think this is an interesting point as it mostly is not black and white; it's different for each (type of) application.

* Mingyu Gao

	* My points for the first paper: According to section 3.1, finding 'bad smell' is the most widespread approach to applying refactoring, which seems to refactor from the specific code to its module and then to the whole system. But how could we refactor a large-scale software if it has too many 'bad smell' codes? By tackling with each 'bad smell' code, and guarantee the preservation of functionality and consistency with the whole system one by one? I will be interested in where and when to apply refactoring in the system in the future class.