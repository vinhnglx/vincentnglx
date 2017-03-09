---
title: Few notes about service oriented design
date: 2017-03-09 11:49 UTC
tags: architecture, design, rails, service oriented design - Part 1
author: Vincent
---

This is my note about Service Oriented Design after reading the book. Although the book is quite old,
but it helps me understand basic concepts about service oriented design and how to transform your web application to multiple services.

Before going to the detail, let's read what's service oriented design?

>   *Service oriented design is about creating systems that group functionality around logical function and business practices.
>   Services should be designed to be interoperable and reusable.
>   The goal of service oriented design is to split up the parts of an application or system into components that can be iterated on,
>   improved, and fixed without having to test and verify all the other components when an individual is updated.*

**One more thing, this is my personal opinion after I read few chapters in the book:**

I knew Ruby on Rails when I was an intern at a outsource company. After 3 years, based on
my experience and from some friends, I realized almost applications that built from Ruby on Rails framework had a big problem about performance.
More specifically, when the application got a lot of business logic with complex view, many if-else conditions in controllers/views, that was time
I feed very bad about performance of application. That was also the time I felt scare and didn't know how to solve that problem.

My friends advise against using Rails because they say it's not scalable. Basically, I don't think Rails framework is the main problem,
even when Rails core code looks quite terrible, for example:
[form_helper.rb](https://github.com/rails/rails/blob/master/actionview/lib/action_view/helpers/form_helper.rb) or Rails architecture is monolithic architecture.

The main problem comes from us, from the way we design application, the way we design database schema.

A services approach provides more tools and ability to deal with scaling. Data can be split across services and the performance
under load can be optimized for each service.

...Continue updating soon
