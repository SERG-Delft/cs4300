---
layout: tud
title: Refactoring Workbook
---

In this lecture, we will discuss two chapters of the [_Refactoring Workbook_](https://www.oreilly.com/library/view/refactoring-workbook/0321109295/) book, by William Wake:

* Chapter 1: Smells within classes
* Chapter 2: Smells between classes

<img src="{{ '/img/books/rw.jpeg' | relative_url }}" class="book-cover">

## Comments and Questions
Nick Decker:
- Within classes:
    - I dont agree that a method name suffices as explanation of the method's inner workings as opposed to a comment. Naming is subjective and interpretation will vary per developer. Adding a comment, or docblock above a function will clear up any confusion, even if only one sentence is required to state the intent of the function. This way, developers do not have to guess about implementations and hidden functionality of a method.
- Between classes:
    - Is primitive obsession a code smell? Or do we just have to be careful of how we implement the primitives? The contraindications do not convince me the primitives themselves are the smell.


Rolf de Vries:

- Chapter 1:
    - "What if you don't have tests? Then add them, at least to the areas affected by the refactoring. Sometimes this is tricky—you may be unable to test effectively without changing the design" I agree that the design must sometimes be changed, but doing so is actually a risk because the change may cause other tests to fail or require to be rewritten, all of which can unintentionally lead to new bugs. Breaking up code just to test it requires the developer to pay attention to more than just the newly written tests.
    - I like how the authors addresses Inconsistent names, like "add(), store(), etc." because in my opinion this actually also happens in languages themselves. For example, a Python Queue has put() and Set has add(). One may argue that for Queue and Set, the same thing happens, so it's strange that the names are inconsistent.
    - "Another cause of complexity is the practice of overgeneralizing the design. This is often in anticipation of future requirements, or premature performance tuning. Remove these problems when you run into them." I disagree that this is always the solution. Sometimes the future requirements to come, and then you would have to re-add the code.
    
- Chapter 2:
    - I found it an interesting perspective that design patterns such as Visitor can be interpreted as putting behavior in the "wrong" class.
    - The Hide Delegate solution to Message Chains does not seem like a real solution that makes the method depend on one object only. If you're adding b() and c() to object a's d() method, you're still relying on the intermediate objects. This solution (at least in this example) seems like nothing more than Extract method

- Overall, the chapters were quite long due to all the exercises, but they were easy to read and showed the idea the author was trying to convey well.


Andrzej Westfalewicz:

- Chapter 1:
    - I agree with the statement that the type of the argument/return value should not be used in the name of a function, but only if you can easily deduce the type from the context. In the given example, if addCourse(Course c) is a method in a CourseCollection class then the type in the name is unnecessary. But if it were in a class like SemesterManager the additional information makes the client code more readable. There is also the question what with the situation when you add the functionality of adding another type, for example addEvent(Event e).
- Chapter 2:
    - In “Inappropriate Intimacy” the author states that's bad if the sub-class accesses internal state of the base-class. I fully agree, that's why languages have the distinction between private and protected and it for sure “Often improves communication”. But I can't see how removing these occurrences “Reduces duplication. May reduce size.”


Wessel van de Brug:

- Chapter 1.4:

    - I agree with the author that the use of prefixes (such as _count or m_count) are redundant. However, I would argue that some style choices (such as ALL_UPPER_CASE constants) are beneficial.
    - The author doesn't expand much on the uncommunicative names. I would, for example, be okay with the use of one- and two-character names in mathematical code (e.g. function variables, coordinates, etc.).
    - I've found that, similar to how some methods are named differently while they shouldn't, the opposite holds as well. For example, it would make sense to name the "add" method of a list, queue, and stack differently. Even though they all "add" an item to their internal dataset.

- Chapter 1.5:
   - I agree that, in most cases, speculative generality is unnecessary. However, if done properly, it need not make code much more complicated and could save time in the future (prevention over cure).

- Chapter 2.8:
    - "your code will be more robust if you organize objects by behavior" is, in my opinion, a subjective statement. Component-based designs (e.g. the entity-component-systems used in most game engines) can be very easy to work with. There, the separation of data and behavior provides greater flexibility and may even improve performance (parallelisation).
    - Data classes could also be useful in networking. For example, an intermediate data class could be used to organize data to be sent/received without providing any additional behavior (the sending/receiving should be done separately, as it would be shared between many different data classes).
    
- Chapter 2.9:
    - In the "lazy class" section, the contraindication of communication of intent is mentioned. While not always useful, I've seen people use inheritance (and type systems in general) as an additional constraint on the behavior of classes. For example, using explicit Position and Translation classes on top of a Vector class, one could limit the interaction between "types" of vectors, without changing their behavior. It wouldn't make sense to add a position to a translation, but it would make sense to add a translation to a position.
    
Ching Chi Chuang:
- In the beginning of chapter 1, the author corrects my misunderstanding that refactoring usually takes lots of time. However, the author suggests that it is best to start with small refactoring which lead us to see the remaining problems more clearly. 

- In chapter 1, the author mentions that the presence of comments probably indicates that the code itself is not clear. However, I always appreciate that responsible developers add clear explanations to their functions, regardless of the complexity of the functions.

- In chapter 2, I find an interesting similarity between the symptoms of Lazy Class and Middle Man. The symptom of Lazy Class is that it isn’t doing much —its parents, children, or callers seem to be doing all the associated work. The symptom of Middle Man is that it mostly delegates its work to method on another object. Despite of these two symptoms, there are still justifications for their continued existence. 


Andries Reurink:
- P1:
    - Measured smells: The point of comments being a smell for refactoring makes me think perhaps to think twice when feeling the need to write a comment. I've always learned basically "the more comments the better" but if a more descriptive function/variable name or an extracted function does the trick better, that's great.
    - What is happening in chapter 3? What do they mean by evolve the patterns?
    
- P2:
    - Responsibility: Message chain: I don't understand how this involves multiple objects. Usually these chains are obtained by having methods return their object, so a.b().c().d() means methods b,c and d are called on object a. I thought this was a good thing? It's very easy to read the sequence of calls. 
    

Danyao Wang:
- General points:
    - I like the way of giving some questions about the content and encouraging readers to think and figure it out. It is also good that these smells can help us refactor code and tell us what kind of codes should be prevented when we write them initially.
    - I am curious about why the author only provided the methods' name without description or explanation. It cannot provide enough information sometimes.

- part3:
    - The author introduced some smells' symptoms but did not explain why they need refactoring, which is not clear or convincing—for example, the primitive obsession.
    - As the author described, when dealing with an incomplete library class, if we Introduce Foreign Method on a client of the library class, it would become Feature Envy. I once have a similar experience, and the library would have compilation errors if we subclass the library class or introduce a foreign method on a client of the library class. As a result, we overwrite the library code directly to solve this problem. I am curious if it is a good solution to change the library code directly.


Haiyin Zhang:
- Chapter 1:
    - Note: This chapter gives a new definition of refactoring: Refactoring is the art of safely improving the design of existing code. The explanation of refactoring is clearer than in the previous book.
    - Note: refactoring preserves the knowledge embedded in the existing code.
    - Note: The author states that "In the best case, refactorings are so well defined that they can be automated", which can be linked to the previous book we read.
    - Note: If you want to refactor, the essential precondition is having solid tests
    - I agree that refactoring changes the balance point between up-front design and emergent design. However, how can we find this balance point in practice?
    - What does it mean by "Most refactorings have built-in bases "? (in chapter "The Refactoring Cycle")

- Chapter 2:
    - What is "Primitive Obsession"? Why is it not good to be "Primitive Obsession"? I feel like it is still not so clear to me…
    

Mingyu Gao:
- General feeling: This book lists many kinds of smells with symptoms, causes, and other three parts. This kind of illustration is clear but it covers too wide. I learn many types of 'smell code' in this book and I will apply these in our project.
My point is about comments, I am used to putting many comments in my code and it will feel easier if an author could offer explicit comments in his code when I read others' code.  However, in chapter2 the author thought comments were "smell code". I am wondering whether an excellent developer should avoid commenting. Because good code can speak for themselves.


Khalid El Haji:
- Chapter 1:
    - In section 7 the author proposes the use of DeMorgan’s Law to simplify complex conditionals. This however is a misapplication of the DeMorgan’s Law as the goal of law is not to simplify propositional logic but to express it in a different equivalent form. Especially in the general context of programming there is no single rule by which the conditional logic can be simplified, this would be entirely context dependent. Always applying DeMorgan’s Law is not a guaranteed to actually make the conditional more easily understandable.
    
- Chapter 2:
    -  I have no particular discussion point for this chapter. Nonetheless, I thought it was interesting how the author described each of the refactoring and the symptoms of the problem (and that sometimes it’s wise to leave the code as it is).

## Discussion
Chapter 1:

- Long and complex methods:
    - Longer methods can always be written smaller, should they? The opinions vary. Some students argue that sometimes, a longer method also allows for more readability/understandability. Just making it short might be counterproductive for readability. Other students argue that long methods are actually hard to follow, as usually they do multiple things. Instead, extracting repeatable functionality with clear method names makes it easier to follow what is happening at every step. If the methods are simple, it is less bad if they are long, because they are easy to follow. However, why would a simple method be long, would it not be easier to split it up into its simple components?
    - Author claims that a method should have only a very small amount of parameters (1 or 2). That is quite low, some students argue that 5 should be a nicer limit, but other students argue that 5 is already too high. Mauricio explains that when he writes domain code, he is content with low amounts of parameters. When he is writing infrastructure code, this is a different story. Making the methods small made them ugly. Sometimes extracting a method did not provide any more readability than just a comment explaining what the next 10 lines would do.

        - Jeanderson gives an example how sometimes methods become complex and less readable because there are so many edge cases to consider. To have high performing code, to treat all edge cases, code can become more complex and less readable, but it allows for the code to work well.
        - Vivek explains that he usually uses 4 parameters. Using more affects the performance, because then it would go to the stack instead of the register. Decision making is outsourced to the leaf node. Going up in the stack would just be method calls. If a method has too many method calls, he groups them and makes subcalls out of them. This is interesting to keep in mind if you are writing code where speed is very important for the performance of the system.
        - Mauricio shows how Flog (by Google) prioritises performance over beautiful code, by writing methods for every possible combination of inputs arguments. E.g. foo(int a1) and foo(int a1, int a2) and foo(int a1, int a2, int a3) etc. A student notes how they could automate the creation of that code, by creating the boilerplate for all these methods.    
    
- Complicated conditionals:
    - The author proposes the use of DeMorgan’s Law to simplify complex conditionals. This however is a misapplication of the DeMorgan’s Law as the goal of law is not to simplify propositional logic but to express it in a different equivalent form. While applying it can improve readability, it is not in general a guarantee to do so. One student argues that enforcing DeMorgan's Law on your code makes it easier to follow. Another states that if you *need* DeMorgan's Law, it can be an indication that your code is too complex and needs splitting up.
    - Using fancy boolean logic to optimise stuff is something you can expect the compiler to do. If you have very complex complex if statements, you can try to extract that as readable method or variable.
    - Mauricio shows an aircraft code example of 30 flags in an if statement. Vivek says that a good approach would be to have each flag have a clear name and group those that belong together. They should not be scattered all over the place.
    - When working with a lot of flags, a student likes to represent them with binary values, so you can compare the state with integers, related to bitmasks. Using wrapper functions and clear methods would improve readability for other users. However, the huge complexity would still be there. It might depend on which approach the developers would prefer.
    

- Semantic naming:
  - The author states a few naming conventions, like how a group of programmers knows that an all caps variable is a constant, this makes communication in the team easier. The author claims that one should not do this, but some students argue that this actually is a good approach, and it can depend on the language type (dynamically vs statically typed). Including the type in a (not typed) Python variable name makes it easier for others to understand what it represents. Another student argues that these standards can be different between teams, so it may make joining a new team harder because their rules conflict with the ones from the old team.
    - IDEs now are very good, they can usually know what the type is of what you're working with, even in dynamically typed languages. However, this is rather new and especially back in the day, it was more conventional to use for example Hungarian notation so others would know what the variable is about.


Chapter 3:
- Message chain:
    - There was some confusion among the students about why message chains (```a.b().c().d()```) are bad. It is not when you can chain methods on the same object every time (e.g. Python: ```"abc".replace("a", "x").replace("b", "y")```. It is bad when ```b()``` and ```c()``` return different classes. This could expose functionality that shouldn't be exposed, and causes problems when any of the intermediate classes change.


- Comments:
  - The author says that removing comments is a good practice. However, some students argue that comments improve code quality and readability. Comments can help your readers/teammates understand you. Not adding comments to your code can sometimes make it very difficult for others to understand your code.
  - Agile believes that your code never needs comments. If it has comments, your method is too long and needs splitting up. But if you don't have time to refactor, a comment could be an alright intermediate solution. A student notes that the next time he writes comments, he will think about whether he can just refactor. Comments can be considered as informal documentation, and given that most developers don't write any documentation, comments at least provide some on an informal level.
  - Sometimes people overdo it, making the comments very tightly coupled to the code, so changing the code would require changing the comment as well.
  - It's okay to comment ***why*** you do certain things, but not what you're doing. If you're doing the latter, you should think about refactoring.
  
- Organising objects by behavior:
  - This is a concept that is used by Jitsi. Some student notes that is it hard to comprehend how this would work. The general object stuff was available. You could use the models wherever you wanted to. It was a data-driven layer with the necessary models. For each feature it would do dependency injection and use the right models to implement the feature.
  - The overall design comes from the use-case. It is up to the developer how to implement the behavior.
  - "Your code will be more robust if you organise by behavior". Looking at the chapter as a whole, there are lots of smells that can emerge if you don't know where to put data. In an object-oriented system, you want to combine behavior and data. Some students are unsure how to interpret the aforementioned quote, and what exactly the smell is.
  - Separating data and behaviour can make sense when doing threading or distributed systems, but in most cases it goes against object-oriented programming.
  - Having data objects can be perfectly fine, for example for Model-View-View-Model. Keep your original rich model, but create data transfer objects for specific clients.
  

- Overall, the book has a lot of examples, making the chapters very long to read. Most students just skipped those.


