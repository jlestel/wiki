---
title: "Saying Goodbye to Agile"
source: "https://lewiscampbell.tech/blog/260414.html"
author:
published:
created: 2026-04-16
description: "Software's \"Agile moment\" has been and gone."
tags:
  - "clippings"
---
RIP Agile, we hardly knew ye.

And I mean that literally - because no one was ever clear on what it was.

Agile washed over our industry like a tsunami. But whenever it was questioned, a voice (perhaps emanating from a gap in the clouds?) would invariably tell us "ah, but that is not True Agile - The Manifesto sayeth naught of Daily Standups, nor Agile Coaches". Yet if one read the [Agile Manifesto (2001)](https://agilemanifesto.org/), this wellspring of our enlightened New Era of Software, one inevitably found it didn't actually tell us much at all. At best it was a sequence of vague platitudes ("Customer collaboration over contract negotiation"), and at worst it was commercially unworkable ("Welcome changing requirements, even late in development").

So if the Agile Industry was not doing Agile Properly, and the manifesto itself was near devoid of meaning, then what exactly was it?

## "A spectre is haunting Software, the spectre of Waterfall"

Agile was always defined primarily in terms of what it wasn't - and what it wasn't was Waterfall. If you were not doing Agile, you are doing Waterfall, and Waterfall Did Not Work.

Except we'd known Waterfall did not work since 1970; and [Winston W. Royce laid out exactly why](https://www.praxisframework.org/files/royce1970.pdf), recommending we instead:

- Start with a program design.
- Make a prototype of the software to gather information to refine requirements.
- Involve the customer ("the involvement should be formal, in depth, and continuing").

All of these things were later claimed as Agile innovations. In reality, they were written the year after the moon landing.[^1]

And even in that decade it was not the only work moving away from Waterfall. [A 1976 paper by Bell and Thayer](https://static.aminer.org/pdf/PDF/000/361/405/software_requirements_are_they_really_a_problem.pdf) - which first coined the term "Waterfall" [^2] - tells us at the end of an empirical study:

> The types of problems detected in requirements changed during the life of a software development project. The system developers often determined requirement deficiency only when they attempted to meet the requirements with a design.

So it's clear that iterative development was not new, and would continue to be further refined in the decades before Agile [^3]. Waterfall was not the state of the art ere The Manifesto liberated us. And no one serious doubted the effectiveness of requirements and specifications.

## Spec-Driven Development

[For good or for ill](https://lewiscampbell.tech/blog/260114.html), the availability of cheap LLMs trained on massive programming datasets has altered the way many of us program computers, and arguably shifted the zeitgeist of software.

One unambiguously positive development that's followed is that software professionals are writing specs again. LLMs - like many of us - do not perform well with ambiguity, and specifying problems is proving to be an effective tool for generating correct code. Agile told us "Working software over comprehensive documentation". Spec-Driven Development is telling us "Comprehensive documentation creates working software". And really, LLMs or no, there is nothing new under the sun. Quoth Royce:

> Until coding begins these three nouns (documentation, specification, design) denote a single thing. If the documentation is bad the design is bad. If the documentation does not yet exist there is as yet no design, only people thinking and talking about the design which if of some value, but not much.

Reading 1970 and 1976, one has to ask what 2001 really brings us. Agile was defined vaguely and marketed as solving something already solved half a century ago by serious engineers whose papers made more sense. As our field continues to change - and we hope evolve - it's time to look at things with a fresh perspective, and put Agile in the dustbin of history where it belongs.

---

  
Think I can help your company? [Get in touch](https://lewiscampbell.tech/contact.html) or [visit my consulting site!](https://outdata.net/)

[^1]: One wonders how the programmers of the Apollo Guidance Computer managed such a feat, programming as they were without Story Points, nor knowing that "Continuous attention to technical excellence and good design enhances agility".

[^2]: Used, of course, as an example of what not to do.

[^3]: I very much wanted to squeeze some references to [Freed Brook's "No Silver Bullet"](https://worrydream.com/refs/Brooks_1986_-_No_Silver_Bullet.pdf) here, but I try to keep these posts short. I also have Boehm's [Spiral Model](https://www.cse.msu.edu/~cse435/Homework/HW3/boehm.pdf) on my reading list.