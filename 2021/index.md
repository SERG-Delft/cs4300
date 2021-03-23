---
layout: tud
title: Seminar on Software Refactoring (CS4300)
---

Modern software systems never stop to grow; and they grow fast. To catch up with the speed of the highly dynamic and complex society we now live in, companies deliver new features to their software systems virtually every second of the day. After all, the faster a new feature gets to the market, the better. 

Technically speaking, this means that software developers are adding (and modifying) a high number of lines of source code every day. In a perfect world, these modifications are done in an effective manner, as the internal structure of the software system is designed with evolution in mind. 

A series of "bad decisions" might make software simply harder to maintain and evolve. As a consequence, our society has to spend more money to keep evolving the software systems we so much rely on. [The Consortium for Information and Software Quality](https://www.it-cisq.org/the-cost-of-poor-quality-software-in-the-us-a-2018-report/The-Cost-of-Poor-Quality-Software-in-the-US-2018-Report.pdf) estimates that, in 2018, the US has spent around US$ 2.84 trillions due to poor software quality, where around 18% (or US$510 billions) due to technical debt and 21% due to challenges in legacy systems. 

Software tends to rot over time. Lehman has indeed predicted that, without action, [software systems tend to increase in complexity and suffer from a quality decline](https://ieeexplore.ieee.org/abstract/document/1456074). Software refactoring techniques, or the act of improving the internal structure of the system in a way that future evolutions are easier and therefore less costly, are fundamental. Software refactoring does pay off; a [study at Microsoft](https://ieeexplore.ieee.org/abstract/document/6802406), for example, showed that developers perceived better maintainability, readability, and even reduced time to market in codebases that have gone through systematic refactoring. The same developers, however, also observed that refactoring might involve substantial costs and risks.

## Lecturer

<img src="{{ "/img/mauricio.jpg" | relative_url }}" width="100px">
[Dr. Maurício Aniche](https://www.mauricioaniche.com). Contact him via e-mail.

## Learning objectives

This course covers the practical, theoretical, and research aspects of software refactoring. After this course, students will:

* Be able to judge the need for refactoring at implementation, design, and architectural levels.
* Be able to evaluate the costs, benefits, and drawbacks of the current state of the software system as well as its possible refactored version.
* Be familiar with state-of-the-art research in empirical software engineering as well as automated refactoring.
* Be able to perform scientific studies in the area of software refactoring.

## Structure of the course

This is a seminar course, which means most of the course is about reading the existing lecture. As you see in the schedule,
each lecture has a different topic. The study flow is:

* You read the required chapters or papers before the lecture. I suggest you to have the paper in a tablet or in a printed version, so that you can make notes while reading it!
* You take notes about anything you want to discuss, questions you may have, things you agree or disagree with the author. Each student is responsible for proposing at least one discussion point per chapter, which should be posted in our Mattermost thread. 
* In the lecture slot, we discuss the two readings. 45 minutes for each.
* A randomly chosen student takes notes of the main points that emerge out of our discussion and submits a PR to this website.

This is a 5 ECTS course, so we expect around 14 hours of dedication a week:

* 4 hours reading the required chapters and papers
* 4 hours in the lectures discussing the readings with all the students
* 6 hours working on the project of the course

## Course project

In groups of 3-4, students work on a research project with the focus of getting a deeper understanding on a software refactoring problem and/or technique. Topics that can be explored are the same as our related literature:

* Empirical studies on the challenges, costs, and benefits of software refactoring.
* Automated detection of refactoring opportunities.
* Automated detection of context-aware code smells.
* Automated software refactoring techniques.
* In-depth case studies on large-scale software refactoring.

To that aim, students might make use of (i) mining software repositories techniques, (ii) artificial intelligence and/or machine learning, (iii) program analysis and AST parsing, (iv) qualitative research and/or controlled experiment methods, and (iv) any other method as long as agreed with the lecturer.

At the end of the quarter, students have to deliver (i) all the tools they developed, (ii) all the data they collect, (iii) a 6-10 pages double-column paper report, (iv) a 15-minutes video that summarises the project, (v) a group weekly diary that reports how each student spent their hours. Finally, students will present their work in a "conference style" afternoon.

Do you need help with coming up with a project? Look at our (private) "project ideas" page in Brightspace, or talk to me.


## Schedule



| Week | Date     | Topic                                              |
| 4.1  | 21/April | <a href="{{ '2021/intro' | relative_url }}">Introduction to CS4300: what do we know about refactoring?</a>              | 
|      | 22/April | <a href="{{ '2021/refactoring-at-scale' | relative_url }}">Refactoring at Scale, by Maude Lemaire</a> | 
| 4.2  | 28/April | <a href="{{ '2021/building-maintainable-software' | relative_url }}">Building maintainable software, by Joost Visser et al</a> |
|      | 29/April | <a href="{{ '2021/refactoring-to-patterns' | relative_url }}">Refactoring to Patterns, by Joshua Kerievsky</a>               | 
| 4.3  | 6/May    | <a href="{{ '2021/refactoring-workbook' | relative_url }}">Refactoring workbook, by William Wake</a>                                      | 
| 4.4  | 12/May   | <a href="{{ '2021/working-effectively-with-legacy-code' | relative_url }}">Working Effectively with Legacy Code, by Michael Feathers</a> | 
| 4.5  | 19/May   | <a href="{{ '2021/empirical-studies-1' | relative_url }}">Empirical studies - I</a> | 
|      | 20/May   | <a href="{{ '2021/empirical-studies-2' | relative_url }}">Empirical studies - II</a> |  
| 4.6  | 26/May   | <a href="{{ '2021/code-smells' | relative_url }}">Code smells</a> | 
|      | 27/May   | <a href="{{ '2021/green-refactoring' | relative_url }}">Green refactoring</a> | 
| 4.7  | 2/June   | <a href="{{ '2021/mining-refactorings' | relative_url }}">Mining refactorings</a> | 
|      | 3/June   | <a href="{{ '2021/search-based-software-refactoring' | relative_url }}">Search-based software refactoring</a> | 
| 4.8  | 9/June   | <a href="{{ '2021/refactoring-recommendations' | relative_url }}">Refactoring recommendation</a> | 
|      | 10/June  | <a href="{{ '2021/diomidis-and-marc' | relative_url }}">Guest lecture: Diomidis Spinellis and Marc Philipp</a> | 
| 4.9  | 14/June  | <a href="{{ '2021/felienne-and-hyrum' | relative_url }}">Guest lecture: Felienne Hermans and Hyrum Wright</a> | 
| 4.10 | 24/June  | Project deadline and final presentations | 

## Grading

The final grade is composed of: research project (90%) + research presentation (10%).

* The research project is the report that describes the research project conducted throughout the course.
* In the research presentation, students will present their findings to the other groups.

_Note that we dropped the seminar presentations due to the number of students._

Notes: 

* No written exam.
* The student is required to have a grade >= 5 in all the components to pass.
* We do not offer resits.
* Grades can not be carried out to the next edition of the course.


## FAQ

* _**How do I access the books and the papers?**_
As a TU Delft student, you have full access to O'Reilly library. Just search for the book using our [library website](https://www.tudelft.nl/en/library/) and you will see the "Read the e-book" option. You can also find the papers using Google Scholar. If there is no open version available, you have access to IEEE, ACM, and other libraries via TU Delft VPN. Or [install the browser plugin that our library provides](https://www.tudelft.nl/en/library/using-the-library/facilities-study-places/off-campus-access/access-anywhere-with-library-access).

* _**Are the reading compulsory?**_
Yes. This is a seminar course. If you have any issue that would prevent you from reading the chapters, please e-mail me.

* _**I failed the project. Can I re-do it?**_
No resits.

* _**I missed the deadline for the final deliverable. What can I do?**_
Deadline is strict and delivering late is not allowed. Personal issues should go through the student advisor.

* _**How are the lectures going to happen?**_ Via Zoom. The link will be shared.

* _**How did you do this website?**_
This website is done with Jekyll and some straightforward HTML. The main picture was taken by [Helloquence](https://unsplash.com/photos/5fNmWej4tAA).

* _**Can I use your material?**_
![Attribution-NonCommercial-ShareAlike CC BY-NC-SA](https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png) This website as well as all the content created by me are licensed through Attribution-NonCommercial-ShareAlike CC BY-NC-SA. This license lets others remix, tweak, and build upon your work non-commercially, as long as they credit you and license their new creations under the identical terms.
The content from others that I link are subject the own authors' licenses.



