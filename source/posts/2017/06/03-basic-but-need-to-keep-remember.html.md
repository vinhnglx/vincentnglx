---
title: "Few things quite simple but need to keep remember"
date: 2017-06-03 11:47 UTC
tags: programming
author: "Vincent"
---

Yo! I came back after 2 months. This post is my note after read a [news](https://blog.codeship.com/refactoring-and-design-patterns/) from CodeShip.

From wiki:

> Code refactoring is the process of restructuring existing computer code without changing its external behavior.

### Why Refactor Your Code

I still think, in the first 2 working years, refactoring is something that I will start to refactor after finish a project.
And of course, after finished the project, I forgot my promise - always.

Until a day, when I faced to senior developers from a different country, they came to Vietnam to work with my team.
I felt very bad, I can't work with them. I saw a big wall, I need to get out of comfortable zone to survive.

I started to re-learn everything about programming, up to now, I still learning .. haha ... Learning is never stop.

Alright! Back to the topic.

> Anyone can write code that computer can understand. And **only good programmer can write code that human can understand**

Refactoring will help the code more readable, performance improvements. Refactoring code doesn't change behavior or output.

In programming, there is a software development process called TDD: requirements are turned into very specific test cases, then
the software is improved to pass new tests, only. There are three phases in TDD:

- Add a test. Each new feature begins with writing a test. To write a test, the developer must clearly understand the feature's specfication and requirements.
After that, run the test to see the test fails. If you skip this step, you may end up with a dead code - missing requirement. This phase is **RED** phase.

- Write the code. Only write some code that causes the test to pass. This phase is **GREEN** phase.

- Tests are passed, the developer can be confident that the new code meets the test requirements and doesn't break or degrade any existing features.
Next, this is the step that you will apply learned knowledge of good code practices and make small adjustment without changing the codes behavior.
New code can be moved from where is was convenient for passing a test to where it more logically belongs. Duplication code must be removed.
This phase is **REFACTOR** phase.

- And the wheel continues to roll. Starting to another new test.

In general, code that doesn't get refactored as a system works by hopes. Pray to system work.

There are specific and general guidelines for refactoring and for creating clean code that all developers must to know.

So where that guidelines? How can I improve my code?

### Where?

Before start to learning anything either new language or new framework, let's start to learn a process of how to think through problems.
Don't only good for learning but none of the good coding practices.

There are design patterns that help decouple and remove most of the heavy query method usage, such as
Tell Don’t Ask, Eastward Oriented Code, and Monads.

*NOTE: I will write blog posts about three this concepts soon!*

Learning to apply patterns such as these will help relieve you of many of the headaches you experienced as a new programmer.

### Rails

By design, Rails has a way to organize data and behavior into specific areas to help maintanability and functionality.

The Rails's code may be implemented something like:

- Model: data store, organize data for presentation
- Controller: selecting data for presentation and rendering the view
- View: the layout with lots of conditional logic based on the user data

Here, Model and View are both doing more than they should - They are not following the SRP (Single Responsibility Principle).
The model should not be reponsible data for presentation and the view should not contain conditional logic for how it's rendered.

So, the new way should like:

- Model: data store
- Controller: selecting data and wrap in presenter and render view
- Presenter: organize model data for presentation (no HTML)
- Helper: Conditional view logic will be re-used.
- View: the layout with simple method calls directly on presenter objects and any helpers.


