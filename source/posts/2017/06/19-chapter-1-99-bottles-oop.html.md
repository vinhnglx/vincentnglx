---
title: Chapter 1 - 99 bottles of OOP
date: 2017-06-19 08:33 UTC
tags: ruby, oop
author: "Vincent"
---

## Chapter 1: Rediscover Simplicity

In the chapter 1, the author has introduced four ways to solve a problem named [99 bottles](https://en.wikipedia.org/wiki/99_Bottles_of_Beer).
Basically, the problem is not difficult but it has many cases - these four ways that author shared are common ways to solve this problem.

Below are my notes after finished chapter 1.

- All we knows: most code will someday change, therefor where you optimized code for understandability, you now focus on its changeability. Your code is less
concrete but more abstract - you've made it initially harder to understand in hopes that it will ultimately be easier to maintain. This is the basic promise of
OOD. **Design decisions inevitably involve trade-offs. There's always a cost.**

For example, almost we know about principles to refactor the code such as DRY or Single Responsibility. DRY and Single Responsibility are great ideas, but that
doesn't mean it's free. Extract methods to many small methods to make sure single repsonsible for each method, or extract the duplication into a single
common method then invoke this method in place of the old code, the price you pay for these ways is that the invoker of new method no longer knows the result,
only the message it should send.

- Each of these design choices has costs, and it only makes sense to pay these costs if you also accure some offsetting benefits. So **picking the right
abstractions is an important thing need to remember when design**.

- There are two goals that the code should meet often: **Concrete enough** to be understood while simutaneously being **abstract enough** to allow for change.

- The difference between Message and Method:

  - A "method" is defined on an object and contains behavior. Methods are defined.
  - A "message" is sent by an object to invoke behavior. Messages are sent.

- For example


        def call(user_auth_token)
          uri = URI('https://graph.facebook.com/debug_token')
          params = { input_token: user_auth_token, access_token: @access_token }
          uri.query = URI.encode_www_form(params)
          res = Net::HTTP.get_response(uri)
          if res.body
            hash_data = JSON.parse(res.body)
            if !(hash_data["data"].nil? || hash_data["data"]["is_valid"].nil?)
              return hash_data["data"]["is_valid"]
            end
          end
          return false
        end

The example above proves one thing: combining many ideas into a small section of codes make it difficult to isolate and name any single concept.
This example named `call`, uses a facebook authentication token, verify it before get facebook user information. You see, three missions in a method named `call`

Hence, code clarity is built upon names. Writing code is like writing a book, your efforts are for other readers.

- **The author gives to us three questions to figure about value and cost before judge a code.**


1. How difficult was it to write?

2. How hard is it to understand?

3. How expensive will it be to change?


The first question is a memory, the last question is imaginary but the second question is true right now, always applies.

- In chapter 1, the author also talked about naming method. I used to refactor code by extract large methods to many small methods, and I always got the trouble
when set new names for methods. The trouble will occur when I change the code to fit with new requirement - I can never change the internal implementation without
ruining the method name.

Therefor, the author said:  **You should name methods NOT after what they do, but after what they mean**. You should name methods after the concept they represent.

That's all about chapter 1.

