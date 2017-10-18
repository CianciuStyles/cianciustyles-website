---
title: Notes From Uncle Bob's Clean Code Videos
date: 2017-10-16 18:47:52
tags:
    - Clean Code
    - Uncle Bob
    - My Notes
---

Over the last few weeks, I have had the opportunity to dedicate a couple of hours of my Mondays to watch the ["Clean Code" video series][1] by [Robert C. Martin][2] (more informally known as Uncle Bob). In the past, I have tried to read the [book][3] from which these videos are produced, but I always ended up not finishing it due to the usual excuses, like lack of time, procrastination, etc. Having a weekly meeting organised at my workplace to watch the videos together and have a discussion about them with my colleagues afterwards has been a vastly superior plan to my own, and indeed this made me stick to watch all the available videos.

During the sessions I have jotted down some notes on the topics I thought were more relevant and applicable to my day-to-day job, and I am going to report them in the remainder of this post:

### Clean Code ###

* The messier the code, the more time it will take to add features later in the project's codebase.
* It's not that programmers aren't working hard, they are; but the code is slowing them down.
* Adding more people at the end of the lifecycle of a project is **not** going to make things go faster; quite the opposite.
* The big redesign is **not** going to work either; it will start a turtle-and-hare race between the old and the new systems.
* A *rigid* system is a system which resists changes, in a way that makes changes very difficult to accomplish and makes estimates not accurate.
* A *fragile* system is a system that starts to malfunction in different ways as soon as some part of the code changes.
* An *inseparable* system is a system for which reading the code is not going to help in understanding the original author's ideas and purposes.

### Names++ ###

