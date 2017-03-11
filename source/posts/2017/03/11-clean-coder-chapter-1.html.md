---
title: Cleancoder chapter 1
date: 2017-03-11 03:40 UTC
tags: cleancoder, attitude, weekend posts
author: Vincent
---

**Personal note after reading The Cleancoder chapter 1. Thanks [Uncle Bob](https://sites.google.com/site/unclebobconsultingllc/) for this awesome book.**

If you are a developer, you have to read it. The perfect time to read is when you have two or three years experience in software/web/backend development.

## Professionalism

All of us want to be a professional software developer. What's professionalism?

You know, it's a lot easier to be a nonprofessional, and me I used to be a nonprofessional software developer. I don't tell now I'm a professional software developer, I'm trying to be a better software developer.

Non-professionals don't have to take responsibility for the job they do, sometimes they leave that to their employers or customers.
If a nonprofessional makes an error, they will fix in a beautiful day or simpler they ignore it and they hope QA or customer won't find it.
But when a professional makes a mistake, he cleans up the mess and tries to prevent it happen again in the future.

So, **professionalism is all taking responsibility.**

## How do we take responsibility?

The book show some principles:

- Do No Harm to Function
- Do No Harm to Structure
- Work Ethic
- Know Your Field
- Continuous Learning
- Practice
- Collaboration
- Mentoring
- Know Your Domain

### Do No Harm to Function

Software is too complex to create without bugs. We have to take responsibility for their implementation to get as close as possible to it.

The book teaches me when I release any feature, I should expect QA to find nothing. Yes, nothing. QA is not a bug catcher. This means I have to know my code works.
So, how do I know my code works? That's easy. Test it, test it again, test it up, test it down, test it seven ways to Sunday - Uncle Bob says

Haha, When I read this paragraph, I suddenly remember I told the same thing with my team and they said they don't have to time to test, many features and bugs are waiting for us.
It can be true, right? lol.

What Uncle Bob said?

- **Automate your tests** Write unit tests that you can execute on a moment's notice and run those tests as often as you can.

- **Every single line of your code should be tested - 100% test coverage.**

But isn't some code hard to test? Yes, in a lot of cases I didn't know how to test.

- The solution is to design your code to be easy to test. **And the best way to do that is to write your tests first, before you write the code to pass them.
Let's Test driven your design, your development.** This is a discipline known as **Test Driven Development (TDD)**

### Do No Harm to Structure

In a few projects I got a lot of troubles, you will ask me what kind of trouble? Huh, look the picture below:


![bug-everywhere](https://docs.google.com/uc?id=0B-S3PHiYZOY1czRkbzZVbUR0VDA)

Based on my experience, I know bugs come from the code, the application's structure. If your application structure and your code are messy, trust me, you will join the Bug Party 24/7.
In these cases, I want to refactor the code, apply the principles and patterns of software design that support structures are flexible and maintainable.

Uncle Bob showed me a trick that I should follow: **If you want your software to be flexible, you have to flex it**

- The only way to prove that your software is easy to change is to make easy changes to it. And when you find that the changes aren't as easy as you thought, you refine the design so that the next design change is easier.

- He introduced me a rule: **Always check in a module cleaner than when you checked it out. Always make some random act of kindness to the code whenever you see it.**

This action is dangerous. No! Uncle Bob said. **What is dangerous is allowing the software to remain static.**
If you aren't flexing it then when you do need a change it, you will find it rigid. And if you scare continuous changes then this mean you don't have tests. It's so TRUE.

100% test coverage will help you confident with any changes.

### Work Ethic

One thing that Uncle Bob said in this part that the thing I didn't know in my first three years experience. **Your career is your responsibility.**
Don't wait your company gives to you a favor, you should find a way to do them by yourself. If you wanna join a conference, you should buy a ticket, wanna read a book, go ahead.

Bob also let me know about professional developers always spend time caring for their profession.

- Plan on working 60 hours per week. 30 to 40 hours for your employer. The remaining 20/30 hours are for you. During this remaining 20/30 hours, you should be reading, practicing, learning, writing to enhance your career.
**20/30 hours is your and you should be doing those things that reinforce programming passion.**

### Know Your Field

Uncle Bob haves a minimal list of the things that every software professional should be conversant with:

- Design Patterns - You should able to describe, understand all 24 patterns in the GOF book and usually using favorite few patterns.
- Design Principles - You should know SOLID principles and have a good understanding of the component principles.
- Methods - You should understand XP, Scrum, Lean, Kanban, Agile ...
- Disciplines - You should practice TDD, Object Oriented Design, Structured Programming, Continous Integration and Pair Programming.
- Artifacts - You should know how to use: UML, DFDs, Structure Charts ...

### Continuous Learning

This part really pushes me up.

- Read books, articles, blogs, tweets. Go to conferences, meetups.
- **Learn things that are outside your comfort zone**. If you are Ruby developer, then learn Java/Elixir/Rust/C. Learn to train your brain.

### Practice

Profession practice. True professional work hard to keep their skills sharp and get ready.

To do that, you have to do daily practice. Solve Katas the good ways to train your fingers and your brain. Solve by multiple languages to maintain your ski Solve Katas the good ways to train your fingers and your brain. Solve by multiple languages to maintain your skill.

At least two katas in every day. From morning to warm up to evening before you sleep.

### Collaboration - Mentoring

Share your knowledge and problems with people - A lot of superman around you, you can learn a lot of from them.

Write blogs to teach people and get their feedback to improve your skill.

### Know Your Domain

Before start any project, let's take the time to research. Interview your customer and users about the foundation and basic of the domain. Spend time with the experts and try to understand
their principles and values.

## Conclusion

This chapter really opened my eyes - helps me know what should I do to become a professional software developer.
