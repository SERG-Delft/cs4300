---
layout: tud
title: Empirical studies - I 
---

In this lecture, we will discuss two papers:

* Kim, M., Zimmermann, T., & Nagappan, N. (2014). An empirical study of refactoring challenges and benefits at microsoft. IEEE Transactions on Software Engineering, 40(7), 633-649.
* E. Murphy-Hill, C. Parnin, and A. P. Black, "How we refactor, and how we know it," 31st International Conference on Software Engineering (ICSE'09), pp. 287-297, 2009.

Although not compulsory, I also recommend the following papers:

* Tómasdóttir, K. F., Aniche, M., & Van Deursen, A. (2018). The adoption of javascript linters in practice: A case study on eslint. IEEE Transactions on Software Engineering, 46(8), 863-891.



## Comments and Questions

- Andries Reurink：

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - Do these tools that measure impact of refactorings actually exist? 1 conclusion implies the technical and developer definition widely differ. Mostly it appears most developers dont -only refactor- but do other things simultaneously. This seems to me something different.
    - "When  we  asked,“how  does  the  abstraction  level  of Martin  Fowler’s  refactorings  or  refactoring  types  sup-ported  by  Visual  Studio  match  the  kinds  of  refactoring that  you  perform?”,  71%  said these  basic  refactorings are  often  a  part  of larger,  higher-level effort  to  improve existing software" 
    - We did not read Fowler I think but in one of the books this is also mentioned. Again, I feel like the authors imply that this is something missing in the definition, but the point of the strict definitions is that they are reduced and atomic so they can be automated right?
    
  - How We Refactor, and How We Know It: 
    - "Questions still remain for researchers to answer. Why is the RENAME refactoring tool so much more popular than other refactoring tools?" I recognize this with myself, that automatic renaming does exactly what you expect it to, so does not really take getting used to, but for example extract method throws code around where you need to sort of readjust to what has happened, which takes some more getting used to. Does anyone else want to speculate on this?

- Chadha Degachi

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - "Preferentially refactored modules have higher test adequacy and they experience defect reduction; however, this defect reduction cannot be attributed to the role of refactoring changes alone according to our regression analysis." - I like this point, it reminds me that it is very difficult indeed to isolate the effects of refactorings from all other code changes in large 'real-life' systems.
    - in general the paper paints an idea of refactoring that is much less formal and rigorously defined/controlled than what academic circles put forth. The second paper also has some finding that support this.
    - "Regarding H4.A, the top 5% has smaller size metrics than the rest in Vista. This indicates that refactoring changes were not preferentially applied to the modules with large size." - interesting that large classes do not be as much a problem or priorities for those developers as one would expect.
    - "Carriere et al.’s case study found the average time taken to resolve tickets decreases after re-architecting the system [49]." - this a pretty interesting benefit, and not a metric of maintainability I had considered before.

  - How We Refactor, and How We Know It
    - "almost 90% of refactorings are performed manually, without the help of tools (Section 3.8)" - the paper posits it might be that the interfaces are too complicated for the developers but I wander if the developers possibly don't trust the tool not to introduce unintended side effects and thus only use it for small refactorings.
    - "Ratzinger describes the most sophisticated strategy for finding refactoring messages of which we are aware [12]: searching for the occurrence of 13 keywords, such as 'move' and 'rename,'" - this point in relation to CVS mining for refactoring related commits furthers my point in 2 in the previous section re: lack of formality in daily refactoring - the developers aren't even mentioning refactoring in their commit messages, its integrated into the lifecycle of the product.

- Rolf de Vries

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - "Developers do not necessarily consider that refactoring is confined to behavior preserving transformations" I wonder why that is, maybe there is still too much ambiguity as to when changing code is a refactoring, or people have different opinions of what behavior preserving means?
    - It is mentioned that the refactoring team developed custom refactoring support tools and processes. Yet, 51% of developers said they do 100% of the refactorings manually. I wonder if the tools/processes do not fit their needs, or they just don't want to use them. Either way, doing it all manually is likely to introduce some bugs, especially for the parts that can easily be automated.

  - How We Refactor, and How We Know It:
    - "Programmers often don't configure refactoring tools" until recently, I did not consider it as a possibility, so I assume this holds for other programmers too.
    - Given the reported numbers on how 'rarely' programmers use refactoring tools, it might be indicative that more effort should be put towards educating students/programmers on using refactoring tools (and not just learning about them)
    
- Andrzej Westfalewicz

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - In 2.2 the authors say “developers do most refactoring manually and they do not use refactoring tools despite their awareness of refactoring types supported by the tools”. I feel like this changed a bit since 2014 and more people become persuaded to use tools as they were tested by others.
    - In 4.14 the authors say “Refactoring was preferentially applied to the modules with high test coverage”. I fully agree, but we have to point out that sometimes we write tests before we refactor. I think that sometimes in these cases adding the tests should be considered as part of refactoring.
    
  - How We Refactor, and How We Know It 
    - In 3.8 the author brings up a survey saying that students rarely use refactoring tools. That got me thinking that we actually don't teach developers how to refactor in college. Student project aren't complex enough to show the value of refactoring and code quality is rarely a meaningful component of the grade.
- Nick Dekker
  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - Since Git sees moving and renaming methods as changes, it is hard to see how the actual behaviour has changed over time. Maybe a second git-like tool can show diffs on a different level to gain insight?
    - It is interesting how almost half the developers do not mention preservation of behaviour as part of refactoring.
    -Refactoring commit messages, I have just been switching to a refactor branch and making "regular" commits, describing what has been done. Releasing a new version with changelog notes or docs where necessary. Is there a best practice? Do we need refactor tags in our commits?
  - How We Refactor, and How We Know It 
    - Do developers know to use refactoring tools? Where / when are they advices to use tools like this and can they experiment in real world scenario.
- Haiyin Zhang
  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - Some developers said “cross-branch integration was the biggest problem” associated with refactoring. I agree with this point. So in practice, how can the developers in a team solve this problem?  
  - How We Refactor, and How We Know It 
    - In this paper, the authors study the different habits of using the refactoring tool between the ordinary programmers and the developers of refactoring tools. This reminds me of the bias we talk about in a former class. Indeed, when we develop a tool, we should evaluate the usability of the tool objectively instead of using our feeling as a user to evaluate.
- Niels Bauman
  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - Would these results also hold for other systems (i.e. non-OS applications or smaller applications/managed by a smaller company)?
    - They're probably missing a lot of data by only considering commits with the word 'refactor' in them (as per the other paper).
  - How We Refactor, and How We Know It 
    - I wonder how much has changed, I personally use refactor tools quite often (especially EXTRACT- and RENAME VARIABLE.
- Wessel van de Brug

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - The author mentions that developers do not directly think of refactoring as behavior preserving, and that program behavior includes readability, maintainability, and performance. I wonder if the surveyed developers were thinking of program behavior in the same sense. If so, the result doesn't seem surprising as the goal of refactoring often is to improve readability and maintainability. However, I would personally not categorize those as program behavior (which seems to infer program functionality instead of code quality).
    - I have experienced the difficulty of reviewing large code refactors myself. How have you dealt with such situations?
    - The author mentions the use of quality gate checks to ensure the layered architecture is kept in place. This reminded me of ArchUnit, which I would really like to try out soon.
  - How We Refactor, and How We Know It 
    - The extensive use of the RENAME refactor tool does not surprise me (modern IDEs make it very easy to use). I wonder how we could improve the usability of other tools like EXTRACT METHOD (which I personally barely use).
- DANYAO WANG

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - It is pretty interesting that the definition of refactoring in practice is broader than behavior-preserving program transformations. According to this paper's conclusion, refactoring does not preserve behaviors in all aspects; does this mean that we should expand the scope of academic research on software refactoring to meet actual application needs?
    - There is a significantly high percentage that developers do refactoring manually as opposed to using automated refactoring tools. However, many developers think there is no great need for better automated refactoring tools; instead, they prefer a validation tool that can help them evaluate their manual refactorings. Why is it like this? Why would developers like to do the refactoring manually?
  - How We Refactor, and How We Know It 
    - According to the paper, commit Messages don't predict refactoring. Why do developers not point out the refactoring in the commit message? Does this mean that refactoring is often less critical than feature change?
- Khalid El Haji

  - An Empirical Study of Refactoring Challenges and Benefits at Microsoft
    - Insightful remark by the authors regarding refactoring can only be measured with multiple dimensions. That is, refactoring does not impact just any single metric.
  - How We Refactor, and How We Know It 
    - I am glad to see a paper critically questioning the important assumptions made in the software refactoring field. Also, the concept of floss refactoring is quite interesting. Although from a scientific perspective we would like to separate the refactoring and other programming activities, programmers seem to not make such a distinction. Which implies that programmers often make “refactoring" which are not behavior conversing.

## Discussion
- Opinion on the papers
  - Developers do not like automated refactoring tools in the past, which may be because people do not trust tools at that time.
  - Some students think the sitution can be different now. They have some experience that using automated refactoring can make the code cleaner.

- Why do developers not use refactoring tools more?
  - Developers do not trust the tools. Doing it automatically is riskier than doing it manually.
  - The papers are in about ten years ago. Refactoring has been built into some IDEs now, so we do not need a separate tool.

- How about the refactoring features in IDEs?
  - We usually only use basic refactorings, such as extract variables and extract methods in common IDEs.
  - Changing the signature method is another useful method.
  - We don't use refactoring in IDEs quite often because it is hard to change habits as we already get used to writing code in a certain way. 
  - Sometimes people want to control the code by themselves, and some refactorings are easy to apply and understand so people just do it manually.
  - People don't use the refactorings tools in IDEs because they don't even know the features are available in the IDEs. The same situation happens to debuggers in IDEs. Developers mostly use basic stuff and don't know that the debugger can do some specific things.

- Refactoring often happens with other behaviors.
  - From the human perspective, nobody only refactors. Refactoring often happens in the middle of other behaviors, such as adding a feature.
  - This kind of mixing in changing and refactoring has also made it harder to study the effect of refactoring by itself.
  - The commit messages are not enough to identify refactorings. You also need to check the code.

- How to measure the value of refactoring
  - Take a look at the metrics. But one metric may go up while another goes down.
  - Some refactorings have a specific effect because they are made to realize it. Refactorings can have the opposite effect in some other cases.
  - See if the time it takes to solve issues decreases. It is challenging to conduct an actual experiment with two ideal worlds where one refactoring happens while in the other, it doesn't happen. It is possible to make use of the history of the team to compare the effect.
  - Looking at it from a high-level perspective, such as project popularity after refactoring.
  - Developers' opinion is soft evidence, but it's valuable and should be taken into consideration.

- One can get used to mess code and do not refactor it. How to overcome it?
  - It can happen when you have only one responsibility, developing the code. If you also need to maintain or present it somewhere, you would overcome this problem. So we should be a peron that has more than one responsibility.
  - We can implement a CI/CD pipeline to check it automatically.
  - Ask developers to write some explaination for the code and let a reviewer review it. If the reviewer cannot understand it, then the code needs refactoring.
  - Do not allow the code to deploy unless you fix it. Let a manager implement the rules.
  - Maurício implemented a tool called codesheriff, which can test the code. If the code does not follow the rules, such as its complexity is higher than 10, there would be a failing test.
  - In reality, programmers may have specific reasons for the destructive code. Linters can provide assistance in this situation. It can create exceptions in line.

- Something can be learned from these empirical papers
  - The preferential refactoring and survey method can be applied in projects.
  - We can learn from the structure of the paper.