* Every time you name something, the name should reveal your intentions. If you need to write a comment after the name, the name is not good enough.
* If you have to go look in the code to understand a name, the name has failed its purpose.
* To disinform means to have a name that gives the reader a different intention than the author's.
* There's no need anymore for prefixes for types (the [Hungarian notation][4]), the IDE and compilers are smart enough to take this for you.
* Boolean variables should be named as predicates, e.g. *isEmpty*.
* Method names should be verbs, as they express actions (except the methods that return boolean values).
* The longer the scope of a variable, the longer its name should be (if the scope is short, the variable name is used very near to the declaration, and hence it's easy to look for what it stands for).
* Methods which are called from many places should have nice and short names; private methods which are called in very few places and with a small scope should have long and detailed names.

### Functions ###

* Functions are the first tier of code containers.
* A functions should do one thing, do it well, and do it only.
* Today's computers and compilers are so good at their jobs that it's no longer needed to worry too much about efficiency, so we should focus on readability first.
* Long functions are where classes go to hide.
* If a function operates on multiple levels of abstraction, it's doing more than one thing.
* You can make your function do one thing only by extracting functions from it until you can't.

### Function structure ###

* We should treat each argument as a liability, not as an asset.
* Usually we should strive for 0 to 2 arguments; with 3 it already becomes a problem to remember the order.
* Most times we pass a boolean argument to a function, we are declaring that the function is actually doing two things: one for the true case, and one for the false case.
* If a function expects a null value, it's like the boolean case: we expect to behave in a different way when the object is null, and in another way when the object is not null. Write two functions instead.
* The [*stepdown rule*][5] says that public, more general methods should go at the top of the class, while private, most detailed methods functions should go at the bottom. This creates a new level of abstraction each time we scroll down the code.
* Interfaces allow to invert the source code dependency between two modules A and B, so they are not required to be deployed together anymore.
* When we have a plug-in structure, it allows the dev team to work independently on different parts of the code. Switch statements and long chains of if-else statements break these premises.
* [*Functional programming*][6] is the programming style which does not allow assignments and side effects. This makes functions "pure" mathematical functions, so that the same inputs will always result in the same output.
* *Temporal coupling* is when the order of function calls matter.
* *Queries* (e.g., getters) should not change the state of an object and just return a value; *commands* should always return void, possibly throwing exceptions for error cases.
* Individual functions should have a limited knowledge of the overall system.
* [*Structured programming*][7] says that a program should composed from three basic blocks: **sequence**, **selection** and **iteration**.
* Error handling is important, but if it obscures the logic, it's wrong.
* Always use unchecked exceptions (i.e., make your exceptions derive from RuntimeException).
* Most of the work should be done by the name, the context and the scope of the exception thrown, so that no message should be needed.
* Functions should do one thing, and error handling is one thing.

### Form ###

* Comments should be rare, and supposed to take our whole attention, and readers should be glad it's there.
* It should be a prerogative of a developer to write code that expresses itself. In this light, comments can be seen as failures.
* Over time, comments degenerate into lies because usually the code changes but the comment does not.
* Worthwhile comment are:
    - legal comments
    - informative comments (e.g., the format a regular expression is trying to match)
    - TODO comments
    - public API comments
    - expression of intent comments
* Bad comments include:
    - mumbling
    - redundant explanations
    - mandated redundancy
    - journal comments
    - big banner comments
    - closing brace comments
    - attribution comments
    - HTML in comments
    - non-local comments
* Formatting is about communicating, and communicating should be the first concern to programmers.
* Things related to each other should be vertically close to each other. Vertical distance is a measure of how related two things are.
* Use the IDE reformat feature on little snippets, not on the whole file, otherwise merges would become a nightmare.
* Polymorphism is the key to independent deployability and plug-in architectures.
* Data structures have public variables and (virtually) no methods, while classes have private variables and public methods.
* Data structures and switch statements are as related as classes and polymorphism are.
* Classes protect us from new types, but suffer from new methods; data structures protect us from new methods, but suffer from new types.
* A row in the database is mapped to a data structure, not a class. This is called the [*impedence mismatch*][8].
* The rule of boundaries states that, when identifying a boundary, the information should go away from the concrete and toward the abstract.

### Test-Driven Development ###

* A test suite with good coverage eliminates the fear of change.
* Tests let you clean your code.
* The three laws of [Test-Driven Development][9] are:
    - you should write no production code unless you have a failing test first
    - you should stop writing tests as soon as you have a failing one
    - you should write only the code that makes the failing test pass
* Writing tests before the production code makes the production code testable (or decoupled).
* Creative work requires iterations and rework.
* The tests test the production code, and the production code tests the tests.

### Advanced Test-Driven Development ###

* [Refactoring][10] is something you do continuously; you never ignore it, you never let it slide, you also don't put it on a schedule or a plan.
* To prepare a working environment to work in, focus on writing an empty test and make it pass.
* Ideally you should write all the degenerate tests first; if that's not possible, make sure you write the next degenerate test as soon as possible.
* Every unit test should have only one assertion in it (*Single Assert rule*).
* According to the *Triple A rule*, every unit test should be divided into three sections:
    - arrangements
    - act
    - assert
* A single assertion is meant to be a single logical assertion, not a single "physical" call to the assert method.
* As the tests get more specific, the code becomes more general.
* Tests cannot fully constrain a program; they can add constraints but they can't specify the final behaviour. Tests can prove a program wrong, they can never prove it right.

### Architecture ###

* Architecture is the set of decisions that serve as the foundation for a software.
* A good architecture "screams" intention.
* A good architecture allows you to postpone decisions about DBs, frameworks, etc.
* A use-case is the formal description of how a user interacts with a system in order to achieve his/her goal.

### The Transformation Priority Premise

* Transformation is a change in code where the structure does not change, but the behaviour does.
* The usual "Red-Green-Refactor" cycle might then change into "Red-Transform to Green-Refactor".
* Usually transformations make the code more general.
* Duplicate the code is always specific, never general.
* Applying the transformations in the priority order helps to come up with better algorithms.

[1]: https://cleancoders.com/videos/clean-code
[2]: https://twitter.com/unclebobmartin
[3]: https://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/
[4]: https://en.wikipedia.org/wiki/Hungarian_notation
[5]: http://tidyjava.com/stepdown-rule/
[6]: https://en.wikipedia.org/wiki/Functional_programming
[7]: https://en.wikipedia.org/wiki/Structured_programming
[8]: https://en.wikipedia.org/wiki/Object-relational_impedance_mismatch
[9]: https://en.wikipedia.org/wiki/Test-driven_development
[10]: https://en.wikipedia.org/wiki/Code_refactoring