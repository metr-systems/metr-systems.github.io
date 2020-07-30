---
layout: post
title: Use cases as code
---

# {{ page.title }}

<p class="meta">30 Jul 2020 - Thiago</p>

## Use cases as code.

At metr we have a few solutions for building management, like submetering and heating systems monitoring and more to come, and at the core of all that is our m-gate. The m-gate is what we call a multi purpose gateway and it’s called that because the same gateway can provide data for all those solutions.

Part of our solution is that we integrate with the existing infrastructure in the building when possible. For that, we rely on a well adopted protocol called OMS to gather the data from different sensors throughout the building. But those sensors are very different between them. Monitoring sensors don't send the same kind of data as the ones used for submetering, they use just the same protocol to transfer the data.

So we have a few new tech problems to solve. First, how can we deal with different sensor data coming from different sensors and going out to the correct places? Second, how can we have software that will support new solutions that will come and we have no idea how they are going to look like?

Like I said before, at metr we have what I’ve called “Code fermentation”. This means that our software is born doing just what we know it needs to and evolves with the new discoveries. That was the key to end up with the architecture we have today. It started really simple, solving just one use case and only after we had the next problem to solve we started thinking about how we could integrate it..

The key to do that is making code that is extensible. It doesn’t try to solve all your problems, but gives you the base to build upon. Also, it can give you hooks, where you can plug in and change what you need. Here we were inspired a lot by how Django Class Based Views works. They do most of the work for you if you just want a simple CRUD, but they are really easy to extend and almost never you would have to do something entirely from scratch.

So, how did we do it? After understanding the problem better, by working on it and having some ugly and repeated code around we figured out which parts of the code change and which don’t. The format of the messages coming in doesn't change, it is always the same because it follows the OMS protocol. But the data we care about (and want to store) changes a lot for each use case. Then we created what we called Channels.

Basically, all the messages come in, then they go through some channels. Each of our m-gates has different channels configured and they can be remotely activated or deactivated. It made our lives so, so much easier! Because, even though we have just one software, it’s easily extendable for our needs.

Also, because each channel is “attached” to a use case, a real world problem that it needs to solve, it’s way easier to think about each one of them separately. We don’t need to come up with a magic generic solution that will kinda work for all the cases. They are strictly separated and can solve their own problems the way that is specific to it and only it.

Here is a nice example of how they really are different: we have channels sending data to different endpoints depending on the use case. At this point someone could think about having this together, after all you are sending a json to a backend. But since we don’t care about aggregating things together here, we have a channel that just writes things to a log to help debugging for example. It’s not just some logs, the channel completely manipulates the messages it receives and prints what we need and it doesn’t interfere with anything else.

It creates the nice feeling of coming back to that code, months later to implement something new and finding out that it’s so easy. There isn’t any need to remember back everything it does or how one thing can break the other. Don’t get me wrong, we do TDD 100% of the time and I’m pretty sure the tests would tell you if something broke. The point is to not even need to think about a solution.

This is one of our nicest examples of fermentation, the code didn’t start this way. It grew to it, using TDD and patience. Understanding the real problem behind the software we are building and then making it possible to change it accordingly to the real needs. This way we avoid a very common mistake in software development: basing the solution on assumptions that were made before the problem could be properly understood, which often turns into code that needs to be completely rewritten to adapt to new requirements.
