---
title: "Adventures in Pair Programming with Gemini"
layout: single
excerpt: "AI is awesome; AI is aweful; whatever your personal feelings, AI is _here_."
share: true
categories:
  - Blog
tags:
  - AI
  - Gemini
  - Programming
header:
  overlay_image: https://i0.wp.com/techwiseacademy.com/wp-content/uploads/2016/12/code-1839406_1920.jpg?resize=845%2C321&ssl=1
published: true
---

When upper management decreed _"Thou Shalt Utilize AI in All Things"_ last year, I struggled to find
a spot for it in my workflow. I knew AI had its uses, I just didn't know how it could be helpful to
**_me_** in my role as a Senior Data Analyst who dabbles in automation scripts.

## In the Beginning, there was Darkness

Most of my experience with AI up to that point was cleaning up its messes when a _non_-programmer
tried to use it to create a Google Apps Script to do a thing without really understanding what they
were asking Gemini to do (and so Gemini would do it poorly). I would then have to figure out the
(frequently halucinated) code it produced and attempt to re-write it to _actually_ accomplish the
task; my main thought was "this is cool and all, but it's just not _reliable_".

Then I ran into the following scenario:

- I had a massive text file with over a million words in it to analyze;
- I wanted to use NotebookLM to help me with discovery, but NLM can only handle 500k words in a
  given source
- I needed to break the text file into "chapters", then import each chapter as a separate
  source-file
- I did _not_ want to do this by hand
- I'm pretty good with Regular Expressions...

Enter Gemini: with a fairly simple yet specific prompt, I handed Gemini a regex to identify the
"Chapter" headers and asked it to create a PowerShell script that would:

1. Stream in a master text file;
1. Use the provided regex to identify chapter headings;
1. Create a _new_ file using the chapter heading as the file name;
1. Stream all content until the _next_ chapter heading into the new file;
1. Continue doing steps 1-4 until the end of the master file.

## And then there was Light

It worked flawlessly; no manual tweaks necessary, no notes - it _just worked._ I ran the generated
script and it created 26 "Chapter" files that I was then able to import into NotebookLM and get to
doing my _actual_ job; the whole thing, from regex to prompt to functional output, was maybe 15
minutes.

I finally understood that all the bs issues I'd been dealing with for the past several months boiled
down to the specificity of the _prompts_, not the capabilities of the LLM. With this Eureka moment
fresh in my mind, I turned to my responsibilities as a Data Analyst with fervor: I began running my
SQL queries through a custom Gem I wrote to concentrate on optimization, bringing my average runtime
from ~7 minutes down under 4. One particularly heavy query of mine dropped from 25 minutes to just
under 13 - a **48% reduction** in runtime.

## There's no Zealot like a Convert

I was hooked. I started working on an app that I'd all but abandoned back in 2022 and took to it
with gusto. I was in the zone, producing working code at a velocity that was hitherto _unfathomable_
for me. I went from concept to production in a week, after a 2 & 1/2 year hiatus; and I was learning
so **much**! It was amazing...

And then I thought to myself "what if I want to expand this app beyond its current borders? I should
refactor my code to a plugin-based system!", so I asked Gemini how best I could accomplish that, and
it suggested I port my existing project to an [Nx](https://nx.dev/) workspace...

Now, up until this point I was working with Angular v20 for the frontend and Firebase Cloud
Functions for the backend, a set up with which I, while rusty, was already familiar. I didn't know
all the fancy new tricks and best practices, but I new what I was looking for when reading the
generated code and could write prompts that were specific enough to get what I wanted to do done
with minimal tweaking.

## Enter 'Hell Week' - Stage Left

Nx, on the other hand, was a whole new beast - I read a few of the docs and concluded that it
sounded like that for which I was looking, but I didn't _understand_ it in the way I understood the
Angular/Typescript code with which I was already working. So I let my Gem take the wheel.

I began moving things around as Gemini suggested; I ran the scripts and commands it produced; I
turned into a Copypasta Gremlin, an unwitting accomplice in a grand scheme Gemini had concocted, and
I knew not what it had wrought.

It took me as long to re-arrange my code as it took me to write it.

Finally, after six days of work, `npx nx run-many -t lint test build` ran Green across the board. "I
can finally _rest_", I thought to myself, as I submitted the PR, "I can finally breathe!" Then the
[Codecov](https://about.codecov.io/) workflow triggered; 3.65% coverage for my apps, 7.55% for my
shared libraries.

"What?!?" I knew my test coverage was low for the backend, but I had something like 97% coverage for
the frontend before I started this refactoring mess, what the hell am I missing?? I started looking
around and while my Angular tests appear to be there, they are NOT getting picked up by Codecov OR
my testing rig; they're all getting skipped for some reason.

That started me looking at my refactored code, itself - everything that stayed put in the frontend
project folder looked good and functioned as expected, but the backend and shared libraries had
turned into a **frightful** mess: missing code blocks, missing configuration, weird additions to my
interfaces, NONE of which I'd noticed in the frenzy to just be _done_ with it. I'd fallen victim to
my own success - I thought that my Gem could be trusted to do the heavy lifting on the refactor and
I could just go back to coding in the new workspace.

## The Real Treasure was the Friends We Made Along the Way

I was wrong. My Gem may _behave_ like a Senior Developer; it may provide useful little details about
what it generates to help me understand its "reasoning", but Gemini, and other LLMs like it, are
still just tools: if you know how to use them you can do some amazing things; if you use them
_without_ knowing what you're doing, you're liable to smash your thumb more than once. We are no
where near a point where someone can say "Build me an X" without having a **detailed understanding**
of how to create an X themselves.

I'm keeping the refactor - it was a good idea, anyway - but I'm not making the same mistake again;
Gemini isn't the kindly old Senior Developer taking me under its wing and coaching me along my
journey; its a Junior Dev, fresh from college without an ounce of real world experience, eager to
show off its (admittedly marvelous) talents without realizing its just making more work for
everybody else.

Time to learn how Nx works, I suppose...
