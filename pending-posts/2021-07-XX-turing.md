---
layout: post
title: "The science behind 'Magic: The Gathering'"
date: 2021-07-08
image: /thumbs/XXX.jpg
---
**Magic: The Gathering** (**MTG**) is a funny trading card game inspired by fantasy role-playing games. MTG emulates a combat between players' creatures, where not only their strength matters but also their abilities. Everything revolves around magic, which is present in the form of enchantments, artifacts, sorceries and many other exciting spells. There is a huge variety of creatures (and other spells) with which to compose your deck, roughly organized in five colors:

* **white** for angels, clerics and spells that evoke life;
* **black** for demons, vampires and other deadly spells;
* **red** for goblins, dragons, fire and explosions;
* **green** for elves and wild forest creatures;
* and **blue** for aquatic monsters and psychic spells.

**Uncolored** and **multi-colored** cards also exist. And cats, [many kinds of cats](https://hobbylark.com/card-games/best-cat-cards-mtg). The catalog is really huge, continually expanding since 1993 and can be consulted on [*Gatherer*](https://gatherer.wizards.com/Pages/Default.aspx), the MTG card database.

MTG, however, has a steep learning curve that makes it hard to understand at first. The complexity of its rules may be discouraging  (each card has its own instructions!) and, to top it off, it's often considered a *game for nerds*. If, despite that, you want to learn how to play, I recommend the computer version, [*MTG Arena*](https://magic.wizards.com/es/mtgarena), which is freemium, fully playable and has an excellent tutorial.

### The science behind MTG
It has recently been [proven](https://arxiv.org/abs/1904.09828) that **MTG is Turing-complete**. A system is Turing-complete when it can be used to simulate any **Turing machine**. Or, in other words, a Turing-complete system can solve any computational algorithm. So, MTG can be used to *program* things!

But let's take it step by step. Turing machines, proposed by the mathematician **Alan Turing** in 1936, are a class of **automata** able to take a program, run that program and show some result. A Turing machine is made up by four components:

1. an infinite one-dimensional **tape** divided into squares;
2. a finite alphabet of **symbols** for the tape;
3. a tape scanner with a finite number of **states**; and
4. a finite **instruction table** that tells what to do with each combination of scanner state and tape symbols.

This is how it works: the machine positions its tape scanner over a square on the tape and *reads* the symbol written on it. Then, based on the symbol read and the state of the tape scanner, the machine looks in the instruction table for

1. which new symbol to write in the square;
2. whether to move the tape one square to the left or to the right; and
3. whether to change the scanner state or stop (halt) the process.

If the process has not halted, the tape scanner reads the current square and so on.

With these simple rules it is possible to run any conceivable algorithm. However, the instruction table may not necessarily be easy to find, and the number of steps required to reach a result may not necessarily be small. [This website](https://turingmaschine.klickagent.ch/einband/?&lang=en#__) illustrates step by step how some Turing machines compute simple operations between numbers. For example, [multiplying 3 by 4](https://turingmaschine.klickagent.ch/einband/?&lang=en#3_*_4) using a 2-symbol, 17-state machine requires 261 steps!