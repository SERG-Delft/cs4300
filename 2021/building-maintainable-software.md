---
layout: tud
title: Building Maintainable Software
---

In this lecture, we will discuss two chapters of the [_Building Maintainable Software_](https://www.oreilly.com/library/view/building-maintainable-software/9781491955987/) book, by Visser et al:

* Chapter 6: Separate Concerns in Modules
* Chapter 7: Couple Architecture Components Loosely

<img src="{{ '/img/books/bms.jpeg' | relative_url }}" class="book-cover">


## Comments and Questions

	
* Wessel van de Brug


	* Chapter 6:

		* I appreciate that the author addressed some of the objections against loose coupling.
		* I really like the idea of replacing generic functionality with a framework/library. It might even be beneficial to create such a framework/library if it does not yet exist, as it may help other development teams clean up their code as well.
		* I would argue that interfaces should also be used inbetween the code base and external systems (such as databases). Even when, at the time of creation, such an interface is not implemented multiple times. It makes it easier to replace the underlying external system and discourages developers from needlessly extending the dependency on it.

	* Chapter 7:

		* I find the term "throughput code" a little confusing. I believe the issue is with code that both processes requests and passes requests on to other components, thus attempting to do too much (violating the single responsibility principle), instead of with all components that delegate work to others. The use of a thin redirection layer should not be problem, and could even be beneficial (e.g. when multiple services need a centralized access point or when functionality needs to be hidden in a component-based, instead of inheritance-based, system).
	
* Ching Chi Chuang


	* The author mentions several possible ways of coupling, which includes direct calls, configuration file, database structure and business logic. However, in chapter 6, the author only focuses on how to prevent tight coupling via less direct calls. What about other possible ways? Is there any guideline we can follow to avoid tight coupling by taking care of configuration file, database structure and business logic?
	* This is an observation. In chapter 6, the author proposes a concept called single responsibility principle. This concept permeates the discussion of chapter 7 especially when introducing throughput code. The throughput code causes negative impact on maintainability because responsibilities are not well divided over components.
	* This is an observation. When I study the author’s example of CloudServerFactory in chapter 7, I was wondering how this example complies with the suggested guideline. Finally, I realize that it is because no matter how many kinds of cloud server we want to support, the incoming calls remain the same. The incoming calls are three methods defined in the CloudServerFactory interface.
	* This is a question. In chapter 7, the author briefly mentioned that more design patterns and software architecture styles can keep architecture components loosely coupled such as using a framework. My personal experience is using the Corda framework in a blockchain course of last quarter. The software architecture of Corda is so clear and loosely coupled that it allows us to learn how to program a blockchain application and test cases in a relative short period. I am curious about other people’s experience in using a good framework that helps you elevate productivity?

* Nick Dekker

	* CH6: 

	* The example class in this chapter is said to have the large class smell. Directly after, the author writes that it is tightly coupled as a consequence. Implying large classes mean tight coupling. This is not the case, as some classes may just implement many functions for good reasons and do not necessarily contain dependencies on other classes. (the author may have meant this separate from the large class smell, just introducing a fact about the system, but that is not very clear from context).
	* The note about coupling states parts are connected when changes are needed. I believe this to be false, since a refactor does not mean changes are needed, yet can cause a coupling can occur.
	* Interesting notion about how every method can comply with general guidelines, yet the class evolves to become tightly coupled.
	* nit: Flashlight is one word, I would call the Camera class' functions 'flashlightOn' and 'flashlightOff' (no capital L), also: there is a typo in the first DigitalCamera class "flaslLightOff"

	* CH7:

		* Outgoing calls between components are healthy, but incoming calls are unhealthy. For every outgoing call, it would be logical to have an incoming call somewhere else in your system. So in general, would you like to have fewer outgoing calls and more internal calls?
	
* Chadha Degachi


	* Chapter 6: 

		* Indeed further to @Ching Chi Chuang point, I also noted the lack of discussion of business logic based coupling and further noted that the suggested code smells (large class and large fan-in calls) do not necessarily hold for this type of coupling as classes can be small and implement SRP while still making hardcoded assumptions about the business logic that they should not and that lead to frequent modification of the class.

	* Chapter 7: 

	* there is a running theme in chapter re: the importance of clearly defined intended architecture, which the author assumes exists, that bring to mind some of the discussions in the previous Software Architecture module regarding the proposed inclusion of an 'architecture.md' file in projects. I was a big fan of this idea as from my experience with that module even with well documented project it is still difficult to find information about the developers reasoning and priorities in relation to their architecture choices. Perhaps the lack of such practice in the development community is another reason entanglements evolve over time; the lack of clear and documented vision and decision making at project inception.
	* the author emphasis not using throughput code (call forwarding) but their example of one the way dependency system as an intended architecture seems to contradict this? -- Edit: I'm keeping this note from earlier in my reading to say if anyone else had this concern it is addressed in the Throughput is Requirement subsection of the Loose Coupling Concerns section.
	
* Rolf de Vries


	* Chapter 6:

		* As other students mentioned, coupling via other matters than source code is only slightly addressed, but it seems just as important to be aware of, and even to prevent the coupling from being too tight. Examples for these types of coupling would be well received, as well as examples/guidelines on how to treat such coupling.
		* The example at the start of the chapter, with the explanations on how the UserService changed through new requirements perfectly shows how code can change from its original (and much simpler) intented purpose. It also shows how easily modules/classes can grow out of hand, but there is usually not a straightforward point where it is clear that the coupling is (too) tight. It requires knowledge about the coupling of all classes to be able to detect (relatively) tight coupling, and then insight in the module/class to know where to refactor or split up the code.
		* The single responsibility principle sounds clear on paper, but in practice, developers can argue how broad or specific a single responsibility is. For example, do you want a single class that handles all database communication, or would you split such a class up, creating one that focusses on each type of database communication, such as things related to users, another to something else etc.? I can imagine this being a subjective matter, even for two developers working on the same codebase.

	* Chapter 7:

		* The authors obviously states that component independence is better than component dependence, and that internal calls (modules within the same component calling each other) are healthy. However, a lot of internal calls between components corresponds to tight coupling between those components, which does not seem healthy. This seems to be contradictory (unless a different type of healthy is meant), and appears to me as the lesser of two evils: rather have tight coupling with component independence than tight coupling with component dependence.
		* Outgoing calls are healthy, but incoming calls are not. Unless the outgoing calls are to third-party libraries, every outgoing call in module A would result in an incoming call in module B. Thus, just delegating distinct concerns to other components is not enough, the other components' involved code should be limited. As such, just having a large amount of outgoing calls should not necessarily be interpreted as healthy.
		* Throughput code seems to be the unwanted child of incoming calls and outgoing calls. However, I think in practice, it is unavoidable to have at least some modules in some components that are throughput code. Not every component is (or should be) able to handle all functionality to answer a call, thus it performs outgoing calls to do so. For example, some component A calls component B, but B needs component C (the database handler component) to answer A's call. Thus, B has some throughput code. However, B's functionality cannot be moved to component C or A (due to seperation of concern), so the throughput code remains.
	
* Haiyin Zhang


	* Chapter6:

		* I like that the author notices some objections and gives further explanations to them. I would agree that inversion of control is indeed a good design principle to achieve loose coupling, since I studied the project Theia in the software architecture class last quarter, and the dependency injection framework inversely.js really plays an important role in the loosely-coupled, component-based architecture.
		* The author says that the best practice is to use the third-party library to replace the custom code. However, if the developer uses the third-party code, he might need to keep an eye on things like the library version update. Will it make things more complicated and require more maintaning effort? It also reminds me of the news that on a Christmas Day, a snow effect appears on buttons on some websites unexpectedly and turns some developers into trouble. It turns out that these websites use the UI framework Ant Design, and that’s a “Christmas Egg” a developer added into the codebase. Generally I agree that most of the popular libraries are well designed, and it’s a good idea to use them, but there might be still some risks.  

	* Chapter7:

		* I like that the author covers the discussion about the throughput code. I would agree that sometimes the throughput is difficult to avoid. Sometimes it might serve for the readability? More opinions about the throughput code? I’m curious about how ofter do the throughput code exists during the work experience and usually whether they’re necessary in the codebase.
	
* Andrzej Westfalewicz

	* Chapter 6:
		* I wanted to undermine the statement “Small, Loosely Coupled Modules Ease Navigation Through the Codebase”. Yes, that is frequently the case, but  not always. For example in event driven systems  debugging and following the code is difficult even when classes that consume events are small. The way the modules are connected is a major factor in navigating the code, not only the sizes of these modules.

	* Chapter 7:
		* In my experience when I was adding new features into a system built from components I had to frequently cut through all of them (new widget on the website, new checks in the API, new functions to the services, new models and tables, new notifications). Is it common that loose component coupling isn't related to logical component coupling.

	
* DANYAO WANG

	* Chapter 6: 
		* I like that the author covered some common objections against loose coupling and provide some analysis and solution. The author mentioned that the design decision to use a framework for implementing IoC should be considered with care to avoid making it harder to maintain the code. I am curious about how to consider this problem? What factors should we consider when choosing a framework?
	* Chapter 7: 
		* As outgoing calls from one component are incoming calls for another component, should we also keep the number of outgoing calls small? Because a large number of outgoing calls may be bad for another component even though it is healthy for a specific component. 

	
* Mingyu Gao
	* chapter 6:
		* Notes: Coupling means the frequency of calls or other connections between two classes. If a class is called more, it should be smaller.
	* chapter 7:
		* Notes: Realizing loose coupling from the level of component is a good idea. 
		* Points: Throughput as a metric of high concurrency performance, poses a threat to loose coupling. Does it means that software systems which need high concurrency performance analysis are more difficult to realize loose coupling. Because more codes are required to add between components to evaluate their performances.

	
* Niels Bauman


	* chapter 6:

		* "Hide Specialized Implementations Behind Interfaces" section: won't this just make development harder in another way?
	* chapter 7:

	* aren't factories just 'throughput' modules? how/when do we separate those terms?
both chapters:

	* how does private vs public encapsulation play a role in this?

	
* Khalid El Haji


	* Chapter 6:
		* The authors make a great case for using a loosely coupled design. In order to accomplish this loosely coupled design the author purposes guidelines. In one of the guideline the concept single responsibility principle is mentioned. This is then “applied” on an example class that has a bunch of methods that all relate to user services. One could argue that this class is tightly coupled but provides a cohesive overview of all functionality related to user services. So in that sense it does meet the single responsibility principle. How should we deal with subjectiveness?

	* Chapter 7:
		* The author states a set of possible objections to loose component coupling. One possible objection which is never dealt with, is that the software requirements can make it impossible to have loose components coupling. How should we deal with this? (albeit probably a rare case in practice)


## Discussion 

* What is the tradeoff between having interfaces to hide implementation but having to maintain many interfaces themselves?

* As with anything, over doing it will be detrimental.

* Interfaces for single classes, as opposed to the advice from the book, is possible for webservices. Also this can be a useful when explicitly wanting to separate the higher level concept from the lower level implementation of a single class.

* Why does hiding implementation reduce coupling in general?
Because when the underlying class changes it is still bound to the overlaying interface, which will reduce refactoring effort. However, for that the interface should be stable.

* Does an interface become useless if you inspect the underlying implementation anyway?

* Then that is probably a problem in the design of the interface. In the case of side effects, thats also design challenge in about the interface.

* Interfaces also increase modularity of code which improves ease of maintenance when the application scales, especially when team the size grows.

* At which point do you decide to split up a class into logical components?
- When specific parts get called together
- Try to think of someone else trying to understand the code base.
- When thinking in terms of entities and their relations it helps to try to reduce dependencies all over, follow what gets used by whom. Try to follow the domain model as best as possible.

* Does coupling only come up when changes are needed?
At least you notice the coupling only if you want to refactor.
It also reduces readability so can be a goal on its own.

* How do we determine good or bad coupling?
Data and config files coupled with other files are good - Logical coupling in different domains is bad

* What about importing too many methods? The book strongly advocates against it.
Having many interface methods not used together is a good sign that it should be split up.

* How to refactor systems to be more event driven is not a part of this course, but it's a current topic. However, many teams appear to avoid it due to execution becomes difficult to follow.

* There is superficial inconsistency between having internal coupling, which chapter 6 deems bad, but chapter 7 deems good.
At some point you must split up modules if they become to large, resulting in internal coupling but in this case it rises naturally.
Splitting up a component in multiple components will result in top level coupling however. This is an engineering tradeoff. 

* Call forwaring is bad, but in an interface layer it's a feature. Or in a sandwich architecture.

* Are outgoing calls always healthy?
It always depends on the business case.

* Documenting the reasoning on this business case to architecture helps in what to refactor later. Especially the engineering tradeoffs. However, choices should speak to themselves ideally. Referring to issues is very helpful in theory, but often old issues and correspondences are not accessible anymore. 

* The ArchUnit framework lets you test your class dependencies by analyzing class names, so you can guarantee explicit architecture choices.

* Besides components that only forward some data without transformation, a real problem is when the component does transform the data in a minimal way that is not actual business logic, there is a dependence that can break but not being actually useful.

* Pure throughput code was actually the adviced architecture by Sun Microsystems.

* A proxy server or load balancer are other good examples of where this throughput code is required, because of the side effects. The data is not changed, but side effects are relevant.