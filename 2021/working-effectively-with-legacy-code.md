---
layout: tud
title: Refactoring Workbook
---

In this lecture, we will discuss two chapters of the [_Working Effectively with Legacy Code_](https://www.oreilly.com/library/view/working-effectively-with/0131177052/) book, by Michael Feathers:

* Chapter 9: I Can't Get This Class into a Test Harness
* Chapter 20: This Class Is Too Big and I Don't Want It to Get Any Bigger

<img src="{{ '/img/books/wewlc.jpeg' | relative_url }}" class="book-cover">

For the interested readers, you may also want to read the [_Object-Oriented Reengineering Patterns_](http://scg.unibe.ch/download/oorp/) (open) book, by Demeyer, Ducasse, and Nierstrasz. In particular:

* Chapter 3: First contact
* Chapter 4: Initial understanding



## Comments and Questions

Nick Dekker:

- Chapter 9:
  - "The best way to see if you will have trouble instantiating a class in a test harness is to just try to do it." seems to be taking the easy way out.
  - The author proposes creating a new constructor for testing and introducing an initialize method. Another book on our reading list said initialize methods are bad. The init method can be a code smell and separating the init behaviour from the constructor might confuse of cause wrong behaviour. Besides that, now it seems like we have created unnecessary code just for our tests that is not used in the production code. This seems like bad practice.
- Chapter 20:
  - testing private methods should not be desirable, instead refactor into a different class where the method is not private. Does this mean that private methods should be avoided?



Andrzej Westfalewicz

- Chapter 9:
  - Author many times mentions that accessing external services (other systems or the database) is undesirable while testing. Yes, it is... in unit testing, but in integration tests you actually want to make these calls.
  - In several examples the author creates a way to change an internal variable, for example the "Supersede Instance Variable" method. Essentially creating a backdoor for tests. But I in Java and C# you can make this substitution using reflections and without exposing the variable in production code.
- Chapter 20:
  - I liked the method “Look for Internal Relationships” because it shows how methods interact with each other and with variables. However I feel like this method can sometimes predict a split that makes no sense from the side of the business model. The naming step should also be a reflection if newly created classes are reasonable.



Chadha Degachi

- Chapter 9:
  - "PermitRepository is a singleton. Because it is, it is particularly hard to fake. [...]. That might be fine in production code, but, when testing, each test in a suite of tests should be a mini-application, in a way: It should be totally isolated from the other tests. So, to run code containing singletons in a test harness, we have to relax the singleton property." this whole section is very interesting, I hadn't thought of the testing related complications when using Singletons before.  - there is a lot of discussion of exact interface and faking objects for testing but it is worth nothing you can do many of those things through libraries like https://site.mockito.org/ without having to clutter your own codebase with test-only classes and methods
- Chapter 20:
  - breaking down classes, and refacotring in general, on an as-needed basis seems like a good compromise between code cleaning and feature development and their competeting priroties which we've discussesd before.  - the feature sketches for refactoring in combination with method grouping based on method name would be an interesting approach to automate and turn into a refactoring aid.



Haiyin Zhang

- Chapter 9: 
  - Note: When doing testing, we can create the fake object to simulate the real object sometimes.
  - Note: Often people create singletons because they want to have a global variable. They feel that it would be too painful to pass the variable around to the places where it is needed. I did this sometimes in the previous project, but I’ll keep in mind that this is not a good choice and avoid doing so in the future.
  - According to the author, there are not many rules for test code. The test code just needs to be clean, easy to understand and change. So in practice, is that true? What may other rules need to be followed when writing test code?
  - Will use null in the parameter decrease the flexibility of the class? Once the class or method changes and the parameter is used, the test case needs to be rewritten again.
- Chapter 20: 
  - This chapter talks a lot about refactoring. Although the book is called “working effectively with legacy code”, it looks like we can’t actually work with legacy code, but we must do the refactoring sometimes. So when the class gets bigger and bigger, refactoring is unavoidable, right? We should avoid big class from the beginning.



Ching Chi Chuang

- In chapter 9, the author briefly discuss about why people want to enforce singletons. This reminds me our discussion about whether singleton is a code smell or not in a lecture of early weeks. Based on this author's explanation, it is fine to use singletons to model the real world. For example, some hardware-controlled systems are unique. However, it would be a code smell if people create singletons because they want to have a global variable.



Niels Bauman

- Chapter 9: 
  - mocking will make things easier



Danyao Wang

- Chapter 9: 
  - “Often people create singletons because they want to have a global variable. They feel that it would be too painful to pass the variable around to the places where it is needed.” It is a thought-provoking conclusion. I often do similar operations. I will be more cautious in using singletons in the future.
- Chapter 20: 
  - As the author said, "In nearly every case that I’ve seen, when teams go on a large refactoring binge, system stability breaks down for a little while, even if they are being careful and writing tests as they go". Therefore, we'd better avoid creating big classes in the beginning. 
  - The author mentioned that "if you have the urge to test a private method, the method shouldn’t be private; if making the method public bothers you, chances are, it is because it is part of a separate responsibility. It should be on another class." Does this mean that private methods should not exist?



## Discussion

In several examples the author creates a way to change an internal variable, for example the "Supersede Instance Variable" method. Essentially creating a backdoor for tests. But I in Java and C# you can make this substitution using reflections and without exposing the variable in production code.

- you may have a lot of classes or methods that you were only using for testing, which may seem to clog up the production code.

- don't know if Mockito was already properly widely used by the time the book was published, but those kinds of mock objects and the libraries that let you make mock objects would let you do a lot of this testing without actually cluttering your code with backdoors and test code.

  

The author proposes creating a new constructor for testing and introducing an initialize method. Another book on our reading list said initialize methods are bad. The init method can be a code smell and separating the init behaviour from the constructor might confuse of cause wrong behaviour. Besides that, now it seems like we have created unnecessary code just for our tests that is not used in the production code. This seems like bad practice.

- making production code changes for testing seems horrible, but sometimes we don't have choice
- Maybe create an additional class in your test suite and make your test code out of your production code is a better choice. Your test code has access to the adapter or extension. It's one-way dependency: the test code depends on the production code, but not the other way round. Just test the public interface.
- Creating some kind of middleware for your test is possible, but it does create some kind of complication. When your code changes, your middleware also needs to be updated.



Should we change the production code to facilitate testing or not? The trade off in changing the production code as little as possible  to facilitate testing.

- For example, he adds a constructor that receives a new dependency. This is a way to facilitate testing and also a way to provide the new clients of this class in the future, a more elegant way to pass a dependency. If you were in a greenfield, you would create a class that receive the dependencies via the constructor because you know this allows for mocking. The old version of the class does not. So you can give a constructor that allows this for the future consumers of this class, but you also have the default constructor because the entire legacy code primarily depends on this one, and deleting this one is tricky. So this type of refactorings is like, you want to do a small change that will make things easier to be tested, and it's also going to make things easier for the future.
- you can just call the parameterized constructor and the empty constructor, and then you will not need the extra initialized method in Java, but maybe not in C++
- In C++, you can call the constructor from another constructor, but the author didn't do this in this book.



Reflection:

- The example is in C++ and C++ doesn't have the reflection
- Java framework powermock [https://powermock.github.io](https://powermock.github.io/)
- Powermock allows people to mock things like static methods or private stuff, and it relies a lot on reflection and sometimes it even changes the class loader.
- Chaining constructors in C++ is allowed since 2011. It's a new feature.



 You don't like to change your production code to facilitate testing. Why is that?

- It clutters your production code.
- It might affect the production code if you're not careful. It could have side effects.
- You are doing a change in the production code to facilitate testing, but this change has a different semantics that you want. 
- Maybe you know even a simple change in your implementation affects your programming in some way that you don't know. This used to be a common bug when people started to migrate their stuff to dependency injection frameworks like spring or Guice or others, because they are you had to think about the lifecycle of the object.



What type of refactorings do you like? Are there types of refactoring you feel more confident in doing and types of refactoring that you do not feel so confident in doing? 

- If after your refactoring, your code can still be executed in production, it's fine. But if you're adding something extra, only for tests, it's usually you're adding something that's it doesn't need to be there. 
- So for me I usually don't mind creating constructors. You know you have just a default constructor in the class that does stuff and adding a new constructor that receives the dependencies. That doesn't really bother me so much I feel very comfortable in doing this refactoring.
- Some languages like PHP has optional parameters but no option for multiple constructors, so you can't introduce a new one. That's against the limitation, so you would have to think of another way. Maybe you just add optional parameters but if you have to change some parameters and you're kind of stuck.
- With those optional parameters, you could always use them as a dependency to the very end. By default, they won't be added. That's ugly but we don't have a choice sometimes. 
- If you're doing this in greenfield development and things are beautiful and you're just making things out of it, then that might be a bad thing. But if we're reusing the legacy system trying to refactor, maybe that's the first solid step you can take, to just make a ugly constructor first. In the future you refactor things by things. And then the ugly things disappear.



Greenfield development 

- Greenfield development is about when you're going to start a new software, and you have no legacy constraints, then you're free to pick the coolest technologies. You can apply the best software design techniques, which means you're starting something from scratch.
- The opposite of this is a legacy system. Some people call it brownfield development, which is, you're developing something but you have the legacy. And this legacy constrains you. For example, we were maintaining this very early ASP software, and ASP was already an outdated language when we started. That system was so huge that it was just impossible to migrate it to another language so developing there was not a greenfield thing. 
- In greenfield development, you're free to take whatever decision you want. You don't suffer from legacy. 



"The best way to see if you will have trouble instantiating a class in a test harness is to just try to do it." seems to be taking the easy way out.

- We don't know the author has tried, but it looks like he just says, I'm just gonna try to make this and it kind of works for me so it's mostly best practice. I'm not sure about that. 
- Another interpretation for the sentence: let the compiler tell you what to do. And you can run it and check what errors you get.
- If he tries to create a test harness for a certain class,  there must be a method to do it step by step. But he is like not doing the research part and just going into the practical work. 
- In practice, we will just open the JUnit code and keep trying things to see things like how the constructor looks and what it depends on. We just submitted a paper where we watched a bunch of developers testing stuff, and we gave them methods that they never saw before. With a beautiful java doc, they spent 30 seconds in the Java doc and then they went to Junit and started to poke the method and see how the method would respond right and I guess this is just how we prefer to do things. We just try and we see the results and we learn from it and we repeat. 
- You would rather have someone read the docs and fully understand it before you try to make something. You don't get further with just poking and prodding and testing and experimenting. 
- That would be challenging to do in very complex class structures. When testing such complex classes, it's pretty hard to understand the class before you open it.
- It is a mix of experimentation, trying out and trying to comprehend what's going on maybe with the documentation, maybe reading other calls to that class right because maybe you don't have tests that you can learn from. But you have other classes in your system that call the class you want to test so you can learn by example. I think that's also a very common strategy in legacy systems. You read how other classes called the test you want to test.



Testing private methods should not be desirable, instead refactor into a different class where the method is not private. Does this mean that private methods should be avoided?

- Sometimes you can't avoid the private method.
- I only know one example that can't avoid the private method. Maybe an API setting that you don't want others to set some values during execution for instance.  Maybe that can be public but then still more security to be private.
- I think they can be necessary. Or not necessarily but preferable to the public method since you don't want to expose the information, but since it's said in the book that private method methods should be refactored to public classes, then you can still access the information somehow. It feels like that counters the idea of a private method, so it feels weird to say that you should refactor private methods into a public one.



- It's in the context of really large classes. The advise doesn't hold for a small method. 

- So then the problem will more be the single responsibility problem.

- The smaller method still holds that your private message should or could be private, but in larger methods larger classes, it will be beneficial to extract them.

- Normally you can test the private method via the public call. However, sometimes in legacy systems, you look at the private methods, and you have this urge to test these methods isolated from the public methods, because this private method just does too much. You can still test it from the public method but you look at it and you think it would be so much easier if I could exercise this private method alone in my unit tests. In this case, if you really feel this is an independent thing that should be tested independently, it might be because this is a different responsibility. So with a different responsibility, you should put it in a different place. You don't want this class to do two things.  That's usually the approach that the testing community TDD community follows. If you want to test the methods of private methods isolated from the public method, it might be that we should go to a different class. This perspective helps me reflect how big my private methods are and if my public methods just not doing too many things that you should start breaking down into different classes.

- It also helps with the number of test cases then. If you can test your private methods separately, and you have n plus n instead of n times n test paths. 

- You can reduce the number of tests by simplifying things. It's something easy to monitor, and the refactoring is not so complicated.

- Example:

  <img src="{{ '/img/books/working-effectively-with-legacy-code/1.png'}}">

- originally you have this class but you want to test the private method isolated, so you can move the private method to the new class.

  <img src="{{ '/img/books/working-effectively-with-legacy-code/2.png'}}">

- in the future you may create a more elegant constructor, and the old constructor will die.

  <img src="{{ '/img/books/working-effectively-with-legacy-code/3.png'}}">

- Not even in legacy systems, sometimes you're developing something new, and you just don't know much about what you're developing because you're still learning. So the refactoring applies even in Greenfield

- it's pretty hard to refactor everything in a huge horrible legacy system at one time.



"PermitRepository is a singleton. Because it is, it is particularly hard to fake. [...]. That might be fine in production code, but, when testing, each test in a suite of tests should be a mini-application, in a way: It should be totally isolated from the other tests. So, to run code containing singletons in a test harness, we have to relax the singleton property." this whole section is very interesting, I hadn't thought of the testing related complications when using Singletons before. 

- There is a testing framework in Java that changes the class loader so that for every test of the test suites, it reloads everything so you wouldn't have this singleton problem. Whenever you run a test, things are clean again in the whole JVM space.
- It is a common approach for frameworks that use AI. eg. Evosuite.



Although the book is called “working effectively with legacy code”, it looks like we can’t actually work with legacy code, but we must do the refactoring sometimes. 

- It depends on how bad the code actually is. 
- Things are not just black and white. Sometimes things are in between and you have some very ugly parts that you really cannot work with and you also have good parts. The challenge for someone who works on those systems is to identify those parts and know how to handle both of them.



How would you handle the situation when your new beautiful system needs to talk to the horrible legacy system?

- I once need to create new additional features that needed the data from the old system. I just created an API that extracts all the data that I needed and put it in a new database and the structure that I wanted. So it had a call back to the old system, but then after that, it didn't need it anymore. So it's a kind of migration.

- Treating the legacy system as something outside of the boundaries and in creating an API. The green part calls the API, gets the data back, converts it to the beautiful new data structures you have, and from there on, everything is clean.

- That's a very common strategy from the microservices people use nowadays. If you think of microservices, you may have some services that are horrible and some services that are beautiful. What you do is you make the horrible things to just offer data, and then the new beautiful service calls the horrible thing gets the data and converts to something more elegant and moves on, that's one strategy. 

- Create a layer, talking to the old system and then talking to the new system.

- Get the old and the new data from different API's, merge the responses, and let the new one overwrite the old data. But if the new data doesn't exist, and the old data is the fallback. 

- Anti-corruption layer: The Anti Corruption layer goes to the system, gets the response back, and translates it back to the beautiful system. This is quite a common approach.

- Data is very important to consider when working with the legacy system.

- Recommend book: Monoliths to Microservices, Sam Newman

  <img src="{{ '/img/books/working-effectively-with-legacy-code/4.png'}}">

- ORMs (Object-Relational Mapping systems) / Hibernate

- When I was developing in PHP and I saw a framework to help you organize your web application, which is beautiful. But it was many years after PHP go through the popular. So there is PHP legacy code out there not because PHP is not good but because it was the best you could do back then.



In chapter 9, the author briefly discuss about why people want to enforce singletons. This reminds me our discussion about whether singleton is a code smell or not in a lecture of early weeks. Based on this author's explanation, it is fine to use singletons to model the real world. For example, some hardware-controlled systems are unique. However, it would be a code smell if people create singletons because they want to have a global variable.

- He spent so much time talking about testing singleton classes and how complicated it is and but still uses them.
- From the book's perspective, discussing Singleton is very important because they do exist. Suppose we're in a Greenfield. Would you create a singleton probably?
- Singleton's exist because that's in the business logic.
- You can find a way not to use Singleton. You can make other objects pointing to that single object instead. So I don't implement Singleton in my domain objects so much, but I do implement Singleton for cross cutting concerns. For example, if I have a class that gives me database connections, I usually mark this class as application scopes, which is kind of the elegant way of doing Singleton. So if you're using some dependency injection framework like spring, you can see that these objects should be just one for the entire application so you create the Singleton.



Question for next class:

- Should we use visual languages like UML?