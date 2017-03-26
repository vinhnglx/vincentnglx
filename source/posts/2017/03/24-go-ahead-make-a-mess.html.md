---
title: Go ahead - Make a mess
date: 2017-03-24 11:39 UTC
tags: Object-oriented design, architecture
author: Vincent
---

This title belongs Sandi Metz. She spoke at a Ruby Conference 5 years ago - Source: [https://www.youtube.com/watch?v=f5I1iyso29U](https://www.youtube.com/watch?v=f5I1iyso29U)

I am learning object oriented design - I watched this video two days ago and I have few notes about what I learned:

### Mess

The coupling and the mess are because of **Knowledge**. In general, knowledge means objects and dependencies around.
And an object always knows thing about them self and they also know thing about the others. There are many ways to solve problems by arranging dependencies.
You have to understand Stability to control dependencies in the right way.

### Stability

Stability is relative and things that we unstable in some circumstances, but from some point of view might be stable from the others.
In programming, stability is when you apply Object Oriented Design to solve confusing about objects.

### Object Oriented Design

OOD knows how to separate stable and unstable; choose how to depend on the first and hide the second. It gives you a way to manage the mess,
so you can write app satisfaction fun and forever. It changes everything. OOD lets you stop worrying and learn to love the mess.

> *The concrete code is easy to understand, costly to change; The abstract code is hard to change when first time looks at it, but it must cheaper to change;
> the principle of OOD move your code to more abstraction, it benefits outweigh the cost.*
> -- **Sandi Metz**

### Omega-Mess

For example: we have a method with many lines inside - it's a big ugly complicated code.

If nothing inside this method can change or force on change out in the app or nothing out in the app can change or force to change inside this method then this method
is special kind of mess - Sandi Metz gave it a name: Omega Mess

To recap, Omega-Mess have no dependencies and no dependent. And Omega-Mess are hidden behind the message.

### Knowledge Plot

This is a plot that your code need to change.

![Knowledge plot](https://docs.google.com/uc?id=0B-S3PHiYZOY1V3I5SXVhbHRjNzQ)

- On the horizontal access, we have Stability. The Stable thing on the left, Unstable thing on the right.
- On the vertical axis is about what the object know. Whether the information that object have within purpose or outside of purpose.

Knowing which quadrant a bit of knowledge falls into telling you how to behave.

- The top-left quadrant: **Stable** thing within your permit are part of **Public API**.
- The **Unstable** thing within your purpose are **Private Behavior** and they should be hidden behind a **Public API**.
- Anything below the line is **Dependencies**.
- You should **EXPOSE** the **Public API**.
- You should **HIDE** the **Private Behavior** behind that.
- **Stable Dependencies** that are outside of your purpose, you have to have in order to collaborate with other objects but you should **MINIMIZE** them.
- **Unstable Dependencies** that don't belong to then you should be **MOVE**.

### Conclusion

From the video, I understood the basic concepts about OOD and the plot help me know what should I do with the messy code.
