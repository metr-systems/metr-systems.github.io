---
layout: post
title: Getting away from code comments
---

{{ page.title }}
================

<p class="meta">21 Jul 2020 - Berlin</p>

# Getting away from code comments

## Code comments: A topic that people love to hate.

I'm on the side that doesn't like them. Being a Python developer who codes based on The Zen of Python and I specially like the `Readability counts.` part, having comments in the code feels like a trap, a way to disguise bad code readability.

But at the same time it can really be helpful. At metr we have our own library to deal with a protocol called OMS. This library is our way to abstract most of the really low level stuff and make the life of our developers easier. There we have many functions with code comments pointing to the specific part of the documentation that explain why that array of bytes is the manufacturer of a device. Even tough our code is explicit enough for the person who reads that, if something goes wrong it's always good to know where did those things came from.

Those are the moments that I think code comments really helps. They can explain for the next developer why something really weird had to be done that way and since we know that most of our time as developers is spent reading code, some help is always good. But here is the point where is really hard to draw a line. What should've been better code readability and what is impossible to express without a real English sentence?

Another common problem with code comments is that they lack context and can easily get lost in time. For me, just having a comment that explain why something weird works is not enough. I want to understand **why** it was done that way in the first place, if I want to refactor that code having no context can be a big problem. And after my refactoring if I forget to change the comment then you just have some extra things to read that doesn't' help at all.

To overcome those problems we use another strategy that's not code comments. We use GIT. Usually we are already very strict about how to commit on GIT, we believe that our commits should tell the story about how that application was built and to do that we use the description of git commits very often.

So instead of having a code comment somewhere in the code we have a commit with that specific change very well explained in the description, very often with links to documentations or anything that would help the person to understand why that piece of code is weird. But more than just that. The person reviewing that code have the entire context to understand what happened. They can check the commits around that, what was the branch name and even what was the GitHub issue related to it.

But to make things more interesting we use some tool to give us this things easier. Our developers at metr usually use vscode and emacs and both of them have extension that allow you show the changes inline. This means that, in vscode for example, you just need to hover your mouse over one line and you have there a detailed explanations about the code you are seeing.

I cannot remember how many time this have helped us when going back to code months or years old and be able to just understand what happened and be able to move forward easily.
