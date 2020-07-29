---
layout: post
title: Coding fermentation
---

{{ page.title }}
================

<p class="meta">28 Jul 2020 - Thiago</p>

## Code fermentation.

For all the metaphors for code I think this is not a very common one. But it's one I think that makes a lot of sense and I want to explain why.

So first, fermentation. The basic thing for fermentation is that you have something in the beginning, let it sit for a while, magic happens and later you have something else. Of course it's not magic that transform wheat flour and water into a nice sourdough bread starter, but without knowing about it it's pretty much magic. But this is just the nice part about it, the bad one is when instead of fermenting it just spoils. Knowing how to control that is key for having a nice product.

My point here with code is that it will ferment. As soon as it goes to production it's now subjected to all kinds of agents that will transform it into something else. Now it's a decisive point on how do you deal with that. Continuing with the bread analogy, you can have a sliced bread with a lot of things to stop it from spoiling or you understand how fermentation works and make a sourdough.

What I see is a lot is people trying to avoid they code to spoil by over engineering their solution, assuming that they know, and will always know exactly what is going to happen to that piece of code. But in reality, that's not true. If you work for a company that uses technology to solve a problem I can guarantee you that that code must change, because in the end, the code, the technology itself is just a means to solve a real problem, and real problems changes all the time.

That's why I prefer to go with the fermentation approach. I know that my code will change, I'm actually counting on that. And so, my way of making it controllable is lowering the amount of variables. It means making just what I know about that problem, very explicitly solving just what needed to be solved, this way we also have less corner cases because there is less things to solve for.

Like I said, I already know that I don't know that problem very well, so instead of trying to solve things that I suppose could happen I just don't. It's the fermentation part of the code, it's starts simple, and it will change over time. What i need to do is create tools to help me understand what is going on over time and avoid the code to spoil.

One of the tools I use to make it happen the most is TDD. It allows me to dissect a problem in small parts and only solve that. I will not have an if statement before having a test case to support that. The goal is not to have a code with tests that will guarantee that my code works all the time, the goal is to show the **only** things that code does.

This way, we try to turn bugs into feature requests, because there is a huge difference between having a code that was supposed to work and doesn't and a code that doesn't do everything you want. The first one I call regression bugs, the second one feature requests.

Because my code was done with TDD and all features are describe there, adding something new it's quite easy. Just add a test, see it breaking and fix it. This way the code is fermenting and not spoiling. Another good thing with that approach is the refactoring part.

Refactoring is what makes everything looks so nice in the end, that code that when you look months later you think: That was really nicely done, congrats past me! But it's only achievable if your code fermented. A good refactoring happens after you have enough information about your code and problem so you can shape it they way it makes more sense.
