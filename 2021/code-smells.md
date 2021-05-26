---
layout: tud
title: Code smells
---

In this lecture, we will discuss two papers:

* Aniche, Maurício, Gabriele Bavota, Christoph Treude, Marco Aurélio Gerosa, and Arie van Deursen. "Code smells for model-view-controller architectures." Empirical Software Engineering 23, no. 4 (2018): 2121-2157.
* Sharma, T., Singh, P., & Spinellis, D. (2020). An empirical investigation on the relationship between design and architecture smells. Empirical Software Engineering, 25(5), 4020-4068.

Although not compulsory, I also recommend the following papers:

* Bavota, G., Dit, B., Oliveto, R., Di Penta, M., Poshyvanyk, D., & De Lucia, A. (2013, May). An empirical study on the developers' perception of software coupling. In 2013 35th International Conference on Software Engineering (ICSE) (pp. 692-701). IEEE.
* F. Khomh, M. Di Penta and Y.-G. Guéhéneuc, "An Exploratory Study of the Impact of Code Smells on Software Change-proneness," 16th Working Conference on Reverse Engineering (WCRE'09), Lille, France, October 2009, pp. 75-84.


## Comments and Questions
	
- Nick Dekker
    - Code smells paper:
        - The answering of the RQs have little background on how the answering methods were chosen. I wonder how different the results were for different criteria, for example for the BOA query on the MVC projects and the resulting data.

    - Architecture smells: 
        - I like the way they approached the manual validation, it shows tools do a pretty good job
        - Figure 6 is said to be an indication of a strong positive correlation between design and architecture smells, I would expect less spread in a strong positive correlation. Is it not a weak positive correlation?


- Andrzej Westfalewicz
    - Code smells for model-view-controller architectures:
        - In .NET with Entity Framework many developers don't consider “Meddling Service” a code smell. In many cases the repository pattern just adds not needed complexity and it would be better to access the database from logic. However it's important to still keep methods short and not violate single responsibility.
        - I'm not surprised that the “Laborious Repository Method” is removed pretty fast. Myself I had this issue many times that I created a method that was querying for two things, only to divide it into separate methods a month later when I only needed one result somewhere else in code.

    - An empirical investigation on the relationship between design and architecture smells:
        - Did the authors include public classes when counting the “Unutilized abstraction”. I feel like in many libraries/packages you are not using the classes that you create, but exposing them to be utilized by client code.
        - The “Imperative Abstraction” code smell is in conflict with CQRS pattern that I usually used. Yes you create many files, but in many cases this actually makes things more organized.
        - “We find that smell density does not depend on repository size.” It would be interesting to investigate smell density vs repository age.
	

- Rolf de Vries
    - Code smells for Model-View-Controller architectures:
        - I like the motivation behind creating the catalog specific for MVC smells. If such catalogs are also created for other design patterns, it would be good to combine them similar to Fowler's Refactoring book, so there is a centralized source of information for developers to learn these design pattern specific smells.
        - Similarly, I like how the authors realize they've only interviewed Spring developers and want to test their generalizability by interviewing non-Spring developers. However, the amount of non-Spring developers (4) is not very high, and it would have been better if more were interviewed.
        - It's interesting to learn that MVC smells are introduced at artifact creation instead of maintenance, similar to traditional smells. This was something we were interested to look into for our project as well (the traditional smells)

    - An empirical investigation on the relationship between design and architecture smells:
        - Interesting to see how the architecture smells and code smells are related and affect each other. The amount of instances the authors found is quite large, and are a good source of examples for future research.
        - While it's always been obvious that code smells are bad, I did not expect them to be such a large cause in architectural anomalies, like the research from Macia et al. \[50\] showed. I wonder how often a code smell is ignored because it seems somewhat innocent, but in fact it has already affected the architecture.
        - Being able to automatically detect architecture smells seems like a good addition to current analysis tools. While the authors used C# repositories, it'd be beneficial if automated detection could be applied to different languages too.

	
- Andries Reurink
    - Code smells:
        - I like the idea of the methodology as standalone research contribution. It feels like a standardized merge of the tools used in this field, which we have seen in the other papers as well. I find it difficult to assess but since it's peer reviewed I will assume its merit. I wonder if this has been adopted as such by other researchers since 2017.

    - Empirical investigation:
        - I haven't heard of causality analysis before but it's very interesting. I would say it's also the most profound conclusion of this paper. I would have thought it would be the other way around: Architecture smells causing design smells, since you would be "forced" to hack solutions when your architecture is lacking.

	
- Khalid El Haji
    - I like how both research papers are explicit in their research questions (and their corresponding answers).
    - Paper “An empirical investigation on the relationship between design and architecture smells”
        - The paper does a great job in explicitly defining architecture/design smells and their detection mechanism using the literature.
        - Interesting to see Cyclic Dependency to be such a prominent smell in codebases. This makes sense considering it’s hard to spot manually. How should we deal with this?

    - Paper “Code smells for Model-View-Controller architectures”
        - Here we again that cycle-related smell occurs the most (similar to the previous paper).
        - Interesting to see how cyclically-dependent modularization and dense structure are related. The authors explain how the cycles increase the complexity of classes which increases the dense structure. I did not know that cyclic-related smell are so prominent and also have quite poor consequences.
	

- Chadha Degachi
    - An empirical investigation on the relationship between design and architecture smells
        - Overall I like this paper but at times I failed to see the difference between the code smells they were suggesting and those that already exists even at the level or granularity e.g. rebellious hierarchy and refused bequest 
        - I noticed a couple of reference to the 'instance of' issue we discussed earlier, its interesting to see this smell manifesting at high levels of abstraction too.

    - Code smells for Model-View-Controller architectures
        - I am interested in the finding re: the long survivability of code smells, why is that so many were never removed. 
        - The paper is an interesting model of how industry experts can inform research decisions. 

## Takeaways

- The term “code smell” doesn't refer only to simple implementation mistakes, but also to design and architectural problems.

- There is a lot of studies and papers about implementation code smell where researchers try to quantitatively measure the effects of these smells. Papers measuring code smells on the design and  architectural level are less frequent.

- Code smells on one levels can lead to smells on another level and this relation is bidirectional. For example, bad architecture can forces developers to make hacks, but also the existence of hacks in code can cause bad architectural decisions.

- Researchers in the 2nd paper used [Designite](https://www.designite-tools.com/) to automatically detect higher level smells. Unlike most other tools, this one focuses on detecting design and architectural smells instead of implementation ones.

- Most papers are investigating projects in Java or in C family (C, C++, C#). This may be because:
    - They dominate the industry. 
    - Datasets aren't so “contaminated” with academic code like it is for Python. 
    - They are statically typed which help with the analysis.
    - The work of Martin Fowler, which is the basis for many papers relates to these languages. 
    - Other languages lack the tooling and most tools use very naive detection strategies.
    - Other languages have a younger community where the concept of throwing away code is more acceptable. Since the code is not eternal, less effort is made to keep it clean. However, throwing away code also means that there is more code created so maybe such research is still necessary.
    - Other languages allow for complicated constructs that are rarely used that break tools.
    - Professional tooling sometimes supports most languages – for example Sigrid from SIG supports more than 350 languages.
 
- Disposable code isn't always bad. The agile methodology actually has disposing and changing the code in its core. However there will be always parts of the systems that cannot be remade.

- Searching for code smells in a given context, for example for a specific design pattern, can give better resuts compared to generic code smells. Searching for code smells within the context of a single company may be to specific and not very useful since the lack of generalizability. However companies still frequently define own convention and support them with e.g. SonarCube rules. It's good to start generic, but then zoom into specific patterns to gain better insights.

- Book “Object-Oriented Design Heuristics” describes ways of measuring code and calculating metrics when looking for code smells. Book “Object-Oriented Metrics in Practice” proposes concrete strategies to detect code smells. PMD static code analyzer measures metrics and detects code smells, but uses same hardcoded thresholds for all classes.

- Code smells and code metrics should be interpreted differently depending on the role of the class. Distribution of most metrics is significantly different for different class kinds (such like Controllers, Services, Entities). This requires to detect what is the kind of a class - for some this is easy (e.g. Controllers have to inherit from a base controller class) but for some this may require user input (which makes the tool much less handy) or parsing the class name (which can introduce errors). However, it's hard to define context specific code smells and at the moment is no way to automate the process for different patterns and architectures.

- Models trained on a specific dataset perform better than on general dataset. For example the system suggesting extract method refactor performed much better at ING when trained on the ING system compared to when trained at open source systems.

- Possible sources of  data for finding new code smells:
     - GitHub repositories,
     - GitHub issues,
     - StackOverflow (however stack overflow entries are usually very technical and lack context),
     - New packages added to Npm or Nuget.

- Grey literature studies leverage blogs and other non-peer-review sources to gain knowledge. In the case of code smells these are developer podcasts and conferences where people discuss problems and solutions they encountered in their work.

- Even thought the statistical data suggests that there is a correlation it's important to investigate the figure visually. It's also important to keep the axis in scale and not focus to much on the outliers. 
See [Simpson's paradox](https://en.wikipedia.org/wiki/Simpson%27s_paradox) and [The Datasaurus Dozen](https://www.autodesk.com/research/publications/same-stats-different-graphs).
